Common network features:
- Hosts/End systems at start and end of chain of communication
- Servers 
- Routers
- Edge routers/Access networks that directly connect to an end system
Early residential access used sound to transmit data, used standard phone lines and modems, dial up:
- Could not use phone and browse at the same time 
- Typically slow 
- Improved with ADSL: Asymmetric Digital Subscriber Line, downloads faster than it uploads
Now we have base stations that transmit to multiple hosts 'simultaneously', Wi-Fi

Companies and universities connect end systems (i.e. computers, devices) to the edge router (i.e. first/last router that data passes through from or to the device), typically connected via ethernet, LAN

<h4>Layered Network Models</h4>
Communication implemented through a network **stack**
**Protocols** defined to pass messages through layers, for this reason, sometimes referred as **protocol stack** 
Modular design allows internal components to be easily replaced, restricts functionality at each level, easier to understand
Potential for **redundancy** - overlapping operations carried out at more than one level

Ideally network layer model should:
- Create layers where a separate **abstraction** required
- Each layer has well-defined **function**
- Layer boundaries minimise the data flow across the boundary 
Concepts identical to object oriented programming:
- Implementation within each layer is **private** (encapsulated)
- Communication between layers is the public **interface**
**Modularisation** eases maintenance and updating the system:
- Changes in implementation of one layer's service transparent to rest of the system = Doesn't affect rest of the system
<h4>Open Systems Interconnection (OSI)</h4>
Reference model developed in 1970s when networking protocols still being defined, probably not intended for the internet

Applies to networks in *general* 
7 Layer stack![[Pasted image 20250519224145.png]]<u>
Application</u>
Contains the user-facing protocols
- ftp, http, smtp, ...

<u>Presentation</u>
Used to interpret data
- Includes compression & encryption protocols
- Data description (i.e. format)

<u>Session</u> 
Organises and structures the dialogue between applications
- Delimiting & synchronisation

<u>Transport</u>
(Downwards), Accepts session data and splits into segments before passing to the *Network layer*
(Upwards), Receives *Network layer* segments & constructs *Session layer* data

Data integrity depends on the protocol 

Host-to-host communication
- Includes destination address in header
- Oblivious to network infrastructure

<u>Network</u>
Controls the operation of the sub-network between hosts
Determines how **packets** (often called datagrams), routed dynamically:
- Links may be made/broken as machines are added to network, break down

May also offer *congestion control* and *quality service*
Highest level of protocol stack for simple routers:
- i.e. routers don't need *Transport/Application* layers, but will often have software to help routing, firewalls, etc

<u>Link</u>
Handles movement of **frames** (packets) from node-to-node along the route
- Ethernet, Wi-Fi & Combinations 
- Layer at which MAC (Media Access Control) addresses are relevant
![[Pasted image 20250519224836.png]]
<u>Physical</u>
Handles movement at the bit level
- Copper wire, fibre optic, radio waves, etc
- Purely 'hardware'

OSI Pros + Cons

| Pros                                                                    | Cons                                                                                                            |
| ----------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| Clearly defined layers & protocols                                      | Often overly complex                                                                                            |
| Very general design, could be applied to any network, not just internet | *Presentation/Session* layers ahve minimal functionality that could easily be subsumed into *Application layer* |
<h4>TCP/IP</h4>
Most widely used mode for the internet, most relevant, simplified version of OSI model
Application -> Transport -> Network -> Link -> Physical

- *Presentation\Session* layers merged into *Application*
- *Network* layer sometimes called *Internet* layer
- *Link/Physical* layers sometimes merged to give 4-layer model (or *Physical* layer simply dropped)
<u>Application</u>
**User Code** & **Interface** reside here
Sends data into the *Transport* layer and delivers data to the user from the *Transport* layer

Protocol used determines what is done with incoming data:
- http - display in a browser
- ftp - deliver data file
- smtp - sending email
Can also create user-defined protocols

<u>Tranport</u>
Raw data packets can be corrupted, arrive out-of-order, or not arrive at all

Essentially 2 protocols exist at this layer:
TCP:
- Transmission Control Protocol
- Ensures all packets/segments are received
- May ask for re-transmission
- Can have high overhead
UDP:
- User Datagram Protocol
- Detects corruption, but not ordering or lost packets\segments
- Low overhead

<u>Network</u>
Most common protocol is *Internet* protocol, IP
- Describes how data is grouped into **datagrams** (packets)
- Network **Addressing Scheme**

Datagram is produced containing the data and header information 

