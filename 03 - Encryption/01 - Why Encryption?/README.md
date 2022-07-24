# Why Encryption is Important?

`Cryptography` is used to protect confidentiality, ensure integrity, ensure authenticity. 

You use cryptography every day most likely, and you’re almost certainly reading this now over an encrypted connection.

When logging into `TryHackMe`, your credentials were sent to the server. 

These were encrypted, otherwise someone would be able to capture them by snooping on your connection.

When you connect to `SSH`, your client and the server establish an encrypted tunnel so that no one can snoop on your session.

When you connect to your bank, there’s a `certificate` that uses cryptography to prove that it is actually your bank rather than a hacker.

When you download a file, how do you check if it downloaded right? 

You can use cryptography here to verify a `checksum` of the data.

You rarely have to interact directly with cryptography, but it silently protects almost everything you do digitally.

Whenever sensitive user data needs to be stored, it should be encrypted. 

Standards like [PCI-DSS](https://www.pcisecuritystandards.org/documents/PCI_DSS_for_Large_Organizations_v1.pdf) state that the data should be encrypted both at rest (in storage) AND while being transmitted. 

If you’re handling payment card details, you need to comply with these `PCI` regulations. 

Medical data has similar standards. 

With legislation like `GDPR` and California’s data protection, data breaches are extremely costly and dangerous to you as either a consumer or a business.

**DO NOT** encrypt passwords unless you’re doing something like a `password manager`. 

Passwords should not be stored in `plaintext`, and you should use `hashing` to manage them safely.
