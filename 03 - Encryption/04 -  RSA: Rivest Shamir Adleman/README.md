# RSA 

## Maths

- `RSA` is based on the mathematically difficult problem of working out the factors of a large number. 

- It’s very quick to multiply two prime numbers together, say 17*23 = 391, but it’s quite difficult to work out what two prime numbers multiply together to make 14351 (113x127 for reference).

## The Attacking Side

- There are some excellent tools for defeating RSA challenges in CTFs, and my personal favorite is [RsaCtfTool](https://github.com/Ganapati/RsaCtfTool) which has worked very well for me. I’ve also had some success with [rsatool](https://github.com/ius/rsatool).

- The key variables that you need to know about for RSA in CTFs are `p, q, m, n, e, d, and c`.

- `p` and `q` are large `prime numbers`, `n` is the `product` of p and q.

- The `public key` is `n` and `e`, the `private key` is `n` and `d`.

- `m` is used to represent the `message` (in plaintext) and `c` represents the `ciphertext` (encrypted text).

## CTFs involving RSA

- Crypto CTF challenges often present you with a set of these values, and you need to break the encryption and decrypt a message to retrieve the flag.

- There’s a lot more maths to `RSA`, and it gets quite complicated fairly quickly. 
- If you want to learn the maths behind it, I recommend reading MuirlandOracle’s blog post here: https://muirlandoracle.co.uk/2020/01/29/rsa-encryption/.
