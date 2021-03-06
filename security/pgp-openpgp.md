[TOC]

# Overview
**Pretty Good Privacy (PGP)** is *data encryption and decryption* software that provides *cryptographic privacy* and *authentication* for data communication.

PGP is often used for signing, encrypting, and decrypting texts, e-mails, files, directories, and whole disk partitions and to increase the security of e-mail communications.

## History
- Phil Zimmermann created the first version of PGP encryption in 1991.
- In July 1997, PGP Inc. proposed to the IETF that there be a standard called OpenPGP.
	+ The current specification is [RFC 4880][3] (November 2007)
	+ In 2012, encryption based on elliptic curve cryptography (ECDSA, ECDH) was extended by [RFC 6637][4]
	+ Support of EdDSA will be added by [draft-koch-eddsa-for-openpgp-00][1] proposed in 2014

# Design
PGP encryption uses a serial combination of **hashing**, **data compression**, **symmetric-key cryptography**, and finally **public-key cryptography**; each step uses one of several supported algorithms.

The first version of this system was generally known as a **web of trust** to contrast with the **X.509 system**. Current versions of PGP encryption include both options through an automated key management server.

## Compatibility
Newer PGP systems that support newer features and algorithms are able to create encrypted messages that older PGP systems cannot decrypt, even with a valid private key. Therefore, it is essential that partners in PGP communication understand the PGP system of each other.

## Confidentiality
PGP can be used to send messages confidentially.
- The message is encrypted using a symmetric encryption algorithm, which requires a symmetric key.
	+ Each symmetric key is used only once and is also called a session key.
- The session key is encrypted by the receiver's public key. Only the private key belonging to the receiver can decrypt the session key.

## Digital signatures
PGP supports message authentication and integrity checking.
- **Integrity checking** is used to detect whether a message has been altered since it was completed.
- **Message authentication** is used to determine whether it was actually sent by the person or entity claimed to be the sender.
	+ PGP computes a hash (a message digest) from the plaintext and then creates the digital signature from that hash using the sender's private key.

## Web of trust
### Introduction
Both when **encrypting messages** and when **verifying signatures**, it is critical that the public key used to send messages to someone or some entity actually does **belong** to the intended recipient.

Simple downloading a public key from somewhere is not an overwhelming assurance of that association; deliberate (or accidental) impersonation is possible.

From its first version, PGP has always included provision for distributing user's public keys in an **identity certificate**, which is also constructed cryptographically so that any tempering (or accidental garble) is readily detectable.

However, merely making a certificate which is impossible to modify without being detected is insufficient; this can prevent corruption only after the certificate has been created, not before. Users must also ensure by some means that the public key in a certificate actually does belong to the person or entity claiming it.

After that version, PGP has included an **internal certificate vetting scheme** to assist with this, a trust model which has been called a web of trust.
- A given public key (information binding a user name to a key) may be digitally signed by a third party user to attest to the association between someone (actually a user name) and the key.
- There are several levels of confidence which can be included in such signatures.
- The web of trust protocol was first described by Zimmermann in 1992, in the manual for PGP version 2.0.
- Its **decentralized trust model** is an alternative to the **centralized trust model** of a public key infrastructure (PKI), which relies exclusively on a *certificate authority*.

### Operation of a web of trust
All OpenPGP-compliant implementations include a certificate vetting scheme; its operation has been termed a web of trust.

OpenPGP identity certificates (which include public key(s) and owner information) can be digitally signed by other users. This is commonly done at [key signing parties][6].

A vote counting scheme which can be used to determine which identity certificates will trust while using PGP.
- Three partially trusted endorsers have vouched for a certificate
- Or one fully trusted endorser has done so.

The scheme is flexible, unlike most public key infrastructure designs, and leaves trust decision(s) in the hands of individual users. It is not perfect and requires both caution and intelligent supervision by users.

### Web of trust problems
- Users, whether individuals or organizations, who lose track of a private key can no longer decrypt messages sent to them produced using the matching public key found in an OpenPGP certificate.
-

# [OpenPGP card][7]
- Remembering to look at references section of the Wikipedia page.
- [Yubico explains secure hardware][8]

# References
1. [Homepage][1]
2. [Wikipedia][2]
3. [RFC4880 - OpenPGP][3]
4. [RFC6637 - ECDSA/ECDH][4]
5. [EdDSA Draft][5]
6. [Key signing parties][6]
7. [OpenPGP card][7]
8. [Yubico explains secure hardware][8]
9. [OpenPGPJS][9]

[1]: http://www.openpgp.org/ "OpenPGP Homepage"
[2]: https://en.wikipedia.org/wiki/Pretty_Good_Privacy "Wikipedia Pretty Good Privacy"
[3]: https://tools.ietf.org/html/rfc4880 "RFC 4880"
[4]: https://tools.ietf.org/html/rfc6637 "RFC 6637"
[5]: https://tools.ietf.org/html/draft-koch-eddsa-for-openpgp-00 "EdDSA Draft"
[6]: https://en.wikipedia.org/wiki/Key_signing_party "Key signing parties"
[7]: https://en.wikipedia.org/wiki/OpenPGP_card "OpenPGP card"
[8]: https://www.yubico.com/2016/05/secure-hardware-vs-open-source/ "Yubico explains secure hardware"
[9]: https://openpgpjs.org/ "OpenPGPJS"
