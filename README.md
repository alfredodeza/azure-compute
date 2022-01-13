# Remote Compute with Azure

Set up a remote Azure compute instance for data science and connect to it with VSCode

## Setup storage

### Create a Storage Account



### Create a new File Share

Click on `File Service` and then on `File Share`. Filling out the blade form will create the SMB share

Once created, click on the resource and then find the `Connect` button to see the connection snippet.

Copy the creation script which includes the secret key.

Enable SMB on the File Share

## Setup VSCode

Open up VSCode and install the Azure Tools extension pack (multiple extensions in one)

Install the Remote SSH extension by Microsoft

### Connect to Azure
### Connect to Remote Compute over SSH

Note how the extensions change. Install the Python extension on the remote

Once connected change to /mnt/{name of share}
### Connect to Azure

## Create a Compute Instance

Head over to ml.azure.com and then to the _Compute_ section and select _New_ to create a new instance. Make sure to select _Advanced Seettings_ so that
SSH can be enabled.

### Enable SSH

In the _Advanced Settings_ section, enable _SSH Access_

Copy your local public SSH key:

```
$ cat ~/.ssh/id_rsa.pub | pbcopy
```

### Connect to Azure

##
##
##
##
##
