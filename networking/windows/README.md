# Domain, ip range and port blocking in Windows

# Tested in Windows 11

## Domain blocking
### It is possible to do domain blocking in Windows firewall, we'll block it using hosts file.
### First find the directory in which windows hosts file is kept. Open 'ragedit.exe' under 'C:\Windows'
### In ragedit go to 'HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters' and the hey is 'DataBasePath' 
![image](https://user-images.githubusercontent.com/85021800/168692089-31185645-5bd2-4530-9f61-805f88177b31.png)
### For my machine it is 'C:\Windows\System32\drivers\etc'

### Open hosts file and add the following line to redirect domain to localhost
![image](https://user-images.githubusercontent.com/85021800/168692900-231da624-36b6-4273-88d6-22426c10fc9c.png)

## Port blocking

### Open Windows Defender Firewall with Advanced Security and create a new 'Inbound rule'
### Select port
![image](https://user-images.githubusercontent.com/85021800/168693312-12453ffc-4e73-416f-abae-cd5420b9a1b6.png)
### Specify TCP and Port
![image](https://user-images.githubusercontent.com/85021800/168693329-a26f6750-ac7f-4b7d-9d58-6aa439f57f6e.png)
### Select 'Block the connection'
![image](https://user-images.githubusercontent.com/85021800/168693343-de0af877-27ec-4e3b-8281-678dbf665963.png)
### Apply to all spaces
![image](https://user-images.githubusercontent.com/85021800/168693361-fa88e0fa-fd4f-4ccc-92ab-b333c78fcd7b.png)
