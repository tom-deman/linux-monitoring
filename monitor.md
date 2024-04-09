# Linux Monitoring

<br>

## Main area of concern of monitoring:

__Resource Utilization:__ Monitoring CPU, memory, disk space, and network bandwidth usage.

__Performance Metrics:__ Tracking response times, throughput, and other performance indicators.

__Availability:__ Monitoring uptime and availability.

__Error and Log Analysis:__ Monitoring system logs and error messages.

__Security:__ Monitoring for suspicious activities, unauthorized access attempts, and potential security vulnerabilities.

__Capacity Planning:__ Analyzing historical usage data.

<br>
<br>

## Find most memory intense process

We can either use top or htop.
With Top just press

```bash
    top
```

You can then press SHIFT M to order by the most intense first.

<br>

For Htop it's also simple to launch:

```bash
    htop
```

<p style="">Then</p> you can press F6 and select with the arrows the desired filter by. (here will be %CPU or %MEM)

<br>
<br>

## Logs

To show log you can simply cat them or less or whatever you want. It could be useful to combine grep to find specific terms.

Here's a list of the most commons and important logs in Linux:

- __/var/log/syslog__ General overview of system activity. Including kernel messages, system startups, shutdowns, and hardware-related messages. (sometimes located at /var/log/messages)

- __/var/log/auth.log__ This log file contains authentication-related messages, including successful and failed login attempts, authentication failures, and user authentication events. (sometimes /var/log/secure)

- __/var/log/kern.log__ This log file contains kernel-related messages, including kernel errors, warnings, and other kernel events. It can provide insights into hardware issues and kernel-level problems.

- __/var/log/boot.log__ This log file contains messages generated during the system boot process. It can be useful for troubleshooting boot-related issues and understanding the sequence of events during system startup.

- __/var/log/cron__ This log file contains messages related to the cron scheduler, including scheduled task executions, cron job failures, and other cron-related events. On my Linux Mint I don't have this file so I used:
```bash
    grep CRON /var/log/syslog
```

<br>

```bash
    journalctl
```

can also be used to see logs.

<br>
<br>

## Last logged user

We have several commands to see informations about users:

```bash
    last
```

Display a list of the last logged in users with informations such as ip address and logging duration time.

<br>

```bash
    w
```

Simple way to log who is currently on the system and what they are doing.

<br>

```bash
    who / whoami
```

Whoami will simply give you who you actually are while who will additionally give you

<br>

```bash
lastlog
```

Can be useful too to log the users last logged sessions. Can be used with paramters to see specific user like: sudo lastlog -u 0

<br>
<br>

## Health metrics

There's a lot of differentz health metrics for a system.
The two main ones that comes in my mind are CPU and Memory but many mores exist so here's a list of some popular ones (for the packet not already installed you can type apt search 'keyword'):

- __CPU Usage__: This metric indicates the percentage of CPU resources being utilized. High CPU usage may indicate that the system is under heavy processing load, which could lead to performance degradation.

```bash
    htop F6 look for %CPU
```

<br>

- __Memory Usage__: Memory usage measures the amount of RAM being used by the system. High memory usage can lead to swapping to disk and reduced performance.

```bash
    htop F6 look for %MEM
```

<br>

- __Disk I/O__: Displays input/output statistics for disks, including metrics like read/write rates and average I/O wait times. (iostat command need to be installed first)

```bash
    iostat
```

<br>

- __Network Traffic__: Provides real-time monitoring of network traffic, showing incoming and outgoing data rates for network interfaces. We can use different tools like iftop, nload, nmap, ss, ...

```bash
    netstat (-i -r -tulp)
```

<br>

- __System load__: Shows system load averages over 1, 5, and 15-minute intervals, indicating the average number of processes waiting for CPU time.

```bash
    uptime
```

<br>

- __Process Activity__: Lists information about active processes, including process IDs, CPU and memory usage, and command names.

```bash
    ps aux
```

<br>

- __Response Time__: Measures network response times to remote hosts or traces the route taken by packets to a destination, providing insights into network latency.

```bash
    ping / traceroute / tracepath
```

<br>

- __Temperature and hardware__: Reports hardware sensor data, including temperatures, fan speeds, and voltage levels, providing insights into system health and potential hardware issues.

```bash
    sensors
```

<br>
<br>

## Additional notes

To see all the cron running and show the main cron file

```bash
    crontab -l
    cat /etc/crontab
```

List disk free space:

```bash
    df
```

<br>

There's a lot more tools listed on this website:

https://www.ubuntupit.com/best-linux-monitoring-tools-for-sysadmin/

Some that got my attention:

- linux Dash
- bandwidthd
- monitorix

Some I used:

- nmon
- bmon

See also:

https://www.linode.com/docs/guides/linux-system-monitoring-fundamentals/
