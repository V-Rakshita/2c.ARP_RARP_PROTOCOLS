# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
P
## PROGRAM - ARP
### Client:
```python
import socket 
s=socket.socket() 
s.connect(('localhost',8000)) 
while True:  
    ip=input("Enter logical Address : ") 
    s.send(ip.encode()) 
    print("MAC Address",s.recv(1024).decode()) 
```
### Server:
```python
import socket 
s=socket.socket() 
s.bind(('localhost',8000)) 
s.listen(5) 
c,addr=s.accept() 
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"}; 
while True: 
            ip=c.recv(1024).decode() 
            try: 
                c.send(address[ip].encode()) 
            except KeyError: 
                c.send("Not Found".encode()) 
```
## OUPUT - ARP
### Server
<img width="821" height="43" alt="image" src="https://github.com/user-attachments/assets/7adfed02-2365-45cc-8b07-ff76d7bdfa1b" />

### Client
<img width="868" height="153" alt="image" src="https://github.com/user-attachments/assets/5858bc69-d79f-4a34-ac5e-252dc14edb1c" />

## PROGRAM - RARP
### Client:
```python
import socket 
s=socket.socket() 
s.connect(('localhost',9000)) 
while True: 
    ip=input("Enter MAC Address : ") 
    s.send(ip.encode()) 
    print("Logical Address",s.recv(1024).decode())
```
### Server:
```python
import socket 
s=socket.socket() 
s.bind(('localhost',9000)) 
s.listen(5) 
c,addr=s.accept() 
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"}; 
while True: 
            ip=c.recv(1024).decode() 
            try: 
                c.send(address[ip].encode()) 
            except KeyError: 
                c.send("Not Found".encode())
```
## OUPUT -RARP
### Server
<img width="841" height="102" alt="image" src="https://github.com/user-attachments/assets/ec5deea4-b903-4076-9f3e-06907e9e2fc5" />

### Client
<img width="861" height="193" alt="image" src="https://github.com/user-attachments/assets/e4759cfd-5531-47b5-8bd6-83780cc56fd2" />


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
