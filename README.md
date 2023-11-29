# remote-docker-setup

How to get basicauth keygeneration:

in the access console (or using ssh connection) you just gotta install apache2-utils to be able to hash a username and password using apache (MD5)

to get this util and be able to hash your own, do these steps:

#Steps

## step 1. install apache2-utils

```bash
 apt install apache2-utils
```
follow the prompts (it'll ask Y/N and which package, just say yes and choose the upper option.)

## step 2. generate a hash

```bash
htpasswd -nbm <username> <password>
```

# OBS: username and password is replaced with whatever username and password you would like to hash into a "key"

## step 3. copy the hash into your compose file like so

### Take this last string (including admin and the period at the end)
![img.png](img.png)

and put it into your compose file like so:

![img_1.png](img_1.png)
