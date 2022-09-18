# imon
Four different internet monitoring tools, all in a single, easy-to-use service.

## Overview

imon implements 4 independent network monitoring functions in a multi-threaded Python app.

* **Dynamic DNS (DDNS) Monitor** &mdash; Monitors your external IP address. If it changes changes, your action script is called to take whatever you'd like, such as update your ddns IP address.
* **Network Failover Monitor** &mdash; If your system has two connections to the internet, internet-monotor can provide a higher availability internet connection using a primary/secondary standby model.
* **Ping monitor** &mdash; Retrieve ping statistics resulting from pinging an IP address at regular intervals.
* **Up/down IP Address Monitor** &mdash; Monitors a specified IP address, and logs outages.

imon logs to the system log by default, and can call a script you provide for further event processing.

imon is python-based and is quite lightweight. (If anyone knows of a good Python library for doing `ip route` commands, please let me know.)

While imon has primarily been tested on RasPiOS, there are no RasPiOS dependencies, and should run on any contemporary Linux distro.

imon is easy to install/configure and runs as a systemd service. 

## Installation

imon can be installed using the installation script `install-imon`:

* `sudo curl -L https://raw.githubusercontent.com/gitbls/imon/main/imon-install | bash`

If you prefer to install imon manually, use these steps:

* `sudo curl https://raw.githubusercontent.com/gitbls/imon/main/imon -o /usr/local/bin/imon`
* `sudo curl https://raw.githubusercontent.com/gitbls/imon/main/imon-configure -o /usr/local/bin/imon-configure`
* `sudo curl https://raw.githubusercontent.com/gitbls/imon/main/imon-action.sample -o /usr/local/bin/imon-action.sample`
* `sudo curl https://raw.githubusercontent.com/gitbls/imon/main/imon@.service -o /etc/systemd/system/imon@.service`
* `sudo chmod 755 /usr/local/bin/{imon,imon-configure,imon-action}`
* `sudo pip3 install icmplib`

After the installation completes, run `sudo imon-configure` to create an instance configuration file. You can have as many instance configuration files as you want, each with a different settings configuration.

A configuration file is selected by using the `--instance` *instancename* switch when run from the command line, or by starting a new systemd service instance named imon@*instancename*.

## imon Capabilities

imon has four different monitoring capabilities. They can all be run in the same imon instance, or can be run in separate instances. If multiple monitors are active in the same instance, the log output identifies the monitor generating the log entry.

imon calls your action script for significant events. See below for details on the action script and further details on each of the monitors.

* **ddns** &mdash; Monitors the external IP address, and calls the action script if/when it changes. This is very useful if your ddns provider has a scripting interface for changing the IP address.
* **failover** &mdash; The failover monitor ensures that one of two WAN networks is always online. This is useful, for instance, if you have a faster, or otherwise more preferred primary connection, and a slower, or less preferred secondary connection.
* **ping** &mdash; Pings the monitored IP address and either logs the ping results or calls your provided action script with the ping results.
* **updown** &mdash; Monitors connectivity changes for a particular IP address. This is useful if you are having connectivity issues with your ISP, or to monitor a system on your LAN that is flapping.  It can also be run on that system that drops offline, and when an offline event happens, network remediation you've built into the action script will be performed.

## Configuration Overview

The imon configuration is kept in a JSON-formatted configuration file in /etc/default. imon is configured by instances. Each instance has its own configuration file in /etc/default. You can name the instance whatever you'd like (*myinstance*, for example). Invalid characters in the instance name are NOT currently checked.

Use the configuration tool `imon-configure` to create an instance configuration file. `imon-configure` prompts for all required inputs. imon-config does not prompt for configuration details for a monitor if you respond NO to *"Enable the 'xxx' monitor?"*, so your first go-around will proceed even faster.

**HINT:** Build a configuration with the updown monitor only, and test that, to get familiar with both imon-config and running imon.

**IMPORTANT!** At the current time, `imon-configure` does not check any of the network configuration (interface names, IP addresses, etc)

Here's a complete `imon-configure` session. An annotated configuration file is shown at the end of this document. The string in parentheses is the variable name for which you are being prompted. Be aware that some yes/no answers have No as the default (`[y/N]`), and some have Yes as the default (`[Y/n]`).

