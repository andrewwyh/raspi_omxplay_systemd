# raspi_omxplay_systemd
Systemd configuration file for autoplay of media files using OMX Player. Raspberry Pi OS.

This service autostarts with the Raspberry Pi, and continuously and repetitively plays back a given URL on HDMI outputs

For Raspberry Pi 4, we can have independent playback on each HDMI

##Installation

Edit the omx.service file, and insert your URL into the lines:

### For Raspi 4, separate HDMI outputs
#### HDMI 1
```
ExecStart=omxplayer --display 2 rtmp://<put your stream here>
```

#### HDMI 2
```
ExecStart=omxplayer --display 7 rtmp://<put your stream here>
```

### For other Raspi models with only 1 HDMI output:

```
ExecStart=omxplayer rtmp://<put your stream here>
```

Copy the file to /lib/systemd/system
```
cp omx.player /lib/systemd/system
```

Enable the service

``` 
sudo systemctl enable omx.service
```

Start the service

```
sudo systemctl start omx.service
```

Stop the service
```
sudo systemctl stop omx.service
```
