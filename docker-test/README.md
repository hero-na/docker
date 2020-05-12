mkdir my_first_project
cd my_first_project

gedit test_server.py

```
# test_server.copy()
import socket

with socket.socket() as s:
    s.bind(("0.0.0.0",12345))
    s.listen()
    print("server is started")
    conn, addr = s.accept()

    # conn 클라이언트와 통신할 소켓
    # addr 클라이언트의 정보가 들어있음
    with conn:
        print("Connected by",addr)
        while True:
            data = conn.recv(1024)
            if not data: break
            conn.sendall(data)
```

ls
gedit dockerfile

```
FROM python:3.7

RUN mkdir /echo
COPY test_server.py /echo

CMD ["python","/echo/test_server.py"]
```


