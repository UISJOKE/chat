import socket

from cryptography.fernet import Fernet

sock = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
sock.bind(('25.46.145.190', 8000))
client = []
key = Fernet.generate_key()
print('Start Server')
print('Key: ' + key.decode('UTF-8'))
while 1:
    cipher = Fernet(key)
    data, addres = sock.recvfrom(1024)
    crypt = cipher.encrypt(data)
    print(crypt)
    if addres not in client:
        client.append(addres)
    for clients in client:
        if clients == addres:
            continue
        sock.sendto(crypt, clients)
