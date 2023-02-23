###UDP

The User Datagram Protocol, or UDP, is a communication protocol used across the Internet for especially time-sensitive transmissions such as video playback or DNS lookups. It speeds up communications by not formally establishing a connection before data is transferred. This allows data to be transferred very quickly, but it can also cause packets to become lost in transit — and create opportunities for exploitation in the form of DDoS attacks.

Like all networking protocols, UDP is a standardized method for transferring data between two computers in a network. Compared to other protocols, UDP accomplishes this process in a simple fashion: it sends packets (units of data transmission) directly to a target computer, without establishing a connection first, indicating the order of said packets, or checking whether they arrived as intended. (UDP packets are referred to as ‘datagrams’.)

UDP is faster but less reliable than TCP, another common transport protocol. In a TCP communication, the two computers begin by establishing a connection via an automated process called a ‘handshake.’ Only once this handshake has been completed will one computer actually transfer data packets to the other.
UDP communications do not go through this process. Instead, one computer can simply begin sending data to the other.

UDP is commonly used in time-sensitive communications where occasionally dropping packets is better than waiting. Voice and video traffic are often sent using this protocol because they are both time-sensitive and designed to handle some level of loss. For example, VoIP (voice over IP), which is used by many Internet-based telephone services, typically operates over UDP. This is because a static-y phone conversation is preferable to one that is crystal clear but heavily delayed.

Programs in the application layer communicate with the transport layer through a port. We assign different ports to different applications so that they can connect and exchange data with any networking-enabled devices within a network using their port.

##Multiplexing and Demultiplexing

Multiplexing
Multiplexing is the process of collecting the data from multiple application processes of the sender, enveloping that data with headers and sending them as a whole to the intended receiver.
In Multiplexing at the Transport Layer, the data is collected from various application processes. These segments contain the source port number, destination port number, header files, and data.
These segments are passed to the Network Layer which adds the source and destination IP address to get the datagram.

Demultiplexing
Delivering the received segments at the receiver side to the correct app layer processes is called demultiplexing.
The destination host receives the IP datagrams; each datagram has a source IP address and a destination IP address.
Each datagram carries 1 transport layer segment.
Each segment has the source and destination port number.
The destination host uses the IP addresses and port numbers to direct the segment to the appropriate socket.

Why does UDP use PORTS?
Because a UDP packet doesn't require an existing connection, network systems use UDP primarily for broadcasting messages (i.e., a one-to-many sending, much like unsolicited junk email). The most common UDP packets—DNS registrations and name-resolution queries—are sent to port 53.

---

##USING UDP with Node.js:

1. New instances of dgram.Socket are created using dgram.createSocket():
   type <string> The family of socket. Must be either 'udp4' or 'udp6'. Required.

2. Creates a dgram.Socket object. Once the socket is created, calling socket.bind() will instruct the socket to begin listening for datagram messages. When address and port are not passed to socket.bind() the method will bind the socket to the "all interfaces" address on a random port (it does the right thing for both udp4 and udp6 sockets).
