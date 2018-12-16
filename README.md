# Docker for Data Science 
### Set up 
First clone this repository.
```commandline
git clone https://github.com/sdn0303/sience-container.git
```

Move to project root
```commandline
cd sience-container
```

Build container
```commandline
docker-compose up --build
```

Container access
```text
http://local:8888
```

When asked for a password
```text
root
```

Exit
```commandline
Control + c
```


### Setup Docker
#### Install [Docker for mac](https://docs.docker.com/compose/install/)
```commandline
brew install docker
```
Install [Docker Compose](http://docs.docker.jp/compose/install.html)
```commandline
curl -L https://github.com/docker/compose/releases/download/1.6.2/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
```
```commandline
chmod +x /usr/local/bin/docker-compose
```

・参考サイト
  - [Docker for Windows のインストール](http://docs.docker.jp/windows/step_one.html)
  - [Windows で Docker Compose のインストール](https://www.kunihikokaneko.com/dblab/toolchain/dockercompose.html)
