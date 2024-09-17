---
title: Cursor AI IDE open source alternative
created: '2024-09-16T14:08:08.582Z'
modified: '2024-09-17T05:30:42.858Z'
---

# Cursor AI IDE open source alternative

https://github.com/meltylabs/melty

https://github.com/yetone/avante.nvim

---
If you use `lazy.nvim` to install `avante.nvim`, the `<leader>` key would be whitespace.

To make `avante.nvim` compatible with local models, you have to modify the code under `~/.local/share/nvim/lazy/avante.nvim/lua/avante/providers/openai.lua`:

```lua
local Utils = require("avante.utils")
local Config = require("avante.config")
local Clipboard = require("avante.clipboard")
local P = require("avante.providers")

---@class OpenAIChatResponse
---@field id string
---@field object "chat.completion" | "chat.completion.chunk"
---@field created integer
---@field model string
---@field system_fingerprint string
---@field choices? OpenAIResponseChoice[]
---@field usage {prompt_tokens: integer, completion_tokens: integer, total_tokens: integer}
---
---@class OpenAIResponseChoice
---@field index integer
---@field delta OpenAIMessage
---@field logprobs? integer
---@field finish_reason? "stop" | "length"
---
---@class OpenAIMessage
---@field role? "user" | "system" | "assistant"
---@field content string
---
---@class AvanteProviderFunctor
local M = {}

M.api_key_name = "OPENAI_API_KEY"

---@param opts AvantePromptOptions
M.get_user_message = function(opts) return table.concat(opts.user_prompts, "\n") end

M.parse_message = function(opts)
  ---@type OpenAIMessage[]
  local user_content = {}
  if Config.behaviour.support_paste_from_clipboard and opts.image_paths and #opts.image_paths > 0 then
    for _, image_path in ipairs(opts.image_paths) do
      table.insert(user_content, {
        type = "image_url",
        image_url = {
          url = "data:image/png;base64," .. Clipboard.get_base64_content(image_path),
        },
      })
    end
    vim.iter(opts.user_prompts):each(function(prompt) table.insert(user_content, { type = "text", text = prompt }) end)
  else
    user_content = vim.iter(opts.user_prompts):fold({}, function(acc, prompt)
      table.insert(acc, { type = "text", text = prompt })
      return acc
    end)
  end

  ret = {
    { role = "system", content = opts.system_prompt },
  }
  vim.iter(user_content):each(function(content) table.insert(ret, { role = "user", content = content.text }) end)
  return ret
end

M.parse_response = function(data_stream, _, opts)
  if data_stream:match('"%[DONE%]":') then
    opts.on_complete(nil)
    return
  end
  if data_stream:match('"delta":') then
    ---@type OpenAIChatResponse
    local json = vim.json.decode(data_stream)
    if json.choices and json.choices[1] then
      local choice = json.choices[1]
      if choice.finish_reason == "stop" then
        opts.on_complete(nil)
      elseif choice.delta.content then
        if choice.delta.content ~= vim.NIL then opts.on_chunk(choice.delta.content) end
      end
    end
  end
end

M.parse_curl_args = function(provider, code_opts)
  local base, body_opts = P.parse_config(provider)

  local headers = {
    ["Content-Type"] = "application/json",
  }
  if not P.env.is_local("openai") then headers["Authorization"] = "Bearer " .. provider.parse_api_key() end

  return {
    url = Utils.trim(base.endpoint, { suffix = "/" }) .. "/chat/completions",
    proxy = base.proxy,
    insecure = base.allow_insecure,
    headers = headers,
    body = vim.tbl_deep_extend("force", {
      model = base.model,
      messages = M.parse_message(code_opts),
      stream = true,
    }, body_opts),
  }
end

return M
```
