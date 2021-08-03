# Unix Socket - Network Addresses

Before we proceed with the actual stuff, let us discuss a bit about the Network Addresses − the IP Address.

The IP host address, or more commonly just IP address, is used to identify hosts connected to the Internet. IP stands for Internet Protocol and refers to the Internet Layer of the overall network architecture of the Internet.

An IP address is a 32-bit quantity interpreted as four 8-bit numbers or octets. Each IP address uniquely identifies the participating user network, the host on the network, and the class of the user network.

An IP address is usually written in a dotted-decimal notation of the form N1.N2.N3.N4, where each Ni is a decimal number between 0 and 255 decimal \(00 through FF hexadecimal\).

## Address Classes

IP addresses are managed and created by the Internet Assigned Numbers Authority \(IANA\). There are five different address classes. You can determine which class an IP address is in by examining the first four bits of the IP address.

* **Class A** addresses begin with **0xxx**, or **1 to 126** decimal.
* **Class B** addresses begin with **10xx**, or **128 to 191** decimal.
* **Class C** addresses begin with **110x**, or **192 to 223** decimal.
* **Class D** addresses begin with **1110**, or **224 to 239** decimal.
* **Class E** addresses begin with **1111**, or **240 to 254** decimal.

Addresses beginning with **01111111**, or **127** decimal, are reserved for loopback and for internal testing on a local machine \[You can test this: you should always be able to ping **127.0.0.1**, which points to yourself\]; Class D addresses are reserved for multicasting; Class E addresses are reserved for future use. They should not be used for host addresses.

### Example

| **Class** | **Leftmost bits** | **Start address** | **Finish address** |
| :--- | :--- | :--- | :--- |
| A | 0xxx | 0.0.0.0 | 127.255.255.255 |
| B | 10xx | 128.0.0.0 | 191.255.255.255 |
| C | 110x | 192.0.0.0 | 223.255.255.255 |
| D | 1110 | 224.0.0.0 | 239.255.255.255 |
| E | 1111 | 240.0.0.0 | 255.255.255.255 |

## Subnetting

Subnetting or subnetworking basically means to branch off a network. It can be done for a variety of reasons like network in an organization, use of different physical media \(such as Ethernet, FDDI, WAN, etc.\), preservation of address space, and security. The most common reason is to control network traffic.

The basic idea in subnetting is to partition the host identifier portion of the IP address into two parts −

* A subnet address within the network address itself; and
* A host address on the subnet.

For example, a common Class B address format is N1.N2.S.H, where N1.N2 identifies the Class B network, the 8-bit S field identifies the subnet, and the 8-bit H field identifies the host on the subnet.

