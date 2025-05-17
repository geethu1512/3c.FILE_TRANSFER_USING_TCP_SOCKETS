# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## NAME:GEETHU R
## REGNO:212224040089
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
Client
~~~
import socket 
s = socket.socket() 
host = socket.gethostname() 
port = 60000 
s.connect((host, port)) 
s.send("Hello server!".encode()) 
with open('received_file', 'wb') as f: 
    while True: 
        print('receiving data...') 
        data = s.recv(1024) 
        print('data=%s', (data)) 
        if not data: 
            break 
        f.write(data) 
f.close() 
print('Successfully get the file') 
s.close() 
print('connection closed')
~~~
Server
~~~
import socket 
port = 60000 
s = socket.socket() 
host = socket.gethostname() 
s.bind((host, port))
s.listen(5) 
while True:
    conn, addr = s.accept() 
    data = conn.recv(1024)
    print('Server received', repr(data))
    filename='mytext.txt'
    f = open(filename,'rb')
    l = f.read(1024)
    while (l):
        conn.send(l)
        print('Sent ',repr(1))
        l = f.read(1024)
    f.close()
    print('Done sending')
    conn.send('Thank you for connecting'.encode())
    conn.close()
~~~
## OUPUT
![432110824-bc25ea35-ef37-4f25-9c8b-9c0d88833494](https://github.com/user-attachments/assets/51a394b4-e26f-49d7-8902-1dd2f9ec07da)

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
