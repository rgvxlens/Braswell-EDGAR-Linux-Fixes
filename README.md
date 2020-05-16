# Fix sound on Braswell-based Chromebooks running Linux

All thanks to [this post](https://askubuntu.com/questions/974073/no-audio-on-acer-chromebook-14-under-ubuntu-17-10) for the fix. Tested on Kubuntu 20.04 on an Acer Chromebook 14 CB3-431.

## Installation
### 1. Fixing Audio via Speakers
1. Download the provided asound.state file - [link](https://github.com/rgvxlens/EDGAR-Linux-Audio-Fix/blob/master/asound.state)
2. Via Terminal,
```bash
pgrep alsa
sudo cp /media/ubuntu/UUID/var/lib/alsa/asound.state /var/lib/alsa/asound.state
sudo alsa force-reload
````
3. Test to check that your sound is working or not (via Sound Mixer/Firefox etc)/
4. If working, use the following commands to make the changes permanent
```bash
alsactl init
sudo alsactl store --file /var/lib/alsa/asound.state
sudo alsa force-reload
```
### 2. Fixing Audio for Headphones
Once you have followed the above steps and your sound is working (check after a reboot as well), you have to follow the following steps to unmute your headphones.
1. Open a terminal and type
```bash
alsamixer
```
2. Press F6 (brightness decrease key)
3. Select your sound card (chtrt5650 for me)
4. Press right arrow key once to move to Headphone Channel
5. Press "m" to unmute it and the ESC key to save these changes.
