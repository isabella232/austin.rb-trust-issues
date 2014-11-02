# Trust Issues in Networking

## A Presentation to Austin.RB by @Rapid7 folks

### presenters
* [Tod Beardsley](https://twitter.com/todb)
* [Trevor Rosen](https://twitter.com/trevrosen)

### What do we trust on the Internet?
All of our interactions online are predicated on some form of trust -
from joining a router to loading a website or getting email, we
are making all kinds of trust decisions, some consciously and most
unconsciously.

Where are those decisions? How can we mitigate them? How is the Internet
like Meatspace human societies? How is it different? What rules govern
Meatspace behavior and behavior on the Internet?

At the protocol level what is happening when I make network connections?
How am I trusting each of the diffferent links in the chain from
connecting to wifi to loading a web page over SSL?

This presentation will seek to answer these questions, putting our trust
environment online into a technical and philisophical context that can
be used to empower developers to create solid products without falling
into paranoia.


### Tricks/Tips

#### Find out what version of SSL something has support for

github supports TLSv1:

```
openssl s_client -connect github.com:443 -tls1
```


but not SSLv3:

```
openssl s_client -connect github.com:443 -ssl3
```

#### Run all traffic through an SSH session

Don't have VPN set up yet but DO have ssh access to a remote host? You
can tell your computer to do all its networking business through that
connection.

1. Initiate a SOCKS proxy over SSH: ``` ssh user@host.com -D 127.0.0.1:8888 ```
2. Go into your network settings and use the proxy. In OSX this is in
   Network Preferences --> Advanced --> Proxies. Choose SOCKS and fill
   in the host loopback address and proper port as used above. Then hit
   Apply.
3. All network traffic on your computer will now use that encrypted pipe
   through the remote machine. Keep any relevant bandwidth agreements in
   mind

#### Learn you some nmap and ncat/socat

nmap and its cousin ncat (netcat) can do all kinds of things. nmap is
used to enumerate hosts and their services. ncat (netcat) and its more
powerful cousin socat, are used to make arbitrary network connections or
more generically, to move data around on different kinds of named pipes.

**Installing (nmap comes with ncat)**

* OSX: ```brew install nmap socat```
* Ubuntu: ```sudo apt-get install nmap socat```


* [ncat tricks](http://nmap.org/ncat/guide/ncat-tricks.html) - pipe data
  around, make ad-hoc servers, listen to traffic on hosts, etc
* [practical nmap usage](http://www.tecmint.com/nmap-command-examples/)
  - scan one or more hosts, use varying levels of probe, etc


### Credits
* ["Liars and Outliers: Enabling the Trust that Society Needs to Thrive"](http://www.amazon.com/Liars-Outliers-Enabling-Society-Thrive-ebook/dp/B006ORT3KG/]) this talk owes a good deal to some insights from Bruce Schneier in his most recent layman-oriented security book. This book does a great job of placing the trust notion into the broader context of government and commerce, and talking about the ways that technology is altering the trust framework.




