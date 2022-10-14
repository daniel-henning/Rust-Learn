
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
