# 2c.SIMULATING ARP /RARP PROTOCOLS
## NAME : DHANUSHA K
## NAME : 212223040034
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
## Client
```
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
## Server
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
```
## OUPUT - ARP
## client
![Screenshot 2024-10-01 090949](https://github.com/user-attachments/assets/6d272839-4cad-457f-b32d-a2d673d3bca9)

## Server
![Screenshot 2024-10-01 090724](https://github.com/user-attachments/assets/2718b53d-cec0-4ab4-8ee5-b582985ffa40)

## PROGRAM - RARP

## client
```
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
## server
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
    ip=input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address",s.recv(1024).decode())
```
## OUPUT -RARP
## client
![Screenshot 2024-10-01 092447](https://github.com/user-attachments/assets/779eafe4-6881-497e-8fd0-890562589ac3)

## server
![Screenshot 2024-10-01 091820](https://github.com/user-attachments/assets/094f0513-640c-4e4b-9e27-b3d24c4b0d37)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
