# DNS - Domain Name Systerm 

## What is DNS?

!!! tldr "ELI5"

    DNS Server is like a public phonebook for the Internet, whenever you type an URL, `www.google.com` for example, into your browser and hit enter, your browser needs to fetch website content from Google's server, but your browser does not know the actual IP address of Google's server yet. 

    - If `www.google.com` is the name of a building you want to visit.
    - IP address of Google's server is the unambiguous address of the building. 

    Therefore, after you requested that you want to visit Google, your request will be routed to a nearby DNS server which helps you get the actual IP Address of the URL you requested.

    DNS exists so that you don't have to memorize the non-human-friendly IP addresses of all the websites you want to visit. Instead, you just need to know their names (URLs), and the DNS server will figure out the actual addresses for you behind the scene.

### DNS Lockup behind a Website Visit

1. User → `Browser` → `DNS Resolver` → `DNS Root Server` → `Top Level Domain (TLD) DNS server` → `Domain Nameserver` → ... → `(Authoritative) Domain Nameserver`
2. `Browser` gets `IP Address` of interest back from `DNS Resolver`
3. `Browser` makes a `HTTP request` to the `IP address`.
4. The server at that `IP address` returns the webpage to be rendered in the `Browser`.
5. User sees the rendered content from the `Browser`.


### 3 Types of DNS Servers

- DNS Resolver
    A DNS resolver (recursive resolver), is designed to receive DNS queries and is responsible for tracking the IP address for that hostname.
- DNS Root Server
    The root server is the first step in the journey from hostname to IP address. It responds to the DNS resolver with the address of a Top Level Domain (TLD) DNS server.
- Authoritative DNS Server
    The Authoritative Name Server is the last stop in the name server query—it takes the hostname and returns the correct IP address to the DNS Resolver (or if it cannot find the domain, returns the message NXDOMAIN).

## DNS Record Configuration 

### A Record

A Records (Address Mapping Record) are for IPv4 addresses only and tell a request where your domain should direct to.

### AAAA Record

AAAA Records (IPV6 Address Mapping Record) are for IPv6 addresses only and tell a request where your domain should direct to.

### CNAME Record

CNAME Records (Canonical Name Record) act as an alias by mapping a hostname to another hostname. When a DNS client requests a record that contains a CNAME, which points to another hostname, the DNS resolution process is repeated with the new hostname.

A Canonical Name or CNAME record is a type of DNS record that maps an alias name to a true or canonical domain name. CNAME records are typically used to map a subdomain such as www or mail to the domain hosting that subdomain’s content.

!!! example
    A CNAME record has Hostname = `www.example.com` and Value = `example.com`
    
    - `www.example.com` becomes an alias for `example.com`.
    - This record maps the web address `www.example.com` to the actual web site for the domain `example.com`.

### MX Record

MX Records (Mail Exchanger Record) specify the mail servers responsible for accepting emails on behalf of your domain, and priority value if your provider has a number of mail servers for contingency.

### NS Record

NS Records (Name Server Record) specify the servers which are providing DNS services for your domain. You can use these to create subzones if you need to direct part of your traffic to another DNS service.

!!! tips
    NS Records could also be used to redirect/delegate DNS services. For example, you bought a domain from one of the domain name vendors (`godaddy.com`, `namecheap.com`, etc), usually the vendor provides free DNS service for your domain, but you prefer another DNS service provider (`DigitalOcean` for example), so that you can manage your DNS configurations at `DigitalOcean` side instead of your domain vendor side.

    To do so, you can add a NS Record that redirect any DNS query comming to your domain vendor's DNS server to your desired DNS service provider.

### TXT Record

TXT Records are used to associate a string of text with a hostname. These are primarily used for verification.


--- 

Futher Readings:

- [Cloudflare: What Is DNS? | How DNS Works](https://www.cloudflare.com/en-gb/learning/dns/what-is-dns/)
- [Google Help: DNS basics](https://support.google.com/a/answer/48090)