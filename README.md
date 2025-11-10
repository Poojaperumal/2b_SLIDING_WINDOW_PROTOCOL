# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
### SERVER
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send : "))
l=list(range(size))
s=int(input("Enter Window Size : "))
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
### CLIENT
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement recived from the server".encode())
```
## OUTPUT
### CLIENT

<img width="632" height="211" alt="Screenshot 2025-11-10 180903" src="https://github.com/user-attachments/assets/9fdbd07e-39fe-4046-859a-b74918741879" />



### SERVER

<img width="686" height="202" alt="Screenshot 2025-11-10 180919" src="https://github.com/user-attachments/assets/33b983c9-0ed8-478d-ba1c-8c13ad9ae4f7" />


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
