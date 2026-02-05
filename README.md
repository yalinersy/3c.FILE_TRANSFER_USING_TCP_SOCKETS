# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
## Client
```
import socket

s = socket.socket()
host = socket.gethostname()
port = 12345

s.connect((host, port))
s.send("Hello server!".encode())

with open('received_file.txt', 'wb') as f:
    while True:
        print('receiving data...')
        data = s.recv(1024)
        print('data=%s' % (data))
        if not data:
            break
        f.write(data)

print('Successfully got the file')
s.close()
print('connection closed')

```

## Server
```
import socket

port = 12345
s = socket.socket()
host = socket.gethostname()

s.bind((host, port))
s.listen(5)

print("Server waiting for connection...")

conn, addr = s.accept()
print("Connected from:", addr)

# receive message from client
msg = conn.recv(1024).decode()
print("Client says:", msg)

# open file and send
with open('sample.txt', 'rb') as f:
    while True:
        data = f.read(1024)
        if not data:
            break
        conn.send(data)

print("File sent successfully")

conn.close()
s.close()

```
## OUTPUT
## Client
<img width="576" height="118" alt="image" src="https://github.com/user-attachments/assets/fa8b3ea2-0c82-4cbb-91a5-298634ec0167" />

## Server
<img width="568" height="93" alt="image" src="https://github.com/user-attachments/assets/4fb45524-7716-4c02-be93-dc4758e0630b" />

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
