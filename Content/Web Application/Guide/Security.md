## Study Guide

#### Topics
1. Web Application
2. Web Services

#### Questions

1. What is a race condition?
2. What is a race window?
3. What is a limit overrun race condition?
4. How do you detect and exploit limit overrun race conditions?
5. What is the primary challenge for exploiting limit overrun race conditions?
6. What are the two mechanism that burp uses to reduce the challenges, mainly network jitter, and which version of HTTP are they used for? 
7. What is the Classic Last-Byte Synchronization Technique (for HTTP/1)?  
8. What is the Single-Packet Attack Technique (for HTTP/2)?
9. Explain how to prevent race condition vulnerabilities. 
10. Explain what a Time-of-Check to Time-of-Use (TOCTOU) race condition is and provide a strategy for mitigating such vulnerabilities.

### Web Security

Content will be separated by attack types.

##### Race conditions

1. What is a race condition attack?  
**Expected Answer**: A race condition attack uses carefully timed requests to cause intentional collisions and exploit this unintended behavior.

1. What is a race window?  
**Expected Answer**: The period of time during which a collision is possible.

1. What is a limit overrun race condition?  
**Expected Answer**: A limit overrun race condition occurs when multiple threads or processes concurrently modify a shared resource, like a counter or an array index, without proper synchronization, potentially causing the resource to exceed its predefined limit.

1. How do you detect and exploit limit overrun race conditions?  
**Expected Answer**: 

   * Identify a single-use or rate-limited endpoint that has some kind of security impact or other useful purpose.
   * Issue multiple requests to this endpoint in quick succession to see if you can overrun this limit.

1. What is the primary challenge for exploiting limit overrun race conditions?  
**Expected Answer**: The primary challenge is timing the requests so that at least two race windows line up, causing a collision. This issues can stem from network latency, jitter, and internal latency. This window is often just milliseconds and can be even shorter.

1. What are the two mechanism that burp uses to reduce the challenges, mainly network jitter, and which version of HTTP are they used for?  
**Expected Answer**: 

   * For HTTP/1, it uses the classic last-byte synchronization technique.
   * For HTTP/2, it uses the single-packet attack technique

1. What is the Classic Last-Byte Synchronization Technique (for HTTP/1)?  
**Expected Answer**: The "last-byte synchronization" method involves preparing multiple requests and then sending all but the last byte of each request to the server. These partial requests are held by the server, waiting for completion. Once all the requests are almost fully sent, the final bytes are rapidly sent out. This causes the server to receive the end of all requests in quick succession, effectively simulating a race condition. This technique relies on the behavior of TCP and HTTP/1, where multiple requests can be lined up on the same connection, and the server processes them as they are fully received.

1. What is the Single-Packet Attack Technique (for HTTP/2)?  
**Expected Answer**: HTTP/2 allows multiple requests to be sent concurrently over the same connection using a multiplexing feature. This means that different requests can be intermingled on the wire, sent in fragments (frames) in an interleaved fashion. The "single-packet attack" refers to a method where the entire request or critical parts of different requests are crafted to fit within a single TCP packet. This can ensure that multiple requests (or critical parts of them) are processed by the server very closely together in time. By controlling the packet construction in this manner, a tester can more effectively simulate race conditions in an HTTP/2 environment, as the server receives and processes these requests in rapid succession.

1. Explain how to prevent race condition vulnerabilities.  
**Expected Answer**: 

   * Synchronization mechanisms, like mutexes, semaphores, critical sections, and locks, help in controlling access to shared resources in a concurrent environment. By ensuring that only one thread or process can access a shared resource at a time, these mechanisms prevent simultaneous conflicting accesses which can lead to race conditions.
   * Atomic operations are executed in a single, indivisible step, ensuring that they complete entirely without any interruption. This characteristic is crucial for preventing race conditions because it ensures the integrity and consistency of operations on shared resources. When an operation is atomic, no other thread can observe the operation in a half-completed state, thereby preventing concurrent access issues.
   * Minimizing shared state involves reducing the amount of data or resources shared among multiple threads or processes. Designing systems with more self-contained and independent modules can effectively minimize shared state.

1. Explain what a Time-of-Check to Time-of-Use (TOCTOU) race condition is and provide a strategy for mitigating such vulnerabilities.  
**Expected Answer**: A Time-of-Check to Time-of-Use (TOCTOU) race condition occurs when a program checks the state of a resource, like a file or a database entry, and then uses that resource based on the check's results at a later time. If the resource's state changes between the check and the use, it can lead to inconsistencies or security vulnerabilities. For example, a program might check if a file exists and has the right permissions, but by the time it actually reads the file, the file might have been changed or replaced.
To mitigate TOCTOU vulnerabilities, one effective strategy is to perform the check and the use of the resource as a single atomic operation, ensuring that the state does not change between the check and the use. Another approach is to use file locks or transactional mechanisms where the resource is locked during the check and remains locked until the use is completed.



