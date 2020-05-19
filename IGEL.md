# IGEL

## Linux General

|command|description|example|
|-|-|-|
|echo|Output Strings|`echo "hello world"`|
|cd|Change folder|`cd /wfs/`|
|cp|Copy||
|chmod|Change file attributes|`chmod +x /wfs/new.sh`|
|mkdir|Create a folder||
|rmdir|Delete a folder||
|rm|Delete a file||
|ls|Show directory content||
|su|Change to root||
|vi|Texteditor||
|kill|Kill a running task by process id||
|killall|Kill a running task by name|`killall pnlogin 2>/dev/null`|
|ps|Show running tasks||
|cat|Display a file||
|more|Display a file page by page|`more /wfs/group.ini`|
|mount|Mount a partition||
|user_shutdown|Shutdown the system||
|user_reboot|Reboot the system||
|grep|Search for regular expression|more /wfs/setup.ini \| grep structure|
|top|Task Monitor||
|killall|Kill process by name||
|sleep|Wait||
|watch|Repeat periodic a command||
|which|Locate command||
|uname|Show Linux details||
|date|Date tool||
|systemctl|service handler|`systemctl restart networkmanager`|

## Network general

|command|description|example|
|-|-|-|
|ping / ping6|Ping IPV4 / Ping IPV6||
|/etc/init.d/network restart|Restart network service||
|ftp|Start a FTP Client||
|netstat|Display open connections||
|hostname|Display current hostname||
|route|Display/Config network routes||
|iptables|Firewall configuration||
|probeport|Test network port on a host||
|nmcli|Manage network connections via CLI||
|ifconfig|Ethernet configuration||
|iwconfig|WIFI configuration||
|ethtool|Tool for ethernet configuration||
|getmyhwaddr|Show current MAC ID's||
|getmyip|Show current IP||
|iwgetid|Report ESSID||
|iwlist|Scan for available WIFI networks||
|iwevent|Display wireless events||
|iwspy|Provide WIFI information's||

## Linux pipes

|command|description|
|-|-|
|>|Write output into a new file|
|>>|Extend file with output|
|\|Output is input for next process||

## Hardware

|command|description|
|-|-|
|dmidecode|Provide hardware details|
|lsusb|List USB devices|
|lspci|List PCI devices|
|rtcwake|Automatic restart/supend|
|speaker-test|Speaker test|
|aplay|Audio device tool|
|x11config|Show display config|
|get-edid|Display DDC details|
|saned|SANE Daemon|
|hardinfo|Display Hardware Info's|
|setserial|Setup/Diagnostic for RS232|
|amixer|Audio configuration tool|
|free|Show memory details|

## Smart Card

|command|description|
|-|-|
|pcsclistreaders|List Smart Card readers|
|/etc/init.d/pcscd|Stop / Start PCSC Daemon|
|opensc-explorer|Show available readers|
|opensc-tool|Commandline SC Tool|

## Printing related

|command|description|
|-|-|
|lpq|Show current print jobs|
|lpstat|Show finished print jobs|
|lpr|Print a file|
|lpc|Printer control tool|
|lprm|Delete a print job|
|cancel|Cancel the current print job|

## Active directory

|command|description|
|-|-|
|klist|Display kerberos tickets|
|kinit|Active Directory login|

## OS folders

|folder|description|
|-|-|
|/wfs|Configurations / Certs|
|/usr/share/icons|Contains Icons of Linux and Igel|
|/license/dsa/licenses|device licenses|
|/media|Removable Storage|
|/services|License related services|
|/var/logs|Various log files|
|/userhome/.ICAClient/logs|ICA Client logs|

## OS files

|file|description|
|-|-|
|/wfs/setup.ini|Local configuration|
|/wfs/group.ini|Configuration from UMS|
|/wfs/server.crt|UMS Server certificate|
|/wfs/dhclient-*.lease|dhcp client lease; DHCP Option 224 + 226|
|/config/sessions|Generated sessions|
|/tmp/wpa_debug.all|network debug log|

## UMS files

