## À quoi sert Netcat ?

**Netcat** or **nc**, is a well-known network analysis tool, also known as the Swiss army knife of hackers, because it has many features, similar to the described knife.

---

### Netcat Cheat Sheet

| **Options**       | **Description**                                                                                                                                                                                                                                 |
| ----------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| -4                | Forces the use of IPv4 (GNU Netcat)                                                                                                                                                                                                             |
| -6                | Forces the use of IPv6 (GNU Netcat)                                                                                                                                                                                                             |
| -d                | Releases Netcat from the console (running in the background; available in Windows and current GNU Netcat versions)                                                                                                                              |
| -D                | Activates the option for debugging sockets (GNU Netcat)                                                                                                                                                                                         |
| -h (display help) | Displays help (commands/options with a short description)                                                                                                                                                                                       |
| -i (secs)         | Delays in seconds for sent lines or scanned ports                                                                                                                                                                                               |
| -k                | At the end of a connection, Netcat waits for a new connection (only possible with GNU Netcat and only in combination with “-l”)                                                                                                                 |
| -l (listen mode)  | Listen and server mode for incoming connection requests (via port indicated)                                                                                                                                                                    |
| -L Listen harder  | Netcat also continues to operate in listen mode after client-side connection terminations (consistently with the same parameters; only supported by the Windows version)                                                                        |
| -n (numeric only) | Only IP numbers, no DNS names                                                                                                                                                                                                                   |
| -o (file)         | A hex dump is carried out for the data traffic (content of files represented in a hexadecimal view); used for fault finding (debugging network applications); recording/sniffing communication is possible (for outgoing and incoming packages) |
| -p (port)         | Enters the local source port that Netcat should use for outgoing connections                                                                                                                                                                    |
| -r                | Use of random port values when scanning (for local and remote ports)                                                                                                                                                                            |
| -s (address)      | Defines the local source address (IP address or name)                                                                                                                                                                                           |
| -t                | Telnet mode (enables server contact via Telnet); requires a special compilation of Netcat, otherwise the option is not available.                                                                                                               |
| -u                | Use of UDP mode (instead of TCP)                                                                                                                                                                                                                |
| -U (gateway)      | Netcat uses Unix domain sockets (GNU Netcat)                                                                                                                                                                                                    |
| -v                | Extensive output (e.g. responsible for the display and scope of displayed fault messages)                                                                                                                                                       |
| -w (secs)         | Defines timeouts; for establishing and terminating connections (unit: seconds)                                                                                                                                                                  |
| -z                | Port scanner mode (zero I/O mode); only listening services are scanned (no data is sent)                                                                                                                                                        |

- Netcat listening on port 567/TCP :

```bash
nc -lnvp 567
```

- Connecting to that port from another machine :

```bash
nc 1.2.3.4 -p 567
```

- To pipe a text file to the listener :

```bash
cat infile | nc 1.2.3.4 -p 567 -q 10
```

- To have the listener save a received text file :

```bash
nc -lnvp 567 > textfile
```

- To transfer a directory, first at the receiving end set up :

```bash
nc -lnvp 678 | tar xvfpz
```

- Then send the directory :

```bash
tar zcfp - /path/to/directory | nc -w 3 1.2.3.4 -p 678
```

- To send a message to your syslog server (the <0> means emerg) :

```bash
echo '<0>message' | nc -w 1 -u syslogger -p 514
```

- Setting up a remote shell listener (reverse shell) :

```bash
nc -v -e '/bin/bash' -l -p 1234 -t
```

or

```bash
nc l -p 1234 -e "c:\windows\system32\cmd.exe"
```

Then telnet to port 1234 from elsewhere to get the shell.

- Using netcat to make an HTTP request :

```bash
echo -e "GET http://www.google.com HTTP/1.0nn" | nc -w 5 www.google.com 80
```

- Making a one-page webserver; this will feed homepage.txt to all comers :

```bash
cat homepage.txt | nc -v -l -p 80
```

- and if you want to create an tty for made an text communication by tty share :

```bash
cat /dev/tty | nc LISTENER_IP 4444
```

```bash
nc -lnvp 4444
```
