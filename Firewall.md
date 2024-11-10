- Firewall is security device which is used to manage and filter the incoming and outgoing network traffic.

- firewall exist since 1980 to filter the packets

**Types of firewall-**
- **Packet Filtering Firewall**:
    
    - Checks individual packets.
    - Uses rules based on source/destination IP, port, and protocol.
    - Fast, but can't track connection state.
- **Proxy Services**:
    
    - Intercepts traffic between client and server.
    - Filters at the application layer (e.g., HTTP).
    - Caches data for improved performance and user anonymity.
- **Stateful Inspection Firewall**:
    
    - Monitors active connections and their states.
    - Maintains a state table for decision-making.
    - Provides more robust security than packet filtering.
- **Next-Generation Firewall (NGFW)**:
    
    - Integrates traditional firewall functions with advanced features.
    - Offers intrusion prevention, application control, and deep packet inspection.
    - Enhances visibility into encrypted traffic and protects against sophisticated threats.
    - ASA firewall stands for Adaptive Security Appliance which is used to permit inbound and outbound traffic.
   - **Types of NGFW-**
   - **Host based firewall**- piece of s/w that runs on a individual computer connected to a network.
   - **Network Based Firewall-** filter the traffic of network.


  - Provide VPN service.
  
![[firewall.png]]


https://drive.google.com/drive/folders/1-31kqCu6xDHnvjDN0RttWYDWCLQS02LO
All device Images.


> [!NOTE]
> Pal Alto - Running version is PAN-OS


==**FortiGate Firewall-**==

> [!NOTE]
> Every Firewall is a Router but not every Router is a Firewall

- Firewall has policy what traffic is allowed.
- Firewall has Session table that contains SIP,DIP,SP,DP,TIME,SESSION_ID when client send SYN to server  then in response the server will send SYN+ACK and firewall will check session table then it will allow that response this is called STATEFUL.
- ![[FORTINET-FORTIGATE-CLI-CHEATSHEET.pdf]]