```
p83~$ sudo imon-configure

Build imon configuration file
See https://github.com/gitbls/imon for configuration details

Instance name [main]: demo
Note to add to config file: one line of info. Or not
Full path to action script (action): /usr/local/bin/imon-action
* Enable the 'ddns' monitor? [y/N]: y
Interval between checks (interval) [10]: 
Ping count (pingcount) [2]: 
Ping wait time (pingwait) [1]: 
* Enable the 'updown' monitor? [y/N]: y
Interval between checks (interval) [10]: 
Ping count (pingcount) [2]: 
Ping wait time (pingwait) [1]: 
Name/IP address to monitor (monitorip): 1.1.1.1
Additional IP addresses to ping (addping): 192.168.92.1,192.168.1.1
Name/IP address of DNS server (dnsserver): 8.8.8.8
DNS name to lookup (dnslookup): microsoft.com
* Enable the 'failover' monitor? [y/N]: y
Interval between checks (interval) [10]: 
Ping count (pingcount) [2]: 
Ping wait time (pingwait) [1]: 
Prefer primary network (prefer-primary) [N]: 
Network default route metric (metric) [201]: 
Primary network interface name (primary-if): enxa0cec8003294
Primary network name (primary-name): pnet
Primary network gateway IP Address (primary-gw): 192.168.42.1
Name/IP Address to check if Primary network is up (primary-ping): 
Name/IP Address to ping after failover to Primary (primary-postping): 
Standby network interface name (standby-if): enxa0cec80380a9
Standby network name (standby-name): snet
Standby network gateway IP Address (standby-gw): 192.168.62.1
Name/IP Address to check if Standby network is up (standby-ping): 
Name/IP Address to ping after failover to Standby (standby-postping): 
* Enable the 'ping' monitor? [y/N]: y
Interval between pings (interval) [10]: 
Ping count (pingcount) [2]: 
Ping wait time (pingwait) [1]: 
Name/IP Address to ping (monitorip): 1.1.1.1

Write configuration file '/etc/default/imon-demo? [Y/n] y
Wrote '/etc/default/imon-demo'
p83~$

```
Once you have created your instance configuration file, test it interactively:

* `sudo /usr/local/bin/imon --nosyslog --instance` *myinstance*

Correct configuration settings as needed, and once you're satisfied with the configuration, enable the service:

* `sudo systemctl enable imon@`*myinstance*
* Add `--now` to this command to cause it to start immediately in addition to enabling it for the next system restart.
* If you only want to start the monitor in the current system boot but not enable it for future boots, use `sudo systemctl start imon@`*myinstance*

See the annotated configuration file at the end of this document for a  description of each item.

## Action Scripts

