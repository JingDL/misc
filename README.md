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
