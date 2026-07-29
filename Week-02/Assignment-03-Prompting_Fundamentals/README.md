# FL-02: Prompt Engineering Iteration Log

## Student
- Name: Habib Ullah
- Internship: FlyRank AI – General AI Fluency Track
- Task from FL-01: Understand technical concepts with AI
- Selected Topic: HTTP vs HTTPS

---

# Objective

My selected task from FL-01 was **Understand technical concepts with AI**. To practice prompt engineering, I chose the topic **HTTP vs HTTPS** because I wanted to understand the concept, how it works, and how it will help me in future work.

---

# Version 1 – Naive Prompt

## Technique
Naive Prompt

### Prompt

```text
What is the difference between HTTP and HTTPS?
```

### Output


HTTP and HTTPS are both protocols used to transfer data between a web browser and a server, but they differ mainly in security:
HTTP (HyperText Transfer Protocol)
Sends data in plain text
No encryption — anyone intercepting the traffic (on public Wi-Fi, for example) can read it
Faster in theory since there's no encryption overhead, though the difference is usually negligible today
Uses port 80 by default
URLs start with http://
HTTPS (HyperText Transfer Protocol Secure)
Encrypts data using TLS (Transport Layer Security, the successor to SSL)
Protects against eavesdropping and man-in-the-middle attacks
Verifies the identity of the website via a digital certificate, so you know you're actually talking to the real server and not an impostor
Uses port 443 by default
URLs start with https://, usually shown with a padlock icon in the browser

