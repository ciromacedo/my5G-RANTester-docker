# my5G-RANTester-docker
This repository is a docker compose version of my5G-core(free5gc stage 3 version v3.0.4) and my5G-RANTester. It's inspire by [free5gc-docker-compose](https://github.com/free5gc/free5gc-compose) mantained by [free5gc](https://github.com/free5gc) and has some modifications to attend my5G-RANTester(that is UE/GNB simulator)

# Reference:
https://github.com/free5gc/free5gc-compose


## Install
The following steps demonstrate how to set up the environment on a DigitalOcean Virtual Machine.
Kernel installation for GTP5 support (choose the first option from the boot menu):
```
sudo apt-get install -y linux-image-5.0.0-23-generic
```
After install reboot de machine. After reboot install __linux-headers__
```
sudo apt-get install -y linux-headers-5.0.0-23-generic
```

**make** and **gcc** are required for the build process
```
apt install make
apt install gcc -y
```

Configuring the **gtp** tunnel, required for the User Plane Function:
```
git clone https://github.com/PrinzOwO/gtp5g.git
cd gtp5g
make
sudo make install
```

Installing Docker:
```
sudo apt-get update
	
sudo 	apt-get install \
     	apt-transport-https \
	ca-certificates \
	curl \
	gnupg-agent \
	software-properties-common
		    
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -		    
	
sudo apt-key fingerprint 0EBFCD88
				    
sudo add-apt-repository \
	   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
	   $(lsb_release -cs) \
	   stable"
	   
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
```
  	
Installing Docker Compose:
 ``` 
sudo curl -L "https://github.com/docker/compose/releases/download/1.28.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
  	
sudo chmod +x /usr/local/bin/docker-compose
sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose 
```
  	  	
Running m5GC, Tester with nf_nwdaf:
``` 
git clone https://github.com/ciromacedo/my5G-RANTester-docker.git
cd my5G-RANTester-docker
make base
docker-compose build
sudo docker-compose up -d 
```

## Add UE's into WebUI
 Run the **CHMOD** by authorizing the **.sh** that adds the UES.
``` 
chmod u+x include_ues.sh 
./include_ues.sh NUMERO_DE_UES
```
