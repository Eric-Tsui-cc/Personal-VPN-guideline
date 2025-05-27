# A simple personal VPN guideline
# An easy tutorial for building a VPN service by yourself, based on Amazon EC2(Ubuntu)

## First of all, you need to have a cloud server; this tutorial is based on Amazon EC2, and there are plenty of substitute services on the Internet, like Vultr, etc. 
For Amazon EC2, you can just use the free tiers, so it's almost free to use for a while, and we recommend t2.micro or t2.nano for your VPN server.

# Build Server
Ensure you have installed Ubuntu on your server(also available for CentOS 6,7, Debian ), and set the security group open for ports 22/80/443. For better testing, add the rule ICMP IPV4 is necessary. 
Run your server, test the ping of your server (use the command for any bash, for example, cmd or powershell for Windows)
```
ping xx.xx.xxx.xx
```
IF ping is too high, you can change the server or location to meet your needs.
# Connect to Server
For macOS or Linux, open the terminal and use the command, xx.xx.xxx.xx is your server ip address.
```
ssh root@xx.xx.xxx.xx
```
For the case Amazon EC2, select your instance, click Connect and select SSH client, copy the Example, it will be like
```
ssh -i "webkey" ubuntu@xx.xx.xxx.xx
```
### webkey is the local key file of your server, you probably already know.
## for Windows, download a software called [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) , for tutorial of using putty to connect your ec2 server, see [Video by Herbertech](https://www.youtube.com/live/TkSuLg-8TD8)
# Build the proxy server
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
# Modify your VPN 
### 1. Set the password for your server, and keep it.
### 2. Set the port for your VPN, and make sure you open it in the security group from your SaaS provider.
### 3. Select the stream cipher you want to use (You can just choose the default:)
### 4. Press any key to start building.
 After the process of building, it will show some information about your VPN, just like this. Take a screenshot or make a note.
 ![Pic](https://github.com/Eric-Tsui-cc/Personal-VPN-guideline/blob/main/image/Image%2027-05-2025%20at%2013.55.jpeg)

# Connect to your VPN
 Now we need software for connecting to your VPN server.
### For macOS and iOS, I recommend [Shadowrocket](https://apps.apple.com/us/app/shadowrocket/id932747118) (better user experience) and [OneClick](https://apps.apple.com/us/app/oneclick-safe-easy-fast/id1545555197)(Free). 
## Simple tutorial for connecting by using Shadowrocket.