|file|description|
|-|-|
|api.log|IMI interface log|
|catalina.log(.yyyy-mm-dd)|UMS log|
|localhost.log(.yyyy-mm-dd)|Tomcat log|
|communication.log|communication between devices and UMS server / UMS console and UMS server log; empty / deactivated by default, has to be activated in log4j.properties; can be very huge when active|
|usgcommunication.log(.x)|communication between devices and ICG / UMS console and ICG log; empty / deactivated by default, has to be activated in log4j.properties; can be very huge when active|
|license_deployment.log|ALD log|
|stdout.log|like catalina.log but only since last server start|
|stderr.log|JVM error output log; critical VM messages|
|umsthreaddump|UMS ThreadDump|
|igel-ums-admin.log|UMS Administrator log|
|install.log|UMS installation log|
|ERP_PROCESS.log|support information|
|ERP_PROCESS_INFOS.log|support information|
|Environment.txt|support information|
|thread_dump_start.\*|support information|
|thread_dump_end.\*|support information|

## Configuration

|command|description|example|
|-|-|-|
|setup|Start IGEL Setup||
|get|Get Variable from registry||
|vget|Get specification for a variable||
|setparam|Write variable to registry|`setparam system.remotemanager.ums_structure_tag "Building1"`|
|setcryptparam|Write a password to the registry||
|list|List a part of the registry||
|delinstance|Delete a session or instance||
|newinstace|Create a session or instance||
|numinstances|Show next available instance nr.||
|superclasses|List all available superclasses||
|store_usbconfig|Write config to USB Storage||
|load_usbconfig|Load config from USB Storage||
|show_usbconfig|List configs from USB Storage||
|reset_to_defaults|Factory reset||

## Firmware Update

|command|description|
|-|-|
|/config/bin/firmware-update|Start firmware update|

## Custom Partition

|command|description|
|-|-|
|custompart|Delete/Create a custom partition|

## Universal Management Suite

|command|description|
|-|-|
|ums_available|Check available UMS Server|
|rmregister|Start tool to register @ UMS|
|rmagent_cli|UMS Agent commandline|
|get_rmsettings|Get UMS config (reboot to apply)|

## Useful keybindings

|keybinding|description|
|-|-|
|ALT+CTRL+TAB|Switch active window|
|TAB+TAB|Show commands|
|ALT+CTRL+Fx|Switch between console|
|CTRL+ALT+F11|terminal 1|
|CTRL+ALT+F12|terminal 2|
|CTRL+ALT+F1|IGELOS UI|

## Other

|command|description|example|
|-|-|-|
|florence|OnScreen Keyboard||
|notify-send-message|Display GUI Text Message||
|Mostly all commands provide an build-in help with|command --h||
|igel_firstboot_wizard|Starts the First Boot Wizard||
|igel_buddy_update_server_scan|Search for Buddy Masters in network||
|start-wireless-manager|Starts the Wireless cafe menu (start as user)||
|xfce4-display-settings|Start the old Display Switcher as binary||
|igel_gamma|TOCHECK Should influence the brightness||
|igel_display_switcher|Start the new Display Switcher||
|xrandr|Controls the Screens from command line||
|systemd-resolve --flush-caches|Flush DNS cache||
|df -h|Shows Partition usage||
|gpicview|Starts an Picture Viewer||
|user_shutdown|Shutdown as User||
|user_reboot|Reboot as user||
|opensc-tool|Lists opensc smartcard informations and tools||
|apparmor_status|Lists all services protected by apparmor||
|applauncher|Starts the application launcher||
|icg-setup|Start the ICG GUI Setup or with parameters the CLI||
|icaconncenter|ICA Connection Center||
|zenity|Dialog select item|`zenity --list --text "Please select a Citrix  Server" --radiolist -column "Select" --column "Server" Storefront1 "Storefront1" Storefront2 "Storefront2"`|
|zenity|Dialog with progress bar|`zenity --progress --text="Trying to ping 4 times" --percentage="0" --auto-close & ping -c 4`|
|setusercryptparam|Saves User encrypted Data like Password to Igel Registry||
|setcryptparam|Saves encrypted Data like Password to Igel Registry||
|pkcs11getloginname|Shows extracted smart card login name||
|curl https://fqdn.of.website|Command line tool to check for trusted certificate||
|icg-config -s cloud-gateway.info -o 1234|IGEL Cloud Gateway config; with url and mass deployment key||
|nmcli radio wifi off|Disables Wifi, On enables it||
|journalctl -f|Sys logs anzeigen und folgen.||
|systemctl restart network-manager|Restart Network||
|killwait_postsetupd|reset and applay setup changes set by "setparam"||
|write_rmsettings|Write local setup changes back to UMS.||
|getmyip|cut -d. -f1-4|show device IP only.||

## Registry

|Path|description|
|-|-|
|network.interfaces.wirelesslan.device0.wpa.debug|wifi debug|
|network.interfaces.ethernet.devices%.ieee8021x.debug|802.1x debug|