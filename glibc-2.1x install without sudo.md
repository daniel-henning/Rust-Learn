
### 查看现有版本和动态库依赖
查看glibc版本
```bash
strings /lib64/libc.so.6 | grep GLIBC
```

### 查看动态库的依赖
主要使用ldd命令。 在linux中， ldd是list, dynamic, dependencies的缩写， 意思是， 列出动态库依赖关系。

使用示例：
```bash
ldd myapp
```

### 常规安装过程
#### 下载&解压
```bash
wget https://ftp.gnu.org/gnu/libc/glibc-2.27.tar.gz  #我这里选择下载的是2.27版本
tar -xzf glibc-2.27.tar.gz

cd  glibc-2.27/  #移动到glibc安装包文件夹里面
mkdir build      #创建一个build文件夹
cd build
```
接下来进行编译和安装
```bash
../configure --prefix=/your/target/path/

make -j4 & make install
```

最后将 LD_LIBRARY_PATH 添加到配置文件
```bash
export LD_LIBRARY_PATH=/your/path/lib:$LD_LIBRARY_PATH
```

非root用户添加LD_LIBRARY_PATH之后会出现系统崩溃，一个有用的解决方案是使用```patchelf```在代码编译后直接修改elf格式的可执行文件，通过设置```-set-rpath```修改library搜索路径，使用```–set-interpreter```修改```dynamic linker```。
首先需要下载```patchelf```，然后使用示例如下（myapp是我的二进制可执行文件）：
```bash
patchelf  --set-rpath /glibc/path/lib --set-interpreter /glibc/path/lib/ld-2.27.so myapp
```
使用示例：
```bash

patchelf  --set-rpath ~/usr/local/glibc-2.17/lib --set-interpreter ~/usr/local/glibc-2.17/lib/libc-2.17.so /amoydx/USER/hening/bio-soft/centos/usr/local/bin/cargo

patchelf  --set-rpath ~/usr/local/glibc-2.17/lib --set-interpreter ~/usr/local/glibc-2.17/lib/libc-2.17.so /amoydx/USER/hening/bio-soft/centos/usr/local/bin/rustc

patchelf  --set-rpath ~/usr/local/glibc-2.17/lib --set-interpreter ~/usr/local/glibc-2.17/lib/libc-2.17.so /amoydx/USER/hening/bio-soft/centos/usr/local/bin/cargo

### rust-analyzer,rustc,rust-demangler,rustdoc,rustfmt,rust-gdb,rust-gdbgui,rust-lldb
```
