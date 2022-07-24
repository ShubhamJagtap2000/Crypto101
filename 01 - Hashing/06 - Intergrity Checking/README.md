# Hashing for Integrity Checking

## Integrity Checking

Hashing can be used to `check that files haven't been changed`. 

If you put the same data in, you always get the same data out. 

If even a single bit changes, the hash will change a lot. 

This means you can use it to check that files haven't been modified or to make sure that they have downloaded correctly. 

You can also use hashing to `find duplicate files`, if two pictures have the same hash then they are the same picture.

## HMACs

HMAC is a method of using a cryptographic hashing function to verify the `authenticity` and `integrity` of data. 

The `TryHackMe VPN` uses `HMAC-SHA512` for message authentication, which you can see in the terminal output. 

A `HMAC` can be used to ensure that the person who created the HMAC is who they say they are (authenticity), and that the message hasn’t been modified or corrupted (integrity). 

They use a secret key, and a hashing algorithm in order to produce a hash.
