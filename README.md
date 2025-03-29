# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
# REG NO: 212224040022
#
## AIM:
 To write a python program for implementation of sliding window protocol
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM:
## client:
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames:"))
l=list(range(size))
s=int(input("Enter window size:"))
st=0
i=0
while True:
    while(i<len(l)):
        st+=s
        c.send(str(l[i:st]).encode())
        ack=c.recv(1024).decode()
        if ack:
            print(ack)
            i+=s
```
## server:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknoledgement recieved from the server".encode())
```
## OUTPUT:
## client:
![Screenshot 2025-03-29 104413](https://github.com/user-attachments/assets/99197c64-4e6f-469f-9745-10e854015129)


## server:
![Screenshot 2025-03-29 104418](https://github.com/user-attachments/assets/1b35b1da-8fe9-4ce6-8568-5378d17d76e8)


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
