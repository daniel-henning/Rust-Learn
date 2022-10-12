# Rust installation
```bash
curl https://sh.rustup.rs -sSf | sh

# Installation configuration for root user 

vim ~/.bashrc

export PATH=$PATH:/root/.cargo/bin`

# Installation configuration for non-root user 

export PATH=~/.cargo/bin:$PATH

# Check the installation
rustc --version
#rustc 1.31.1 (b6c32da9b 2018-12-18)


# Verfication
mkdir ~/projects
cd ~/projects
mkdir hello_world
cd hello_world 
cat main.rs    
#
#fn main() {
#    println!("Hello, world!");
#    }

rustc main.rs 
ls
#main  main.rs
./main 
#Hello, world!

```


## ERROR INFROAMTION
```
# ERROR INFO
rustup-init.sh: line 465:  6244 Illegal instruction     "$@"

```
