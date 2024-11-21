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

## CLIENT
```
import socket
s=socket.socket()
host=socket.gethostname()
port=60000
s.connect((host,port))
s.send("Hello server!".encode())
with open('received_file','wb')as f:
  print('receiving data....')
  while True:
    data=s.recv(1024)
    print('data=%s',data)
    if not data:
       break
    f.write(data)
print('Successfully received the file')
s.close()
print('connection closed')
```
## SERVER
```
import socket
port=60000
s=socket.socket()
host=socket.gethostname()
s.bind((host,port))
s.listen(5)
print("Server listening on port",port)
while True:
  conn,addr=s.accept()
  print("Connected to",addr)
  data=conn.recv(1024)
  print('Server received',repr(data))
  filename = 'C:\\Users\\admin\\Desktop\\COLLEGE\\COM NETWORKS\\CN exp.txt'
  with open(filename,'rb') as f:
   l=f.read(1024)
   while l:
     conn.send(l)
     print('sent',repr(l))
     l=f.read(1024)
print("Done sending")
conn.send('Thank you for connecting'.encode())
conn.close()
```
## OUPUT


## CLIENT
![image](https://github.com/user-attachments/assets/49e43d42-5e65-49ef-a8d7-6417b62ead8f)

## SERVER
![image](https://github.com/user-attachments/assets/f7af0952-0c7e-4097-a775-5ae9f090c3cf)
## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.

