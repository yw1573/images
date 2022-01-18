---
typora-copy-images-to: ./
---

### tunnel collision

My topology is as follows：

![1](1.png)

#### 10.0.13.35

The configuration file on 10.0.13.35 is as follows

![2](2.png)

![3](3.png)

![4](4.png)

I did ipsec restart and ipsec statusall

![5](5.png)

You can see that the leftid and rightid in the two tunnel configuration files are the same

#### 10.0.13.9:

Next I'll be working on linking on 10.0.13.9

![6](6.png)



![7](7.png)

Yes, the link is successful

#### 10.0.13.35:

![8](8.png)

It can also be seen on 10.0.13.35, the tunnel is established successfully

#### 10.0.13.10:

Then I want to start the tunnel on 10.0.13.10 also to link with 10.0.13.35

![9](9.png)

![10](10.png)

As you can see, the link is successful

But the tunnel with 10.0.13.9 is gone and terminated

#### 10.0.13.35:

![11](11.png)

I did a packet grab on 10.0.13.9

![12](12.png)

and I scraped the logs on 10.0.13.9

![13](13.png)

I don't know much about the underlying problem, I want to know how this is caused and how should I deal with it

This situation occurs mainly because the config setup option is not set

 Use different identities or disable `uniqueids` (see [ConfigSetupSection](https://wiki.strongswan.org/projects/strongswan/wiki/ConfigSetupSection)). 

