# Uses For Hashing

## What can we do with hashing?

Hashing is used for 2 main purposes in Cyber Security:

    To verify integrity of data 
    For verifying passwords.

## Hashing for password verification

Most webapps need to verify a user's password at some point. 

Storing these passwords in plain text would be bad. 

You've probably seen news stories about companies that have had their database leaked. 

Knowing some people, they use the same password for everything including their banking, so leaking these would be really really bad.

Quite a few data breaches have leaked plaintext passwords. 

### 1.

You’re probably familiar with `“rockyou.txt”` on `Kali` as a password wordlist. 

This came from a company that made widgets for `MySpace`. 

They stored their passwords in plaintext and the company had a data breach. 

The txt file contains over `14 million` passwords (although some are *unlikely* to have been user passwords).

### 2.

`Adobe` had a notable data breach that was slightly different. 

The passwords were encrypted, rather than hashed and the encryption that was used was not secure. 

This meant that the plaintext could be relatively quickly retrieved. 

If you want to read more about this breach, this post from `Sophos` is excellent: https://nakedsecurity.sophos.com/2013/11/04/anatomy-of-a-password-disaster-adobes-giant-sized-cryptographic-blunder/

### 3.

`Linkedin` also had a data breach. 

Linkedin used `SHA1` for password verification, which is quite quick to compute using GPUs. 

# 

You can't `encrypt` the passwords, as the key has to be stored somewhere. If someone gets the key, they can just decrypt the passwords.

This is where `hashing` comes in. 

What if, instead of storing the password, you just stored the hash of the password? 

This means you never have to store the user's password, and if your database was leaked then an attacker would have to crack each password to find out what the password was. 

That sounds fairly useful.

There's just one problem with this. 

What if two users have the `same` password? 

As a hash function will always turn the same input into the same output, you will store the same password hash for each user. 

That means if someone cracks that hash, they get into more than one account. 

It also means that someone can create a `"Rainbow table"` to break the hashes.

A `rainbow table` is a lookup table of hashes to plaintexts, so you can quickly find out what password a user had just from the hash. 

A rainbow table trades time taken to crack a hash for hard disk space, but they do take time to create.

Here's a quick example so you can try and understand what they're like.

|Hash |	Password|
|-- | -- |
|02c75fb22c75b23dc963c7eb91a062cc |	zxcvbnm|
|b0baee9d279d34fa1dfd71aadb908c3f |	11111|
|c44a471bd78cc6c2fea32b9fe028d30a |	asdfghjkl|
|d0199f51d2728db6011945145a1b607a |	basketball|
|dcddb75469b4b4875094e14561e573d8 |	000000|
|e10adc3949ba59abbe56e057f20f883e |	123456|
|e19d5cd5af0378da05f63f891c7467af |	abcd1234|
|e99a18c428cb38d5f260853678922e03 |	abc123|
|fcea920f7412b5da7be0cf42b8c93759 |	1234567|

Websites like `Crackstation` internally use HUGE rainbow tables to provide fast password cracking for hashes without salts. 

Doing a lookup in a sorted list of hashes is really quite fast, much much faster than trying to crack the hash.

## Protecting against rainbow tables

To protect against rainbow tables, we add a `salt` to the passwords. 

The salt is randomly generated and stored in the database, unique to each user. 

In theory, you could use the same salt for all users but that means that duplicate passwords would still have the same hash, and a rainbow table could still be created specific passwords with that salt.

The salt is added to either the `start or the end` of the password before it’s hashed, and this means that every user will have a different password hash even if they have the `same` password. 

Hash functions like `bcrypt` and `sha512crypt` handle this automatically. 

Salts `don’t need` to be kept private.

