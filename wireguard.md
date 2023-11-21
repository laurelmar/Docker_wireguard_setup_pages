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

Make sure you are in /opt or making wireguard in /opt

```shell
sudo mkdir /opt/wireguard-server
```
![Image of code](/assets/in_opt.png)

#### cd into /opt/wireguard-server/ and create your yaml or yml file

![Image of code](/assets/yaml_file.png)

- Make sure you change the PUID, GUID, TZ, SERVERURL, and also PEERs for how many people will be connecting to your VPN
- I said PEERS=2 because I will be testing this on my phone and computer

### Once done you can you can launch wireguard with the command

```shell
docker-compose up -d
```