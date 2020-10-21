# ss_tcp_queue
Custom Datadog agent check for collecting TCP queue metrics using "ss" command

![Dashboard](https://github.com/adulmovits/ss_tcp_queue/blob/main/Screen%20Shot%202020-10-20%20at%208.47.18%20PM.png)

## Description

This check runs the command `ss --numeric --listening --tcp` every 1 second on the host and parses the output to collect Send-Q and Recv-Q bytes broken down by port.

## Metrics Collected

ss.listening.sendq

ss.listening.recvq


## Enabling the Check

To enable this check follow the same steps as a custom agent check: https://docs.datadoghq.com/developers/metrics/agent_metrics_submission/?tab=count#tutorial


1. Install the Datadog agent: https://app.datadoghq.com/account/settings#agent

2. Create the directory `ss_tcp_queue.d/` in `/etc/datadog-agent/conf.d/`

3. Within `/etc/datadog-agent/conf.d/ss_tcp_queue.d` add the file [ss_tcp_queue.yaml](https://github.com/adulmovits/ss_tcp_queue/blob/main/ss_tcp_queue.yaml)

4. Go to `/etc/datadog-agent/checks.d/` and add the file [ss_tcp_queue.py](https://github.com/adulmovits/ss_tcp_queue/blob/main/ss_tcp_queue.py)

5. [Restart the agent](https://docs.datadoghq.com/agent/guide/agent-commands/?tab=agentv6v7#restart-the-agent)

6. Validate the custom check is running correctly with the Agent’s status subcommand. Look for ss_tcp_queue under the Checks section:

```
=========
Collector
=========

  Running Checks
  ==============

    (...)

    ss_tcp_queue (1.0.0)
    -----------------------
      Instance ID: metrics_example:d884b5186b651429 [OK]
      Total Runs: 2
      Metric Samples: Last Run: 8, Total: 16
      Events: Last Run: 0, Total: 0
      Service Checks: Last Run: 0, Total: 0
      Average Execution Time : 2ms

    (...)
    ```
