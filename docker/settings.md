## 1. How to change docker root directory  

Find the docker.service file.  
```
systemctl status docker
```
Add the `--data-root` option to the end of `ExecStart`.  
```
ExecStart=/usr/bin/dockerd -H fd:// --containerd=/run/containerd containerd.sock --data-root=/your/docker/new/root/path
```
Restart docker  
```
systemctl daemon-reload
systemctl restart docker
```

## 2. How to grant docker permission to your account.  
```
// Changes the primary group for a user.
usermod -g [groupid] [userid]
// Add a supplementary groups.
usermod -Ga [groupid] [userid]
```
