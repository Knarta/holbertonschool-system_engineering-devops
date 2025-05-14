# Simple Web Infrastructure Design

## Component Explanations

### What is a server?
A server is a computer or system that provides resources, data, services, or programs to other computers, called clients, over a network. In this infrastructure, it's a single physical or virtual machine that hosts all the components.

### What is the role of the domain name?
The domain name (foobar.com) serves as a human-readable address that maps to the server's IP address (8.8.8.8). It makes it easier for users to remember and access the website instead of using the IP address directly.

### What type of DNS record www is in www.foobar.com?
The "www" in www.foobar.com is a CNAME (Canonical Name) record. It's an alias that points to the main domain name (foobar.com), which in turn points to the server's IP address (8.8.8.8).

### What is the role of the web server?
The web server (Nginx) is responsible for:
- Handling HTTP requests from clients
- Serving static content (HTML, CSS, images)
- Forwarding dynamic requests to the application server
- Managing SSL/TLS encryption
- Handling basic security features

### What is the role of the application server?
The application server is responsible for:
- Executing the application code
- Processing business logic
- Generating dynamic content
- Handling user sessions
- Managing application state

### What is the role of the database?
The database (MySQL) is responsible for:
- Storing and managing data
- Handling data queries from the application server
- Ensuring data integrity
- Managing data relationships
- Providing data persistence

### What is the server using to communicate with the computer of the user requesting the website?
The server communicates with the user's computer using the HTTP/HTTPS protocol over TCP/IP. This communication is typically secured using SSL/TLS encryption to protect data in transit.

## Infrastructure Issues

### Single Point of Failure (SPOF)
- The entire website goes down if the server fails
- No redundancy or backup systems
- All components (web server, application server, database) are on the same machine

### Downtime when maintenance needed
- The entire website must be taken down for maintenance
- Updates to any component require a full server restart
- No ability to perform zero-downtime deployments
- Database maintenance affects the entire application

### Cannot scale if too much incoming traffic
- Limited by the server's resources (CPU, RAM, storage)
- Cannot handle high traffic loads
- No load balancing capabilities
- Database performance becomes a bottleneck under heavy load
- No horizontal scaling possible
