## Ex. No: 7 – Configure Initial Router Settings
# Date: 05-02-2025
________________________________________
# Objective
To perform basic router configuration tasks in Cisco Packet Tracer including:<br>
•	Verifying the default router configuration.<br>
•	Configuring initial router settings (hostname, MOTD, passwords).<br>
•	Securing access to the CLI and console port.<br>
•	Encrypting passwords.<br>
•	Verifying and saving the configuration to NVRAM and flash.<br>
________________________________________<br>
# Apparatus/Tools Required
•	Cisco Packet Tracer<br>
•	1 Router (R1 – 2911 or equivalent)<br>
•	1 PC (for console connection)<br>
•	Console cable (RS-232 to Console)<br>
________________________________________<br>
# Network Topology Diagram

<img width="858" height="581" alt="492225262-85906d79-169a-4211-8873-bf331115c8cf" src="https://github.com/user-attachments/assets/dba8200c-5a63-464e-a4e3-ffb3198d8ced" />

________________________________________
# Procedure
# Part 1: Verify the Default Router Configuration
1.	Connect PC → Router R1 using a Console cable.<br>
2.	On PC → Desktop → Terminal → Connect to R1.<br>
3.	Enter privileged EXEC mode:<br>
4.	Router> enable<br>
5.	Router#<br>
6.	Display running configuration:<br>
7.	Router# show running-config<br>
o	Observe hostname, interfaces, vty lines.<br>
8.	Display startup configuration:<br>
9.	Router# show startup-config<br>
o	Router shows: startup-config is not present (because nothing is saved in NVRAM yet).<br>
________________________________________
# Part 2: Configure and Verify Initial Router Configuration
1.	Enter global configuration mode:<br>
2.	Router# configure terminal<br>
3.	Configure hostname:<br>
4.	Router(config)# hostname R1<br>
5.	Configure MOTD banner:<br>
6.	R1(config)# banner motd # Unauthorized access is strictly prohibited #<br>
7.	Configure passwords:<br>
o	Console password:<br>
o	R1(config)# line console 0<br>
o	R1(config-line)# password letmein<br>
o	R1(config-line)# login<br>
o	R1(config-line)# exit<br>
o	Enable password (unencrypted):<br>
o	R1(config)# enable password cisco<br>
o	Enable secret (encrypted):<br>
o	R1(config)# enable secret itsasecret<br>
8.	Encrypt all plain-text passwords:<br>
9.	R1(config)# service password-encryption<br>
10.	Exit and verify login prompts:<br>
o	On exit, router shows MOTD.<br>
o	User is prompted for password.<br>
o	Enter letmein (console) → access User EXEC mode.<br>
o	Enter itsasecret → access Privileged EXEC mode.<br>
________________________________________
# Part 3: Save the Running Configuration
1.	Save running configuration to NVRAM:<br>
2.	R1# copy running-config startup-config<br>
Short version:<br>
R1# wr<br>
3.	Verify NVRAM contents:<br>
4.	R1# show startup-config<br>
o	Confirms saved configuration.<br>
5.	Save startup config to flash (backup):<br>
6.	R1# copy startup-config flash<br>
o	Use show flash to verify file stored in flash.<br>
________________________________________
# Commands Used
•	To enter privileged mode: enable<br>
•	To view config: show running-config, show startup-config<br>
•	To configure hostname: hostname<br>
•	To configure MOTD banner: banner motd<br>
•	To set passwords: enable password, enable secret, line console<br>
•	To encrypt passwords: service password-encryption<br>
•	To save configuration: copy running-config startup-config, wr, copy startup-config flash<br>
________________________________________
# Output (Attach Screenshots)
•	Console connection to router<br>
•	Running configuration before and after<br>
•	MOTD banner display<br>
•	Password prompts<br>

<img width="1919" height="1079" alt="exp7-1" src="https://github.com/user-attachments/assets/94e1ce96-4194-454b-a4d0-d21807e7b5ee" />

<img width="957" height="1007" alt="image" src="https://github.com/user-attachments/assets/d7aaa333-e95b-4ef9-8ce2-8c58b8811831" />


•	Saved configuration in NVRAM and flash<br>

<img width="961" height="1079" alt="exp7-2" src="https://github.com/user-attachments/assets/bb5e5196-1a3b-4592-b9fb-67486466955e" />

<img width="1172" height="1008" alt="image" src="https://github.com/user-attachments/assets/44574fc6-096e-448f-a74f-665cd972bfc2" />

<img width="954" height="1012" alt="image" src="https://github.com/user-attachments/assets/e26232b8-2139-4029-aa42-a811d6badfd6" />

<img width="959" height="1017" alt="image" src="https://github.com/user-attachments/assets/99517de3-ffb6-4834-bfd0-f7379ef0d35b" />

<img width="1919" height="1017" alt="image" src="https://github.com/user-attachments/assets/693c3008-3024-4789-9189-3d69d4756750" />

________________________________________
# Result
The router was successfully configured with hostname, banner, encrypted passwords, and secure console access. The configuration was verified and saved to NVRAM and flash, ensuring persistence across reboots.