Why it matters
Any site handling logins, payments, or personal data should use HTTPS
Browsers now flag plain HTTP sites as "Not Secure"
Search engines like Google factor HTTPS into rankings
Getting an HTTPS certificate (e.g., via Let's Encrypt) is free and standard practice now, so there's little reason for modern sites to still use plain HTTP

In short: HTTPS is HTTP with a layer of encryption and authentication added on top, making it the safer choice for pretty much any website today.

### Observation

The AI only explained the differences between HTTP and HTTPS. It did not explain what HTTP is first or why HTTPS is needed, making it less helpful for understanding the overall concept.

---

# Version 2 – Role Assignment

## Technique
Role Assignment

### Prompt

```text
You are an experienced computer networking instructor. Explain the difference between HTTP and HTTPS.
```

### Output


Good question — this is one of those topics that seems simple on the surface but actually touches several core networking concepts, so let's build it up properly rather than just listing differences.

Start with what HTTP actually is

HTTP (HyperText Transfer Protocol) is an application-layer protocol — it sits at the top of the OSI/TCP-IP stack. Its job is simple: define a request/response format so a client (browser) can ask a server for a resource and get it back. Think of it as the "grammar" of web communication — GET, POST, headers, status codes like 200 or 404.

Here's the key thing to understand: HTTP says nothing about security. It was designed in the early '90s when the web was mostly academic documents. Every request and response travels as plain text over the TCP connection.

Now, what problem does that create?

Ask yourself: what happens to that plain text as it travels from your laptop to the server? It passes through your router, your ISP, maybe several intermediate routers on the internet backbone. At every one of those hops, someone could read it — or worse, alter it. This is called a man-in-the-middle vulnerability. If you log into a site over HTTP, your password is sent as readable text.

This is where HTTPS comes in — but here's the important conceptual point:

HTTPS is not a different protocol from HTTP. It's HTTP running inside an encrypted tunnel called TLS (Transport Layer Security). Picture it like this:

Plain HTTP:    [Browser] --- HTTP (plaintext) ---> [Server]

HTTPS:         [Browser] --- TLS(encrypted tunnel) --- [Server]

                            └── HTTP travels inside here ──┘

So HTTP is still HTTP — same requests, same headers, same structure. It's just been wrapped in encryption before it hits the wire.

Let's walk through what happens when you connect to an HTTPS site, because this is where students usually have gaps:

Your browser opens a TCP connection to the server (port 443 instead of 80).
Before any HTTP data flows, a TLS handshake happens:
The server sends its digital certificate, issued by a trusted Certificate Authority (CA), proving "I am really amazon.com."
Browser and server perform a key exchange (typically ECDHE) to agree on a shared secret key — done in a way that even someone watching the handshake can't derive the key.
Once that handshake finishes, both sides now share a symmetric encryption key. Only then does the actual HTTP request get sent — encrypted.

So HTTPS gives you three things HTTP doesn't — and I want you to remember these as a set:

Property	What it means
Confidentiality	Nobody sniffing the wire can read the data
Integrity	Nobody can tamper with the data in transit without detection
Authentication	You have cryptographic proof you're talking to the real server, not an imposter

A quick check for understanding: if HTTPS is just HTTP inside TLS, does the server have to do anything differently to handle HTTP requests once TLS is set up?

No — the web server software just sees decrypted HTTP requests, same as always. The TLS layer handles all the encryption/decryption transparently underneath. That's an important architectural insight: security was added as a layer, not by rewriting the application protocol.

One more thing worth knowing at this level: modern TLS (version 1.3) streamlined the handshake to a single round trip, so the performance cost of HTTPS today is nearly negligible — which is part of why there's no good excuse anymore for any site to run plain HTTP.

Want me to go deeper into the TLS handshake itself — the actual packet exchange and key derivation — or would it be more useful to look at how a firewall or proxy deals with HTTPS traffic it technically can't inspect?

### Observation

Now the AI explained the topic in a teacher-like style. It first explained what HTTP is, then why HTTPS is needed, and why HTTPS is better. It also used a simple text visualization, making the explanation easier to understand than Version 1.

---

# Version 3 – Context & Motivation

## Technique
Context and Motivation

### Prompt

```text
You are an experienced computer networking instructor. I know basic about networking. Explain HTTP and HTTPS so I understand clearly and use it in future work.
```

### Output


Good — since you already know basic networking, let's build on that foundation properly so this sticks with you long-term, not just for one project.

Start with what you already know

You know that when your browser talks to a server, data travels through the internet — through your router, your ISP, and various nodes in between — before reaching the destination. Keep that picture in mind, because it's the whole reason HTTPS exists.

HTTP: the foundation

HTTP (HyperText Transfer Protocol) is the application-layer protocol that defines how a browser (client) and a server talk to each other. It's basically a request-response system:

Client sends a request: "GET me this webpage"
Server sends a response: the HTML, images, data, etc.

That's it. Simple, lightweight, and it's been the backbone of the web since the early 1990s.

The catch: HTTP was designed for a web that didn't need to worry about security. So it sends everything — your requests, your data, your passwords if you're logging in — as plain, readable text.

Why that's a problem

Remember that picture of data hopping through multiple network nodes? At any of those hops, someone could technically intercept and read your traffic. This is called a man-in-the-middle scenario. On HTTP, if you log into a site on public Wi-Fi, your credentials are visible to anyone capturing that traffic with a tool like Wireshark.

HTTPS: HTTP plus a security layer

HTTPS doesn't replace HTTP — it wraps it in encryption using a protocol called TLS (Transport Layer Security — the modern version of what used to be called SSL).

Here's the mental model to keep for the future:

HTTP  = the message
TLS   = the locked envelope it travels in
HTTPS = HTTP sent inside that locked envelope
What happens when a connection is made (conceptually)

This is the part instructors love to test, so let's get it right:

Browser connects to the server (on port 443 instead of HTTP's port 80).
TLS handshake happens first, before any actual webpage data moves:
Server proves its identity using a digital certificate issued by a trusted Certificate Authority (CA).
Both sides agree on an encryption key through a secure key exchange — without ever transmitting that key in plain text.
Once that handshake completes, the browser and server now share a secret key. From this point on, all HTTP traffic between them is encrypted.

The server software itself doesn't even "see" the encryption — TLS handles that transparently underneath. The application still just processes normal HTTP requests once decrypted.

The three things HTTPS gives you — remember these as a set
Property	Meaning
Confidentiality	No one can read the data in transit
Integrity	No one can secretly alter the data in transit
Authentication	You have proof you're talking to the legitimate server, not an imposter
Why this matters for your future work

As you go further into networking or development, you'll run into HTTPS constantly:

Certificates — you'll need to know how to obtain and install them (e.g., via Let's Encrypt, a free and automated CA).
Reverse proxies — in real deployments, tools like Nginx often handle TLS termination, decrypting HTTPS traffic before passing plain HTTP to your actual application server.
APIs — virtually all modern APIs require HTTPS; understanding the handshake helps you debug connection/certificate errors instead of being confused by them.
Security tools — firewalls, proxies, and monitoring tools handle HTTPS traffic differently than HTTP because they often can't inspect encrypted content without special configuration (like SSL inspection).

A quick check for your understanding: if HTTPS encrypts everything, does that mean someone watching the network traffic can't tell which website you're visiting at all?

Not entirely — there's a detail called SNI (Server Name Indication), where the browser has to tell the server which hostname it wants before encryption is fully established, so the server knows which certificate to present. That hostname is technically visible unless newer protections like Encrypted Client Hello are used. It's a good example of how security is layered and imperfect — always worth digging one level deeper.

Want me to walk through the TLS handshake in more packet-level detail next, or would it help more to see how HTTPS fits into the broader picture of network security (like VPNs, firewalls, etc.)?

### Observation

The AI explained that HTTPS does not replace HTTP but works by sending HTTP through TLS. It also connected the explanation to future work by mentioning certificates, reverse proxies, APIs, and security tools, which made the response more relevant to my learning goal.

---

# Version 4 – Few-shot Examples

## Technique
Few-shot Examples

### Prompt

```text
Here is an example of how I want explanations.

Concept: Firewall

Explanation:
A firewall is a security system that controls which network traffic is allowed to enter or leave a computer.

Real-life analogy:
Think of a firewall as a security guard at the entrance of a building. The guard checks who is allowed to enter and blocks unauthorized people.

Why it matters:
Without a firewall, anyone could try to access your computer or network. A firewall helps protect your system from unwanted or malicious traffic.

Now explain HTTP vs HTTPS in the same style.
```

### Output


Concept: HTTP
Explanation:
HTTP (HyperText Transfer Protocol) is a set of rules that lets a browser and a server communicate and exchange data, like web pages. It sends this data as plain, readable text.

Real-life analogy:
Think of HTTP like sending a postcard through the mail. Anyone who handles that postcard along the way — the mail carrier, someone at a sorting center — can read exactly what's written on it.

Why it matters:
Because the data isn't hidden or protected, anyone intercepting the traffic (like on public Wi-Fi) can read sensitive information, such as passwords or personal details, as they travel across the network.

Concept: HTTPS
Explanation:
HTTPS (HyperText Transfer Protocol Secure) is HTTP combined with encryption, using a protocol called TLS. It scrambles the data before sending it, so only the sender and receiver can read it.

Real-life analogy:
Think of HTTPS like sealing that same message in a locked box before mailing it. Even if someone intercepts the box along the way, they can't open it or read what's inside — only the person with the correct key (the receiver) can unlock it.

Why it matters:
HTTPS protects your data — logins, payments, personal information — from being read or tampered with by anyone watching the network. It also verifies you're talking to the real website, not an imposter pretending to be one.

### Observation

The AI followed the style shown in my example. The explanation was more focused, easier to understand, and stayed closer to what I wanted. Unlike Version 3, it did not spend much time on advanced topics like the TLS handshake.

---

# Version 5 – Output Structure

## Technique
Output Structure

### Prompt

```text
Explain HTTP and HTTPS using this structure:

1. What is HTTP?
2. Difference between HTTP and HTTPS
3. Real-life analogy
4. What are the cons of HTTP?
5. How HTTPS helps in future work
```

### Output


1. What is HTTP
HTTP (HyperText Transfer Protocol) is a set of rules that lets a browser (client) and a server communicate. It works on a request-response basis — your browser sends a request ("give me this page"), and the server sends back a response (the webpage data). It runs on port 80 and sends all data as plain, readable text.

2. Difference between HTTP and HTTPS

	HTTP	HTTPS
Security	No encryption	Encrypted using TLS
Port	80	443
Data format	Plain text	Scrambled/encrypted
Certificate needed	No	Yes (issued by a trusted CA)
Identity verification	No	Yes — proves you're talking to the real server
URL prefix	http://	https://

3. Real-life Analogy
HTTP is like sending a postcard — anyone handling it along the way (mail carrier, sorting center) can read what's written on it.

HTTPS is like sealing that same message in a locked box before sending it. Even if someone intercepts the box, they can't open it — only the person with the right key can read the contents.

4. Cons of HTTP

No encryption — data travels as plain text, so anyone intercepting it (e.g., on public Wi-Fi) can read it.
No authentication — you have no way to verify you're actually talking to the real server, not an imposter.
No integrity protection — an attacker can secretly modify the data in transit (e.g., inject malicious code into a page) without you knowing.
Browser warnings — modern browsers flag HTTP sites as "Not Secure," which damages user trust.
SEO penalty — search engines like Google rank HTTPS sites higher, so HTTP hurts visibility.
Not compliant — many industries (finance, healthcare, e-commerce) legally require HTTPS for handling sensitive data.

5. How HTTPS helps in future work

Building secure applications — any project handling logins, payments, or personal data needs HTTPS by default.
Working with APIs — most modern APIs (payment gateways, cloud services, third-party integrations) require HTTPS-only connections.
Deployment skills — you'll need to know how to get and manage certificates (e.g., via Let's Encrypt) and configure tools like Nginx for TLS termination.
Debugging — understanding the TLS handshake helps you troubleshoot certificate errors, connection failures, and mixed-content warnings instead of being confused by them.
Security mindset — this is your entry point into broader security concepts you'll keep using — VPNs, firewalls, SSL inspection, and secure API design.
### Observation

