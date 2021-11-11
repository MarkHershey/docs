# Network Data Units

***Datagram*** vs **Segment** vs **Packet** vs **Frame** vs **Fragment** 

## Datagram

Datagram is only used in two places.

Usages:

- UDP Datagram (Transport Layer)
- IP Datagram (Network Layer)

## Segment

Usages:

- TCP Segment (Transport Layer)

## Packet

Packet is the most general term to describe a unit of data in a network. Usually a packet is the actual data (payload) needs to be sent wrapped in some protocol-defined headers. Mostly use in Transport Layer and Network Layer.

Usages:

- TCP Packet (same as TCP Segment) (Transport Layer)
- UDP Packet (same as UDP Datagram) (Transport Layer)
- IP Packet (same as IP Datagram) (Network Layer)

## Frame

Frame is only used in Link Layer or Physical Layer.

## Fragment

Fragment is used when data needs to be chopped/split into smaller pieces or **fragments** due to _MTU (Maximum Transmission Unit)_ limitation.


## References

- [StackOverflow - Definition of Network Units: Fragment, Segment, Packet, Frame, Datagram](https://stackoverflow.com/a/11637061)
- [Definition of Network Units: Packet, Fragment, Frame, Datagram, and Segment](https://www.baeldung.com/cs/networking-packet-fragment-frame-datagram-segment)
- [Wikipedia - Internet Protocol Suite](https://en.wikipedia.org/wiki/Internet_protocol_suite)