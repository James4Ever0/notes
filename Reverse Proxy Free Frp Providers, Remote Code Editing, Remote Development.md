---
title: 'Reverse Proxy Free Frp Providers, Remote Code Editing, Remote Development'
created: '2022-08-04T15:49:02.034Z'
modified: '2022-08-05T13:50:09.813Z'
---

# Reverse Proxy Free Frp Providers, Remote Code Editing, Remote Development

## methods

try out [code-server](https://github.com/coder/code-server) by [coder](https://coder.com/), might work?

also we use builtin vscode connectors, using ssh.

currently we only have [one](https://www.idonglei.com/free-frp), which uses direct ip address instead of a hijacked domain. maybe it is time to consider some faster server providers.

use a universal ssh as workspace extension called [SSH FS](https://marketplace.visualstudio.com/items?itemName=Kelvin.vscode-sshfs)

## drawbacks of SSH FS extension

some drawbacks of this SSH FS plugin is that it cannot use the plugins from remote machine, also having issue whe jumping to remote files from terminal output. to run code-insider instead of code-oss, maybe we could spin up the official ssh connector, which can only be automated by publickey authentication.

## syncing, updating and viewing using watchdog and sshfs

to make sure the changes are updated regularly, we need a filesystem watchdog on kali, which will trigger the action of syncing, utilizing inotify. shall that be adopted on macos? maybe. but my extra editors can be vim or nvim, so it is not so hard to predict. but if it can monitor the file read events, we don't need those legacy editor program hooks.

at least we need to see the output, so we need to mount the remote filesystem as sshfs, then use ffplay to view it.

## solution

for now, two viable ways:

one using code-server, the other using code-server-insider provided by code-insider. when using builtin code-server-insider, remember it will not share the plugins installed by code-insider. the remote executable location is at `/root/.vscode-server-insiders/bin/12b08be500f8a307f30e92cbc3ee39ba115eab69/bin/code-server-insider` or something. must set the local setting `remote.SSH.useLocalServer` to false.

when using code-server, one can connect to the workspace using browser, instead of vscode builtin remote connector.
