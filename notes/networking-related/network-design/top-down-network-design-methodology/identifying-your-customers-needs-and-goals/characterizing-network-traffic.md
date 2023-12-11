# Characterizing Network Traffic

## Step 1.

**Identify major traffic sources and stores**

* Identify [user communities](#user-content-fn-1)[^1] and [data stores](#user-content-fn-2)[^2] for existing and new applications
* User community is a set of workers who use a particular application or set of applications

## Step 2.

**Document traffic flow on the existing network**

* Identify and characterize individual [traffic flows](#user-content-fn-3)[^3] between sources and stores
* Help network designers to do the following:
  * Characterize the behavior of existing networks
  * Plan for network development and expansion
  * Quantify network performance
  * verify the quality of network service
  * ascribe network usage to users and applications

## Step 3.

**Characterize types of traffic flow for new network applications**

Flow types:

* terminal/host
* client/server
* peer-to-peer
* server/server
* distributed computing

## Step 4.

**Document traffic flow for new and existing network applications**

Document the flow type for each application and list user communities and data stores that are associated with applications

<figure><img src="../../../../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

[^1]: * user community name
    * community size / number
    * location
    * application used

[^2]: * data stores (server etc.)
    * location
    * application
    * used by who

[^3]: * protocol used (eg. IP)
    * from a to b, how much Mb/sec
