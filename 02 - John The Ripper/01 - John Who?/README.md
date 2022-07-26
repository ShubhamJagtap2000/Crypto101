# John Who?

## What Are Hashes?

- A hash is a way of taking a piece of data of any length and representing it in another form that is a fixed length. This masks the original value of the data. This is done by running the original data through a hashing algorithm. 
- There are many popular hashing algorithms, such as MD4,MD5, SHA1 and NTLM. Lets try and show this with an example:

- If we take `polo`, a string of `4` characters- and run it through an `MD5` hashing algorithm, we end up with an output of: `b53759f3ce692de7aff1b5779d3964da` a standard `32` character `MD5` hash.

- Likewise, if we take `polomints`, a string of `9` characters- and run it through the same `MD5` hashing algorithm, we end up with an output of: `584b6e4f4586e136bc280f27f9c64f3b` another standard `32` character MD5 hash

## What makes Hashes secure?

- Hashing algorithms are designed so that they only operate one way. This means that a calculated hash cannot be reversed using just the output given. This ties back to a fundamental mathematical problem known as the [P vs NP relationship](https://en.wikipedia.org/wiki/P_versus_NP_problem) .

- While this is an extremely interesting mathematical concept that proves fundamental to computing and cryptography I am in no way qualified to try and explain it in detail here; but abstractly it means that the algorithm to hash the value will be `NP` and can therefore be calculated reasonably. 
- However an un-hashing algorithm would be `P` and intractable to solve- meaning that it cannot be computed in a reasonable time using standard computers. 

## Where John Comes in...

- Even though the algorithm itself is not feasibly reversible. That doesn't mean that cracking the hashes is impossible. If you have the hashed version of a password, for example- and you know the hashing algorithm- you can use that hashing algorithm to hash a large number of words, called a `dictionary`. 

- You can then compare these hashes to the one you're trying to crack, to see if any of them match. If they do, you now know what word corresponds to that hash- you've cracked it!

- This process is called a `dictionary attack` and `John the Ripper`, or John as it's commonly shortened to, is a tool to allow you to conduct fast brute force attacks on a large array of different hash types.



