---
title: Implementing NAT for port redirections
slug: nsx-t-configure-nat-redirection
excerpt: How to Configure NAT to Create Port Redirection
section: NSX-T
order: 07
---

**Last updated 13th February 2023**

> [!warning]
> Guides for **NSX-T** in the VMware solution are not final, they will be modified when the BETA version is released and finalised when the final version is ready.
>


## Objectif

**Comment configurer le NAT pour créer une redirection de port avec NSX-T**

> [!warning]
> OVHcloud provides services for which you are responsible, with regard to their configuration and management. It is therefore your responsibility to ensure that they work properly.
>
> This guide is designed to assist you as much as possible with common tasks. However, we recommend contacting a [specialist provider](https://partner.ovhcloud.com/en-gb/) if you experience any difficulties or doubts when it comes to managing, using or setting up a service on a server.
>

## Requirements

- Being an administrative contact of your [Hosted Private Cloud infrastructure](https://www.ovhcloud.com/en-gb/enterprise/products/hosted-private-cloud/) to receive login credentials
- A user account with access to the [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.co.uk/&ovhSubsidiary=GB)
- Having **NSX-T** deployed with two segments configured in your NSX-T configuration, you can use this guide [Segment management in NSX-T](https://docs.ovh.com/gb/en/private-cloud/nsx-t-segment-management).

## Instructions

We will create a redirection rule from the public virtual IP address on port 2222 in TCP to a virtual machine on LINUX on port 22 in TCP. In our example, we will use fictitious IP addresses.

In the NSX-T interface, go to the `Networking`{.action} tab, select `NAT`{.action} in the **Network Services** section, select `ovh-T0-gw | Tier-0`{.action} to the right of **Gateway** and click `ADD NAT RULE`{.action}.

![01 Create DNAT rule 01](images/01-create-dnat-rules01.png){.thumbnail}

Choose this information :

* **Action** : Select `DNAT`{.action}.
* **Source IP** : Enter the IP address or range of addresses that can use this redirection.
* **Destination IP** : Public virtual IP address of NSX-T.
* **Destination PORT** : Listening port on public address like `2222`{.action}.
* **Translated IP** : IP address of the virtual machine being redirected to.

Then click on the `vertical suspension points`{.action} to the right of **Select Services**.

![01 Create DNAT rule 02](images/01-create-dnat-rules02.png){.thumbnail}

Type `SSH22`{.action} under the **Name** column and click `Set`{.action} under the **Service Entry** column.

![01 Create DNAT rule 03](images/01-create-dnat-rules03.png){.thumbnail}

Click `ADD SERVICE ENTRY`{.action}.

![01 Create DNAT rule 04](images/01-create-dnat-rules04.png){.thumbnail}

Fill in these values :

* **Name** : Type `SSH22`{.action}.
* **Service Type** : Take `TCP`{.action}.
* **Source Ports** : Write the number `22`{.action}.

Then click `APPLY`{.action}.

![01 Create DNAT rule 05](images/01-create-dnat-rules05.png){.thumbnail}

Click `SAVE`{.action}.

![01 Create DNAT rule 06](images/01-create-dnat-rules06.png){.thumbnail}

Click `SAVE`{.action} to confirm the creation of the redirection rule.

![01 Create DNAT rule 07](images/01-create-dnat-rules07.png){.thumbnail}

The rule is created and active.

![01 Create DNAT rule 08](images/01-create-dnat-rules08.png){.thumbnail}

## Go further <a name="gofurther"></a>

[Getting started with NSX-T](https://docs.ovh.com/gb/en/private-cloud/nsx-t-first-steps/)

[Segment management](https://docs.ovh.com/gb/en/nsx-t-segment-management/)

[VMware NAT documentation in NSX-T](https://docs.vmware.com/en/VMware-NSX-T-Data-Center/3.2/administration/GUID-A52E1A6F-F27D-41D9-9493-E3A75EC35481.html)

Join our community of users on <https://community.ovh.com/en/>.

