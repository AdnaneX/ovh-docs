---
title: Add a new Tier-1 Gateway
slug: nsx-t-add-new-tier1-gateway
excerpt: How to add a Tier-1 Gateway
section: NSX-T
order: 10
---

**Last updated 23th February 2023**

> [!warning]
> Guides for **NSX-T** in the VMware solution are not final, they will be modified when the BETA version is released and finalised when the final version is ready.
>

## Objective

**How to add an East-West (Tier-1 Gateway) gateway to your NSX-T configuration**

> [!warning]
> OVHcloud provides services for which you are responsible, with regard to their configuration and management. It is therefore your responsibility to ensure that they work properly.
>
> This guide is designed to assist you as much as possible with common tasks. However, we recommend contacting a [specialist provider](https://partner.ovhcloud.com/en-gb/) if you experience any difficulties or doubts when it comes to managing, using or setting up a service on a server.
>

## Requirements

- Being an administrative contact of your [Hosted Private Cloud infrastructure](https://www.ovhcloud.com/en-gb/enterprise/products/hosted-private-cloud/) to receive login credentials
- A user account with access to the [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.co.uk/&ovhSubsidiary=GB)
- Having **NSX-T** deployed.

## Overview

OVHcloud provides you with NSX-T with two gateways, a north-south gateway (ovh-T0-gw) and an east-west gateway (ovh-T1-gw). You can create additional East-West gateways.

> [!warning]
> Through your NSX-T interface, you can create North-South gateways. Do not do this because some options are not available and you will not be able to make it work correctly.

For more information on NSX-T at OVHcloud, please refer to this guide [Getting started with NSX-T](https://docs.ovh.com/fr/private-cloud/nsx-t-first-steps/).

## Instructions

We will add a new East-West gateway (Tier-1-Gateways) and link it to the North-South gateway provided by OVHcloud (ovh-T0-gw).

Next, we will create a segment and attach a virtual machine to it.

### Creation of the new east-west gateway

In the NSX-T interface, go to the `Networking`{.action} tab and click on `Tier-1 Gateway`{.action} on the left.

Then click on `ADD TIER-1 GATEWAY`{.action}.

![Add tier1-gw 01](images/01-add-tier1-gw01.png){.thumbnail}

Type the name of your new gateway as `new-T1-gw`{.action} below **Name** and choose these parameters:

* **Linked Tier-0-Gateway** : Your north-south gateway `ovh-T0-gw`{.action}.
* **Edge Cluster** : Your `edgeXXX-X`{.action}.
* **Fail Over** : `Non Preemptive`{.action}.
* **Edge Pool Allocation Size** : `Routing`{.action}.

Then click the `Down Arrow`{.action} to the left of **Route Advertisement**.

![Add tier1-gw 02](images/01-add-tier1-gw02.png){.thumbnail}

Select the `{.action} button to the right of **All Connected Segment & Service Ports** if you want to connect outside this gateway and click `SAVE`{.action}.

![Add tier1-gw 03](images/01-add-tier1-gw03.png){.thumbnail}

Click `NO`{.action}.

![Add tier1-gw 04](images/01-add-tier1-gw04.png){.thumbnail}

Your new gateway is displayed and we can see it connected to your north-south gateway (ovh-T0-gw).

![Add tier1-gw 05](images/01-add-tier1-gw05.png){.thumbnail}

Click `Network Topology`{.action} in the vertical menu bar on the left to view your network topology to bring up your new gateway **new-T1-gw** connected to **ovh-T0-gw**.

![Add tier1-gw 06](images/01-add-tier1-gw06.png){.thumbnail}

### Adding a segment on your new gateway

Go to `Segments`{.action} on the left and click `ADD SEGMENT`{.action}.

![02 Add Segment on new gateway 01](images/02-add-segment-on-new-gw01.png){.thumbnail}

Choose this information : 

* **Name** : Name of your segment `ov3-segment`{.action}.
* **Connected Gateway** : Your new gateway `new-T1-gw`{.action}.
* **Transport Zone** : Your subnet `192.168.120.254/24`{.action}.

And click on `SAVE`{.action}.

![02 Add Segment on new gateway 02](images/02-add-segment-on-new-gw02.png){.thumbnail}

Click `NO`{.action}.

![02 Add Segment on new gateway 03](images/02-add-segment-on-new-gw03.png){.thumbnail}

Your new segment is created and connected to your new gateway **new-T1-gw**. 

![02 Add Segment on new gateway 03](images/02-add-segment-on-new-gw03.png){.thumbnail}

### Display a complete configuration with a virtual machine on your segment.

The segment created is of type Overlay but it is possible to add a segment of type VLAN and connect it to your new gateway.

Use this guide [Segment management in NSX-T](https://docs.ovh.com/fr/nsx-t-segment-management/) to add a new virtual machine to your new segment.

Then click `Network Topology`{.action}.

![03 Display VM on segment in new gw 03](images/03-display-vm-on-segment-in-new-gw01.png){.thumbnail}

## Go further <a name="gofurther"></a>

[Getting started with NSX-T](https://docs.ovh.com/gb/en/private-cloud/nsx-t-first-steps/)

[Segment management](https://docs.ovh.com/gb/en/nsx-t-segment-management/)

[VMware documentation for adding a Tier-1 Gateway](https://docs.vmware.com/en/VMware-NSX-T-Data-Center/3.2/administration/GUID-EEBA627A-0860-477A-95A7-7645BA562D62.html)

Join our community of users on <https://community.ovh.com/en/>.

