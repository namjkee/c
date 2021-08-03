# Unix Socket - Structures - Tutorialspoint

Various structures are used in Unix Socket Programming to hold information about the address and port, and other information. Most socket functions require a pointer to a socket address structure as an argument. Structures defined in this chapter are related to Internet Protocol Family.

## sockaddr

The first structure is sockaddr that holds the socket information −

```text
struct sockaddr {
   unsigned short   sa_family;
   char             sa_data[14];
};
```

This is a generic socket address structure, which will be passed in most of the socket function calls. The following table provides a description of the member fields −

<table>
  <thead>
    <tr>
      <th style="text-align:left">Attribute</th>
      <th style="text-align:left">Values</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">sa_family</td>
      <td style="text-align:left">
        <p>AF_INET</p>
        <p>AF_UNIX</p>
        <p>AF_NS</p>
        <p>AF_IMPLINK</p>
      </td>
      <td style="text-align:left">It represents an address family. In most of the Internet-based applications,
        we use AF_INET.</td>
    </tr>
    <tr>
      <td style="text-align:left">sa_data</td>
      <td style="text-align:left">Protocol-specific Address</td>
      <td style="text-align:left">The content of the 14 bytes of protocol specific address are interpreted
        according to the type of address. For the Internet family, we will use
        port number IP address, which is represented by sockaddr_in structure defined
        below.</td>
    </tr>
  </tbody>
</table>

## sockaddr in

The second structure that helps you to reference to the socket's elements is as follows −

```text
struct sockaddr_in {
   short int            sin_family;
   unsigned short int   sin_port;
   struct in_addr       sin_addr;
   unsigned char        sin_zero[8];
};
```

Here is the description of the member fields −

<table>
  <thead>
    <tr>
      <th style="text-align:left">Attribute</th>
      <th style="text-align:left">Values</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">sa_family</td>
      <td style="text-align:left">
        <p>AF_INET</p>
        <p>AF_UNIX</p>
        <p>AF_NS</p>
        <p>AF_IMPLINK</p>
      </td>
      <td style="text-align:left">It represents an address family. In most of the Internet-based applications,
        we use AF_INET.</td>
    </tr>
    <tr>
      <td style="text-align:left">sin_port</td>
      <td style="text-align:left">Service Port</td>
      <td style="text-align:left">A 16-bit port number in Network Byte Order.</td>
    </tr>
    <tr>
      <td style="text-align:left">sin_addr</td>
      <td style="text-align:left">IP Address</td>
      <td style="text-align:left">A 32-bit IP address in Network Byte Order.</td>
    </tr>
    <tr>
      <td style="text-align:left">sin_zero</td>
      <td style="text-align:left">Not Used</td>
      <td style="text-align:left">You just set this value to NULL as this is not being used.</td>
    </tr>
  </tbody>
</table>

## in addr

This structure is used only in the above structure as a structure field and holds 32 bit netid/hostid.

```text
struct in_addr {
   unsigned long s_addr;
};
```

Here is the description of the member fields −

| Attribute | Values | Description |
| :--- | :--- | :--- |
| s\_addr | service port | A 32-bit IP address in Network Byte Order. |

## hostent

This structure is used to keep information related to host.

```text
struct hostent {
   char *h_name; 
   char **h_aliases; 
   int h_addrtype;  
   int h_length;    
   char **h_addr_list
	
#define h_addr  h_addr_list[0]
};
```

Here is the description of the member fields −

| Attribute | Values | Description |
| :--- | :--- | :--- |
| h\_name | ti.com etc. | It is the official name of the host. For example, tutorialspoint.com, google.com, etc. |
| h\_aliases | TI | It holds a list of host name aliases. |
| h\_addrtype | AF\_INET | It contains the address family and in case of Internet based application, it will always be AF\_INET. |
| h\_length | 4 | It holds the length of the IP address, which is 4 for Internet Address. |
| h\_addr\_list | in\_addr | For Internet addresses, the array of pointers h\_addr\_list\[0\], h\_addr\_list\[1\], and so on, are points to structure in\_addr. |

**NOTE** − h\_addr is defined as h\_addr\_list\[0\] to keep backward compatibility.

## servent

This particular structure is used to keep information related to service and associated ports.

```text
struct servent {
   char  *s_name; 
   char  **s_aliases; 
   int   s_port;  
   char  *s_proto;
};
```

Here is the description of the member fields −

<table>
  <thead>
    <tr>
      <th style="text-align:left">Attribute</th>
      <th style="text-align:left">Values</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">s_name</td>
      <td style="text-align:left">http</td>
      <td style="text-align:left">This is the official name of the service. For example, SMTP, FTP POP3,
        etc.</td>
    </tr>
    <tr>
      <td style="text-align:left">s_aliases</td>
      <td style="text-align:left">ALIAS</td>
      <td style="text-align:left">It holds the list of service aliases. Most of the time this will be set
        to NULL.</td>
    </tr>
    <tr>
      <td style="text-align:left">s_port</td>
      <td style="text-align:left">80</td>
      <td style="text-align:left">It will have associated port number. For example, for HTTP, this will
        be 80.</td>
    </tr>
    <tr>
      <td style="text-align:left">s_proto</td>
      <td style="text-align:left">
        <p>TCP</p>
        <p>UDP</p>
      </td>
      <td style="text-align:left">It is set to the protocol used. Internet services are provided using either
        TCP or UDP.</td>
    </tr>
  </tbody>
</table>

## Tips on Socket Structures

Socket address structures are an integral part of every network program. We allocate them, fill them in, and pass pointers to them to various socket functions. Sometimes we pass a pointer to one of these structures to a socket function and it fills in the contents.

We always pass these structures by reference \(i.e., we pass a pointer to the structure, not the structure itself\), and we always pass the size of the structure as another argument.

When a socket function fills in a structure, the length is also passed by reference, so that its value can be updated by the function. We call these value-result arguments.

Always, set the structure variables to NULL \(i.e., '\0'\) by using memset\(\) for bzero\(\) functions, otherwise it may get unexpected junk values in your structure.

