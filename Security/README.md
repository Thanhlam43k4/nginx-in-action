## Nginx Security 

**Overview**

- TLS (Transport Layer Security) and SSL(Secure Sockets Layer) are cryptographic protocols designed to provide secure communication over a computer network. They are most commonly used in securing connections between web browsers and servers.

**How TLS/SSL Works**

1. Handshake: When a client (eg., a web browser) connects to a server, they perform a handshake. During this process, they agree on encryption algorithms and exchange keys to establish a secure connection.

2. Encryption: Data transmitted between the client and server is encrypted using the agreed-upon encryption algorithm, ensuring that any intercepted data is unreadable.

3. Certificates: The server typically presents a digital certificate issued by a trusted Certificate Authority (CA) to verify its identity to the client.

4. Session: Once the handshake is complete,the client and server can securely exchange data over the established encrypted session.

**Key Differences Between TLS and SSL**

- Security: TLS is more secure than SSL, with improved cryptographic algorithms and stronger security measures.

- Compatibility: Modern systems and browsers support TLS, with most having deprecated support for SSL due to its vulnerabilities.

- Performance: TLS offers better performance, especially with TLS 1.3, which has more streamlined handshake process.


In summary, TLS is more secure and modern protocol that has replaced SSL. Whenever you see "HTTPS" in a web address, it's typically secured with TLS, even if it is sometimes still referred to as "SSL"
