# Password Cracking

We've mentioned `rainbow tables` as a method to crack hashes that don't have a `salt`, but what if there's a salt involved?

You can't `"decrypt"` password hashes. They're `not` encrypted. 

You have to crack the hashes by hashing a large number of different inputs (often `rockyou`, these are the possible passwords), potentially adding the salt if there is one and comparing it to the target hash. 

Once it matches, you know what the password was. 

Tools like Hashcat and `John the Ripper` are normally used for this.

## Why Crack on GPUs?

Graphics cards have thousands of cores. 

Although they can’t do the same sort of work that a CPU can, they are very good at some of the maths involved in hash functions. 

This means you can use a graphics card to crack most hash types much more quickly. 

Some hashing algorithms, notably `bcrypt`, are designed so that hashing on a GPU is about the same speed as hashing on a CPU which helps them resist cracking.

## Cracking on VMs?

It’s worth mentioning that virtual machines normally don’t have access to the host's graphics card(s) (You can set this up, but it’s a lot of work). 

If you want to run `hashcat`, it’s best to run it on your `host` (Windows builds are available on the website, run it from `powershell`). 

You can get `Hashcat` working with `OpenCL` in a `VM`, but the speeds will likely be much worse than cracking on your host. 

`John the ripper` uses CPU by default and as such, works in a VM out of the box although you may get better speeds running it on the `host OS` as it will have more threads and no overhead from running in a VM.

*`NEVER (I repeat, NEVER!) use --force for hashcat.`* 

It can lead to false positives (wrong passwords being given to you) and false negatives (skips over the correct hash).

**`UPDATE:`** As of `Kali 2020.2`, hashcat `6.0` will run on the CPU without `--force`. 

I still recommend cracking on your host OS if you have a GPU, as it will be much much faster.





