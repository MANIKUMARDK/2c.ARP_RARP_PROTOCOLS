# 2c.SIMULATING ARP /RARP PROTOCOLS:
## REG NO:212223230121
## NAME:MANIKUMAR.DK
## AIM:
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## CLIENT:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## SERVER:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.

## PROGRAM - ARP:
## CLIENT:
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,address=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"}
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```
## SERVER:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip = input("Enter logical address: ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
```
## OUPUT - ARP:
## CLIENT:
![image](https://github.com/MANIKUMARDK/2c.ARP_RARP_PROTOCOLS/assets/147215581/c44041f2-1c5d-41f2-bc9e-8762fcfc0d1e)

## SERVER:
![image](https://github.com/MANIKUMARDK/2c.ARP_RARP_PROTOCOLS/assets/147215581/ad9bf47e-ca2c-436b-bd3a-38c00dda9967)

## PROGRAM - RARP:
## CLIENT:
```
import socket
s = socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr = s.accept()
address = {"6A:08:AA:C2":"165.165.80.1","8A:BC:E3:FA":"165.165.79.1"}
while True:
    ip = c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```
## SERVER:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip = input("Enter MAC Address: ")
    s.send(ip.encode())
    print("Logical Address:",s.recv(1024).decode())
```

## OUPUT -RARP:
## CLIENT:
![image](https://github.com/MANIKUMARDK/2c.ARP_RARP_PROTOCOLS/assets/147215581/25550fd5-b125-4d3e-8b74-214a179f05af)

## SERVER:
![image](https://github.com/MANIKUMARDK/2c.ARP_RARP_PROTOCOLS/assets/147215581/ca9b40ed-146e-45c6-90ef-36df2cca6636)

## RESULT:
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
