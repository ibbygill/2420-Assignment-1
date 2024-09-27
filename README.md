# 2420-Assignment-1
#### Quick Tutorial of Creating a Remote Server using DigitalOcean

Welcome to this full tutorial on setting up a remote Arch Linux server using [DigitalOcean](https://www.digitalocean.com/). This guide will walk you through generating SSH Keys, adding a custom Arch Linux image, and creating a DigitalOcean Droplet running Arch Linux. By the end you'll be able to have a functional running server, and understand concepts that make it secure and efficient.

____________________________

## Table of Contents

1. [Understanding SSH Keys](#understanding-ssh-keys)
2. [Generating SSH Keys](#generating-ssh-keys)
3. [Downloading Arch Linux](#downloading-arch-linux)
4. [Uploading Arch Linux Image to DigitalOcean](#uploading-arch-linux-image-to-digitalocean)
5. [Adding SSH Keys to DigitalOcean](#adding-ssh-keys-to-digitalocean)
6. [Creating a Droplet Running Arch Linux](#creating-a-droplet-running-arch-linux)
7. [Connecting to Your Droplet](#connecting-to-your-droplet)
8. [References](#references)


_____________

## Understanding SSH Keys
#### What are SSH Keys?

Secure Shell (SSH) is used to set up a secure connection between a device and server over an unsecure network. These SSH Keys resemble passwords they give you access and control over your system. We will be using these SSH Keys that we create to add them to our Droplet.  

> [!Note]
> A droplet is the a name that DigitalOcean uses for a virtual private server (vps). Using DigitalOcean we are able to rent a server making it very affordable for most cases.

#### Why we use SSH over Password Authentication

- ##### **Security**
	- SSH incorporates a process of encryption and authentication together. This process is called ***Cryptography***
	- SSH keys function through a cryptographic protocols where the private key never leaves the user's machine.
	- SSH keys are effectively unguessable, unlike passwords which are vulnerable to guessing and brute force attacks (Barrett, Silverman, & Byrnes, 2005).


________________________________________________________________

## Generating SSH Keys

The next steps will showcase how to generate a new SSH key pair on your local machine. We are creating SSH Keys to provide a more secure and efficient method of authentication as explained above.  This will be used to establish a connection between your machine and the remote server we will create on DigitalOcean.

#### Step 1: Open Terminal
1. On my local machine, I run Windows therefore I use GitBash or PowerShell

> [!Note]
> You may have to create a .ssh directory in your home directory. 
> `~` = home directory

#### Step 2: Run Commands

1. Use the following command to create SSH keys for your DigitalOcean Droplet:

```powershell
ssh-keygen -t ed25519 -f ~/.ssh/do-key -C "your_email@example.com"
```

##### Explaining Commands - 

- **`ssh-keygen`**: This is used to generate SSH key pairs.
-  **`-t`**: option specifies the type of key to generate, such as RSA or ed25519 (Barrett, Silverman, & Byrnes, 2005). We use the ed25519 keys because they are considered to be more secure than others.
- **`-f`**: This is used to specify the **file name** for storing the SSH keys. We use it to set a custom file name and path to avoid overwriting existing keys (Barrett, Silverman, & Byrnes, 2005). Here we stored it in our `.ssh` path as `do-key`
- **`-C`**: Allows you to embed a comment in the public key file. (Barrett, Silverman, & Byrnes, 2005)

#### Step 3: Verify

1. After creating the SSH Key, you will should have **Two** keys the **`do-key`** and a **`do-key.pub`**. The **`do-key`** will be your private key, the public key which will be copied to your server is the      **`do-key.pub`**. 
2. **`do-key`** should be saved to your local machine
3. **`do-key.pub`** will be uploaded to **DigitalOcean** 

## Downloading Arch Linux

It allows you to deploy operating systems that are not native by DigitalOcean. We use Arch Linux because it is designed with simplicity and customizability in mind. They have a philosophy of KISS "Keep It Simple Stupid", creating a system which is avoids complexity and allows the user to have full control (Arch Linux Wiki, n.d.).

### Arch Linux Image

Visit [Arch Linux Image](https://gitlab.archlinux.org/archlinux/arch-boxes/-/packages/1545) once you are there, be sure to select the file extension with .qcow2 it can be found at the bottom with a rough **Size** of 450 MiB. Once that is downloaded, we can move onto the next step of creating a droplet in DigitalOcean.
![](Assets/Screenshot%202024-09-24%20125125.png)


## Uploading Arch Linux Image to DigitalOcean
Now we are going to create a droplet on DigitalOcean, with the Arch Linux image we downloaded, with this droplet

1. **Click** on the Create button at the top of your screen![](Assets/Screenshot%202024-09-26%20165047.png)
2. . **Click** on the Droplets button ![](Assets/Screenshot%202024-09-26%20165115.png)
3. **Select** *San Francisco* as your region
4. Scroll down to Choose an image section, **Click** on Custom images ![](Assets/Screenshot%202024-09-26%20170723.png)
5. **Click** on Upload Image button which will be located in your downloads folder ![](Assets/Screenshot%202024-09-26%20171016.png)
6. Here you will select the **Distribution** Arch Linux
7. You will choose **San Francisco** datacenter region and **select** option 3![](Assets/Screenshot%202024-09-26%20173119.png)
8. Leave the tags and notes section empty and **Click** on Upload Image![](Assets/Screenshot%202024-09-26%20173228.png)
9. Your page should look similar to this after you have uploaded the Arch Linux image ![](Assets/Screenshot%202024-09-26%20173336.png)


## Adding SSH Keys to DigitalOcean

## Creating a Droplet Running Arch Linux

You are now going to create a droplet after uploading the image. We are going to use SSH as the authentication method. 

> [!Note]
> Confirm you have uploaded the Arch Linux Image before moving to the next step.

1. 

## References

Barrett, D. J., Silverman, R. E., & Byrnes, R. G. (2005). _SSH, The Secure Shell: The Definitive Guide_ (2nd ed.). O'Reilly Media.
Arch Linux Wiki. (n.d.). _Arch Linux_. https://wiki.archlinux.org/title/Arch_Linux
DigitalOcean. (n.d.). _How to choose a data center location for your business_. DigitalOcean. https://docs.digitalocean.com/products/networking/regions/


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