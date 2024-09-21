# 2420-Assignment-1
#### Quick Tutorial of Creating a Remote Server using DigitalOcean

Welcome to this full tutorial on setting up a remote Arch Linux server using [DigitalOcean](https://www.digitalocean.com/).  This guide will walk you through generating SSH Keys, adding a custom Arch Linux image, and creating a DigitalOcean Droplet running Arch Linux. By the end you'll be able to have a functional running server, and understand concepts that make it secure and efficient.

____________________________

## Table of Contents

1. [Understanding SSH Keys](#understanding-ssh-keys)
2. [Generating SSH Keys](#generating-ssh-keys)
3. [Downloading Arch Linux](#downloading-arch-linux)
4. [Adding SSH Keys to Your DigitalOcean Account](#adding-ssh-keys-to-your-digitalocean-account)
5. [Adding a Custom Arch Linux Image](#adding-a-custom-arch-linux-image)
6. [Creating a Droplet Running Arch Linux](#creating-a-droplet-running-arch-linux)
7. [Connecting to Your Droplet](#connecting-to-your-droplet)
8. [Conclusion](#conclusion)


_____________

## SSH Keys
#### What are SSH Keys?

Secure Shell (SSH) is used to set up a secure connection between a device and server over an unsecure network. Using SSH to make the information you are sending cryptic.

#### Why we use SSH over Password Authentication

- ##### **Security**
	- SSH incorporates a process of encryption and authentication together. This process is called ***Cryptography***


________________________________________________________________

## Generating SSH Keys

The next steps will showcase how to generate a new SSH key pair on your local machine.

#### Step 1: Open Terminal
1. On my local machine, I run Windows therefore I use GitBash or PowerShell

> [!Check]
> You may have to create a .ssh directory in your home directory. 
> `~` = home directory

#### Step 2: Run Commands

1. Use the following command to create SSH keys for your DigitalOcean Droplet:

```powershell
ssh-keygen -t ed25519 -f ~/.ssh/do-key -C "your_email@example.com"
```

##### Explaining Commands

- **`ssh-keygen`**: This is used to generate SSH key pairs.
-  **`-t`**: This is used to create the ***type*** of key. ed25519 keys are considered to be more secure than others.
- **`-f`**: This is used to specify the **file name** and **path** where you want to store the SSH keys. Here we stored it in our `.ssh` path as `do-key`
- **`-C`**: This is used to create a comment, for identification purposes.

#### Step 3: Verify

1. You will be prompted to provide a file location and an optional passphrase. 
2. 

## Downloading Arch Linux
#### Why we use a Custom Image?

It allows you to deploy operating systems that are not native by DigitalOcean.

### Arch Linux Image

Visit [Arch Linux Image](https://gitlab.archlinux.org/archlinux/arch-boxes/-/packages/1545) once you are there, be sure to select the file extension with .qcow2 it can be found at the bottom with a rough **Size** of 450 MiB. Once that is downloaded, we can move onto the next step. 

- [ ] Download Arch Linux Image


> [!NOTE]
> Information the user should notice even if skimming.

> [!TIP]
> Optional information to help a user be more successful.

> [!IMPORTANT]
> Essential information required for user success.

> [!CAUTION]
> Negative potential consequences of an action.

> [!WARNING]
> Dangerous certain consequences of an action.

