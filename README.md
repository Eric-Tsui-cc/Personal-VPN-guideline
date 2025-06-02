# Personal VPN and Website
### Student Name: Can Cui, Student ID: 35661409
### Server Domain: [ict35661409.click](https://ict35661409.click/), Globle IP:[13.58.36.157](http://13.58.36.157)
This document and project are based on Amazon EC2 Ubuntu server. 
## Launch a EC2 instance 
* sign up/ login [EC2 Console](https://aws.amazon.com/ec2/)
* Choose the location you need.
* Follow the steps on the AWS site.
* Choose Ubuntu OS.
* Instance type - **t2.micro** is fine.
* Key pair - for security concerns, download the key file to log into  your server.
* Configure Security Group - tick allow SSH/HTTP/HTTPS traffic from anywhere.
* Review and Launch
* Click "Launch".
[Tutorial for build EC2 if you don't know](https://www.youtube.com/watch?v=86Tuwtn3zp0)
# Part 1:Build the Web server
## Modify your instance
For better testing, adding the rule ICMP IPV4 to your security group is necessary. 
Run your server, test the ping of your server (use the command for any bash, for example, cmd or powershell for Windows)
```
ping xx.xx.xxx.xx
```
If ping is too high, you can change the server or location to meet your needs.
## Connect to Server
For macOS or Linux, open the terminal and use the command, xx.xx.xxx.xx is your server ip address.
```
ssh root@xx.xx.xxx.xx
```
For the case Amazon EC2, select your instance, click Connect and select SSH client, copy the Example, it will be like
```
ssh -i "webkey" ubuntu@xx.xx.xxx.xx
```
### webkey is the local key file of your server.
For Windows, download a software called [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) , for tutorial of using putty to connect your ec2 server, see [Video by Herbertech](https://www.youtube.com/live/TkSuLg-8TD8)
## Build basic web server
* After connection, update and install Apache2: Run
```
sudo apt update
```
Update apt repositories
```
sudo apt install apache2
```
Install Apache web service
After finish, you have basic web page now, the web page file is located 
``
var/www/html/index.html
``
Modify the content by using the nano command.
## Get SSL/TLS for your website.
Run
```
sudo snap install --classic certbot
```
Install Certbot
```
sudo ln -s /snap/bin/certbot /usr/bin/certbot
```
Ensure that the certbot command can be run.
```
sudo certbot --apache
```
Install your certificates
After this, visit your website to see the lock icon for the test.
## Get a Domain
* Go back to the AWS console, search **router53**
* At the box of the register domain, type in your ideal domain name.
* Click "check"
* Pick an acceptable price domain for your server, and pay for that.
## Get Elastic IP address and associate it with your instance
* Go back to the AWS console, search **Elastic IP address**
* Click Allocate **elastic IP address**
* After Allocated, tick your IPv4 address and Click **Action -> Associate Elastic IP address**
* Then choose your instance
* Now you have the fixed IP address for your instance. :)
## Associate your Domain with your IP address(DNS)
* Go back to router 53
* Go **Hosted zones -> your domain -> Creat record**
* Type in your IP address in **"Value"**
* Other keep the default, then Create records.
* After finish, try to visit the domain to test, may it take 10 mins.
# Part 2: Build VPN service.
## Build the VPN proxy service
After connecting your server, run the commands below
```
sudo -i 
```
Run commands as root
```
wget --no-check-certificate https://raw.githubusercontent.com/teddysun/shadowsocks_install/refs/heads/master/shadowsocks-go.sh
```
Download the script from GitHub, thanks to the script by [Teddysun](https://github.com/teddysun)
```
chmod +x shadowsocks-go.sh
```
Add execute permission for all users
```
./shadowsocks-go.sh
```
Run the script
## Modify your VPN 
1. Set the password for your server, and keep it.
2. Set the port for your VPN,
## make sure you open it in the security group from your IaaS provider.
3. Select the stream cipher you want to use (You can just choose the default:)
4. Press any key to start building.
 After the process of building, it will show some information about your VPN, just like this. Take a screenshot or make a note.
 ![Pic](https://github.com/Eric-Tsui-cc/Personal-VPN-guideline/blob/main/image/Image%2027-05-2025%20at%2013.55.jpeg)

## Connect to your VPN
Now we need software for connecting to your VPN server.
For macOS and iOS, I recommend [Shadowrocket](https://apps.apple.com/us/app/shadowrocket/id932747118) (better user experience) and [OneClick](https://apps.apple.com/us/app/oneclick-safe-easy-fast/id1545555197)(Free).
For Windows systems, I recommend [Clash for windows](https://www.clashforwindows.net/) or [SS for windows](https://github.com/shadowsocks/shadowsocks-windows) All free to use.
## Simple tutorial for connecting by using Shadowrocket.
 ![Pic](https://github.com/Eric-Tsui-cc/Personal-VPN-guideline/blob/main/image/Image%2027-05-2025%20at%2013.33.jpeg)
 ![Pic](https://github.com/Eric-Tsui-cc/Personal-VPN-guideline/blob/main/image/Image%2027-05-2025%20at%2013.31.jpeg)
### After clicking save, you can connect to your VPN now.
 ![Pic](https://github.com/Eric-Tsui-cc/Personal-VPN-guideline/blob/main/image/Image%2027-05-2025%20at%2021.42.jpeg)
 ## Test IP, complete.



