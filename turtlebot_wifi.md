# Connecting the Turtlebot to MWireless

You can connect to MWireless using the parameters specified by a wpa\_supplicant file.  



```
$ sudo wpa_cli -i wlan0
```
This opens an interactive cli version of wpa. Enter these commands to connect to mwireless:

```
> add_network
(returns a number you'll use for following commands, assume 0 for now)
> set_network 0 ssid "MWireless"
> set_network 0 key_mgmt WPA-EAP
> set_network 0 eap PEAP
> set_network 0 identity "me-rousewifi"
> set_network 0 password hash:<hash value>
> enable network 0
(will print some stuff)
> quit
```  
Replace <hash value> with the password found in this UM-protected google sheet: [https://bit.ly/30zEzPCRPi](https://bit.ly/30zEzPCRPi)  


This is basically doing what a supplicant file would do, manually. I set the values based on the [supplicant file from neurobionics](https://github.com/neurobionics/neurobionicspi/blob/main/wpa_supplicant.Pifile). You should be able to do this automatically with the supplicant file, but I was having some issues. If the supplicant doesn't work, we can probably have a script run on startup that does this.  