Also ICMP (Internet Control Message Protocol), which is how routers communicate to ensure efficient transport of messages through network 

Java only understands IP

<u>Link</u>
Controls how packets transported between network nodes
- How e.g. your device or laptop detected by Wi-Fi network
- Error checking, may be redundant 

<u>Phsyical</u>
Data converted to/from e.g. electrical or radio signals 
- May involve digital-to-analogue conversion
- Sometimes merged with *Link* layer

TCP/IP Pros + Cons

| Pros                          | Cons                                              |
| ----------------------------- | ------------------------------------------------- |
| Suited to network programming | Layers and protocols not always clearly defined   |
| Simpler than OSI model        | e.g. Some security protocols sit 'between' layers |
| Well suited to internet       | Lacks generality (unlike OSI)                     |
<h2>Ports</h2>
Application layer linked to the transport layer via **network ports**
- Different port numbers can be associated with different Application layer processes
- Allows multiple applications to run simultaneously on the same host with the same IP address
- Purely software, provided by OS
- Can be allocated to a particular service, e.g. email, HTTP

Converting host-to-host delivery to process-to-process delivery is the job of transport layer
- Known as **multiplexing** (sending) and **demultiplexing** (receiving)

Applications typically publish the port they are **listening to** (receiving on)
- Sending process will attempt to establish a connection using the published port number
- Will continue to communicate using the same port number, but the port can also be used to initiate new contacts 
![[Pasted image 20250519234127.png]]
Ports 1-65535 available on any given host
- 16-bit unsigned int, 0 not allowed
- TCP & UDP ports are **independent**
Ports characterised by:
- Ports 1-1023 **reserved**; approved by IANA (Internet Assigned Numbers Authority)
- Commonly used ports lie outside this range 
- Can freely use any ports in this range
<h4>Port Lists</h4>
<u>Remote login & file transfer</u>

telnet
- port 23
- Teletype Network
- original client-server communication protocol
- now rarely used as insecure
ssh
- port 22
- secure shell
ftp
- file transfer protocol
- port 21 for commands (dir, put, get)
- port 20 used for data (original use; slow)

<u>Email</u>

smtp
- port 25
- simple mail transfer protocol
- sending mail
imap
- port 143
- access mail
- internet message access protocol
pop3
- port 110
- also access mail
- post office protocol

<u>Web</u>

http
- port 80
- hypertext transfer protocol
- insecure
https
- port 443
- secure version of http, requires authentication

<h4>Network Communication</h4>
At application layer, data to be sent to destination host & port number packaged for transport

Transport layer oblivious to subnet that enables the communication
- Adds header that includes information such as port numbers, checksum

At network layer & below, subnet is explicitly involved
- e.g. Network layer determines which network nodes message will pass through

Subnets are segmented pieces of a larger network, help organise and manage networks efficiently, divides larger IP network into sections.
Improves network performance, security and routing efficiency

2 Key protocols for transport layer
- TCP
- UDP

Differ in:
- Information provided by headers
- Reliability of service
- Performance
Both have checksum for data integrity

<h4>UDP</h4>
**Connectionless** protocol
- Each message is independent

Prepends 8-byte header to message including:
- Destination port number 
- Source port number 
- Message length
- Checksum
Ports identify the processes on both source and destination hosts
Has checksum for data integrity, simply discards data segments that have been corrupted

<u>Header</u>
![[Pasted image 20250519235417.png]]
No host (IP) addresses in header for UDP, same is true for TCP
- Responsibility of Network layer

<u>Uses of UDP</u>

Important use is to access a DNS (domain name system) server to map a readable internet address to an IP address

Useful for real-time multi-media, often wrapped into the Real-time Transport protocol (RTP)
- Sits between Application & transport layers
- UDP packets numbered such that receiver can determine if packets missing
- No correction or retransmission
- Receiver can interpolate lost data

<h4>TCP</h4>
**Connection-oriented protocol**, i.e. maintains persistent connection between 2 hosts
- Ensures **reliable data transfer**, possibly requesting re-transmissions of lost or corrupt segments
- Also provides degree of **congestion control**

20-byte header:
- Sequence & acknowledgement numbers
- Bits used for maintaining connection
- Some specialist fields
Remaining fields are the same as UDP 
Sequence and acknowledgement numbers are used to guarantee ordering and to check for missed packets![[Pasted image 20250519235949.png]]

