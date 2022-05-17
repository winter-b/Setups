# Domain, ip range and port blocking in Windows

# Tested in Windows 11

## Domain blocking using hosts file
### First find the directory in which windows hosts file is kept. Open 'ragedit.exe' under 'C:\Windows'
### In ragedit go to 'HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters' and the hey is 'DataBasePath' 
![image](https://user-images.githubusercontent.com/85021800/168692089-31185645-5bd2-4530-9f61-805f88177b31.png)
### For my machine it is 'C:\Windows\System32\drivers\etc'

### Open hosts file and add the following line to redirect domain to localhost
![image](https://user-images.githubusercontent.com/85021800/168692900-231da624-36b6-4273-88d6-22426c10fc9c.png)
## Ip/ip range blocking using firewall
### Open Windows Defender Firewall with Advanced Security and create a new 'Outbound rule'
### Select Custom
![image](https://user-images.githubusercontent.com/85021800/168787894-4a3c18ec-276d-49df-a7a0-c095be841051.png)
### Select all programs
![image](https://user-images.githubusercontent.com/85021800/168787951-61042b71-700d-4d24-86a0-b001299a2eac.png)
### Select any protocol type
![image](https://user-images.githubusercontent.com/85021800/168788088-37190e26-30ec-40bb-9758-81882722d8d3.png)
### Add ip range or ip under remote ip address
![image](https://user-images.githubusercontent.com/85021800/168789365-acc83235-0c57-4714-a85d-742d6d19da6f.png)
### Block connection
![image](https://user-images.githubusercontent.com/85021800/168789488-11787a48-7c4c-4a3c-8bfd-9cda57540e36.png)
### All spaces
![image](https://user-images.githubusercontent.com/85021800/168789560-5ff8da19-4fac-4df4-8d85-34c3346ce66b.png)
### Give name
![image](https://user-images.githubusercontent.com/85021800/168789740-dc84a471-8ac9-4559-9501-0c2f9499e9e8.png)

### Test
![image](https://user-images.githubusercontent.com/85021800/168786602-ba4353bd-2f56-4efe-a696-0cf4dc78af29.png)

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

## View activiy logs
### Use windows integrated event viewer or download more advanced Process monitor from Sysinternals [link to download](https://docs.microsoft.com/en-us/sysinternals/downloads/procmon)
