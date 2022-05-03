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

##





