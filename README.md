# 2c.SIMULATING ARP /RARP PROTOCOLS
## NAME:SANJAY AHWIN P
## REG NO:212223040181
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
### Server:
import socket   
s = socket.socket()   
s.connect(('localhost',8000))   
while True:   
    ip = input("Enter logical address: ")   
    s.send(ip.encode())   
    print("MAC Address",s.recv(1024).decode())  
## OUPUT - ARP
### client:
![Screenshot 2024-04-09 171431](https://github.com/sanjayashwinP/2c.ARP_RARP_PROTOCOLS/assets/147473265/4bc2bdd2-b31c-477e-8121-df29e0481d5f)
### server:
![Screenshot 2024-04-09 171521](https://github.com/sanjayashwinP/2c.ARP_RARP_PROTOCOLS/assets/147473265/c17ae337-01aa-4d7c-8eff-3c2473ac5ed6)

## PROGRAM - RARP
### Client:
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
### Server:
import socket     
s = socket.socket()          
s.connect(('localhost',8000))     
while True:    
    ip = input("Enter MAC address: ")     
    s.send(ip.encode())                           
    print("Logical Address",s.recv(1024).decode())      
## OUPUT -RARP
### Client:
![Screenshot 2024-04-09 172725](https://github.com/sanjayashwinP/2c.ARP_RARP_PROTOCOLS/assets/147473265/0abdd3f0-f256-4528-85de-5d06b5769aaf)

### Server:
![Screenshot 2024-04-09 172803](https://github.com/sanjayashwinP/2c.ARP_RARP_PROTOCOLS/assets/147473265/d03be8b1-e702-4c5c-8017-dd6ce9fa8977)
    
## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
