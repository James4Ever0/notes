---
title: 'Reverse Proxy Free Frp Providers, Remote Code Editing, Remote Development'
created: '2022-08-04T15:49:02.034Z'
modified: '2022-08-06T14:49:50.346Z'
---

# Reverse Proxy Free Frp Providers, Remote Code Editing, Remote Development

## serve and mount remote filesystem

before serving, make sure the path `/media/root/help/pyjom` exists by running our mount script

create htpasswd file:

```bash
htpasswd -bc webdav_htpasswd <username> <password>

```

use rclone:

```bash
rclone serve webdav /media/root/help/pyjom --addr 0.0.0.0:8468 --key /root/.local/share/code-server/localhost.key --cert /root/.local/share/code-server/localhost.crt --htpasswd /root/Desktop/works/sync_git_repos/remote_deploys/webdav_htpasswd -L
```

before mounting, use `rclone config` to setup remote associated with a name. make sure the hostname is `localhost` instead of ip address to avoid certificate issues. do not install rclone from brew since it does not support fuse. instead, install from [here](https://rclone.org/downloads/)

```bash
rclone mount webdav_local_nginx:/ /Volume/CaseSensitive/pyjom_remote_mountpoint --ca-cert /Users/jamesbrown/Desktop/works/host_discovery_ssh_local_connect/certificates/localhost.crt
```
after mounting, seems zsh on macos is not working very well with macfuse. bash works. does bash/fish works with sshfs as well? maybe that will save efforts.

## encryption and invalid HTTPS certificates

use `nginx` to redirect remote server as localhost, since the host name on the certificate is localhost we cannot let chrome to trust anything other than that

```c
worker_processes auto;
error_log error.log;
events { }
stream {
  server {
    listen 127.0.0.1:7576;
    proxy_pass REMOTE_HOST:7576;
  }
}
```

## code-server(browser) color fixes

```css
.cursor{
  background: white;
}

body.web{
  caret-color: white;
}

.monaco-editor .view-line span.inline-selected-text{
  background: blue;
  color: white;
}
```

## connectors other than frp

code-server recommends [some other methods](https://coder.com/docs/code-server/latest/guide#external-authentication) like [cloudflared](https://github.com/cloudflare/cloudflared#installing-cloudflared) and [ngrok](https://dashboard.ngrok.com/login). 花生壳可能也有用 但是可能不好用

## methods

try out [code-server](https://github.com/coder/code-server) by [coder](https://coder.com/), might work?

also we use builtin vscode connectors, using ssh.

currently we only have [one](https://www.idonglei.com/free-frp), which uses direct ip address instead of a hijacked domain. maybe it is time to consider some faster server providers.

use a universal ssh as workspace extension called [SSH FS](https://marketplace.visualstudio.com/items?itemName=Kelvin.vscode-sshfs)

## drawbacks of SSH FS extension

some drawbacks of this SSH FS plugin is that it cannot use the plugins from remote machine, also having issue whe jumping to remote files from terminal output. to run code-insider instead of code-oss, maybe we could spin up the official ssh connector, which can only be automated by publickey authentication.

## syncing, updating and viewing using watchdog and sshfs(deprecated since it shares connection with vscode remote and maybe slower than rclone serve webdav?)

to make sure the changes are updated regularly, we need a filesystem watchdog on kali, which will trigger the action of syncing, utilizing inotify. shall that be adopted on macos? maybe. but my extra editors can be vim or nvim, so it is not so hard to predict. but if it can monitor the file read events, we don't need those legacy editor program hooks.

at least we need to see the output, so we need to mount the remote filesystem as sshfs, then use ffplay to view it.

## solution

for now, two viable ways:

one using code-server, the other using code-server-insider provided by code-insider. when using builtin code-server-insider, remember it will not share the plugins installed by code-insider. the remote executable location is at `/root/.vscode-server-insiders/bin/12b08be500f8a307f30e92cbc3ee39ba115eab69/bin/code-server-insider` or something. must set the local setting `remote.SSH.useLocalServer` to false.

when using code-server, one can connect to the workspace using browser, instead of vscode builtin remote connector.
