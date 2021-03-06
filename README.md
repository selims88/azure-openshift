# Red Hat OpenShift Container Platform on Azure

When creating the Red Hat OpenShift Container Platform on Azure, you will need a SSH RSA key for access.

## SSH Key Generation

1. [Windows](ssh_windows.md)
2. [Linux](ssh_linux.md)
3. [Mac](ssh_mac.md)

## Create the Installation
### Create the Installation on the Azure Portal

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fglennswest%2Fazure-openshift%2Fmaster%2Fazuredeploy.json" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>
<a href="http://armviz.io/#/?load=https%3A%2F%2Fraw.githubusercontent.com%2Fglennswest%2Fazure-openshift%2Fmaster%2Fazuredeploy.json" target="_blank">
    <img src="http://armviz.io/visualizebutton.png"/>
</a>

[Experimental Additional Functions](addfunctions.md)

## Parameters

For OsX:

1. SSHKeyData - Public Key - Copy/Paste from .ssh/id_rsa.pub - pbcopy < ~/.ssh/id_rsa.pub

2. PoolId - From RHEL - subscription-manager list --available

3. SSHPrivate Data - Base64 Encoded id_rsa - cat ~/.ssh/id_rsa | base64 | pbcopy

For RHEL/Fedora/Centos:

1. SSHKeyData - Public Key - Copy/Paste from .ssh/id_rsa.pub - xclip -selection clipboard < ~/.ssh/id_rsa.pub

2. PoolId - From RHEL - subscription-manager list --available

3. SSHPrivate Data - Base64 Encoded id_rsa - cat ~/.ssh/id_rsa | base64 | xclip -selection clipboard

### Input Parameters

| Name| Type           | Description |
| ------------- | ------------- | ------------- |
| adminUsername  | String       | Username for SSH Login and Openshift Webconsole |
|  adminPassword | SecureString | Password for the Openshift Webconsole |
| sshKeyData     | String       | Public SSH Key for the Virtual Machines |
| masterDnsName  | String       | DNS Prefix for the Openshift Master / Webconsole |
| numberOfNodes  | Integer      | Number of Openshift Nodes to create |
| masterVMSize | String | The size of the Master Virtual Machine |
| infranodeVMSize| String | The size of the Infranode Virtual Machine |
| nodeVMSize| String | The size of the each Node Virtual Machine |

### Output Parameters

| Name| Type           | Description |
| ------------- | ------------- | ------------- |
| openshift Webconsole | String       | URL of the Openshift Webconsole |
| openshift Master ssh |String | SSH String to Login at the Master |
| openshift Router Public IP | String       | Router Public IP. Needed if you want to create your own Wildcard DNS |

------

This template deploys Red Hat Openshift on Azure.

Attribution:

Thanks to:
Daniel Falkner - Microsoft Germany - For original templates.

Harold Wong <Harold.Wong@microsoft.com> for his great support.

Ivan McKinley

For full commit history: Please see - https://github.com/glennswest/azure-openshift
