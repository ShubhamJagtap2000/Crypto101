# SSH Authentication

## Encryption and SSH authentication

- By default, SSH is authenticated using usernames and passwords in the same way that you would log in to the physical machine.

- At some point, you’re almost certain to hit a machine that has `SSH` configured with key authentication instead. This uses public and private keys to prove that the client is a valid and authorised user on the server. 
- By default, `SSH keys are RSA keys`. You can choose which algorithm to generate, and/or add a passphrase to encrypt the SSH key. `ssh-keygen` is the program used to generate pairs of keys most of the time.

## SSH Private Keys

- You should treat your private `SSH keys` like passwords. Don’t share them, they’re called private keys for a reason. If someone has your private key, they can use it to log in to servers that will accept it unless the key is encrypted.

- It’s very important to mention that the `passphrase` to decrypt the key isn’t used to identify you to the server at all, all it does is decrypt the SSH key. The passphrase is never transmitted, and never leaves your system.

- Using tools like `John the Ripper`, you can attack an encrypted SSH key to attempt to find the passphrase, which highlights the importance of using a secure passphrase and keeping your private key private.

- When generating an `SSH key` to log in to a remote machine, you should generate the keys on your machine and then copy the public key over as this means the private key never exists on the target machine. For temporary keys generated for access to CTF boxes, this doesn't matter as much.

## How do I use these keys?

- The `~/.ssh` folder is the default place to store these keys for `OpenSSH`. The `authorized_keys` (note the US English spelling) file in this directory holds public keys that are allowed to access the server if key authentication is enabled. 
- By default on many distros, key authentication is enabled as it is more secure than using a password to authenticate. Normally for the root user, only key authentication is enabled.

In order to use a private SSH key, the permissions must be set up correctly otherwise your SSH client will ignore the file with a warning. Only the owner should be able to read or write to the `private key (600 or stricter)`. 
- `ssh -i keyNameGoesHere user@host` is how you specify a key for the standard Linux `OpenSSH client`.

## Using SSH keys to get a better shell

- `SSH` keys are an excellent way to `upgrade` a reverse shell, assuming the user has login enabled (www-data normally does not, but regular users and root will). Leaving an SSH key in `authorized_keys` on a box can be a useful backdoor, and you don't need to deal with any of the issues of unstabilised reverse shells like `Control-C` or lack of tab completion.

# Answer the following questions

Crack the password with John The Ripper and rockyou, what's the passphrase for the key?
```
delicious
```
