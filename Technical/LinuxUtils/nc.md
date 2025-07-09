---
tags: Linux, Utils, nc, network, diag, diagnostic, diagnostics, diagnosis
alias: []
created: 2025-07-08
updated:
source:
---

# `nc` Command Note
`nc` is a network read/write of netowrk connections tool, it can play two main roles:
- **In client end**: Connected to a port of ther remote server, and it can send some packet to the server, or just listen the port.
- **In server end**: Listen a port, and waiting for client to connect, then it can interactive with client.

## Command Basic Usage
`nc [-option] [host-ip] [port]`
Command format:
```bash
nc -vz 192.168.1.168 8080
# It may output 'Connection to 192.168.1.135 8022 port [tcp/*] succeeded!'
# or refuse: "nc: connect to 192.168.1.135 port 8022 (tcp) failed: Connection refused"
```

Option:
`-v`: Show detail of connection info and progress, It huge help to diagnose the problem of connection.
`-z`: zero-I/O, it mean `nc` will not sned or recive any packet when connected, it ject try to connect and discommect immidiatly.
`-l`: Listen, `nc` will listen the port which specified, and wait for connection. 

Example:
- In client end: 
	```bash
	nc example.com 80
	# It will entry connection mode, now can send the HTTP request.
	GET / HTTP/1.1
	Host: exmple.com
	
	# type Enter two time.
	# and you can see the response head information.
	```
- In server mode:
	```bash
	nc -l 8888
	# listening port 8888.	
	```
	and now you can try to connected to server on client end.
	```bash
	nc [server_ip] 8888
	# now can interactive with server
	# like chat with server
	```