<h4>Network Layer - IP</h4>
Forwards Transport layer data with 20-byte (IPv4) / 40-byte (IPv6) header
- Source and destination address (IPv4/IPv6)
- Protocol (TCP/UDP)
- Checksum for header integrity (IPv4)
- Time-to-live
Time-to-live decrements whenever the datagram (packet) passes through a network node. Once it reaches zero, message is discarded
- Avoids datagrams that circulate forever

**Frames** of data are forwarded to the physical layer, for example, **ethernet frames** have a 22-byte header containing:
- **Preamble**, used for synchronisation
- MAC address for source and destination
- A **type** field
Also **checksum** although this is often in a **footer**![[Pasted image 20250520004912.png]]
Each header has a source and destination 'address':
- **Ports** in between the *Transport* and *Application* layers
- **IP** Addresses in the *Network* layer
- **MAC** Addresses in the *Link* layer

Route from source to destination passes through multiple devices (typically)

Network-layer **routers** determine the path between hosts
Link layer **bridges** & **switches** forward frames between network components
Physical layer **repeaters** & **hubs** regenerate the signal, thereby enabling a greater range![[Pasted image 20250520005600.png]]

<h2>DNS</h2>
DNS now critical support protocol for other network applications 

Host can be addressed in one of two compatible ways:
- Readable host name (i.e. www.comp.leeds.ac.uk)
- IP Address
	- IPv4 (i.e. 129.11.144.10)
	- IPv6 (i.e. 2001:630:62:59::53)
DNS provides a system that maps between these two addressing formats 
www.comp.leeds.ac.uk <-> 129.11.144.10
<h4>Key Concepts</h4>
Indirection
- Names replace IP addresses
- Rarely use IP addresses directly

Hierarchy 
- Apparent in IP addresses, their names, and DNS structure itself

Distribution 
- No single DNS server contains all names or IP addresses 
- Scalable

Caching
- Local caching of DNS results for re-use

Addresses are the 'raw data' for network communication
- Part of the Network layer protocol

Addresses are organised hierarchically and more immediately relate to host location
<h4>Uniqueness</h4>
Every **public** device on internet has unique IP address
Hosts in **private** networks, i.e. LANs can use their own internal addresses
- Some ranges of IP addresses reserved for this purpose, e.g. 10.\*.\*.\* in IPv4
Outward-facing servers, i.e. public hosts visible to the WAN, do have unique IP address
- They forward messages from LAN hosts to the WAN, vice versa, using a Network Address Translation (NAT) table
- Does this by (ab-)using port numbers

One hostname can map to **multiple** IP addresse:
- Popular servers will typically have multiple IP addresses around the world
- DNS server may try to select the 'closest' to the sender
- May also rotate through the list of IP addresses, to reduce congestion
**Multiple** names can map to a **single** IP address
- known as Aliasing

Especially useful for mail addresses
- E.g. f.bloggs@leeds.ac.uk, leeds.ac.uk short address
- Not the name of the server
- When sending a mail to this address, email client can query the DNS to find full, **canonical** address
Can also be used to simplify host names for e.g. web sites in much the same way
<h4>DNS Tools</h4>
nslookup
- Resolves hostnames to IP addresses
- Depreciated but still installed on most UNIX systems
host
- Basic resolution of hostnames and IP addresses
dig
- Resolves hostnames and IP addresses
- Can also trace the DNS query
- Allows for more detailed response

Hierarchical name space:
- Divided into zones
- Distributed across DNS servers
- No single, centralised list - so also no single point of failure

Server structure matches hierarchical name space:
- Root servers
- Top-level Domain (TLD) servers
- Authoritative DNS servers
- Local DNS servers
<h4>Root Servers</h4>
13 Root servers covering the internet
- Actually many more (>400), only 13 IP addresses, i.e. we can only 'see' 13 from one host
- Exception to the 'unique' IP address
These distributed geographically, although most in US
Root server locations are 'hard-wired' into DNS servers

Responsible for TLD:
- .com, .org, .net

Countries:
- .uk, .fr

One server per TLD, maintained by a company or organisation

Organisations who want their sites viewed publicly must provide accessible DNS records for their hosts
- Either their own authoritative DNS server, or that of a service provider
- Universities, ISPs 
- Likely to also maintain secondary DNS server (back-up)

Using UDP, although can use TCP in special circumstances (i.e. if transferring large amount of data from one server to another)

Queries may **fail** if not answered within set time limit
- May retry until successful
Uses port 53
Messages are either 'query' or 'reply' using same format

