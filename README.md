# Echoserver
Echo server and client using python socket

# AIM:

To develop a simple webserver to serve html programming pages.

## DESIGN STEPS:

### Step 1:

Design of echo server and client using python socket

### Step 2:

Implementation using Python code

### Step 3:

Testing the server and client 

## PROGRAM:
```client.py

import socket
HOST = "127.0.0.1"  # The server's hostname or IP address
PORT = 65432  # The port used by the server
with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
    s.connect((HOST, PORT))
    s.sendall(b"Atchaya,03/03/25")
    data = s.recv(1024)

print(f"Received {data!r}")



server.py
import socket

HOST = "127.0.0.1"  # Standard loopback interface address (localhost)
PORT = 65432  # Port to listen on (non-privileged ports are > 1023)

with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
    try:
        s.bind((HOST, PORT))
    except Exception as e:
        print(f"Error binding to {HOST}:{PORT}: {e}")
        exit()

    s.listen()
    print(f"Listening on {HOST}:{PORT}...")

    conn, addr = s.accept()  # Accept client connection
    with conn:
        print(f"Connected by {addr}")
        while True:
            try:
                data = conn.recv(1024)
                if not data:
                    break
                conn.sendall(data)  # Echo back
            except Exception as e:
                print(f"Error receiving/sending data: {e}")
                exit()
```


## OUTPUT:
![Screenshot 2025-03-28 103802](https://github.com/user-attachments/assets/846ba766-b572-433d-aede-4d89d0c52aa9)


## RESULT:
The program is executed successfully
