# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL

## AIM
To implementation of Sliding Window Protocol

## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
   
## PROGRAM

### Client 
```
import socket

# Create a socket object
s = socket.socket()

# Bind the socket to localhost and port 8000
s.bind(('localhost', 3000))

# Listen for incoming connections
s.listen(5)

c, addr = s.accept()

size = int(input("Enter number of frames to send: "))

l = list(range(size))

window_size = int(input("Enter Window Size: "))
st = 0
i = 0
while True:
    while i < len(l):
        st += window_size
        c.send(str(l[i:st]).encode())
        ack = c.recv(1024).decode()
        if ack:
            print(ack)
            i += window_size

```
### Server
```
import socket 
s=socket.socket() 
s.connect(('localhost',3000)) 
while True:    
    print(s.recv(1024).decode()) 
    s.send("acknowledgement recived from the server".encode())

```
## OUPUT

### Client 
![CN Lab02-b (Cli)](https://github.com/SivaramakrishnanBaskar/2b_SLIDING_WINDOW_PROTOCOL/assets/119476322/6d0e285e-682a-477c-a866-20b3ad56080b)

### Server
![CN Lab02-b (Ser)](https://github.com/SivaramakrishnanBaskar/2b_SLIDING_WINDOW_PROTOCOL/assets/119476322/cd446bbf-7444-44ca-8d94-f3a2c1a133c8)


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
