# A simple personal VPN guideline
# An easy tutorial for building a VPN service by yourself, based on Amazon EC2(Ubuntu)

# Build Server
### First of all, you need to have a cloud server; this tutorial is based on Amazon EC2, and there are plenty of substitutions on the Internet. 
### Ensure you have installed Ubuntu on your server, and set the security group open for ports 22/80/443. For better testing, add the rule ICMP IPV4 is necessary. Security group like the pic below.//Pic
### Run your server, test the ping of your server // use command for any bash, for example, cmd for Windows
```
ping xx.xx.xxx.xx
```
# Connect to Server
## for macOS or Linux, open the terminal and use the command, xx.xx.xxx.xx is your server ip address.
```
ssh root@xx.xx.xxx.xx
```
### for the case Amazon EC2, select your instance, click Connect and select SSH client, copy the Example, it will be like
```
ssh -i "webkey" ubuntu@xx.xx.xxx.xx
```
### webkey is the local key file of your server, you probably already know.
## for Windows, download a software called [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) , for tutorial of using putty to connect your ec2 server, see [Video by Herbertech](https://www.youtube.com/live/TkSuLg-8TD8)

### After connecting your server, run commands below
```
sudo -i 
```
Run commands as root
```
wget --no-check-certificate https://raw.githubusercontent.com/teddysun/shadowsocks_install/refs/heads/master/shadowsocksR.sh
```
Download the script from GitHub, thanks to the script by [Teddysun](https://github.com/teddysun)
