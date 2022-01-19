# Remote Compute with Azure

Set up a remote Azure compute instance for data science and connect to it with VSCode

## Watch the Video tutorial

[![Azure Remote Compute for VSCode](https://img.youtube.com/vi/Fa_ubqmJcMw/0.jpg)](https://youtu.be/Fa_ubqmJcMw "Azure Remote Compute For VSCode")

## Setup storage

Setting up storage is the first step to making this environment work well. However, there is no requirement to have this done before creating the compute instance. Creating storage to attach it to the compute instance allows you to store your data separately. The compute can become ephemeral. It doesn't matter if it gets removed or reprovisioned.

### Create a Storage Account
First step is to create a storage account. A storage account is like a parent service for services that you can attach to it. For example, you can create a file share, but the file share must be part of a storage account.

There are no specifics needed other than the defaults and adding a unique name for the storage account.

### Create a new File Share
Once you have a storage account ready it should take you to the resource. In the _Overview_ section, you should see _File service_. Select it so that you can create a new file share.

Next, click on `File Share`. Filling out the blade form will create the SMB share.

Once created, click on the resource and then find the `Connect` button to see the connection snippet.

Copy the creation script which includes the secret key.

## Setup VSCode

Open up VSCode and install the Azure Tools extension pack (multiple extensions in one)

Install the Remote SSH extension by Microsoft


## Create a Compute Instance

Head over to ml.azure.com and then to the _Compute_ section and select _New_ to create a new instance. Make sure to select _Advanced Seettings_ to enable SSH.

### Enable SSH

In the _Advanced Settings_ section, enable _SSH Access_. You can let Azure create a unique key for you or use your public key.

This is how you can copy your local public SSH key (note that `pbcopy` is OSX only):

```
$ cat ~/.ssh/id_rsa.pub | pbcopy
```

### Connect to Remote Compute over SSH
Once the compute instance is up and running on Azure, you can go to the resource and find the menu option for _Connect_. This will get you the right `SSH` command to connect to the resource.

Make note of this command so that you can use it to connect VSCode to it later.

### Test SSH connection

From your computer, use the `SSH` command to connect to the remote instance. If your key was added, you should be able to connect without a password prompt.

### Mount storage
From the File share service that you enabled earlier, go to the _Connect_ menu and capture the code snippet for Linux. Paste that into the remote server into a file. Call the file _setup.sh_ and then run it with `sudo`:

```
$ sudo bash setup.sh
```

That should mount the SMB share onto `/mnt/{name of share}`.

### Connect to Azure
Open VSCode and the command palette (Command-Shift-P on OSX). Alternatively, use the menu option View→ Command Palette. Start typing _Remote-SSH_ and select the option to *add a new host*. Follow the prompts to complete the information requested including the `SSH` command and configuration.

Once the host is added you will be prompted to connect. Select _Yes_.

Finally, open the file explorer and use _Open Folder_ to go to `/mnt/{name of share}`. This is where all your work should happen since it is the SMB share.
