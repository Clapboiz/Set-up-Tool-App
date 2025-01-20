if you have this bug `exec /tmp/entrypoint.sh: no such file or directory` when you run docker, please follow this step

```
dos2unix entrypoint.sh
chmod +x entrypoint.sh
```

The script file 'entrypoint.sh' cannot be executed because its line endings are in Windows format (CRLF). This causes the Linux-based Docker container to misinterpret the file, resulting in the error: 'no such file or directory'
