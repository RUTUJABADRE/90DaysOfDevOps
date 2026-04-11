
### OSI layers (L1–L7) vs TCP/IP stack (Link, Internet, Transport, Application)

- The OSI model is a 7-layer framework that explains how computers communicate over a network.
- It helps different systems and protocols work together smoothly.

- The TCP/IP model divides networking into four layers, each responsible for handling different parts of data communication.
- It ensures reliable and standardized data transmission across networks.

### Where IP, TCP/UDP, HTTP/HTTPS, DNS sit in the stack

- Application Layer: HTTP, HTTPS, DNS → handle user-level communication
- Transport Layer: TCP, UDP → manage data delivery (reliable vs fast)
- Internet Layer: IP → handles addressing and routing

### One real example: “curl https://example.com = App layer over TCP over IP”

- Application Layer:
curl creates an HTTP/HTTPS request (like asking a website for data)
- Transport Layer:
TCP breaks the data into small pieces and makes sure everything arrives correctly
- Internet Layer:
IP adds source and destination addresses so data knows where to go
- Network Access Layer:
Data is converted into signals (Wi-Fi/Ethernet) and sent over the network

### 

1. dig shows how a domain name is translated into an IP address using DNS.
2. ss -tulpn Indicates which services are active on the system
   - Found a listening service (e.g., SSH on port 22)
   - Indicates which services are active on the system
3. hostname -I showed the system IP address
4. ping google.com
   - Received replies with low latency (~10–30 ms)
   - 0% packet loss indicates stable connectivity
5. traceroute google.com 
   - Displays multiple hops between my system and Google
   - Some hops may show * (timeout), which is normal due to blocked ICMP
6. curl -I google.com
   - Received HTTP status 301 Redirect
   - Confirms web server is reachable and responding
7. netstat -an | head
   - Multiple ESTABLISHED connections observed to remote servers over port 443 (HTTPS)
   