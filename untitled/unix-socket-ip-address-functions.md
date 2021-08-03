# Unix Socket - IP Address Functions

Unix provides various function calls to help you manipulate IP addresses. These functions convert Internet addresses between ASCII strings \(what humans prefer to use\) and network byte ordered binary values \(values that are stored in socket address structures\).

The following three function calls are used for IPv4 addressing −

* int inet\_aton\(const char \*strptr, struct in\_addr \*addrptr\)
* in\_addr\_t inet\_addr\(const char \*strptr\)
* char \*inet\_ntoa\(struct in\_addr inaddr\)

## int inet\_aton\(const char \*strptr, struct in\_addr \*addrptr\)

This function call converts the specified string in the Internet standard dot notation to a network address, and stores the address in the structure provided. The converted address will be in Network Byte Order \(bytes ordered from left to right\). It returns 1 if the string was valid and 0 on error.

Following is the usage example −

```text
#include 

(...)

   int retval;
   struct in_addr addrptr
   
   memset(&addrptr, '\0', sizeof(addrptr));
   retval = inet_aton("68.178.157.132", &addrptr);

(...)
```

## in\_addr\_t inet\_addr\(const char \*strptr\)

This function call converts the specified string in the Internet standard dot notation to an integer value suitable for use as an Internet address. The converted address will be in Network Byte Order \(bytes ordered from left to right\). It returns a 32-bit binary network byte ordered IPv4 address and INADDR\_NONE on error.

Following is the usage example −

```text
#include 

(...)

   struct sockaddr_in dest;

   memset(&dest, '\0', sizeof(dest));
   dest.sin_addr.s_addr = inet_addr("68.178.157.132");
   
(...)
```

## char \*inet\_ntoa\(struct in\_addr inaddr\)

This function call converts the specified Internet host address to a string in the Internet standard dot notation.

Following is the usage example −

```text
#include 

(...)

   char *ip;
   
   ip = inet_ntoa(dest.sin_addr);
   
   printf("IP Address is: %s\n",ip);
   
(...)
```

