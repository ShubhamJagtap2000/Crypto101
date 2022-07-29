# Practical 

## 1. John Basic Syntax

- The basic syntax of John the Ripper commands is as follows. We will cover the specific options and modifiers used as we use them.

- **Syntax**

```
john [options] [path to file]
```

- `john` -  Invokes the John the Ripper program 
- `path to file` - The file containing the hash you're trying to crack, if it's in the same directory you won't need to name a path, just the file

- **Example Usage:**

```
john --wordlist=/usr/share/wordlists/rockyou.txt hash_to_crack.txt
```