DNS query will pass through hierarchy:
- Local host configured to connect to **local** DNS server
- negotiates with **root** DNS server to find **TLD** server
- then negotiates with **TLD** server to find **Authoritative** DNS server
- then negotiates with Authoritative DNS server to resolve host name to IP address
- then returns this IP address to local host
![[Pasted image 20250520013729.png]]
This example includes both **recursive** and **iterative queries**: 
- Local host asking the local DNS server to resolve a host name is a **recursive** query
- 3 Queries from local DNS to root, TLD, Authoritative servers in turn an **iterative** query
8 messages required in total, for each host name resolution
![[Pasted image 20250520013900.png]]
<h4>DNS Caching</h4>
Query process has overhead:
- Primarily delay, especially if one of queries is lost and needs to be re-sent
- May also cause congestion, as number of messages for each server can become very high
To improve performance, query results are **cached** on the local DNS server:
- Cache is checked before the root DNS server is used
- Can cache IP addresses for TLD servers, bypassing the need to access root server
![[Pasted image 20250520014032.png]]
If query is successful:
- Returned DNS message will include a Time-to-live, TTL
- Will cache until TTL expires, typically days

If query is unsuccessful:
- Overhead for unknown domain names (e.g. mistyped domain) is greater than for known domains, requires exhaustive search
- Caching avoids repeat of this overhead
- In this instance, typically has shorter TTL, or the order of hours

<h2>IP Addresses</h2>Every **public** host on internet has unique IP address

2 protocols currently in use:
- IPv4
- IPv6
IPv6 gradually replacing IPv4
<h4>IPv4</h4>
Usually written as 4-byte string of 4 integers
- a.b.c.d
- Each byte takes value from 0-255 (i.e Unsigned)
- The '4' in IPv4 refers to version, not no. bytes

Some addresses and ranges of addresses have special meaning
Even without this, only (256)<sup>4</sup> $\approx$ 4.29 x 10<sup>9</sup> possible addresses, i.e. about 4.3 billion

Originally were several **classes** IPv4 address:
- Class A: 0.\*.\*.\* to 127.\*.\*.\*
- Class B: 128.\*.\*.\* to 191.\*.\*.\*
- Class C: 192.\*.\*.\* to 223.\*.\*.\*
- Class D: 224.\*.\*.\* to 239.\*.\*.\*
- Class E: 240.\*.\*.\* to 255.\*.\*.\*
Vary in size: Class A > B > C > D, E

**Classful** model not perfect, Various classes reserved for reducing space:
- Class D: Multi-casting
- Class E: Reserved for some unspecified 'future use' 
- Some special addresses:
	- 0.0.0.0 for 'this' machine
	- 255.255.255.255 used for **broadcasting** (device discovery)
	- 127.\*.\*.\* used for *loopback*
Least significant 3 bytes were not always managed efficiently

Additionally to first byte ranges, difference classes also allows **subnetworks** to be defined:
- Class A allows 128 networks, each with 256<sup>3</sup> $\approx$ 16.7 million hosts a.\*.\*.\*
- Class B allows 64 x 256 = 16384 networks, each with 65536 hosts: a.b.\*.\*
- Class C allows 32 x 256<sup>2</sup> $\approx$ 2 million networks, each with 256 hosts: a.b.c.\*
Idea was each organisation could choose subnet
- Most organisations need more than 256 hosts, but less than 65536
- Tended to select Class B and **under-utilise** their subnetwork
<h4>Classless Inter-Domain Routing CIDR</h4>
First fix was to define subnetworks by *any* number of bits
- Greater range of subnetwork sizes (i.e. 256, 512, 1024, ...)
- Notation: a.b.c.d/x with x the number of common bits

E.g. 220.10.128.0/20 means 'all addresses' that share their first 20 bits with 220.10.128.0:
- All of first byte (220)
- All of second byte (10)
- Most significant 4-bits of third byte (128-143 inc):
- Full range:
	- 220.10.128.0 -> 220.10.143.255
<h4>Network Address Translation NAT</h4>
Allows more networks, and gaps in Class B networks can be filled, but here is still a limit on hosts

Second fix was for **private** networks to have their own **internal** addresses, and only public-facing servers that have an actual IP address
- Re-direct messages to/from private hosts using **ports**
- 10.\*.\*.\* most common
- Known as NAT
Not regarded as permanent solution, more of 'quick fix'

<h4>IPv6</h4>
Long term solution is to expand address space
- IPv6 uses 16-byte addresses
- Total of 256<sup>16</sup> $\approx$ 3 x 10<sup>38</sup> possible addresses
- Even if managed inefficiently should never run out
Currently around 45% users access Google via IPv6

