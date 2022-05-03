# NGINX-Configuration

### NGINX Web server instalation and configuration for 2 subdomains.

#### Index.html source code provided by <a href="https://onehtmlpagechallenge.com/">onehtmlpagechallenge.com</a>

## Index

> ### Deploy Cloud Server
>
> ### Connect to the server
>
> ### Download NGINX (Debian)
>
>> - Landing page NGINX server on browser
>
>### Edit config files on NGINX server
>
>> - Sites-available directory
>> - Modify the new template files
>> - Sites-enabled directory
>>- Modifying the hosts directory for DNS testing
>> - Create directories and main file to load (index.html) for each subdomain
>
>### Install text-based web browser for Linux (Links)

## Deploy cloud server
Server cloud platform <a href="https://upcloud.com/">upcloud.com</a> with free trial (30 days).

![upcloudServerConfig](https://user-images.githubusercontent.com/77643882/166478966-4225e69e-635e-41cf-8b3c-4e7b858780e5.png)

Initial default password: _j39995tms29rjm7q_

## Connect to the server
From Windows:
SSH Client as PuTTY

Enter the public IP address `5.22.219.33` for this server, to the Hostname field and then click the Open button to connect, saving the connection config or not:

![PuTTY-config](https://user-images.githubusercontent.com/77643882/166479987-18834ef2-2306-4a09-a59d-990220eacd7a.png)

On the first time connecting to the server, you might see the following security alert. Click the 'Accept' button to save the host key and continue.

![PuTTY-security-alert](https://user-images.githubusercontent.com/77643882/166480320-52eb8c92-8085-4c77-b210-3e9d0e917285.png)

If this is the first time you log into this server, you will be prompted to change the password.

![LoginAsRoot-changePass](https://user-images.githubusercontent.com/77643882/166480511-eda71ccb-d817-4364-a06e-cc433f14de3e.png)

New password: `admin1234`

## Download NGINX (Debian)

`apt-get install nginx`

![apt-get-install-nginx](https://user-images.githubusercontent.com/77643882/166480807-da1db5ca-4267-4c69-baae-3785ae3e7039.png)

### Landing page NGINX server on browser

IP address <a href="http://5.22.219.33">5.22.219.33</a> of the Debian cloud server.

![landingPageNginxServerWebBrowser](https://user-images.githubusercontent.com/77643882/166481723-78a964f0-1e90-4694-8843-6b016173a9ee.png)

## Edit config files on NGINX server

`cd /etc/nginx/`
`ls -l`

![nginx-config-files](https://user-images.githubusercontent.com/77643882/166482200-010952e1-f8b4-4126-ac1f-7de31c2467ad.png)

The two most important directories are 'sites-available' and 'sites-enabled'.
They are directories to keep order when we store different sites on the server.
The server can differentiate the virtual host by using domains or subdomains resolution.

### sites-available directory

On this level we can find a 'default' file witch contains the welcome message from the server.
We should copy the file 'default' as a template with the subdomain/domain name.

`cd sites-available/`
`ls -l`
`cp default bit-rain.4heber.com`
`cp default ant-colony.4heber.com`

![defaultTemplate-sitesAvailableDirectory](https://user-images.githubusercontent.com/77643882/166483467-bd4b8d6a-fb33-4ba4-963b-b7215e3c3bc2.png)

### Edit the new template files

`nano ant-colony.4heber.com`

![09-nanoCopiedFile](https://user-images.githubusercontent.com/77643882/166483806-bffc7df8-4666-41aa-a9e4-e1b552582d12.png)

Change `server_name _;` to `server_name subdomainFullRoute;`

Replace `/html;` on root section to `/subdomainNameFiles;`

Same process for the second file copied (second subdomain):

![10-nanoCopiedFile2](https://user-images.githubusercontent.com/77643882/166484422-96d26152-57a5-44e9-973c-c0cb42a3a2aa.png)

Delete the option `default_server` there must be only one default server (ant-colony for this example):

![10 1-deleteOptionDefaultServer-onlyOneDefaultServer](https://user-images.githubusercontent.com/77643882/166484650-e3230db6-5e9e-4b32-bff0-2d9e342eadb1.png)

## sites-enabled directory

Switch to `sites-enabled` to activate the sites configured on `sites-available` via symbolic link.

`cd ../sites-enabled/`
`ls -l`

![11-sitesEnabledAddNewSymbolicLink](https://user-images.githubusercontent.com/77643882/166485235-cbc65cfd-5ded-4b2e-ae91-74d08fd1c5dd.png)

Create new links via:

`ln -s ../sites-available/ant-colony.4heber.com`
`ln -s ../sites-available/bit-rain.4heber.com`

![12-createNewLinks](https://user-images.githubusercontent.com/77643882/166485509-0773a7d6-3352-4f1b-8dd3-0e2f817bf475.png)

Reload the server with `nginx -s reload`

## Modifying the hosts directory for DNS testing

Locate and modify the "/hosts" file with nano, on sites-enabled directory move to /etc:

`cd ../../`
`nano hosts`

![13-editHostsFileForDNStesting](https://user-images.githubusercontent.com/77643882/166486244-7d0cd128-eabd-42b4-b352-f3b38be4f627.png)

Add the server IP and the both subdomains to resolve:

**5.22.219.33** ant-colony.4heber.com bit-rain.4heber.com

![14-editHostFile-addIPserverSubdomainsFullRoute](https://user-images.githubusercontent.com/77643882/166486624-f5dee700-b007-4501-8cf1-b99a90b7c7c0.png)

## Create directories and main file to load (index.html) for each subdomain

On "/var/wwww/" :

`ls -l`
`mkdir and-colony`
`mkdir bit-rain`
`cd ant-colony/`
`touch index.html`
`nano index.html`

![15-createDirectoriesMainFileIndexHTML](https://user-images.githubusercontent.com/77643882/166488662-be1bf796-5905-4f5c-af5c-158c3d97f26a.png)

Insert the "Ant colony" source code from <a href="https://onehtmlpagechallenge.com/">onehtmlpagechallenge.com</a> :

![16-antColonySourceCodeInsert](https://user-images.githubusercontent.com/77643882/166488785-1d38b8e0-4b40-4430-a14f-94c0ba47561c.png)

Insert the "Bit rain" source code from <a href="https://onehtmlpagechallenge.com/">onehtmlpagechallenge.com</a> :

![17-bitRainSourceCodeInsert](https://user-images.githubusercontent.com/77643882/166489311-85db09f4-969e-417b-a08e-6a7bacac4973.png)

## Install thext-based web browser for Linux (Links)

`apt-get install links`

![18-installLinks](https://user-images.githubusercontent.com/77643882/166489514-705b7f21-ad64-4c00-b872-73e4a50abc08.png)

`links ant-colony.4heber.com`

![19-openLinksWithSubdomain1](https://user-images.githubusercontent.com/77643882/166489907-1b46c22d-7c23-4782-8d07-e7f0f73bfffd.png)

![20-url1Open](https://user-images.githubusercontent.com/77643882/166489937-47fcee1d-cbc9-47cb-ad61-95ae7cc9b27a.png)

*For this text-based browser the styles on the main file did not represented, but the redirection on the subdomain name works fine.*<br/>
*<a href="https://onehtmlpagechallenge.com/entries/ant_colony.html">View original site here</a>*

`links bit-rain.4heber.com`

![21-url2Open](https://user-images.githubusercontent.com/77643882/166490718-0b41d702-59f4-414d-8dd4-a3afc4458adf.png)

*For this text-based browser the styles on the main file did not represented, but the redirection on the subdomain name works fine.*<br/>
*<a href="https://onehtmlpagechallenge.com/entries/bits-rain.html">View original site here</a>*

The IP resolution for both subdomains respond correctly with the index.html file of each website.
