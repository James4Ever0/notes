---
tags: [p2p, remote control, sync]
title: 'Reverse Proxy Free Frp Providers, Remote Code Editing, Remote Development'
created: '2022-08-04T15:49:02.000Z'
modified: '2022-12-22T14:12:43.595Z'
---

# Reverse Proxy Free Frp Providers, Remote Code Editing, Remote Development

if you install p2p server nodes on primary server (with hard-to-crack password and proper configs (no brute-forcing)?) you might want to add that (n2n) server node at home.

## p2p network

[nps](https://github.com/ehang-io/nps/) also supports p2p

(deprecated! does not pass the connectivity test) [opengnb](https://github.com/gnbdev/opengnb) p2p network, faster than n2n v3, can run without public ip

[gost](https://github.com/ginuerzh/gost) as an frp alternative

turned out n2n is necessary, since the speed comparasion strongly disencourage the usage of frp directly.

n2n test commands, using compatible v3 protocol to communicate:

supernode v3: n2n.laiyx.win:10090

warning: it is useless to add multiple supernodes.

```
-l nton.eu.org:10090 -l n2n.lu8.win:10090 -l n2n.haoren.eu.org:10090 -l 	
supernode.ntop.org:7777 -l 47.102.102.77:10090 -l n2n.myan.cc:10090 -l n2n.sfcs.eu.org:10090 -l n2n.eriol.cn:10090 -l n2n.x0x.cn:10090 -l n2n.vvcd.win:10090
```

kali:
```bash
sudo edge -c <name> -k <password> -a 192.168.100.1 -f -l n2n.laiyx.win:10090 -Er -A3 -e auto
```

macos, since we use sudo you might consider doing it with system service:
```bash
sudo edge -c <name> -k <password> -a 192.168.100.2 -f -l n2n.laiyx.win:10090 -Er -A3 -e auto
```

[public shared n2n supernodes](http://www.supernode.ml/)

you could test the speed and decide to use it or not.

in kali discovery service, when local connection is not avaliable, usually the p2p network is preferred than direct frp tunneling.

brew has [tinc](https://www.xmodulo.com/how-to-install-and-configure-tinc-vpn.html) as a package!

[tinc conf](https://tinc-vpn.org/documentation/tinc.conf.5)

[tinc setup with core server](https://chanix.github.io/TincCookbook/examples/1-HowToInstallTincOnUbuntu1604.html)

[remote access with vps using tinc](https://zhuanlan.zhihu.com/p/419173153)

[install and config tinc on linux](https://www.xmodulo.com/how-to-install-and-configure-tinc-vpn.html)

tinc is somehow complex and it may requires some tinkering on `tinc-up` or using docker.

[install n2n without macports](https://www.jianshu.com/p/559c1e582724)

use [n2n](https://github.com/ntop/n2n) to send udp packages among clients, try to create direct link between devices which will speed up ssh connection speed. supernode creation could be used along with frpc

somehow brew does not have n2n as a package. macports has it, which requires xcode (huge!) to be installed.

[peervpn tutorial](https://peervpn.net/)

## daemonize (launch at startup)

on macos, when crontab is created, cron will be automatically launched by launchd.

cronjobs may need to launch with the `$(which env)` prefix.

the problem of internet disconnetion will most not likely to interfere with the server since frpc has auto reconnection and the update hook is the filesystem watchdog, which will not run when no changes made (including the offline period)

the watchdog may be replaced by some mirror fuse system, which will report every access request to our dedicated server.

we have seen this behavior (filesystem mirroring) in our gitfuse code. but does that support symlink? should we really take care of that? or should we forget that and just use inotify instead?

maybe it will affect the client when mounting the remote filesystem using sshfs or rclone, but that has to be verified.

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

to mount the filesystem via sshfs:

```bash
sshfs root@192.168.10.4:/media/root/help/pyjom /Volumes/CaseSensitive/pyjom_remote_mountpoint -o follow_symlinks
```

to make sure the changes are updated regularly, we need a filesystem watchdog on kali, which will trigger the action of syncing, utilizing inotify. shall that be adopted on macos? maybe. but my extra editors can be vim or nvim, so it is not so hard to predict. but if it can monitor the file read events, we don't need those legacy editor program hooks.

at least we need to see the output, so we need to mount the remote filesystem as sshfs, then use ffplay to view it.

## solution

for now, two viable ways:

one using code-server, the other using code-server-insider provided by code-insider. when using builtin code-server-insider, remember it will not share the plugins installed by code-insider. the remote executable location is at `/root/.vscode-server-insiders/bin/12b08be500f8a307f30e92cbc3ee39ba115eab69/bin/code-server-insider` or something. must set the local setting `remote.SSH.useLocalServer` to false.

when using code-server, one can connect to the workspace using browser, instead of vscode builtin remote connector.
