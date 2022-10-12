# Rust installation
```bash
curl https://sh.rustup.rs -sSf | sh

# Installation configuration for root user 

vim /etc/profile
export PATH=$PATH:/root/.cargo/bin`

# Installation configuration for non-root user 

export PATH=~/.cargo/bin:$PATH

# Check the installation
rustc --version
#rustc 1.31.1 (b6c32da9b 2018-12-18)

```
