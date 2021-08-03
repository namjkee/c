# Unix Socket - Ports and Services

When a client process wants to a connect a server, the client must have a way of identifying the server that it wants to connect. If the client knows the 32-bit Internet address of the host on which the server resides, it can contact that host. But how does the client identify the particular server process running on that host?

To resolve the problem of identifying a particular server process running on a host, both TCP and UDP have defined a group of well-known ports.

For our purpose, a port will be defined as an integer number between 1024 and 65535. This is because all port numbers smaller than 1024 are considered well-known -- for example, telnet uses port 23, http uses 80, ftp uses 21, and so on.

The port assignments to network services can be found in the file /etc/services. If you are writing your own server then care must be taken to assign a port to your server. You should make sure that this port should not be assigned to any other server.

Normally it is a practice to assign any port number more than 5000. But there are many organizations who have written servers having port numbers more than 5000. For example, Yahoo Messenger runs on 5050, SIP Server runs on 5060, etc.

## Example Ports and Services

Here is a small list of services and associated ports. You can find the most updated list of internet ports and associated service at [IANA - TCP/IP Port Assignments](http://www.iana.org/assignments/port-numbers).

| **Service** | **Port Number** | **Service Description** |
| :--- | :--- | :--- |
| echo | 7 | UDP/TCP sends back what it receives. |
| discard | 9 | UDP/TCP throws away input. |
| daytime | 13 | UDP/TCP returns ASCII time. |
| chargen | 19 | UDP/TCP returns characters. |
| ftp | 21 | TCP file transfer. |
| telnet | 23 | TCP remote login. |
| smtp | 25 | TCP email. |
| daytime | 37 | UDP/TCP returns binary time. |
| tftp | 69 | UDP trivial file transfer. |
| finger | 79 | TCP info on users. |
| http | 80 | TCP World Wide Web. |
| login | 513 | TCP remote login. |
| who | 513 | UDP different info on users. |
| Xserver | 6000 | TCP X windows \(N.B. &gt;1023\). |

## Port and Service Functions

Unix provides the following functions to fetch service name from the /etc/services file.

* **struct servent \*getservbyname\(char \*name, char \*proto\)** − This call takes service name and protocol name, and returns the corresponding port number for that service.
* **struct servent \*getservbyport\(int port, char \*proto\)** − This call takes port number and protocol name, and returns the corresponding service name.

The return value for each function is a pointer to a structure with the following form −

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
      <td style="text-align:left">It is the official name of the service. For example, SMTP, FTP POP3, etc.</td>
    </tr>
    <tr>
      <td style="text-align:left">s_aliases</td>
      <td style="text-align:left">ALIAS</td>
      <td style="text-align:left">It holds the list of service aliases. Most of the time, it will be set
        to NULL.</td>
    </tr>
    <tr>
      <td style="text-align:left">s_port</td>
      <td style="text-align:left">80</td>
      <td style="text-align:left">It will have the associated port number. For example, for HTTP, it will
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