If you have specified an action script, it will be called for several different events. The action script arguments are described in the provided /user/local/bin/imon-action.sample, which is also located at [imon-action.sample](https://github.com/gitbls/imon/blob/main/imon-action.sample) on this github. The sample action script doesn't actually *do* anything other than log all the calls. If you have basic scripting knowledge it should be fairly understandable.

## imon Monitor Details

The following sections discuss each of the 4 monitors in more detail.

### ddns Monitor

The **ddns monitor** monitors your external IP address. Changes are logged in the system log, and if provided, the action script is called. **NOTE:** without an action script, the only output from an external IP address change will be an entry in the system log. No changes are made to your ddns service unless you use an action script that you've updated for your ddns provider.

The action script can do whatever you'd like. Some ddns providers have a scripting interface using `curl` (or similar), and tools such as [dns-lexicon](https://github.com/AnalogJ/lexicon) support a broad set of DNS providers. The sample `imon-action` will call $(hostname)-ip-update, if present, to do the update. Here's the script I use to update my DNS records:
```
#!/bin/bash
_update() {

    # Do whatever you need to do to react to External IP Address change
    # This script called as root
    #
    # $1: New External IP
    # $2: Old External IP (not used)
    newip=$1
    [ "$newip" == "" ] && exit
    lastip=""
    flastip="/usr/local/etc/imon.lastaddress"
    [ -f $flastip ] && source $flastip
    if [ "$newip" != "$lastip" ]
    then
        logger "Internet Monitor Action: Updating DNS entries at Hover"
        (
         hn=$(hostname)
         # Repeat as needed for other A names
         lexicon hover --auth-username xxx --auth-password xxx  update mydom.com A --name \* --content $newip
         sts1=$?
        ) | mail -s "Updated External IP Address to $newip" -r "$hn Admin<root@mydom.com>" me@somewhere.com
        [ -f $flastip ] && rm -f $flastip
        echo "lastip=$newip" > $flastip
    else
       # If last and current IP address are the same, we must have rebooted
       mail -s "$hn rebooted at $(date)" -r "myhost Admin<root@mydom.com>" me@somewhere.com < /dev/null
    fi
    return
}
_update "$1" "$2"
exit 0
```

### failover Monitor

The **failover monitor** uses two WAN network interfaces, and tries to keep the LAN routing to the internet as long as one of the two WAN networks is online.

This is useful, for instance, if you have a faster, or otherwise more preferred primary connection, and a slower, or less preferred secondary connection, although that's not the only use case for it.

The failover monitor can either prefer the primary network or just ensure that the LAN is routing to one of the internet connections.

Consider the following network:

```
           LAN<---->Imon [imrouter]
                     ^          ^
                     |          |
                  ISP1-Router ISP2-Router
```

In this configuration, the LAN uses only host imrouter to get to the internet, so this system would need to be designated as the gateway to the internet for computers on the LAN. Alternatively, this system can sit between the LAN router and the internet. This is all network configuration dependent so something you'll need to sort out for your use case.

imon maintains the default routes (via `ip route`) on imrouter, with only one ***default*** route active at any given time. When the primary network comes back online after a failover, imon will make the primary network the active route if *prefer-primary* is true.

By default imon will check the gateway IP for each network to determine if the network is up or down. Specify a different target with the *ping* argument for one or both of Primary/Standby networks if appropriate for your configuration.

A bit of network configuration is required on imrouter. Each of the three networks (LAN, ISP1, and ISP2) must be configured with no default gateway set. The LAN network clearly doesn't have a gateway to the internet, and imon manages the routes for the failover networks. If you leave the gateway on the LAN network on imrouter, connections to the internet may fail or not work as expected. There shouldn't be a problem if you leave the gateways on ISP1 and ISP2, but there will likely be more system log spew than necessary.

For example, if you're using dhcpcd to configure the networks on a Pi, you would add the following to /etc/dhcpcd.conf (adjusted for your specific configuration). The IP and router addresses shown here are purely examples and show that each of the failover networks must have a unique IP range.

```
interface eth0
nogateway

interface eth1
static ip_address=192.168.42.2/24
static routers=192.168.42.1
nogateway

interface eth2
static ip_address=192.168.62.2/24
static routers=192.168.62.1
nogateway

```

It's important that the network adapter names (eth0, eth1, eth2) in the OS don't ever change, since they are hardwired into the imon instance configuration file. On RasPiOS this is done by enabling *predictable network interface names* in raspi-config. Other distros do this differently. Of course. 

### ping Monitor

The **ping monitor** pings your specified IP address at regular intervals. If an action script has been specified imon will call it with the ping results. If there is no action script, the results are logged in the system log.

The information provided includes the IP address, whether the host is up, and the ping result for the monitored IP address: minrtt, avgrtt, maxrtt, pktloss, and jitter.

### updown Monitor

The **updown monitor** regularly checks that an IP Address you specify is online. The online check is done by pinging the system.

It's useful for checking up on your internet connection availability, tracking a system on your network that occasionally drops offline, or to address network connectivity issues on a particular system.

Some large internet systems are known to block inbound ping when their system load is high. In order to verify that a system is really down (and hence the internet is down), the monitor can try to do a DNS name lookup (parameter *dnslookup*) on an internet-based DNS server (parameter *dnsserver*). If the ping target reports down but the DNS name resolves, imon considers the network to be online.

The updown monitor can also be used to deal with a flakey network. For example, if a system ends up in a problem state that can only be resolved by restarting dhcpcd, use imon on that system to monitor your router. If the router goes offline, your action script can restart dhcpcd, or whatever else you determine is appropriate.

## Usage Hints

You can use the command `sudo journalctl -b | grep -i imon` to quickly scan the system log for Internet outages. `-b` tells journalctl to only look at logs from the current running system.

### Runnning multiple monitors in a single instance

Although multiple monitors can be run concurrently in a single imon instance, you may find it easier to follow this process to get them working:

* Use imon-configure to fully configure all the services
* Edit the configuration file /etc/default/imon-*instance* and set all the services to *false* except one, which should be set to *true*. This is done by changing the value of the **enable** configuration setting for each of the monitors.
* Get that one service working, editing the configuration file as needed
* Once a monitor is working, disable it and repeat for the other monitors you want to run
* When all the desired services are working independently, enable all the desired services and restart imon

### What internet target should I use?

Large internet hosts such as 1.1.1.1, 8.8.8.8, etc., are run by commercial organizations and have plenty of network capacity. If you have your own Internet IP address outside of your LAN (e.g., on a VPC instance in the cloud), you can of course use that if it responds to ping requests. My ISP has a DNS server that (usually) responds to ping requests, so I use that. However, I also use that DNS server to check whether the internet is really down (see *updown monitor* section above).

### Using *addping* to help identify connectivity issues

The Internet can also become unavailable if your router has crashed. You can use the `--addping` switch to have imon also check your router, and report its availability as well to help with early diagnosis. If imon reports that your internet is down and your router is down as well, you'll quickly know that the problem is with your router rather than your Internet connection or your ISP.

Some home internet configurations have two routers: one for the ISP, and a personal router sitting behind it. In this case, imon can be used to check both routers by using `--addping myrouter-ip,isp-router-ip`. For example, `--addping 192.168.16.1,192.168.1.1`. Your IP addresses will most likely be different from these. The order of the IP addresses is your preference.

## Sample Annotated Instance Configuration File

Intervals can be specified as either integers or floating point.

```
{
    "global": {
        ### Full file path to action script [string, Optional]
        "action": "/usr/local/bin/imon-action",
        ### Date format for printing log to terminal if --nosyslog specified [string, Optional]
        "datefmt": "%Y-%m-%d %H:%M:%S",
        ### Instance name [string, Required, has default]
        "instance": "main",
        ### Free-form text string or blank [string, Optional]
        "note": "all but failover",
        ### Version of imon-configure that wrote this config file
        "imon-configure-version": "V1.0",
        ### Date configuration was created
        "imon-configure-created": "2022-04-29 14:42:56"
    },
    "ddns": {
        ### Set to true to enable monitoring for this service
        "enable": false,
        ### Interval in seconds between External IP address checks [float, Required, has default]
        "interval": 10.0,
        ### Number of pings to send (independent setting for each service) [int, Required, has default]
        "pingcount": 2,
        ### Number of seconds to wait for ping response (ditto) [int, Required, has default]
        "pingwait": 1
    },
    "updown": {
        "enable": true,
        "interval": 10.0,
        "pingcount": 2,
        "pingwait": 1,
        ### Name/IP Address to monitor [DNS or IP Address, Required]
        "monitorip": "1.1.1.1",
        ### Comma-separated list of additional IP addresses to check
        ###   when monitorip state transitions [DNS or IP Address, Optional]
        "addping": "192.168.92.1,192.168.1.1",
        ### Name/IP address of DNS server to 2nd test against (see README) [DNS or IP Address, Optional]
        "dnsserver": "1.1.1.1",
        ### Name to look up on dnsserver [DNS, Optional]
        "dnslookup": "google.com"
    },
    "failover": {
        "enable": false,
        "interval": 1.0,
        "pingcount": 2.0,
        "pingwait": 1.0,
        ### true:Use primary if it's up
        ### false:Do not failback to primary [true/false, Required]
        "prefer-primary": true,
	    ### Metric to use when setting default routes [int, Required, has default]
	    "metric": 201,
        ### Primary network interface name [string, Required]
        "primary-if": "enxa0cec8003294",
        ### User-provided name for primary network [string, Required]
        "primary-name": "net42",
        ### Gateway IP for primary network [IP Address, Required]
        "primary-gw": "192.168.42.1",
        ### Name/IP address to ping check instead of gateway [DNS or IP Address, Optional]
        "primary-ping": "",
        ### Name/IP address to ping check after network transitions online [DNS or IP Address, Optional]
        "primary-postping": "",
        ### Standby network interface name [string, Required]
        "standby-if": "enxa0cec80380a9",
        ### User-provided name for standby network [string, Required]
        "standby-name": "net62",
        ### Gateway IP for standby network [IP Address, Required]
        "standby-gw": "192.168.62.1",
        ### Name/IP address to ping check instead of gateway [DNS or IP Address, Optional]
        "standby-ping": "",
        ### Name/IP address to ping check after network transitions online [DNS or IP Address, Optional]
        "standby-postping": ""
    },
    "ping": {
        "enable": false,
        "interval": 10.0,
        "pingcount": 2,
        "pingwait": 1,
        ### Name/IP address to ping monitor [DNS or IP Address, Required]
        "monitorip": "192.168.1.1"
    }
}

```

## imon logging

By default, imon logs everything to the system log. For interactive testing, you can use the `--nosyslog` switch to have the log output displayed on the terminal.

You can see some sample logs at [sample-logs.md](https://github.com/gitbls/imon/blob/main/sample-logs.md)
