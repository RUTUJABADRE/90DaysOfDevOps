## Task 1: DNS – How Names Become IPs

1. Explain in 3–4 lines: what happens when you type google.com in a browser?
When you type **google.com** in a browser, it first performs a **DNS lookup** to convert the domain name into an IP address.
Then your browser sends an **HTTP/HTTPS request** to that server over the internet.
The server processes the request and returns the webpage data (HTML, CSS, JS).
Finally, the browser **renders the page** so you can see and interact with it.

2. What are these record types? Write one line each:
A, AAAA, CNAME, MX, NS
* **A record** – maps a domain name to an IPv4 address.
* **AAAA record** – maps a domain name to an IPv6 address.
* **CNAME record** – points one domain name to another domain name (alias).
* **MX record** – specifies the mail server responsible for receiving emails for a domain.
* **NS record** – defines the authoritative name servers for a domain.

3. Run: dig google.com — identify the A record and TTL from the output
Domain google.com resolved to IP 142.250.182.78 (A record)
TTL is 177 seconds, indicating how long the result is cached

## Task 2: IP Addressing

1. What is an IPv4 address? How is it structured? (
An IPv4 address is a 32-bit unique identifier written as four numbers (0–255) used to identify devices on a network.

2. Difference between public and private IPs — give one example of each
Public IP
Used on the internet (globally reachable)
Assigned by ISP and must be unique worldwide
Example:
8.8.8.8 (Google DNS)

Private IP
Used inside local networks (home, office)
Not accessible directly from the internet
Example:
192.168.1.10

3. What are the private IP ranges?
The three private IP ranges:
10.0.0.0 – 10.255.255.255
→ (10.x.x.x)
172.16.0.0 – 172.31.255.255
→ (172.16.x.x – 172.31.x.x)
192.168.0.0 – 192.168.255.255
→ (192.168.x.x)

## Task 3: CIDR & Subnetting

1. What does /24 mean in 192.168.1.0/24?
In 192.168.1.0/24, the /24 is called the CIDR notation
It means: first 24 bits are for the network
Remaining bits are for hosts

2. how many usable hosts in a /24? A /16? A /28?

Example: /24
Host bits = 32 - 24 = 8  
Total IPs = 2^8 = 256  
Usable hosts = 256 - 2 = 254

/24 → 254 usable hosts
/16 → 65,534 usable hosts
/28 → 14 usable hosts

3. Explain in your own words: why do we subnet?
- We subnet to break a large network into smaller, manageable pieces.
- subnetting helps use IP addresses efficiently instead of wasting them.

4. Quick exercise — fill in:
CIDR   Subnet Mask        Total IPs   Usable Hosts
/24    255.255.255.0      256         254
/16    255.255.0.0        65,536      65,534
/28    255.255.255.240    16          14

## Task 4: Ports – The Doors to Services

1. What is a port? Why do we need them?
A **port** is a logical number (0–65535) used to identify a specific service or process on a computer.
We need ports because a single machine can run multiple services at the same time (like web, SSH, email).
Ports ensure that incoming network traffic goes to the **correct application** instead of getting mixed up.
For example, HTTP uses port 80 and SSH uses port 22.

2. Document these common ports:

Port    Service
22      SSH (Secure Shell)
80      HTTP (Web)
443     HTTPS (Secure Web)
53      DNS (Domain Name System)
3306    MySQL
6379    Redis
27017   MongoDB

## ask 5: Putting It Together
1. ou run curl http://myapp.com:8080 — what networking concepts from today are involved?

2. Your app can't reach a database at 10.0.1.50:3306 — what would you check first?
nc -zv 10.0.1.50 3306 --> checking network connectivity
systemctl status mysql ---> Check if MySQL is running 
ss -tulpn | grep 3306 ---> verify it’s listening on port 3306
ensure it’s bound to 0.0.0.0 (not 127.0.0.1)