The AI produced organized notes using the requested structure. The headings made the response easier to read and review. Compared with Version 4, the information was better organized and followed my required format.

---

# Version 6 – Step Decomposition

## Technique
Step Decomposition

### Prompt

```text
Step 1: First explain what HTTP and HTTPS are.

Step 2: Explain the difference between HTTP and HTTPS.

Step 3: Explain why using HTTP is risky.

Step 4: Explain the benefits of HTTPS.

Step 5: Explain how HTTPS helps in future work.
```

### Output

Step 1: What is HTTP and HTTPS

HTTP (HyperText Transfer Protocol) is a set of rules that lets a browser and a server communicate — your browser sends a request for a page, and the server sends back the data. It does this using plain, readable text, over port 80.

HTTPS (HyperText Transfer Protocol Secure) is the same HTTP communication, but wrapped in an encryption layer called TLS (Transport Layer Security). Before any data is exchanged, the browser and server perform a "handshake" to verify identity and agree on an encryption key. It runs on port 443.

Step 2: Difference between HTTP and HTTPS

	HTTP	HTTPS
Security	No encryption	Encrypted via TLS
Port	80	443
Data format	Plain text	Scrambled/unreadable to outsiders
Certificate	Not required	Required (issued by trusted CA)
Identity check	None	Verifies you're on the real server
Browser indicator	"Not Secure" warning	Padlock icon

