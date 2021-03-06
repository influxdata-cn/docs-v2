---
title: Monitor HAProxy
description: >
  Use the [HAProxy for InfluxDB v2 template](https://github.com/influxdata/community-templates/tree/master/haproxy) to monitor your HAProxy instance.
menu:
  v2_0:
    parent: Monitor networks
    name: HAproxy
weight: 201
---

Use the [HAProxy for InfluxDB v2 template](https://github.com/influxdata/community-templates/tree/master/haproxy) to monitor your HAProxy instances. First, [apply the template](#apply-the-template), and then [view incoming data](#view-incoming-data).
This template uses the [HAProxy input plugin](/v2.0/reference/telegraf-plugins/#haproxy) to collect metrics stored in an HAProxy instance and display these metrics in a dashboard.

The HAProxy for InfluxDB v2 template includes the following:

- one [dashboard](/v2.0/reference/glossary/#dashboard): **HAProxy**
- one [bucket](/v2.0/reference/glossary/#bucket): `haproxy`
- label: `haproxy`
- one [Telegraf configuration](/v2.0/write-data/no-code/use-telegraf/auto-config/view-telegraf-config/): HAProxy input plugin, InfluxDB v2 output plugin
- one variable: `bucket`

## Apply the template

1. Use the [`influx` CLI](/v2.0/reference/cli/influx/) to run the following command:

    ```sh
    influx apply -f https://raw.githubusercontent.com/influxdata/community-templates/master/haproxy/haproxy.yml
    ```
    For more information, see [influx apply](/v2.0/reference/cli/influx/apply/).

    > **Note:** Ensure your `influx` CLI is configured with your account credentials and that configuration is active. For more information, see [influx config](https://v2.docs.influxdata.com/v2.0/reference/cli/influx/config/).

2. [Install Telegraf](/telegraf/latest/introduction/installation/) on a server with network access to both the HAProxy instances and [InfluxDB v2 API](/v2.0/reference/api/).
3. In your [Telegraf configuration file (`telegraf.conf`)](/v2.0/write-data/no-code/use-telegraf/auto-config/view-telegraf-config/), do the following:
    - Set the following environment variables:
      - INFLUX_TOKEN: Token must have permissions to read Telegraf configurations and write data to the `haproxy` bucket. See how to [view tokens](/v2.0/security/tokens/view-tokens/).
      - INFLUX_ORG: Name of your organization. See how to [view your organization](/v2.0/organizations/view-orgs/).
      - INFLUX_HOST: Your InfluxDB host URL, for example, localhost, a remote instance, or InfluxDB Cloud.

4. [Start Telegraf](/v2.0/write-data/no-code/use-telegraf/auto-config/#start-telegraf).

## View incoming data

1. In the InfluxDB user interface (UI), select **Boards** (**Dashboards**).

    {{< nav-icon "dashboards" >}}
2. Open the **HAProxy** dashboard to start monitoring.
