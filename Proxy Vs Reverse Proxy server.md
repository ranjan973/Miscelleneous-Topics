# Reverse Proxy – Quick Notes

## What is a Reverse Proxy?

A **reverse proxy** is a server that sits in front of one or more web servers and forwards client requests to those servers.

Instead of users directly accessing the web server, they communicate with the reverse proxy, which then communicates with the backend servers on their behalf.

### Flow

```text
Client Browser
      |
      v
+----------------+
| Reverse Proxy  |
+----------------+
      |
      v
+----------------+
| Web Server(s)  |
+----------------+
```

---

# What is a Forward Proxy?

A **forward proxy** sits in front of clients and forwards their requests to the Internet.

### Flow

```text
Client
   |
   v
+---------------+
| Forward Proxy |
+---------------+
   |
   v
Internet Websites
```

### Why use a Forward Proxy?

- Bypass network restrictions
- Content filtering
- Hide client IP address
- Improve user privacy

---

# Forward Proxy vs Reverse Proxy

| Forward Proxy | Reverse Proxy |
|--------------|---------------|
| Protects clients | Protects servers |
| Sits in front of users | Sits in front of web servers |
| Hides client identity | Hides server identity |
| Used for browsing control | Used for performance and security |

### Easy Way to Remember

- **Forward Proxy = Client Side Proxy**
- **Reverse Proxy = Server Side Proxy**

---

# Reverse Proxy Architecture

```text
Users
  |
  v
+----------------+
| Reverse Proxy  |
+----------------+
       |
  -----------------
  |       |       |
  v       v       v
Server1 Server2 Server3
```

Users never communicate directly with backend servers.

---

# Benefits of Reverse Proxy

## 1. Load Balancing

Distributes incoming requests across multiple servers.

### Example

```text
Request 1 -> Server A
Request 2 -> Server B
Request 3 -> Server C
```

### Benefits

- Prevents server overload
- Improves availability
- Handles traffic spikes

---

## 2. Security Protection

Backend server IPs remain hidden.

### Benefits

- Protection from DDoS attacks
- Reduced attack surface
- Blocks malicious traffic before reaching servers

---

## 3. Global Server Load Balancing (GSLB)

Users are routed to the geographically nearest server.

### Example

```text
India User  -> India Server
US User     -> US Server
Europe User -> Europe Server
```

### Benefits

- Lower latency
- Faster page load times
- Better user experience

---

## 4. Caching

Frequently requested content is stored at the proxy.

### Example

```text
User 1 requests image
Proxy fetches from origin and caches it

User 2 requests same image
Proxy serves cached copy
```

### Benefits

- Faster response times
- Reduced backend load
- Lower bandwidth usage

---

## 5. SSL/TLS Offloading

The reverse proxy handles HTTPS encryption/decryption instead of the backend servers.

### Flow

```text
Client HTTPS
      |
      v
Reverse Proxy
(Decrypts SSL)
      |
      v
Backend Server
```

### Benefits

- Reduces server CPU usage
- Simplifies certificate management
- Improves application performance

---

# Real-World Examples

## Cloudflare

Acts as a reverse proxy:

```text
User
  |
Cloudflare
  |
Origin Server
```

Provides:

- CDN
- DDoS protection
- Caching
- SSL termination

---

## Nginx as Reverse Proxy

```text
Internet
   |
 Nginx
   |
Apache/Tomcat/Application
```

Commonly used for:

- Load balancing
- SSL termination
- Request routing
- Caching

---

# Reverse Proxy in Kubernetes

```text
User
  |
Ingress Controller
(Nginx)
  |
Services
  |
Pods
```

Ingress Controller acts as a reverse proxy.

---

# Interview Questions

### What is a reverse proxy?

A server that sits in front of backend servers and forwards client requests while hiding the origin servers.

### Why use a reverse proxy?

- Load balancing
- Security
- Caching
- SSL offloading
- High availability

### Difference between forward and reverse proxy?

A forward proxy represents clients, whereas a reverse proxy represents servers.

### Is Nginx a reverse proxy?

Yes. Nginx is commonly used as a reverse proxy, load balancer, and web server.

### Is Cloudflare a reverse proxy?

Yes. Cloudflare sits between users and origin servers and acts as a global reverse proxy.

---

# Quick Revision

✅ Forward Proxy → Protects Clients

✅ Reverse Proxy → Protects Servers

✅ Load Balancing → Distributes traffic

✅ Caching → Faster responses

✅ SSL Offloading → Handles HTTPS encryption

✅ Hides Origin Server IP

✅ Improves Security, Performance, and Availability

### Memory Trick

```text
Forward Proxy  -> User Side
Reverse Proxy  -> Server Side
```
