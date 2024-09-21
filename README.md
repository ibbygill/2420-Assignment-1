# 2420-Assignment-1
#### Quick Tutorial of Creating a Remote Server using DigitalOcean

Welcome to this full tutorial on setting up a remote Arch Linux server using [DigitalOcean](https://www.digitalocean.com/).  This guide will walk you through generating SSH Keys, adding a custom Arch Linux image, and creating a DigitalOcean Droplet running Arch Linux. By the end you'll be able to have a functional running server, and understand concepts that make it secure and efficient.

____________________________

## Table of Contents

1. [Prerequisites](#prerequisites)
2. [Understanding SSH Keys](#understanding-ssh-keys)
3. [Downloading Arch Linux](#downloading arch linux)
5. [Generating SSH Keys](#generating-ssh-keys)
6. [Adding SSH Keys to Your DigitalOcean Account](#adding-ssh-keys-to-your-digitalocean-account)
7. [Adding a Custom Arch Linux Image](#adding-a-custom-arch-linux-image)
8. [Creating a Droplet Running Arch Linux](#creating-a-droplet-running-arch-linux)
9. [Connecting to Your Droplet](#connecting-to-your-droplet)
10. [Conclusion](#conclusion)


_____________

## SSH Keys
#### What are SSH Keys?

Secure Shell (SSH) is used to set up a secure connection between a device and server over an unsecure network. Using SSH to make the information you are sending cryptic.

#### Why we use SSH over Password Authentication

- ##### **Security**
	- SSH incorporates a process of encryption and authentication together. This process is called ***Cryptography***


________________________________________________________________


## Downloading Arch Linux
#### Why we use a Custom Image?

It allows you to deploy operating systems that are not native by DigitalOcean.

### Step 1: Where to download Arch Linux Image

Visit [Arch Linux Image](https://gitlab.archlinux.org/archlinux/arch-boxes/-/packages/1545) once you are there, be sure to select the file extension with .qcow2 it can be found at the bottom with a rough **Size** of 450 MiB. Once that is downloaded, we can move onto the next step. 

- [ ] Download Arch Linux Image
