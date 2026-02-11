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
Server.py:
```
import socket
s = socket.socket()
s.connect(('localhost', 8002))
while True:
    print(s.recv(1024).decode())
    s.send("Acknowledgement received from the server".encode())
```
Client.py:
```
import socket
s = socket.socket()
s.bind(('localhost',8002))
s.listen(5)
c, addr = s.accept()
ListSize = int(input("Enter the number of frames to send : "))
List = list(range(ListSize))
WindowSize = int(input("Enter Window Size : "))
st, i = 0, 0
while True:
    while(i < ListSize):
        st += WindowSize
        c.send(str(List[i:st]).encode())
        Acknowledgment = c.recv(1024).decode()
        if Acknowledgment:
            print(Acknowledgment)
            i+=st
```
## OUPUT
Server.py:
<img width="1151" height="963" alt="image" src="https://github.com/user-attachments/assets/b0d98580-6354-4e17-bfce-7ca23c5428d4" />
Client.py:
<img width="1154" height="899" alt="image" src="https://github.com/user-attachments/assets/c0a3c16a-56f5-473f-a1de-7efe67a7e70f" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
