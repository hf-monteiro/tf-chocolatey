# How to Deploy Chocolatey server.

1. Deploy chocolatey_repo module using Terraform.

2. The terraform module will create and configure IIS web server site called **ChocolateyServer** that will manage all request from choco clients. A default configuration called *Web.config* will be created in **C:\tools\chocolatey.server** directory. We recomendate to change default user/password and default API Key for production environment.

    You can populate your Chocolatey repository using `choco push ` command to upload *.npkg* files or directly store the files in **C:\tools\chocolatey.server\App_Data\Packages**.

3. To start pulling package from local choco server, you need add the local server as a source in your choco client via powershell

```shell 
choco source add -n=MyRepoName -s="http://X.X.X.X/chocolatey"
```