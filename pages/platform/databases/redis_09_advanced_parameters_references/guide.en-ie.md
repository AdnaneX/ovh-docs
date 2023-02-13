---
title: Redis - Advanced parameters references
slug: redis/advanced-parameters-references
excerpt:
section: Redis - Guides
order: 080
updated: 2023-02-06
---

<style>
table thead {
  display: none;
}
table tr {
  display: block;
  margin-bottom: 40px;
}
table tr:nth-child(2n) {
  background:none !important;
}
table tr:last-child {
  margin-bottom: 0;
}
table td {
  border-bottom:none !important;
  box-shadow:inset 13ch 0 0 rgb(241, 241, 241),inset calc(13ch + 1px) 0 0 #59d2ef;
  display: block;
  min-height:46px;
  position: relative;
  padding-left:14ch !important;
}
table td:last-child {
  border-bottom:1px solid #59d2ef !important;
}
table td:before {
  color: #000;
  font-weight: 600 !important;
  left: 0;
  padding: 0 1ch;
  position: absolute;
}
table td:nth-child(1):before {
  content:'Parameter';
}
table td:nth-child(2):before {
  content:'Type';
}
table td:nth-child(3):before {
  content:'Minimum';
}
table td:nth-child(4):before {
  content:'Maximum';
}
table td:nth-child(5):before {
  content:'Values';
}
table td:nth-child(6):before {
  content:'Description';
}
</style>

**Last updated 6th February 2023**

## Objective

This guide lists all the supported advanced parameters that allow you to configure your Public Cloud Databases for Redis according to your use cases.

## Requirements

- A [Public Cloud project](https://www.ovhcloud.com/en-ie/public-cloud/) in your OVHcloud account   
- A database running on your OVHcloud Public Cloud Databases ([this guide](https://docs.ovh.com/ie/en/publiccloud/databases/getting-started/) can help you to meet this requirement)   
- Access to your [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.ie/&ovhSubsidiary=ie) or to the [OVHcloud API](https://api.ovh.com/console/)   


## Instructions

> [!warning]
>
> The management of advanced parameters is not supported via Terraform.
>

### Using the OVHcloud Control Panel

Please refer to this [guide](https://docs.ovh.com/ie/en/publiccloud/databases/advanced-configuration/#using-the-ovhcloud-control-panel) to find out how to change your advanced parameters from the OVHcloud Control Panel.

### Using API

Please refer to this [guide](https://docs.ovh.com/ie/en/publiccloud/databases/advanced-configuration/#using-api) to find out how to change your advanced parameters from the OVHcloud API.


### Advanced parameters for Redis

Below you can find a summary of every configuration option available for Redis service:

| Parameter | Value Type | Minimum | Maximum | Values | Description |
|:---|:---|:---|:---|:---|:---|
| `redis_acl_channels_default` | string | | | "allchannels", "resetchannels" | Determines default pub/sub channels' ACL for new users if ACL is not supplied. When this option is not defined, all_channels is assumed to keep backward compatibility. This option doesn't affect Redis configuration acl-pubsub-default. |
| `redis_io_threads` | long | 1 | 32 | | Redis IO thread count |
| `redis_lfu_decay_time` | long | 1 | 120 | | LFU maxmemory-policy counter decay time in minutes |
| `redis_lfu_log_factor` | long | 0 | 100 | | Counter logarithm factor for volatile-lfu and allkeys-lfu maxmemory-policies |
| `redis_notify_keyspace_events` | string | | | | Set notify-keyspace-events option |
| `redis_number_of_databases` | long | 1 | 128 | | Set number of redis databases. Changing this will cause a restart of redis service. |
| `redis_persistence` | string | | | "off", "rdb" | When persistence is 'rdb', Redis does RDB dumps each 10 minutes if any key is changed. Also RDB dumps are done according to backup schedule for backup purposes. When persistence is 'off', no RDB dumps and backups are done, so data can be lost at any moment if service is restarted for any reason, or if service is powered off. Also service can't be forked. |
| `redis_pubsub_client_output_buffer_limit` | long | 32 | 512 | | Set output buffer limit for pub / sub clients in MB. The value is the hard limit, the soft limit is 1/4 of the hard limit. When setting the limit, be mindful of the available memory in the selected service plan. |
| `redis_ssl` | boolean | | | | Require SSL to access Redis |
| `redis_timeout` | long | 0 | 31536000 | | Redis idle connection timeout in seconds |


## Go further

Visit our dedicated Discord channel: <https://discord.gg/ovhcloud>. Ask questions, provide feedback and interact directly with the team that builds our databases services.

Join our community of users on <https://community.ovh.com/en/>.
