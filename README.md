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
## SERVER CODE:
```

import socket

# Create server socket
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

host = '127.0.0.1'
port = 5000

server_socket.bind((host, port))
server_socket.listen(1)

print("Server waiting for connection...")

client_socket, addr = server_socket.accept()
print("Connected to:", addr)

# Open and read file
file = open("sample.txt", "rb")
data = file.read()

# Send file to client
client_socket.sendall(data)

print("File sent successfully")

file.close()
client_socket.close()
server_socket.close()
```
## CLIENT CODE
```

import socket

# Create client socket
client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

host = '127.0.0.1'
port = 5000

client_socket.connect((host, port))

print("Connected to server")

# Receive file from server
with open("received.txt", "wb") as file:
    while True:
        data = client_socket.recv(1024)

        if not data:
            break

        file.write(data)

print("File received successfully")

client_socket.close()
```

## OUPUT

<img width="521" height="112" alt="image" src="https://github.com/user-attachments/assets/ed7b2899-fb61-4d50-9e52-fb5d43a7bdca" />

<img width="527" height="91" alt="image" src="https://github.com/user-attachments/assets/119743d8-e547-46ef-8e96-66cd635712db" />


<img width="433" height="110" alt="image" src="https://github.com/user-attachments/assets/4dd1f374-6cd9-4446-9b0e-feaa75a46124" />

<img width="442" height="110" alt="image" src="https://github.com/user-attachments/assets/35934b67-686c-429c-93e9-cd9b57fc3bb7" />

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
