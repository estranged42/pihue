# pihue
DIY HomeKit enabled RGB Lightstrips

## Pi Setup

### Change the password for the `pi` user.

Every initial install of raspbian has the same default username/password.  Change it!

    $ passwd

### Setup WiFi

    $ sudo nano /etc/wpa_supplicant/wpa_supplicant.conf

Add the following to the end of that file. The scan_ssid line is required if 
your WiFi SSID is not public (ie hidden).

    network={
        ssid="yourHiddenSSID"
        scan_ssid=1
        psk="Your_wifi_password"
    }

Then reconfigure the WiFi interface:

    $ wpa_cli -i wlan0 reconfigure

After a few moments, check to see that your wlan0 interface has an IP address:

    $ ifconfig wlan0
    wlan0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
            inet 10.0.1.106  netmask 255.255.255.0  broadcast 10.0.1.255

### Enable SSH

    $ sudo raspi-config

Go down to Interfaces and enable the SSH server.


Once all that is done, you should be able to ssh to the new pi from elsewhere
on the same wifi network, so you don't need a keyboard and monitor hooked 
up anymore.

## Fadecandy / Open Pixel Control

The light strips are controlled directly from a [fadecandy]() board.

[fadecandy]: https://github.com/scanlime/fadecandy
