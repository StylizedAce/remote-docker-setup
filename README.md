# remote-docker-setup

## Important parts:

Line 29: provider is digitalocean  
Line 31: should be your own email, personal email is fine  
Line 32: I already set for you, leave that as is, but it loads your certificates    
Line 35: should be your DigitalOcean Auth token, which you can generate on digitalOcean website.   
 - digitalOcean > API > Generate Token > YES TO READ AND YES TO WRITE > GENERATE.)  

Line 53: should be an "endpoint of your choice, i chose Host('traefik.stylizedace.dk')
- write the same exact thing on line 58  

Line 69: will be basicauth  which will need a few extra steps, follow these below  

How to get basicauth keygeneration:

Inside a digitalOcean access console (or using ssh connection if you dont want to use the built in digital ocean console) you should install apache2-utils to be able to hash a username and password using apache (MD5)

![Image showing how to access a console inside the droplet, instead of using SSH](images/DigitalOceanAccessConsole.png)

to get this util and be able to hash your own, follow these steps:

## step 1. install apache2-utils by copying the following:

```bash
 apt install apache2-utils
```
follow the prompts (it will ask a Y/N question and which package, just say yes and choose the upper option.)

## step 2. generate a hash like so:

```bash
htpasswd -nbm <username> <password>
```

# OBS: username and password is replaced with whatever username and password you would like to hash into a "key" (and remove the "<>" after )

## step 3. copy the hash into your compose file like so:

### Take this last string (including admin and the period at the end)
![img.png](images/KeygeneratedAPACHE(MD5).png)

and put it into your compose file like so:

![img_1.png](images/ComposeAuthPlacement.png)

now you have a basicauth key that you can use to access your traefik dashboard. Let us move on to the last step

line 104: your restAPI endpoint, which should match the endpoint you wrote in line 53 and 58 but instead of 'traefik' like what i wrote, you write api.something"
example: Host('api.stylizedace.dk')
 - do the exact same for line 109.  

# Now you're done! C:

