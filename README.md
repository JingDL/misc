### SQL statement execution order
Usually the execution order is
1. FROM and JOIN
2. WHERE
3. GROUP BY
4. HAVING
5. SELECT
6. ORDER BY
7. LIMIT


### New Raccoon Attack Could Let Attackers Break SSL/TLS Encryption
According to [The Hacker New](https://thehackernews.com/2020/09/raccoon-ssl-tls-encryption.html), a new raccoon attack could steal the premaster screte.
Unlike RSA handshake, where the client generates the premaster screte, Diffie-Hellman algorithm generates the premaster screte on the server side.  The Racoon attack can figure out the DH ephemeral key by using high precision timing measurements.  We must avoid static DH algorithm, which reuses the same DH ephemeral key across sessions.


### IEEE 802.1X Related Information
[Wired 802.1X Deployment Guide](https://www.cisco.com/c/en/us/td/docs/solutions/Enterprise/Security/TrustSec_1-99/Dot1X_Deployment/Dot1x_Dep_Guide.html)

[Understanding IEEE* 802.11 Authentication and Association](https://www.intel.com/content/www/us/en/support/articles/000006508/network-and-i-o/wireless.html)

[Machine Authentication and User Authentication](https://www.networkworld.com/article/2940463/machine-authentication-and-user-authentication.html)

EAP — extensible authentication protocol (802.1x/EAP)
```
  1. A authentication server is added to the infrastructure.
  2. Suppliant — Authenticator — Authentication server
  3. Authentication server usually relies on a backend database (Microsoft Active Directory, Cisco ISE, or LDAP server) for maintaining usernames and passwords
```

EAPoL (EAP over LAN), protocol used between Supplicant and Authenticator.

RADIUS (Remote Authentication Dial-in User Service), protocol used between Authenticator and Authentication server.
```
Supplicant — EAPoL— Authenticator — RADIUS — Authentication server
```
Sequence of Operations
1. Initiation
    1. The authentication can be initiated by the supplicant or the switch(as an Authenticator).
    2. The supplicant can initiate Authentication by sending EAP-Start frame.
    3. The switch can initiate Authentication by sending an EAP-Request-Identity message when it detects a link up on a port
2. Authentication
    1. The switch relays messages between the supplicant and the authentication server by copy EAP messages in the EAPoL frame to the Attribute Value pairs (AV-pair) Innside a RADIUS packet and vice versa.
    2. The supplicant and the switch agree on EAP method (e.g. EAP-FAST, EAP-TLS, PEAP).
    3. Based on the selected EAP method, the supplicant may submit a token, password, certificate, or other kind of credential.
3. Authorization
    1. The authentication server returns a RADIUS Access-Accept message with an encapsulated EAP-Success message, or a RADIUS Access-Reject message with an encapsulated EAP-Failure message.
4. Accounting
    1. The switch can send details about the authorized session to the authentication server.
    2. The supplicant is not involved in accounting
5. Termination
    1. Link down for directly connected endpoints
    2. EAPoL Logoff messages
    3. An Inactivity timer on the switch

LEAP — lightweight EAP
	introduced by CISCO, but deprecated. It should not be used.
	It uses a dynamic key.
	user must provide username and password
