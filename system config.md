
### Set the environmental variable LD_LIBRARY_PATH in Linux
Keep the previous path, don't overwrite it:
```bash
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/your/custom/path/
```
You can add it to your ~/.bashrc:
```bash
echo 'export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/your/custom/path/' >> ~/.bashrc
```
```ldconfig``` - configure dynamic linker run-time bindings


### crates.io 镜像

~/.cargo/config:
 ```config
[source.crates-io]
# To use sparse index, change 'rsproxy' to 'rsproxy-sparse'
replace-with = 'rsproxy'

[source.rsproxy]
registry = "https://rsproxy.cn/crates.io-index"
[source.rsproxy-sparse]
registry = "sparse+https://rsproxy.cn/index/"

[registries.rsproxy]
index = "https://rsproxy.cn/crates.io-index"

[net]
git-fetch-with-cli = true
```


### Rustup 镜像

~/.zshrc or ~/.bashrc:
```bash
export RUSTUP_DIST_SERVER="https://rsproxy.cn"
export RUSTUP_UPDATE_ROOT="https://rsproxy.cn/rustup"
```
                        
### 安装 Rust

```bash
# export the env above first
curl --proto '=https' --tlsv1.2 -sSf https://rsproxy.cn/rustup-init.sh | sh
```
