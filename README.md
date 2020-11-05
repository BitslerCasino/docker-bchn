# docker-bchn
Docker Image for Bitcoin Cash using BCHN Client. Cross compatible to Bitcoin ABC data before November 15 2020 fork. Installing after the fork, a full sync will be required.

### Quick Start
Create a bchd-data volume to persist the bchd blockchain data, should exit immediately. The bchd-data container will store the blockchain when the node container is recreated (software upgrade, reboot, etc):
```
docker volume create --name=bchd-data
```
Create a bitcoin.conf file and put your configurations
```
mkdir -p .bchdocker
nano /home/$USER/.bchdocker/bitcoin.conf
```

Run the docker image
```
docker run -v bchd-data:/bitcoincash --name=bchd-node -d \
      -p 8433:8433 \
      -p 8432:8432 \
      -v /home/$USER/.bchdocker/bitcoin.conf:/bitcoincash/.bitcoin/bitcoin.conf \
      unibtc/docker-bchn:latest
```

Check Logs
```
docker logs -f bchd-node
```

Auto Installation
```
sudo bash -c "$(curl -L https://git.io/JTp0u)" -- 22.1.0
```
