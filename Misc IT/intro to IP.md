network topology is Ethernet, DSL, or cable system. Think of Internet Protocol (IP) as a moving truck for data. Inside the truck are boxes of data(TCP and UDP). Inside those boxes is the info we care about.

IP- Ethernet header, Ethernet Payload, Ethernet trailer. Ethernet payloads are made up of an IP and an IP payload. the IP payload is made up of a TCP and a TCP payload. Lastly, the TCP payload is made up of HTTP data.

TCP and UDP. both are transported inside of IP. they are two ways of moving data from place to place, they have different features for different applications. They are both on the OSI Model Layer 4(The Transport Layer).

TCP(Transmission control Protocol), it is a connection oriented protocol. Is a Reliable mode of communication. because it always gives a return receipt. it also numbers the date that it sends so it can double check if any data is missing. The receiver can control the flow of transmission.

UDP(User Datagram Protocol), it is connection-less because it has no formal open or close to the connection. it is considered unreliable. it has no way of checking if there is any missing data and there is no receiver flow control only the sender can control flow.

The IP truck is sent from one address to another then it is unpacked. each box has an additional label to state where it must go once its arrived at the stated IP address. The additional label is known as a port number. common ports are 80,443,123,25 and so on you get the point.

IPv4 sockets, -Server IP address, protocol, server application port number. - Client IP address, protocol, client port number. There are two kinds of port groups, one is non-ephemeral ports, also know as permanent port numbers. usually ports 0 through 1,023. usually on a server or service. Ephemeral port, also known as temporary port numbers. Usually ports 1,024 through 65,535. usually determined in real time by the client.

TCP port numbers are not the same as UDP port numbers. VoIP(Voice over IP)
