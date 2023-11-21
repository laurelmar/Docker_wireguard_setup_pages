## 1. Project references  

Links/resources: https://youtu.be/GZRTnP4lyuo?si=8wtTXg_t7-BSSFMX , https://github.com/christianlempa/videos/tree/main/wireguard-docker


## 2. Droplet set up

The first part of this project is making sure you set up your droplet in digital ocean as Ubuntu 20.04 
 - I configured it with a password

![Image of code](/assets/ip_droplet.png)

#### Sign into your VPN using terminal to ssh in

![Image of code](/assets/Launch_and_signin.png)

## 3. Docker/ docker-compose

### Tools
```shell
sudo apt install apt-transport-https ca-certificates curl software-properties-common -y
```
### docker-compose
Installing docker compose 
```shell
sudo curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

Set permissions
```shell
sudo chmod +x /usr/local/bin/docker-compose
```

![Image of code](/assets/sudo_curl_L.png)


## Setting up Wireguard

I had some trouble in this part becuase I got my files in the wrong places and as a result my QR code didnt work. I found that if this happens just take down the server if it is already up using ' docker stop wireguard_server', move what you need to around, and relaunch it. 

Make sure you are in /opt or making wireguard in /opt

```shell
sudo mkdir /opt/wireguard-server
```
![Image of code](/assets/in_opt.png)

#### cd into /opt/wireguard-server/ and create your yaml or yml file

![Image of code](/assets/yaml_file.png)

- Make sure you change the PUID, GUID, TZ, SERVERURL, and also PEERs for how many people will be connecting to your VPN
- I said PEERS=2 because I will be testing this on my phone and computer

### Once done you can you can launch your wireguard server with the command

```shell
docker-compose up -d
```
![Image of code](/assets/Launch_wireguard.png)

## check to make sure your server is up

```shell
docker-compose ps
```
![Image of code](/assets/wirguard_up.png)


## Make sure you can connect to the VPN 

You will need to run this command 
```shell 
docker exec -it wireguard wg 
```
![Image of code](/assets/Public_private.png)

If you go into the config file within your server and you follow the path /opt/wireguard-server/config/peer1 you can see where the QR code file 

![Image of code](/assets/config_files.png)

![Image of code](/assets/peer1.png_QR.png)

## Test VPN on phone 

Show the QR code
```shell
docker exec -it wireguard /app/show-peer 1
```
![Image of code](/assets/peer1_QR.png)

![Image of code](/assets/phone_screen.png)
![Image of code](/assets/Iphone_screenshot.png)

#### Test was successful

## Test VPN on desktop
![Image of code](/assets/computer_test_website.png)













