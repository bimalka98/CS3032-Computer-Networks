# Modes of operation


```
// =============================User Execution Mode============================
Router>
router> ? --> show all the possible commands

// ===============================Privilege Mode===============================
Router>
Router> enable
Router#
Router# ? --> show all the possible privileges

// =========================Global Configuration Mode==========================
Router>
Router> enable
Router#
Router# configure terminal
Router(config)#
Router(config)# ? --> show all the possible configurations

```
# Tasks under above modes

|Mode|Command|Task|
|:---|:---|:---|
|Privilege|show version| Version of the Router|
|Privilege|show running-config|Shows current configurations(what is in volatile memory)|
|Privilege|show startup-config|Shows startup configurations(what is in non-volatile memory)|
|Global|hostname <your-hostname-here>| Change name of the Router|
|Privilege|reload| Reload the Router|
|Privilege|write|Save to Non-volatile memory|
|Privilege|copy running-config startup-config| Write to Non-volatile memory|
|Global|enable password <your-password-here>| Give a password to the Router. Password is not encrypted |
|Global|enable secret <your-password-here>| Give a password to the Router. Password is encrypted |
|Global|banner motd <#WARNING: your-message to display when initializing user execution mode>|When users connect to the router, the "Message Of The Day (MOTD)" banner is presented|
