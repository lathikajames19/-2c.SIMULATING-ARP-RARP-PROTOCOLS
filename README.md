# -2c.SIMULATING-ARP-RARP-PROTOCOLS
## Developed by : LATHIKA .K
## Reg no : 212224230140

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

## Client:
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

## Server:
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

## Client:
![Screenshot 2025-04-26 105716](https://github.com/user-attachments/assets/f383cf0f-ae55-44bd-8f31-7abe389b4fb3)

## Server:
![image](https://github.com/user-attachments/assets/0c964e8d-1f84-457c-b337-f898852ce702)

## PROGRAM - RARP

## client:
```import socket
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
```import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
    ip=input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address",s.recv(1024).decode())

```

## OUPUT -RARP

## client:
![image](https://github.com/user-attachments/assets/add85a13-518c-49d9-aacc-adf9a962d979)

## server:
![image](https://github.com/user-attachments/assets/8b5e0de3-a141-4fe5-a33d-19e84813af1e)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
