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




# Install RUST on centOS.6 without root user.

[https://pkgs.org/]
### update curl.
[https://centos.pkgs.org/7/centos-x86_64/curl-7.29.0-59.el7.x86_64.rpm.html]
[https://centos.pkgs.org/7/centos-x86_64/libcurl-7.29.0-59.el7.x86_64.rpm.html]

### RUST rpm
[rust-toolset-7](https://centos.pkgs.org/7/centos-sclo-rh-x86_64/rust-toolset-7-1.26.2-1.el7.x86_64.rpm.html)   

[rust-toolset-7-build](https://centos.pkgs.org/7/centos-sclo-rh-x86_64/rust-toolset-7-build-1.26.2-1.el7.x86_64.rpm.html)   

[rust-toolset-7-cargo](https://centos.pkgs.org/7/centos-sclo-rh-x86_64/rust-toolset-7-cargo-1.26.0-3.el7.x86_64.rpm.html)   

[rust-toolset-7-runtime](https://centos.pkgs.org/7/centos-sclo-rh-x86_64/rust-toolset-7-runtime-1.26.2-1.el7.x86_64.rpm.html)   

[rust-toolset-7-rust](https://centos.pkgs.org/7/centos-sclo-rh-x86_64/rust-toolset-7-rust-1.26.2-3.el7.x86_64.rpm.html)   

[rust-toolset-7-rust-std](https://centos.pkgs.org/7/centos-sclo-rh-x86_64/rust-toolset-7-rust-std-static-1.26.2-3.el7.x86_64.rpm.html)   

[rust-toolset-7-rust-doc](https://centos.pkgs.org/7/centos-sclo-rh-x86_64/rust-toolset-7-rust-doc-1.26.2-3.el7.x86_64.rpm.html)   


### shared library.so for RUST
[libffi.so.6](https://centos.pkgs.org/7/centos-x86_64/libffi-3.0.13-19.el7.x86_64.rpm.html)   

[libLLVM-7.so](http://mirror.centos.org/centos/7/sclo/x86_64/rh/Packages/l/llvm-toolset-7.0-llvm-libs-7.0.1-4.el7.x86_64.rpm)   


### ADD SHARE LIB TO ENVIRONMENT
```bash
sLIB='$HOME/centos/opt/rh'
L='/lib:/lib64:/usr/lib:/usr/lib64'

export LD_LIBRARY_PATH="$sLIB/rust-toolset-1.41/root/usr/lib:$sLIB/rust-toolset-1.41/root/usr/lib64:$sLIB//llvm-toolset-7.0/root/usr/lib64:$L"
```




# CentOS离线安装Rust

条件所限，无法在线连接外网，或是下载慢，容易中断时，可以采用。

一，下载离线安装包

https://forge.rust-lang.org/other-installation-methods.html#standalone

### 二，解压安装包
```tar zxvf rust-1.64.0-x86_64-unknown-linux-gnu.tar.gz```

### 三，运行```install.sh```脚本

### 四，验证
``` rustc --version ```
