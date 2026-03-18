# 4.Execution_of_NetworkCommands
## AIM :Use of Network commands in Real Time environment
## Software : Command Prompt And Network Protocol Analyzer
## Procedure: To do this EXPERIMENT- follows these steps:
<BR>
In this EXPERIMENT- students have to understand basic networking commands e.g cpdump, netstat, ifconfig, nslookup ,traceroute and also Capture ping and traceroute PDUs using a network protocol analyzer 
<BR>
All commands related to Network configuration which includes how to switch to privilege mode
<BR>
and normal mode and how to configure router interface and how to save this configuration to
<BR>
flash memory or permanent memory.
<BR>
This commands includes
<BR>
• Configuring the Router commands
<BR>
• General Commands to configure network
<BR>
• Privileged Mode commands of a router 
<BR>
• Router Processes & Statistics
<BR>
• IP Commands
<BR>
• Other IP Commands e.g. show ip route etc.
<BR>

##program
Server
```
import socket
import os

# Create socket
s = socket.socket()
s.bind(('localhost', 8000))
s.listen(1)

print("Server listening on port 8000...")

conn, addr = s.accept()
print(f"Connected to {addr}")

while True:
    try:
        hostname = conn.recv(1024).decode('utf-8')

        if not hostname or hostname.lower() == 'exit':
            print("Client disconnected.")
            break

        print(f"Pinging {hostname}...")

        # Windows ping command (-n 4 = 4 packets)
        response = os.popen(f"ping {hostname} -n 4").read()

        conn.send(response.encode('utf-8'))

    except Exception as e:
        conn.send(f"Error: {e}".encode('utf-8'))

conn.close()
s.close()
```

client
```
import socket

# Create socket
s = socket.socket()
s.connect(('localhost', 8000))

while True:
    ip = input("Enter the website you want to ping (or type 'exit' to quit): ")

    s.send(ip.encode('utf-8'))

    if ip.lower() == 'exit':
        break

    # Receive response
    result = s.recv(4096).decode('utf-8')
    print(result)

s.close()
```

## Output
<img width="1860" height="290" alt="Screenshot 2026-03-18 103604" src="https://github.com/user-attachments/assets/eed7ba8b-64c7-4ec9-8a95-d9c8737fe428" />
<img width="1833" height="676" alt="Screenshot 2026-03-18 103706" src="https://github.com/user-attachments/assets/57aa3788-bc97-4583-8ea6-3b543467c773" />

## Result
Thus Execution of Network commands Performed 
