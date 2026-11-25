# 2a_Stop_and_Wait_Protocol
## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
CLIENT
```
import socket

s = socket.socket()
s.connect(('localhost', 12345))

n = int(input("Enter number of frames: "))

for i in range(n):
    frame = input("Enter frame: ")

    s.send(frame.encode())

    ack = s.recv(1024).decode()

    print("Frame sent:", frame)
    print("Acknowledgement received:", ack)

s.close()
```
SERVER
```
import socket

s = socket.socket()
s.bind(('localhost', 12345))
s.listen(1)

print("Waiting for sender...")

c, addr = s.accept()
print("Sender connected")

while True:
    frame = c.recv(1024).decode()

    if not frame:
        break

    print("Frame received:", frame)

    c.send("ACK".encode())

    print("Acknowledgement sent")

c.close()
s.close()
```
## OUTPUT
<img width="1310" height="612" alt="image" src="https://github.com/user-attachments/assets/0982b8aa-4a42-4856-a57d-f1cf1777163b" />


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
