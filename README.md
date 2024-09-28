# Assignment01

## Tutorial
Hello, we will be doing a tutorial on how to do Arch linux set up through DigitalOcean

- [Create a ssh key on your windows powershell](#Create-a-ssh-key-on-your-windows-powershell)
- [Download a custom Arch linux](#Download-a-custom-Arch-linux)
- [Add your public key to your DigtialOcean account!](#Add-your-public-key-to-your-DigtialOcean-account!)
- [Droplet creation](#Droplet-creation)
- [Now connect to your droplet](#Now-connect-to-your-droplet)

## Create a ssh key on your windows powershell 
It's also important to download the ssh-keygen util for your MacOS or Windows machine.
Also create a .ssh directory file in your home directory first before you implement your ssh key

Here are the steps to make a .ssh directory, on your terminal, type:
```
cd ~
``` 
Now type this command to create the directory
```
mkdir .ssh
```


After that, here is what you should type to create new .ssh key,
```
ssh-keygen -t ed25519 -f ~/.ssh/do-key -C "your email address"
```
example: ssh-keygen -t ed25519 -f ~/.ssh/do-key -C "wchoi53@my.bcit.ca"

If it doesn't work, use the full path instead,
```
ssh-keygen -t ed25519 -f C:\Users\your-user-name\.ssh\do-key -C "youremail@email.com"
```
example: ssh-keygen -t ed25519 -f C:\Users\woosu\ .ssh\do-key -C "wchoi53@my.bcit.ca"

-t: stands for "type", this refers to the method used to encrypt the key.

-f: stands for "filename", it Indicates the file name and where it's stored.

-C: stands for "comment", it adds a note to a key.

do-key: private key

do-key pub: public key

---------------
## Download a custom Arch linux 
To download a custom Arch linux image, click the url below which will direct you to the website.
https://gitlab.archlinux.org/archlinux/arch-boxes/-/packages/
You're going to need the most recent one, so click the top one (images)
![Screenshot 2024-09-27 102809](https://github.com/user-attachments/assets/fccbe8f5-2bd3-442b-8e9b-3d22c908f079)
Then, scroll down and look for the name that ends with .qcow2 (Remember to choose the most recent one!) here's an example of what it suppose to look like, 
![Screenshot 2024-09-27 102809](https://github.com/user-attachments/assets/fccbe8f5-2bd3-442b-8e9b-3d22c908f079)
Once you found it, click on it and download it.


## Add your public key to your DigtialOcean account!
after you have it set up the key pair, you need to add your public key to your DigitalOcean account! 
If you do not have a DigitalOcean account, make one right now

Before that, copy the code (for Powershell users) below and then open your vscode.
```
Get-Content C:\Users\your-user-name\.ssh\do-key.pub | Set-Clipboard
```
MacOS users
```
pbcopy < ~/.ssh/do-key.pub
```

Since the key is a plain text file, you can open it in VSCode and copy it like any other text. Or, use terminal commands to copy the file contents directly to your clipboard.

Once you get on to your DigitalOcean account, go to "Settings," then "Security." Click "Add SSH Key," paste your public key, and name it. This helps identify keys from different devices, name it however you like but I would recommand to make the name simple like for example, "Happy-2420"



## Droplet creation 
Now it's time to create a droplet, head to your DigitalOcean account and if you look to your top right you'll see the "Create" button that is in coloured, green. Click on it and you'll see a list of options and I want you to find and click on, "Droplets". 

Here are the instructions you need to do, 

1. For the region part, choose San Francisco
2. The Datacenter click on, San Francisco - Datacenter 3 - SF03
3. For Choose an image, click on "Custom Images" and find your own Arch linux image. Note, it should be the only option to choose for Arch Linux
4. For sizes, just leave it as basic
5. Then for CPU options, the best I would recommand would be under Premium AMD, the $7 option.
6. Choose Authentication Method, click on the SSH Key, and you should choose the key that you added to your DigitalOcean account recently
7. After that, scroll down to look for Hostname, and  change the name to your liking, but make it shorter like BCIT for example. The name you chose will show up in your command line when you're logged into your server.
![Example Image](102809.png)
8. After all that, leave the rest you did not do as default.


## Now connect to your droplet
Once you've created a droplet, connect to it using SSH.
```
ssh -i .ssh/do-key arch@your-droplets-ip-address
```
example: ssh -i .ssh/do-key arch@209.38.132.111

You can find your IP by going to your named project and then clicking on Resources. The image shown below is what it looks like, 
![Example Image](103834.png)

-i: stands for identity_file 

arch: your username.

Now you're done! To get out of terminal, just type, 
```
exit
```
