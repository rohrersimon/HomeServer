# WiFi Configuration from CLI

I am using WiFi instead of Ethernet cable for the home server because I don't want a cable going across the living room from the router to the laptop.

Connecting to WiFi is a challenge from the CLI interface. The tool to use is called 'nmcli' and can be installed like this:
```bash
sudo apt install nmcli
```

Once installed check if WiFi radio is on:
```bash
nmcli r wifi on
```

List available WiFi networks:
```bash
nmcli d wifi list
*  SSID           MODE   CHAN  RATE       SIGNAL  BARS  SECURITY
   ...
   my_wifi      Infra  5     54 Mbit/s  89      ▂▄▆█  WPA2
```

Connect to the WiFi:
```bash
nmcli d wifi connect my_wifi password <password>
```

Check if WiFi is set to autoconnect:
```bash
nmcli -f name,autoconnect connection
NAME                AUTOCONNECT
my_wifi             no

sudo nmcli con mod mywifi connection.autoconnect yes
NAME                AUTOCONNECT
my_wifi             yes
```