Some legacy systems don't support IPv6
- Can wrap IPv6 datagrams into IPv4 datagrams if some intermediate routers only IPv4
- Known as **tunnelling**

Address format usually written in hexadecimal, with 8 groups (pairs of bytes) separated by colons. E.g., dns6.leeds.ac.uk is:
2001:0630:0062:0059:0000:0000:0000:0053

Can simplify by removing leading zeroes in each group:
2001:630:62:59:0:0:0:53

Further simplify by replacing consecutive sections of zeroes by double colon:
2001:630:62:59::53

Note can only have **one double colon** in address, otherwise would be ambiguous
For instance shortened address 2001:630::53:: could be 
2001:0630:0000:0000:0053:0000:0000:0000 or,
2001:0630:0000:0000:0000:0053:0000:0000

When multiple runs of all-zero values, only longest should be contracted using double colon
- If runs same length, **leftmost** contracted

CIDR also applies to IPv6, same '/' notation
e.g. 2001:630:62:59::/64
specifies the range (not using double colons for clarity)
Start address: 2001:630:62:59:0:0:0:0
End address: 2001:630:62:59:ffff:ffff:ffff:ffff

Private address used to denote machines on same local network can use the addresses:
- 10.\*.\*.\* or 10.0.0.0/8 in Ipv4
- fc00::/8 in IPv6
<h4>InetAddress class</h4>
IP addresses handled using InetAddress class in Java
- Defined in java.net
- Used by most of important network classes:
	- Socket
	- ServerSocket
	- URL
- Includes **both** IP address & host name
- Used to represent **both** IPv4 & IPv6 addresses

No public constructor for InetAddress, instead three **static** methods can return InetAddress object:
```java
public static InetAddress getByName(String hostname)
// Most common

public static InetAddress[] getAllByName(String hostname)
// Returns array of InetAddress objects
// Depends on configuration of local DNS server

public static InetAddress getLocalHost()
// i.e. the address of the host running the code
```

These methods don't simply set object state by using constructor arguments (which is how a public constructor usually works)
- Make DNS queries on your behalf
Don't need to specify IPv4 or IPv6
- Uses **polymorphism**
- Has subclasses Inet4Address & Inet6Address
- User is usually oblivious to which subclass has been returned
- Can specify the IPv4/IPv6 subclass if desired

Creating objects in this way without specifying the exact class to be created called **factory method pattern** in OO programming

Here it means that:
- Supply a string that **may** resolve to an address
- Do not know in advance if the hostname exists
- Factory method returns either Inet4Address or Inet6Address object
- Through polymorphism, can refer to either as InetAddress

<u>Issues</u>

These methods will connect to DNS server
- If you are not connected it may prompt for connection or throw exception
Make their **own external network connections** to get the information they need:
- Not normal constructor behaviour
- Can fail for variety of reasons (no network connection, unknown host, security, etc)
- Need to catch **UnknownHostException** (checked exception)
- Relatively expensive (slow) due to DNS overhead (although will use DNS cache where possible)
<h4>Getters</h4>
Some common 'get' methods to access instance of InetAddress are:
```java
public String getHostName()
// Returns hostname you used to create object

public String getHostAddress()
// Textual representation of IP address (IPv4/IPv6)

public byte[] getAddress()
// Returns IP address as array of 4 or 16 bytes
```
In addition, System.out.println() will print combination of hostname and IP address
<h4>Setters</h4>
**No** public 'set' methods for InetAddress
- **Immutable** object whose state cannot be changed once created
- At least not externally - internal state changes are possible with private methods
Why:
- Assume DNS sets correct state
- Letting user change parts of object runs the risk of breaking consistency with DNS
<h4>OO Design</h4>
Encapsulation 
- Public access to getters
- Private constructors and setters
Inheritance
- Inet4Address & Inet6Address extent InetAddress
Polymorphism
- Typically used by parent InetAddress class
- All we need is application layer
Abstraction
- Do not need to know if our address is IPv4/IPv6, only that it resolves to a host that exists

<u>Other Methods:</u>
```java
public boolean isReachable(int timeOut)
// Tests if address is reachable
// Waits maximum of timeOut milliseconds
// Similar to ping, uses IP rather than ICMP

public boolean isLoopBackAddress()
// Loopback addresses returned as soon as they reach the Network layer
// Useful for testing without physical infrastructure 
// IPv4: 127.*.*.*, or 127.0.0.0/8
// IPv6: 0:0:0:0:0:0:0:1, usually written ::1
```