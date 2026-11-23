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
server.py
~~~
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)

print("Server waiting for client...")
c, addr = s.accept()

while True:
    i = input("Enter a data: ")

    if i.lower() == "exit":
        break

    c.send(i.encode())

    ack = c.recv(1024).decode()

    if ack:
        print("Acknowledgement:", ack)
    else:
        break

c.close()
s.close()
~~~
client.py
~~~
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    data = s.recv(1024).decode()

    if not data:
        break

    if data.lower() == "exit":
        print("Server disconnected")
        break

    print("Received data:", data)

    ack = "ACK: Data received"
    s.send(ack.encode())

s.close()
~~~
## OUTPUT
<img width="1023" height="320" alt="image" src="https://github.com/user-attachments/assets/a9be9879-2856-4a6b-92d5-94172dc87bc8" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
