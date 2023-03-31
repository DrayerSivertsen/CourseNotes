# Linux Permissions

## How to change ownership
Change owner
```
sudo chown -R drayer lab6
```

Change group
```
sudo chgrp -R drayer lab6
```

## How to change permissions
Directories
```
chmod 755 $(find directory/* -type d)
```

Files
```
chmod 644 $(find directory/* -type f)
```