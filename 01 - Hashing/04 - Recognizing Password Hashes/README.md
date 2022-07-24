# Recognizing Password Hashes

Automated hash recognition tools such as https://pypi.org/project/hashID/ exist, but they are unreliable for many formats. 

For hashes that have a prefix, the tools are reliable. 

Use a healthy combination of context and tools.  

If you found the hash in a web application database, it's more likely to be md5 than NTLM. 

Automated hash recognition tools often get these hash types mixed up, which highlights the importance of learning yourself.

Unix style password hashes are very easy to recognise, as they have a prefix. 

The prefix tells you the hashing algorithm used to generate the hash. 

The standard format is`$format$rounds$salt$hash`.

Windows passwords are hashed using NTLM, which is a variant of md4. 

They're visually identical to md4 and md5 hashes, so it's very important to use context to work out the hash type.

On Linux, password hashes are stored in `/etc/shadow`. 

This file is normally only readable by root. 

They used to be stored in `/etc/passwd`, and were readable by everyone.

On `Windows`, password hashes are stored in the `SAM`. 

Windows tries to prevent normal users from dumping them, but tools like mimikatz exist for this. 

Importantly, the hashes found there are split into `NT` hashes and `LM` hashes.

Here's a quick table of the most Unix style password prefixes that you'll see.

|Prefix	| Algorithm |
|--|--|
|$1$|	md5crypt, used in Cisco stuff and older Linux/Unix systems|
|$2$, $2a$, $2b$, $2x$, $2y$|	Bcrypt (Popular for web applications)|
|$6$	|sha512crypt (Default for most Linux/Unix systems)|

A great place to find more hash formats and password prefixes is the hashcat example page, available here: https://hashcat.net/wiki/doku.php?id=example_hashes.


For other hash types, you'll normally need to go by length, encoding or some research into the application that generated them. 

Never underestimate the power of research.
