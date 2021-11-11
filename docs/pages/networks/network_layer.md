# Network Layer

## Control Plane

- Per-router control plane 
- Logically centralized control plane


## IP - Internet Protocol

### IP Datagram Format

- `5 x 32-bit` fixed-length headers 
    - `4 bits` protocol version
    - `4 bits` header length (number of words)
    - `8 bits` type of service
    - `16 bits` total length (total datagram length in bytes)
    - `16 bits` identification (identifier for fragmentation)
    - `3 bits` flags (set to 1 if this is not the last fragment)
    - `13 bits` fragment offset (for reassembly)
    - `8 bits` time to live (maximum number of remaining hops)
    - `8 bits` protocol (specifies the encapsulated protocol in data)
    - `16 bits` header checksum
    - `32 bits` source IP address
    - `32 bits` destination IP address
- options (variable length)
- variable-length payload

### IP Addressing

- IPV4: 32-bit address
- IPV6: 128-bit address

What is an interface?

What is a subnet?




## References

- [Description of the Internet Protocol, IP](https://www.eit.lth.se/ppplab/IPHeader.htm)