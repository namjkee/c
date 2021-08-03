# Unix Socket - Summary - Tutorialspoint

Here is a list of all the functions related to socket programming.

## Port and Service Functions

Unix provides the following functions to fetch service name from the /etc/services file.

* **struct servent \*getservbyname\(char \*name, char \*proto\)** − This call takes a service name and a protocol name and returns the corresponding port number for that service.
* **struct servent \*getservbyport\(int port, char \*proto\)** − This call takes a port number and a protocol name and returns the corresponding service name.

## Byte Ordering Functions

* **unsigned short htons \(unsigned short hostshort\)** − This function converts 16-bit \(2-byte\) quantities from host byte order to network byte order.
* **unsigned long htonl \(unsigned long hostlong\)** − This function converts 32-bit \(4-byte\) quantities from host byte order to network byte order.
* **unsigned short ntohs \(unsigned short netshort\)** − This function converts 16-bit \(2-byte\) quantities from network byte order to host byte order.
* **unsigned long ntohl \(unsigned long netlong\)** − This function converts 32-bit quantities from network byte order to host byte order.

## IP Address Functions

* **int inet\_aton \(const char \*strptr, struct in\_addr \*addrptr\)** − This function call converts the specified string, in the Internet standard dot notation, to a network address, and stores the address in the structure provided. The converted address will be in Network Byte Order \(bytes ordered from left to right\). It returns 1 if the string is valid and 0 on error.
* **in\_addr\_t inet\_addr \(const char \*strptr\)** − This function call converts the specified string, in the Internet standard dot notation, to an integer value suitable for use as an Internet address. The converted address will be in Network Byte Order \(bytes ordered from left to right\). It returns a 32-bit binary network byte ordered IPv4 address and INADDR\_NONE on error.
* **char \*inet\_ntoa \(struct in\_addr inaddr\)** − This function call converts the specified Internet host address to a string in the Internet standard dot notation.

## Socket Core Functions

* **int socket \(int family, int type, int protocol\)** − This call returns a socket descriptor that you can use in later system calls or it gives you -1 on error.
* **int connect \(int sockfd, struct sockaddr \*serv\_addr, int addrlen\)** − The connect function is used by a TCP client to establish a connection with a TCP server. This call returns 0 if it successfully connects to the server, otherwise it returns -1.
* **int bind\(int sockfd, struct sockaddr \*my\_addr,int addrlen\)** − The bind function assigns a local protocol address to a socket. This call returns 0 if it successfully binds to the address, otherwise it returns -1.
* **int listen\(int sockfd, int backlog\)** − The listen function is called only by a TCP server to listen for the client request. This call returns 0 on success, otherwise it returns -1.
* **int accept \(int sockfd, struct sockaddr \*cliaddr, socklen\_t \*addrlen\)** − The accept function is called by a TCP server to accept client requests and to establish actual connection. This call returns a non-negative descriptor on success, otherwise it returns -1.
* **int send\(int sockfd, const void \*msg, int len, int flags\)** − The send function is used to send data over stream sockets or CONNECTED datagram sockets. This call returns the number of bytes sent out, otherwise it returns -1.
* **int recv \(int sockfd, void \*buf, int len, unsigned int flags\)** − The recv function is used to receive data over stream sockets or CONNECTED datagram sockets. This call returns the number of bytes read into the buffer, otherwise it returns -1 on error.
* **int sendto \(int sockfd, const void \*msg, int len, unsigned int flags, const struct sockaddr \*to, int tolen\)** − The sendto function is used to send data over UNCONNECTED datagram sockets. This call returns the number of bytes sent, otherwise it returns -1 on error.
* **int recvfrom \(int sockfd, void \*buf, int len, unsigned int flags struct sockaddr \*from, int \*fromlen\)** − The recvfrom function is used to receive data from UNCONNECTED datagram sockets. This call returns the number of bytes read into the buffer, otherwise it returns -1 on error.
* **int close \(int sockfd\)** − The close function is used to close a communication between the client and the server. This call returns 0 on success, otherwise it returns -1.
* **int shutdown \(int sockfd, int how\)** − The shutdown function is used to gracefully close a communication between the client and the server. This function gives more control in comparison to close function. It returns 0 on success, -1 otherwise.
* **int select \(int nfds, fd\_set \*readfds, fd\_set \*writefds, fd\_set \*errorfds, struct timeval \*timeout\)** − This function is used to read or write multiple sockets.

## Socket Helper Functions

* **int write \(int fildes, const void \*buf, int nbyte\)** − The write function attempts to write nbyte bytes from the buffer pointed to by buf to the file associated with the open file descriptor, fildes. Upon successful completion, write\(\) returns the number of bytes actually written to the file associated with fildes. This number is never greater than nbyte. Otherwise, -1 is returned.
* **int read \(int fildes, const void \*buf, int nbyte\)** − The read function attempts to read nbyte bytes from the file associated with the open file descriptor, fildes, into the buffer pointed to by buf. Upon successful completion, write\(\) returns the number of bytes actually written to the file associated with fildes. This number is never greater than nbyte. Otherwise, -1 is returned.
* **int fork \(void\)** − The fork function creates a new process. The new process, called the child process, will be an exact copy of the calling process \(parent process\).
* **void bzero \(void \*s, int nbyte\)** − The bzero function places nbyte null bytes in the string s. This function will be used to set all the socket structures with null values.
* **int bcmp \(const void \*s1, const void \*s2, int nbyte\)** − The bcmp function compares the byte string s1 against the byte string s2. Both the strings are assumed to be nbyte bytes long.
* **void bcopy \(const void \*s1, void \*s2, int nbyte\)** − The bcopy function copies nbyte bytes from the string s1 to the string s2. Overlapping strings are handled correctly.
* **void \*memset\(void \*s, int c, int nbyte\)** − The memset function is also used to set structure variables in the same way as bzero.

