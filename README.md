# Tidal Connect for Raspberry PI using Docker.
Based on the great work of TonyTromp : https://github.com/TonyTromp/tidal-connect-docker

## Purpose
This repo is a small extract of the project mentioned above to only get what I needed : **Tidal Connect using Docker on Raspberry Pi** accessible by all Tidal apps.

<img src="https://github.com/cstaelen/docker-tidal-connect/blob/main/capture/capture-tidal.png?raw=true" width="400" />

### Parameters

Set env vars in `docker-compose.yml`:

```
- PLAYBACK_DEVICE=dmix # sound device name (use "aplay -L" to get device list)
- FRIENDLY_NAME=Sexy device name
- MODEL_NAME=Sexy device name
- MQA_CODEC=false # for DAC and stuff
- MQA_PASSTHROUGH=true # for DAC and stuff
```

## Install

```
git clone <repo> tidal-connect
cd tidal-connect
docker-compose up -d
```

## Start service on boot

Update `WorkingDirectory` path in `docker-tidal-connect.service` :
```
chmod +x </path/to/repo/>docker-tidal-connect.service
sudo cp </path/to/repo/>docker-tidal-connect.service /etc/systemd/system/docker-tidal-connect.service
sudo systemctl enable docker-tidal-connect
sudo service docker-tidal-connect.service start 
sudo systemctl daemon-reload
```