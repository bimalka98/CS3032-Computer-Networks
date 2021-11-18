# Remember
* Router and PC are of the same network architecture! Use copper crossover cables. Connection made via GigabitEthernet of Router and FastEthernet of PC.
* Switch and PC are of different kinds! Use straight through cables. Connection made via FastEthernet Ports.
* Switch and router are of different kinds! Use straight through cables. Connection made via FastEthernet of switch and GigabitEthernet of Router.

# Most frequently used commands

### Modes of operation


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


### Console into the router and enable privileged EXEC mode.
```
Make a connection between a PC and the Router using console cable.
In PC: RS 232 port
In Router: Console Port
Click on PC -> Desktop-  >Terminal:
Type “no” to not to enter the initial configuration mode!

Router> enable
Router#
```
### Enter configuration mode.
```
Router# configure terminal
```

### Assign a device name to the router.
```
Router(config)# hostname R1 (HOST_NAME)
```

### Disable DNS lookup to prevent the router from attempting to translate incorrectly entered commands as though they were host names.
Why disable? Otherwise, DNS tries to convert everything we input into an IP address! And it get stuck when it cannot find a corresponding IP.

```
Privilege mode -> SOME_ WIERED _SHIT
R1#bimalka98
Translating "bimalka98"...domain server (255.255.255.255) -> THIS WILL RUN UNTIL TIME OUT!
To abort the Lookup: Use Global Escape Sequence for CISCO: CTRL+ ^  (^ IS THE SYMBOL GIVEN BY SHIFT+6)

Disabling DNS Lookup:
Global config Mode-> no ip domain-lookup

R1(config)#no ip domain-lookup
R1(config)#do sdgsgvsdv (EXECUTING PRIVILAGE MODE COMMANDS WITHIN 	GOBAL CONFIG 	MODE)

Translating "sdgsgvsdv"
% Unknown command or computer name, or unable to find computer address
```

### Assign *class* as the privileged EXEC(to enter the privileged mode[Router Password]) encrypted password.

```
R1(config)#enable secret class
```

### Assign cisco as the console password(to enter user execution mode) and enable login.

```
R1(config)#line console 0
R1(config-line)#password cisco
R1(config-line)#login
R1(config-line)#
```

### Assign cisco as the VTY password and enable login.
```
R1(config)#line vty 0 15
R1(config-line)#password cisco
R1(config-line)#login
R1(config-line)#
```

### Encrypt the clear text passwords.
Before encrypting let’s see what the clear text passwords in our running configurations are!
```
R1#show running-config 

Building configuration...
!
!
Current configuration : 751 bytes
!
line con 0
password cisco
login
!
line aux 0
!
line vty 0 4
password cisco
login
line vty 5 15
password cisco
login
!
End
```

Problem is above passwords are in plain text. And therefore visible. Need to encrypt those.
Go to global config mode and type:

```
R1(config)#service password-encryption

Now see the running config again in privilege mode
R1#show running-config
line con 0
password 7 0822455D0A16
login
!
line aux 0
!
line vty 0 4
password 7 0822455D0A16
login
line vty 5 1
password 7 0822455D0A16
login
!
end
```

### Create a banner that warns anyone accessing the device that unauthorized access is prohibited.

```
R1(config)#banner motd "Unauthorized access is prohibited"

Go back to suer execution mode:

Unauthorized access is prohibited
User Access Verification
Password: CONSOLE_PASSWORD
R1>enable
Password: PRIVILEGE_EXEC_ENCRYPTED_PASSWORD
R1#configure terminal
Enter configuration commands, one per line. End with CNTL/Z.
R1(config)#
```

### Configure and activate both interfaces on the router.

```
  R1(config)#interface gigabitEthernet 0/0
	R1(config-if)#ip address 192.168.1.1 255.255.255.0
	R1(config-if)#no shutdown

	R1(config-if)#
	%LINK-5-CHANGED: Interface GigabitEthernet0/0, changed state to up
	%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0, changed state to up

	R1(config)#interface gigabitEthernet 0/1
	R1(config-if)#ip address 192.168.0.1 255.255.255.0
	R1(config-if)#no shutdown

	R1(config-if)#
	%LINK-5-CHANGED: Interface GigabitEthernet0/1, changed state to up
	%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/1, changed state to up

	Now all the cables must be in the active mode 
```

### To remove IP addresses! In case you set the wrong IP address.

```
R1(config)#interface gigabitEthernet 0/1
R1(config-if)#no ip address
R1(config-if)#do show ip interface brief
Interface IP-Address OK? Method Status Protocol 
GigabitEthernet0/0 unassigned YES manual up up 
GigabitEthernet0/1 unassigned YES manual up up 
Vlan1 unassigned YES unset administratively down down
R1(config-if)#
```

### Configure an interface description for each interface indicating which device is connected to it.
```
R1(config)#interface gigabitEthernet 0/0
R1(config-if)#description LAN-A
R1(config-if)#exit
R1(config)#interface gigabitEthernet 0/10
%Invalid interface type and number
R1(config)#interface gigabitEthernet 0/1
R1(config-if)#description LAN-B
R1(config-if)#
```

### set the clock rate on the first serial interface to 64,000 bps:

```
Router(config)# interface serial 0
Router(config-if)# clock rate 64000
```


### Save the running configuration to the startup configuration file.
```
R1#copy running-config startup-config 
Destination filename [startup-config]? 
Building configuration...
[OK]
R1#
```

### Ping PC-B from a command prompt window on PC-A.
```
Packet Tracer PC Command Line 1.0
C:\>ping 192.168.0.1

Pinging 192.168.0.1 with 32 bytes of data:

Reply from 192.168.0.1: bytes=32 time=107ms TTL=255
Reply from 192.168.0.1: bytes=32 time<1ms TTL=255
Reply from 192.168.0.1: bytes=32 time<1ms TTL=255
Reply from 192.168.0.1: bytes=32 time<1ms TTL=255

Ping statistics for 192.168.0.1:
Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
Minimum = 0ms, Maximum = 107ms, Average = 26ms

C:\>
```
