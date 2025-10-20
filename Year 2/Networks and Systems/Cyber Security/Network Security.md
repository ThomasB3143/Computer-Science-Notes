Section: [[Cyber Security (Root)]]

Info exchanged between entities can have:

- Confidentiality
- Integrity
- Availability
# TCP/IP Problems

- No confidentiality, everything is displayed in plain-text
- No integrity, information can be modified in the packets (spoofing)
- No availability. it is easy to flood the network and disrupt packets
# Routing Protocols

When a routing point does not know the address of an entity, it broadcasts on the network to request to other entities if they know the address. Hence, any message on the internet can be intercepted and modified
# SSL/TLS

These are cryptographic protocols working between the transport and application layers. A certificate contains information from an entity, including its identity and its public key, and this information is signed by a known Certification Authority.

The client and server agree on their cryptographic preference, then the server sends its public key (signed by a certificate). The client sends a pre-master-key (PMS), encrypted by the public key. A pseudo-random function (PRF) then derives the session key from the PMS
# Network Management

Cryptography solves a lot of problems, but:

- Denial of Service attacks can still happen
- Encrypted messages can still be modified
- Encrypted information can still be captured and brute forced
- Encryption is inefficient

Network management techniques can cover these areas that cryptography misses.
# Firewall

A firewall sits between two networks, and implements a set of rules dictating which packets are accepted or denied

This a reference monitor, therefore must be [[Malicious Code#Reference Monitors|NEAT]]
### Packet Filtering

The decision to accept a packet is based on the structure of the packet. This can create virtual networks.
### Stateful

The current state of the connection is also considered. This can prevent SYN flooding attacks
### Application-aware

Data relevant to the application layer is also taken into account. This can filter out code injection and other sketchy keywords
### Policy Configuration

Rules are carried out from top to bottom. If the packet satisfies a rule, the action is applied. Otherwise, the next rule is checked and so on. Rules can have the following relationships:

- Shadowing:
	- When a rule matches all the packets that are matched by the rule below
	- The rule below is never activated
- Correlation:
	- Two rules have different actions, and some that match one match the other
- Generalisation:
	- Two rules have different actions, but the first rule can match all the packets that match the second rule
- Redundancy:
	- A rule is redundant if there is another rule with the same action, such that the policy is the same without the rule
### Limitations

Data can be tunnelled (through a SSH tunnel), and a firewall does not protect against insider attacks