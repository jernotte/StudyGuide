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

##### Prototype Pollution

1. What is prototype pollution?  
**Expected Answer**: Prototype pollution is a JavaScript vulnerability that enables an attacker to add arbitrary properties to global object prototypes, which may then be inherited by user-defined objects. Although prototype pollution is often unexploitable as a standalone vulnerability, it lets an attacker control properties of objects that would otherwise be inaccessible. If the application subsequently handles an attacker-controlled property in an unsafe way, this can potentially be chained with other vulnerabilities. In client-side JavaScript, this commonly leads to DOM XSS, while server-side prototype pollution can even result in remote code execution.

1. How do prototype pollution vulnerabilities arise?  
**Expected Answer**: when a JavaScript function recursively merges an object containing user-controllable properties into an existing object, without first sanitizing the keys. This can allow an attacker to inject a property with a key like __proto__, along with arbitrary nested properties. The merge operation may assign the nested properties to the object's prototype instead of the target object itself. As a result, the attacker can pollute the prototype with properties containing harmful values, which may subsequently be used by the application in a dangerous way.

1. What is the special meaning of the __proto__ property?  
**Expected Answer**: Every object has a special property that you can use to access its prototype. Although this doesn't have a formally standardized name, __proto__ is the de facto standard used by most browsers. This property serves as both a getter and setter for the object's prototype. This means you can use it to read the prototype and its properties, and even reassign them if necessary. 

1. Is it possible to pollute any prototype object?  
**Expected Answer**: Yes, but this commonly occurs with the built-in global `Object.prototype`.

1. Exploitation of prototype pollution requires the what key components?  
**Expected Answer**: 

   * A prototype pollution source - This is any input that enables you to poison prototype objects with arbitrary properties.
   * A sink - In other words, a JavaScript function or DOM element that enables arbitrary code execution.
   * An exploitable gadget - This is any property that is passed into a sink without proper filtering or sanitization.

1. What are prototype pollution sources?  
**Expected Answer**: A prototype pollution source is any user-controllable input that enables you to add arbitrary properties to prototype objects. The most common sources are as follows:

   * The URL via either the query or fragment string (hash)
   * JSON-based input
   * Web messages

1. Explain how prototype pollution via the URL works?  
**Expected Answer**: For the url `https://vuln.com/?__proto__[evilProperty]=payload`. A URL parser may interpret __proto__ as an arbitrary string, but if `key:value` are merged into an existing object as properties. The recursive merge operation may assign the value of evilProperty using a statement equivalent to the following: `targetObject.__proto__.evilProperty = 'payload';` During this assignment, the JavaScript engine treats __proto__ as a getter for the prototype. As a result, evilProperty is assigned to the returned prototype object rather than the target object itself. Assuming that the target object uses the default Object.prototype, all objects in the JavaScript runtime will now inherit evilProperty, unless they already have a property of their own with a matching key.

 