# RootMe

## Deploy the machine
> No answer needed

========================================================================================================

Những câu ở task 2 thì chỉ cần **nmap** phát là nó ra hết à...

Đây là kết quả sau khi nmap máy mục tiêu
```c
└─$ cat scan_result     
# Nmap 7.94 scan initiated Mon Oct 16 21:56:44 2023 as: nmap -sC -sV -oN nmap/scan_result 10.10.36.56
Nmap scan report for 10.10.36.56
Host is up (0.28s latency).
Not shown: 998 closed tcp ports (conn-refused)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 4a:b9:16:08:84:c2:54:48:ba:5c:fd:3f:22:5f:22:14 (RSA)
|   256 a9:a6:86:e8:ec:96:c3:f0:03:cd:16:d5:49:73:d0:82 (ECDSA)
|_  256 22:f6:b5:a6:54:d9:78:7c:26:03:5a:95:f3:f9:df:cd (ED25519)
80/tcp open  http    Apache httpd 2.4.29 ((Ubuntu))
|_http-title: HackIT - Home
| http-cookie-flags: 
|   /: 
|     PHPSESSID: 
|_      httponly flag not set
|_http-server-header: Apache/2.4.29 (Ubuntu)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Mon Oct 16 21:57:34 2023 -- 1 IP address (1 host up) scanned in 49.66 seconds
```
## Scan the machine, how many ports are open?
> 2
## What version of Apache is running?
> 2.4.29
## What service is running on port 22?
> ssh
## Find directories on the web server using the GoBuster tool.
> No answer needed
## What is the hidden directory?
 Với file ẩn thì dùng GoBuster để tìm

    gobuster dir -w /usr/share/wordlists/dirb/common.txt 10.10.185.22

 Và đây là kết quả:
 ```c
===============================================================
Gobuster v3.6
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://10.10.185.22
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/wordlists/dirb/common.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.6
[+] Timeout:                 10s
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
/.hta                 (Status: 403) [Size: 277]
/.htpasswd            (Status: 403) [Size: 277]
/.htaccess            (Status: 403) [Size: 277]
/css                  (Status: 301) [Size: 310] [--> http://10.10.185.22/css/]
/index.php            (Status: 200) [Size: 616]
/js                   (Status: 301) [Size: 309] [--> http://10.10.185.22/js/]
/panel                (Status: 301) [Size: 312] [--> http://10.10.185.22/panel/]
/server-status        (Status: 403) [Size: 277]
/uploads              (Status: 301) [Size: 314] [--> http://10.10.185.22/uploads/]
Progress: 4614 / 4615 (99.98%)
===============================================================
Finished
===============================================================```

