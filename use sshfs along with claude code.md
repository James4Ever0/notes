---
created: 2026-03-26T17:59:18+08:00
modified: 2026-03-27T11:25:40+08:00
---

# use sshfs along with claude code

https://zhuanlan.zhihu.com/p/714003462

```bash
# mount fs in foreground
sshfs <user>@<hostname>:<source_path> <dest_path> -d -v
```

---
# LINUX：使用SSHFS挂载远程目录

SSHFS 使用安全加密将远程目录挂载到本地机器，连接比标准 FTP 安全得多。

> 译自：[Linux: Mount Remote Directories With SSHFS](https://example.com)，作者 Jack Wallen。

Secure Shell(SSH) 不仅仅是让你远程登录服务器来处理管理任务。借助这个安全的网络协议，你还可以借助 SSH 文件系统 (SSHFS) 挂载远程目录。

SSHFS 使用 SFTP（SSH 文件传输协议）通过安全的加密将远程目录挂载到本地机器，这意味着连接比你的标准 FTP 安全得多。此外，一旦远程目录被挂载，它就可以像本地机器上的目录一样使用。

可以将 SSHFS 视为一种更安全的方式来创建网络共享，唯一的区别是，你需要在任何需要连接到共享的机器上安装 SSHFS（而使用 Samba，你只需要在托管共享的机器上安装它）。

让我们一起了解如何设置 SSHFS 并运行它，这样你就可以安全地将远程目录挂载到你的本地机器。

## 你需要什么

要使此方法生效，你需要至少两台 Linux 机器。这些机器可以是 Ubuntu 或基于 Fedora 的，因为 SSHFS 在大多数 Linux 发行版的标准存储库中都可以找到。你还需要一个具有 sudo 权限的用户。

## 安装 SSHFS

由于 SSHFS 在标准存储库中可以找到，因此安装非常简单。登录到服务器（将托管要共享的目录）并使用以下命令之一安装 SSHFS：

- **基于 Ubuntu 的发行版**  
  ```bash
  sudo apt-get install sshfs -y
  ```

- **基于 Fedora 的发行版**  
  ```bash
  sudo dnf install fuse-sshfs -y
  ```

- **基于 Arch 的发行版**  
  ```bash
  sudo pacman -S sshfs
  ```

- **基于 openSUSE 的发行版**  
  ```bash
  sudo zypper -n in sshfs
  ```

接下来，登录到你的本地机器并安装该软件包。

安装完成后，你需要在本地机器上的 SSHFS 配置文件中设置 `user_allow_other`。为此，使用以下命令打开该文件：

```bash
sudo nano /etc/fuse.conf
```

在该文件中，找到以下行：

```plaintext
#user_allow_other
```

将其更改为：

```plaintext
user_allow_other
```

保存并关闭该文件。

## 创建用于挂载的目录

回到服务器，我们必须创建一个将在客户端机器上挂载的目录。我们将使用以下命令将新目录放在 `/srv` 中：

```bash
sudo mkdir /srv/data
```

创建新目录后，我们需要授予它所有权，以便用户或组可以访问它。如果你只有一个用户需要访问它，你可以使用以下命令更改所有权：

```bash
sudo chown -R USERNAME:USERNAME /srv/data
```

如果你想允许多个用户访问该目录，你需要先使用以下命令创建一个组：

```bash
sudo groupadd GROUP
```

其中 `GROUP` 是新组的名称。

接下来，使用以下命令将必要的用户添加到该组（一次添加一个）：

```bash
sudo usermod -aG GROUP USERNAME
```

其中 `GROUP` 是组的名称，`USERNAME` 是要添加的用户的名称。

然后，你需要使用以下命令将新目录的所有权更改为新组：

```bash
sudo chown -R USERNAME:GROUP /srv/data
```

在本地机器上，你需要创建一个目录来存放挂载的远程目录。我们将使用以下命令在用户的 home 目录中创建它：

```bash
mkdir ~/data_mount
```

## 挂载目录

现在是时候挂载我们的远程目录了。请记住，我们将远程目录 `/srv/data` 挂载到本地目录 `~/data_mount`。这可以通过以下命令完成：

```bash
sshfs USER@SERVER:/srv/data ~/data_mount
```

其中 `USER` 是远程用户名，`SERVER` 是远程服务器的 IP 地址。系统会提示你输入远程用户的密码。身份验证成功后，远程目录将被挂载到本地目录，你可以像访问本地机器上的目录一样访问它。如果你在 `~/data_mount` 中保存或编辑文件，它将在远程机器上的 `/srv/data` 中反映出来。
