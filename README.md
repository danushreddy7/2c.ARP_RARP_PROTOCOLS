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
## PROGRAM - ARP:
# CLIENT:
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
 # SERVER:
 import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
 ip=input("Enter logical Address : ")
 s.send(ip.encode())
 print("MAC Address",s.recv(1024).decode())
## OUPUT - ARP:
# CLIENT:

![Screenshot 2024-04-27 115750](https://github.com/danushreddy7/2c.ARP_RARP_PROTOCOLS/assets/149035740/35bdc756-0550-41b6-a9ad-dfb4710da4cf)
# SERVER:

![Screenshot 2024-04-27 115750](https://github.com/danushreddy7/2c.ARP_RARP_PROTOCOLS/assets/149035740/05f54bed-e590-45c9-ada7-b96b4491bf1c)

## PROGRAM - RARP:
# CLIENT:
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
 # SERVER:
 import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
 ip=input("Enter MAC Address : ")
 s.send(ip.encode())
 print("Logical Address",s.recv(1024).decode())
## OUPUT -RARP:
# CLIENT:

![Screenshot 2024-04-13 112851](https://github.com/danushreddy7/2c.ARP_RARP_PROTOCOLS/assets/149035740/cea6c1cf-3a00-408a-95c9-4ed0bb113d29)
# SERVER:

![Screenshot 2024-04-13 113028](https://github.com/danushreddy7/2c.ARP_RARP_PROTOCOLS/assets/149035740/269e46b2-c4dc-4ab1-94bf-136d88439b9d)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
