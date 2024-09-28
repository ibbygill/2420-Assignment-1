# 2420-Assignment-1
#### Quick Tutorial of Creating a Remote Server using DigitalOcean

Welcome to this full tutorial on setting up a remote Arch Linux server using [DigitalOcean](https://www.digitalocean.com/). This guide will walk you through generating SSH Keys, adding a custom Arch Linux image, and creating a DigitalOcean Droplet running Arch Linux. By the end you'll be able to have a functional running server, and understand concepts that make it secure and efficient. Also includes installing DOCTL and installing a droplet only using the command line, **BEWARE** *its hard*

____________________________

## Table of Contents

1. [Understanding SSH Keys](#understanding-ssh-keys)
2. [Generating SSH Keys](#generating-ssh-keys)
3. [Downloading Arch Linux](#downloading-arch-linux)
4. [Creating a New Project in DigitalOcean](#creating-a-new-project-in-digitalocean)
5. [Uploading Arch Linux Image to DigitalOcean](#uploading-arch-linux-image-to-digitalocean)
6. [Adding SSH Keys to DigitalOcean](#adding-ssh-keys-to-digitalocean)
7. [Creating a Droplet Running Arch Linux](#creating-a-droplet-running-arch-linux)
8. [Creating a Droplet Running Arch Linux Using DOCTL](#creating-a-droplet-running-arch-linux-using-doctl)
9. [References](#references)


_____________

## Understanding SSH Keys
#### What are SSH Keys?

Secure Shell (SSH) is used to set up a secure connection between a device and server over an unsecure network. These SSH Keys resemble passwords they give you access and control over your system. We will be using these SSH Keys that we create to add them to our Droplet.  

> [!Note]
> A droplet is the a name that DigitalOcean uses for a virtual private server (vps). Using DigitalOcean we are able to rent a server making it very affordable for most cases.

#### Why we use SSH over Password Authentication

- ##### **Security**
	- SSH incorporates a process of encryption and authentication together. This process is called ***Cryptography***
	- SSH keys function through a cryptographic protocols where the private key never leaves the user's machine (Barrett, Silverman, & Byrnes, 2005).
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

##### Explaining Commands 

- `ssh-keygen`: This is used to generate SSH key pairs.
-  `-t`: option specifies the type of key to generate, such as RSA or ed25519 (Barrett, Silverman, & Byrnes, 2005). We use the ed25519 keys because they are considered to be more secure than others.
- `-f`: This is used to specify the **file name** for storing the SSH keys. We use it to set a custom file name and path to avoid overwriting existing keys (Barrett, Silverman, & Byrnes, 2005). Here we stored it in our `.ssh` path as `do-key`
- `-C`: Allows you to embed a comment in the public key file. (Barrett, Silverman, & Byrnes, 2005)

#### Step 3: Verify

1. After creating the SSH Key, you will should have **Two** keys the **`do-key`** and a **`do-key.pub`**. The `do-key` will be your private key, the public key which will be copied to your server is the      `do-key.pub`. 
2. `do-key` should be saved to your local machine
3. `do-key.pub` will be uploaded to **DigitalOcean** 

## Downloading Arch Linux

It allows you to deploy operating systems that are not native by DigitalOcean. We use Arch Linux because it is designed with simplicity and customizability in mind. They have a philosophy of KISS "Keep It Simple Stupid", creating a system which is avoids complexity and allows the user to have full control (Arch Linux Wiki, n.d.).

### Arch Linux Image

Visit [Arch Linux Image](https://gitlab.archlinux.org/archlinux/arch-boxes/-/packages/1545) once you are there, be sure to select the file extension with .qcow2 it can be found at the bottom with a rough **Size** of 450 MiB. Once that is downloaded, we can move onto the next step of creating a droplet in DigitalOcean.
![](Assets/Screenshot%202024-09-24%20125125.png)

## Creating a New Project in DigitalOcean
This project will be used when creating a droplet, you will have to select a project fthat you are working on.

1. In the Top Right of the screen. Click **+ New Project**                                                                        ![](Assets/Screenshot%202024-09-26%20190432.png)
2. Type the name of the **Project**, I entered `fkey-project`
3. Select the purpose as **Class Project / Educational Purposes** 
4. Click on **Create Project**                                                                                                                    ![](Assets/Screenshot%202024-09-26%20190615%201.png)

You have created your project, you can move onto the next step.


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
Steps to add SSH Keys to DigitalOcean to provide a more efficient and secure way of accessing our Droplet that we will create later. 

1. On the side navigation bar **Click** on the settings tab                                                                    
![](Assets/Screenshot%202024-09-26%20175403.png)
2. **Click** on the security tab
3. **Click** on the Add SSH Key button ![](Assets/Screenshot%202024-09-26%20175608.png)
4. Next we are going to open up Windows PowerShell to get our **public key**
 - For Windows users, in PowerShell use the following command
		 ``Get-Content C:\Users\your-user-name\.ssh\do-key.pub | Set-Clipboard``
-  For MacOS users, in the Terminal use the following command
		 `pbcopy < ~/.ssh/do-key.pub`
-  For Linux users, in the Terminal use the following command
		 ``wl-copy < ~/.ssh/do-key.pub`` 

5. **Paste** the contents of your public key into the "SSH Key content" box
6. **Type** Key Name in our case we will be using `fkey` it can be anything, it is just to differentiate multiple keys
7. Once completed, this key will automatically be copied to the droplet that we are going to create
## Creating a Droplet Running Arch Linux

You are now going to create a droplet after uploading the image.

> [!Note]
> Confirm you have uploaded the Arch Linux Image before moving to the next step.

1. Click **Create** and select **Droplets** from the Dropdown Menu ![](Assets/Screenshot%202024-09-26%20184042.png)
2. Click **San Francisco** as your Region, and Select **Datacenter 3 SFO3** for the Datacenter option ![](Assets/Screenshot%202024-09-26%20184307%201.png)
3. Click **Custom Images** and select the **Arch Linux** image we added previously ![](Assets/Screenshot%202024-09-26%20184737.png)
4. Select **Basic** for the Droplet Type
5. Select **Premium AMD** or **Premium Intel** and the lowest monthly option for this scenario![](Assets/Screenshot%202024-09-26%20185002.png)
6. Move down to **Choose Authentication Method** select your **SSH Key** ![](Assets/Screenshot%202024-09-26%20185449.png)
7. Click on **Advance Options**![](Assets/Screenshot%202024-09-27%20151057%201.png)
8. **Add Initialization scripts (free)** should be selected ![](Assets/Screenshot%202024-09-27%20151106.png)
9. Type the following into the `Enter user data here...` 

   ```shell
#cloud-config
users:
  - name: ibby
    ssh-authorized-keys:
      - ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAINsTV4MWsTql7pSe+5ELl9s02Hb85rYegWtSGVsVOc1J ibjyot@gmail.com
    sudo: ['ALL=(ALL) NOPASSWD:ALL']
    groups: sudo
    shell: /bin/bash
packages:
    neovim
    fd
disable_root: true```

Explaining Commands - 

- `#cloud-config` The #cloud-config header indicates that the file contains instructions for system initialization (Cloud-init Documentation, n.d.)
- `users`: The users: section is to create a new user and configure their settings, here we added our name, included our .public key from the fk-key.pub file (Barrett & Silverman, 2005)
- `sudo:` gives full sudo privileges without entering a password (Barrett & Silverman, 2005).
- `packages:` here we initialize the software packages that will be installed during the boot of this instance
- `newvim` installs the vim text editor so we can insert and delete text (Neovim Documentation, n.d.).
- `fd` installs the fd package which is a more modern version of `find` to search for files and directories quicker
- `disable_root: true` this setting disables the login from the root, to reduce cyber attacks on our server (Nemeth et al., 2017)

10. Now under **Hostname** give your droplet a name that you can remember it by `fkey` is what I named it ![](Assets/Screenshot%202024-09-26%20191413.png)
11. Finally, click on **Create Droplet**
12. It should take you to a new page, where the droplet is loading ![](Assets/Screenshot%202024-09-26%20191603.png)
13. After loading, you will copy the IP address by hovering over it and clicking. 
	- The IP address will be used to connect via SSH
14. Open up Windows Powershell to connect to your live droplet
15. Type ``ssh -i .ssh/do-key arch@your-droplets-ip-address`` to connect to the droplet
	  - `-i` is the path that we give to our private key
	  - `arch` the image that we used contains a regular user named "arch"
16. Type `yes` to confirm the droplet
17. You will now be logged in it                                                               ![](Assets/Screenshot%202024-09-27%20150927.png)
18. We can now confirm if `#cloud-config` automatically installed our packages
19. Type `fd --version` and `nvim --version` you should see the following
    ![](Assets/Screenshot%202024-09-27%20154239%201.png)
Congratulations! You have successfully completed the install using the Arch Linux Image.

## Creating a Droplet Running Arch Linux Using DOCTL

> [!NOTE]
> ##### Complete SSH Keys creation and Arch Linux Image download before beginning this step
> -------------------------------------------------------
> Here we are going to use doctl a `command-line tool` to create the a Arch Linux droplet

To start this tutorial lets, install doctl using `winget`, winget is a command that is apart of Windows Package Manager. With this you can install packages straight from the command line. 

1. Install doctl using the following command `winget install DigitalOcean.Doctl` ![](Assets/Screenshot%202024-09-27%20221053.png)
3. Next we will need to generate a DigitalOcean API Key.
4. On the main dashboard of DigitalOcean navigate to the left bar, click **API**
5. Click **Generate New Token** button to create an API token![](Assets/Screenshot%202024-09-27%20215505.png)
6. In the next screen, type a **Token Name**
7. Move down to **Quick Bulk Scope Select** and select **Creates, Updates, Reads, and Deletes** ![](Assets/Screenshot%202024-09-27%20215921.png)
8. Then click **Generate Token** at the bottom in green
9. Save the **Token** somewhere save on your local machine 

> [!Caution]
> Confirm you have saved the **Token** as you will not be able to view it again after leaving this page

8. Next we want to follow the steps in [Creating a Droplet Running Arch Linux](#creating-a-droplet-running-arch-linux) guide above and get to the step below
9. Next to the button Create Droplet click **Create Via Command Line** ![](Assets/Screenshot%202024-09-27%20214519.png)
10. Where it says select a library click **doctl** because we will be using this to create our droplet this time around.
11. You should be prompted with information such as the image id, size, region, etc. ![](Assets/Screenshot%202024-09-27%20214835.png)
12. **Copy** it and save it, we will need it soon
13. Next we will run the doctl authentication command, run `doctl auth init` in the command line
14. Here enter the **API TOKEN** that you have saved![](Assets/Screenshot%202024-09-27%20222418.png)
15. Now type in `doctl compute ssh-key list` ![](Assets/Screenshot%202024-09-27%20222719.png)
16. Copy the **FingerPrint** for the correct SSH Key, in this case fkey
17. Next we will start the server using doctl take the command from step 11  and at the end add `--ssh-keys e9:dd:f9:69:d1:b7:f5:ac:9d:c9:e7:1f:fb:4c:02:55 fkey-test` which selects the correct FingerPrint and give it a name, here I gave it fkey-test ![](Assets/Screenshot%202024-09-27%20213215.png)
18. You can run `doctl compute droplet list` in the command line, to show the list of your created droplets ![](Assets/Screenshot%202024-09-27%20223509.png)
19. Congratulations, you have now created a droplet using the doctl command line


## References

Barrett, D. J., Silverman, R. E., & Byrnes, R. G. (2005). _SSH, The Secure Shell: The Definitive Guide_ (2nd ed.). O'Reilly Media.
Arch Linux Wiki. (n.d.). _Arch Linux_. https://wiki.archlinux.org/title/Arch_Linux
DigitalOcean. (n.d.). _How to choose a data center location for your business_. DigitalOcean. https://docs.digitalocean.com/products/networking/regions/
Cloud-init Documentation. (n.d.). _User Data and Cloud-init_ https://cloudinit.readthedocs.io/en/latest/topics/format.html
Neovim Documentation. (n.d.). _Introduction to Neovim_. https://neovim.io/
Nemeth, E., Snyder, G., & Hein, T. R. (2017). _UNIX and Linux System Administration Handbook_ (5th ed.). Pearson Education.
Microsoft. (n.d.). _Windows Package Manager (winget)_. [https://docs.microsoft.com/en-us/windows/package-manager/](https://docs.microsoft.com/en-us/windows/package-manager/)


> [!NOTE]
> Information the user should notice even if skimming.

> [!TIP]
> Optional information to help a user be more successful.

