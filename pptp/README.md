# Description
This repository provides a way to construct a docker image which enables you
to connect to a PPTP VPN server. The image is based on alpine and uses
[pptpclient](https://pkgs.alpinelinux.org/packages?name=pptpclient&branch=edge)
to connect to the VPN server.   

## Sample Usage
1. git clone [this repository](https://github.com/kquiet/docker-image) to your
machine.
2. switch to directory 'pptp' of the repository, and then execute
```docker build -t pptp:test .``` to build the docker image 
3. execute ```docker run --name test -d --cap-add=NET_ADMIN --device=/dev/ppp
-e pptp_address=VPN_SERVER_ADDRESS -e pptp_username_file=/username
-e pptp_password_file=/password -v VPN_USERNAME_FILE:/username
-v VPN_PASSWORD_FILE:/password pptp:test```
* VPN_SERVER_ADDRESS: the address of VPN server
* VPN_USERNAME_FILE: the path of file which contains the user name to connect to
VPN server
* VPN_PASSWORD_FILE: the path of file which contains the password to connect to
VPN server
4. wait a few seconds, and then execute ```docker exec -it test apk add curl &&
curl https://www.showmyip.com | grep "Your IPv4"``` to check if current IP
matches the IP of VPN server