Step 3: Why using HTTP is like taking a risk

Using HTTP is like handing your data to a stranger and trusting everyone who touches it along the way. Your request travels through multiple points — your router, your ISP, various internet nodes — before reaching the server. At any of those points, someone with the right tools can intercept and read it, since nothing is hidden.

This means:

Passwords, personal details, and payment info can be read in plain text
An attacker on the same network (e.g., public Wi-Fi) can eavesdrop easily
Data can be silently altered in transit — someone could inject malicious code into a page you're loading, and you'd have no way of knowing
You have no proof the server you're talking to is actually legitimate, so you could be sending data to an imposter

It's less "if" something goes wrong and more "when," especially on untrusted networks.

Step 4: Benefits of HTTPS

Confidentiality — your data is unreadable to anyone intercepting it
Integrity — data can't be secretly modified in transit without detection
Authentication — you get cryptographic proof you're talking to the real server, not a fake one
Trust signals — browsers show a padlock instead of a warning, which builds user confidence
Better SEO — search engines rank HTTPS sites higher
Compliance — required for handling sensitive data in finance, healthcare, e-commerce, etc.

Step 5: How HTTPS helps in future work

You'll be able to build applications that securely handle logins, payments, and personal data
Most modern APIs (payment gateways, cloud platforms, third-party services) require HTTPS-only connections, so you can't skip this
You'll gain hands-on skills managing certificates (e.g., via Let's Encrypt) and configuring servers like Nginx for TLS
Understanding the handshake process makes debugging certificate errors and connection issues much faster
It builds a foundation for broader security topics you'll keep encountering — VPNs, firewalls, secure API design, and encrypted communication in general

### Observation

The AI followed each step in order without missing any requested topic. Compared with Version 5, the explanation followed a logical learning sequence, used bullet points, and was easy to understand.

---

# Cross-Model Comparison

## Comparison

| Aspect | Claude | ChatGPT |
|---------|---------|----------|
| Tone | Simple| Medium|
| Accuracy |Accurate | Accurate|
| Structure | Less|More |
| Strength |Uses easy words, so it is easy to understand and provides detailed explanations | Uses slightly technical words and provides a more structured response|
| Weakness | May provide more explanation than needed| Gives shorter, to-the-point answers with less expansion|

## Conclusion:

After testing the same prompt on both models, I found that ChatGPT was easier to understand because of its simple wording and detailed explanations, while Claude provided a more structured and concise response. Both models performed well, but their communication styles were different.
---

# Final Prompt Template

```text
You are an experienced [ROLE].

My background:
[USER KNOWLEDGE]

Goal:
[LEARNING GOAL]

Please explain [TOPIC] by following these steps:

Step 1: Explain the basic concept.

Step 2:Compare it with related concepts when applicable, or explain important differences and relationships.

Step 3: Use a real-life analogy.

Step 4: Explain why it matters.

Step 5: Explain how it is used in real-world projects.

Present the response using clear headings and bullet points, and end with a short summary of the key takeaways.
```

---

# What I Learned

- Role assignment changes the teaching style.
- Adding context helps the AI tailor the explanation to my goal.
- Few-shot examples guide the AI to follow a preferred explanation style.
- Output structure makes the response easier to read and revise.
- Step decomposition helps the AI follow a logical teaching sequence without missing important points.

