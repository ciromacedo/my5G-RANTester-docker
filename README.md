# my5G-RANTester-docker
This repository is a docker compose version of my5G-core(free5gc stage 3 version v3.0.4) and my5G-RANTester. It's inspire by [free5gc-docker-compose](https://github.com/free5gc/free5gc-compose) mantained by [free5gc](https://github.com/free5gc) and has some modifications to attend my5G-RANTester(that is UE/GNB simulator)

# Reference:
https://github.com/free5gc/free5gc-compose



Instalação do Kernel:
	``` sudo apt-get install -y linux-image-5.0.0-23-generic ```

reiniciar a máquina após instalação.

Linux headers 5.0.0.23 necessário no gtp5:
	``` sudo apt-get install -y linux-headers-5.0.0-23-generic```

Instalar o make
	```apt install make```
	```apt install gcc -y```

Instalar GTP5:
	```git clone https://github.com/PrinzOwO/gtp5g.git```
	```cd gtp5g```
	```make```
	```sudo make install```

Instalar o docker:
	```sudo apt-get update```
	
	```sudo apt-get install \
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
   	sudo apt-get install docker-ce docker-ce-cli containerd.io ```
   	
   	
  Instalar o docker compose:
  	``` sudo curl -L "https://github.com/docker/compose/releases/download/1.28.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
  	
  	sudo chmod +x /usr/local/bin/docker-compose
  	sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose ```
  	
  	
  Inicializar o my5GCore e o Tester:
	``` git clone https://github.com/my5G/my5G-RANTester-docker.git
	cd my5G-RANTester-docker
	make base
	docker-compose build
	sudo docker-compose up -d ```
   	
  Executar o comando CHMOD autorizando o .sh que adiciona os UES.
  	``` chmod u+x include_ues.sh ```
  	
  Executar o .sh p/ adicionar os UES
  	``` ./include_ues.sh NUMERO_DE_UES```