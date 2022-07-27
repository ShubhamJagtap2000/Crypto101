# Setting Up John The Ripper

## Parrot, Kali and AttackBox 

- Already installed, if not, use `sudo apt install john`

## Blackarch

- If you're using `Blackarch`, or the Blackarch repositories you may or may not have Jumbo John installed, to check if you do, use the command `pacman -Qe | grep "john"`

- You should be met with an output similar to `john 1.9.0.jumbo1-5` or similar with a different version number. If you do not have it installed, you can simply use `pacman -S john` to install it. 

## Building from Source for Linux

- If you wish to build the package from source to meet your system requirements, you can do this in five fairly straightforward steps. Further advice on the installation process and how to configure your build from source can be found [here](https://github.com/openwall/john/blob/bleeding-jumbo/doc/INSTALL).

     - Use `git clone https://github.com/openwall/john -b bleeding-jumbo john` to clone the jumbo john repository to your current working
     - Then `cd john/src/` to change your current directory to where the source code is. 
     - Once you're in this directory, use `./configure` to check the required dependencies and options that have been configured.
     - If you're happy with this output, and have installed any required dependencies that are needed, use `make -s clean && make -sj4` to build a binary of john. This binary will be in the above run directory, which you can change to with `cd ../run`
     - You can test this binary using `./john --test`

## Installing on Windows

- To install `Jumbo John the Ripper` on Windows, you just need to download and install the zipped binary for either `64` bit systems [here](https://www.openwall.com/john/k/john-1.9.0-jumbo-1-win64.zip) or for `32` bit systems [here](https://www.openwall.com/john/k/john-1.9.0-jumbo-1-win32.zip).

