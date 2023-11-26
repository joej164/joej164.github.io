Title: Intro to NixOS 
Date: 2023-11-25
Category: NixOS 
Tags: Tutorial, Instructions, Setup, NixOS 

# Overview 
This is a page where I can put my notes for a tutorial on how to use the NixOS Linux Distribution.

This tutorial is going to use Virtual Box on a Windows PC.

The goals of this tutorial are to:
- Install NixOS in a Virtual Machine
- Configure the VM using the `configuration.nix` file
- Rebuild the OS with the added configurations

# Install the OS
The easiest way to get NixOS up and running is to use the [Virtual Box OVA](https://nixos.org/download#nixos-virtualbox) provided by the project.

- Make sure that [Virual Box](https://www.virtualbox.org/) is installed on your system.
- Navigate to the [NixOS Virtual Box OVA](https://nixos.org/download#nixos-virtualbox) 
- Download the OVA file.  This may take awhile as the download is 2.4GB in size.
- Follow the instructions on the NixOS Virtual Box OVA page for importing the OVA into Virtual Box.
- Once imported you should have a VM with a name similar to `NixOS 23.05.4969.1216a5ba22a9 (x86_64-linux)`
- Start the Virtual Machine.

# Find the Config File
The `configuration.nix` file by default is found in the `/etc/nixos` folder.

From the Virtual Box Terminal, log into the VM.  Username and password are in the download link above.

From the Plasma Desktop, click on the folder icon on the toolbar to launch the Dolphin file manager.  Click on the `nixos` drive.  Then click on `etc` and then `nixos` and you should see a file labeled `configuration.nix`.

# Modify the Config File
In order to modify the file, we need to use a text editor.  By default the only next editor installed is a command line tool called `nano`.

Do the following:

- Right click on the `configuration.nix` file.
- Select `Open Terminal Here` to launch the *Konsole* terminal application.
- By default you should be in the `/etc/nixos` directory.
- Type the following `sudo nano configuration.nix` to launch nano text editor.
- Using the arrow keys, navigate to the bottom of the file and look for the line beginning with `# time.timeZone`.
- Remove the `# ` from that line and update the timezone to "America/Los_Angeles" or whichever timezone you wish from the [List of Timezones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)
- Once your the line looks something like `time.timeZone = "America/Los_Angeles";` you are read to save and exit.
- Type *Ctrl-O* to save the file and *Ctrl-X* to exit out of nano.


NOTE: you have to use sudo becuase by default the file is read only and the `demo` user does not have permissions to read the file.


# Rebuild NixOS
Once changes are made to your NixOS Configuration file, we now rebuild the OS using [nixos-rebuild](https://nixos.wiki/wiki/Nixos-rebuild)

- From the command prompt type `sudo nixos-rebuild switch`.
- Wait for the OS to command to finish (about 5 minutes) and then the timezone should be updated.

NOTE:  you have to use sudo because the default demo user doesn't have permissions to edit the OS.