
### CentOS /usr/local/lib system wide $LD_LIBRARY_PATH?

You can add it in /etc/bashrc, say, at the end.
```bash
export PATH=$PATH:/usr/local/lib
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/lib
```

```ldconfig``` - configure dynamic linker run-time bindings
