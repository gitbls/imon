# Sample log output

## Log output from a 'ddns' instance
```
Apr 30 13:32:06 p83 imon[5432]: imon [ddns] Starting
Apr 30 13:32:06 p83 imon[5432]: imon [ddns] Version V2.90
Apr 30 13:32:06 p83 imon[5432]: imon [ddns] Command line: /usr/local/bin/imon --instance ddns
Apr 30 13:32:06 p83 imon[5432]: imon [ddns] Configuration file /etc/default/imon-ddns
Apr 30 13:32:06 p83 imon[5432]: imon [ddns] ** [global] **
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     action
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     datefmt           %Y-%m-%d %H:%M:%S
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     instance          ddns
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     note              ddns test
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     imon-configure-version V1.0
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     imon-configure-created 2022-04-30 12:13:20
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     debug             True
Apr 30 13:32:06 p83 imon[5432]: imon [ddns] ** [ddns] **
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     enable            True
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     interval          5.0
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     pingcount         2
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     pingwait          1
Apr 30 13:32:06 p83 imon[5432]: imon [ddns] ** [updown] **
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     enable            False
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     interval          10
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     pingcount         2
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     pingwait          1
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     monitorip
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     addping
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     dnsserver
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     dnslookup
Apr 30 13:32:06 p83 imon[5432]: imon [ddns] ** [failover] **
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     enable            False
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     interval          10
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     pingcount         2
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     pingwait          1
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     prefer-primary    False
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     metric            201
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     primary-if
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     primary-name
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     primary-gw
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     primary-ping
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     primary-postping
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     standby-if
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     standby-name
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     standby-gw
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     standby-ping
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     standby-postping
Apr 30 13:32:06 p83 imon[5432]: imon [ddns] ** [ping] **
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     enable            False
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     interval          10
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     pingcount         2
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     pingwait          1
Apr 30 13:32:06 p83 imon[5432]: imon [ddns]     monitorip
Apr 30 13:32:06 p83 imon[5432]: imon [ddns] Start External IP Address tracking
Apr 30 13:32:06 p83 imon[5432]: imon [ddns] External IP Address changed from unknown to 192.168.14.1
Apr 30 13:32:11 p83 imon[5432]: imon [ddns] External IP Address changed from 192.168.14.1 to 172.16.12.2
Apr 30 13:32:16 p83 imon[5432]: imon [ddns] External IP Address changed from 172.16.12.2 to 10.1.10.3
Apr 30 13:32:21 p83 imon[5432]: imon [ddns] External IP Address changed from 10.1.10.3 to 192.168.14.4
```
## Log output from a 'ping' instance
```
Apr 30 13:32:30 p83 imon[5438]: imon [ping] Starting
Apr 30 13:32:30 p83 imon[5438]: imon [ping] Version V2.90
Apr 30 13:32:30 p83 imon[5438]: imon [ping] Command line: /usr/local/bin/imon --instance ping
Apr 30 13:32:30 p83 imon[5438]: imon [ping] Configuration file /etc/default/imon-ping
Apr 30 13:32:30 p83 imon[5438]: imon [ping] ** [global] **
Apr 30 13:32:30 p83 imon[5438]: imon [ping]     action
Apr 30 13:32:30 p83 imon[5438]: imon [ping]     datefmt           %Y-%m-%d %H:%M:%S
Apr 30 13:32:30 p83 imon[5438]: imon [ping]     instance          ping
Apr 30 13:32:30 p83 imon[5438]: imon [ping]     note              ping only
Apr 30 13:32:30 p83 imon[5438]: imon [ping]     imon-configure-version V1.0
Apr 30 13:32:30 p83 imon[5438]: imon [ping]     imon-configure-created 2022-04-30 12:23:04
Apr 30 13:32:30 p83 imon[5438]: imon [ping] ** [ddns] **
Apr 30 13:32:30 p83 imon[5438]: imon [ping]     enable            False
Apr 30 13:32:30 p83 imon[5438]: imon [ping]     interval          10
Apr 30 13:32:30 p83 imon[5438]: imon [ping]     pingcount         2
Apr 30 13:32:30 p83 imon[5438]: imon [ping]     pingwait          1
Apr 30 13:32:30 p83 imon[5438]: imon [ping] ** [updown] **
Apr 30 13:32:30 p83 imon[5438]: imon [ping]     enable            False
Apr 30 13:32:30 p83 imon[5438]: imon [ping]     interval          10
Apr 30 13:32:30 p83 imon[5438]: imon [ping]     pingcount         2
Apr 30 13:32:30 p83 imon[5438]: imon [ping]     pingwait          1
Apr 30 13:32:30 p83 imon[5438]: imon [ping]     monitorip
Apr 30 13:32:30 p83 imon[5438]: imon [ping]     addping
Apr 30 13:32:30 p83 imon[5438]: imon [ping]     dnsserver
Apr 30 13:32:30 p83 imon[5438]: imon [ping]     dnslookup
Apr 30 13:32:30 p83 imon[5438]: imon [ping] ** [failover] **
Apr 30 13:32:30 p83 imon[5438]: imon [ping]     enable            False
Apr 30 13:32:30 p83 imon[5438]: imon [ping]     interval          10
Apr 30 13:32:30 p83 imon[5438]: imon [ping]     pingcount         2
Apr 30 13:32:30 p83 imon[5438]: imon [ping]     pingwait          1
Apr 30 13:32:30 p83 imon[5438]: imon [ping]     prefer-primary    False
Apr 30 13:32:30 p83 imon[5438]: imon [ping]     metric            201
Apr 30 13:32:30 p83 imon[5438]: imon [ping]     primary-if
Apr 30 13:32:30 p83 imon[5438]: imon [ping]     primary-name
Apr 30 13:32:30 p83 imon[5438]: imon [ping]     primary-gw
Apr 30 13:32:30 p83 imon[5438]: imon [ping]     primary-ping
Apr 30 13:32:30 p83 imon[5438]: imon [ping]     primary-postping
Apr 30 13:32:30 p83 imon[5438]: imon [ping]     standby-if
Apr 30 13:32:30 p83 imon[5438]: imon [ping]     standby-name
Apr 30 13:32:30 p83 imon[5438]: imon [ping]     standby-gw
Apr 30 13:32:30 p83 imon[5438]: imon [ping]     standby-ping
Apr 30 13:32:30 p83 imon[5438]: imon [ping]     standby-postping
Apr 30 13:32:30 p83 imon[5438]: imon [ping] ** [ping] **
Apr 30 13:32:30 p83 imon[5438]: imon [ping]     enable            True
Apr 30 13:32:30 p83 imon[5438]: imon [ping]     interval          10.0
Apr 30 13:32:30 p83 imon[5438]: imon [ping]     pingcount         2
Apr 30 13:32:30 p83 imon[5438]: imon [ping]     pingwait          1
Apr 30 13:32:30 p83 imon[5438]: imon [ping]     monitorip         192.168.92.1
Apr 30 13:32:30 p83 imon[5438]: imon [ping] Start Ping Monitor
Apr 30 13:32:31 p83 imon[5438]: imon [ping] Ping Result: IP:192.168.92.1 State:True minrtt:0.434 avgrtt:2.664 maxrtt:4.894 loss:0.0 jitter:4.46
Apr 30 13:32:42 p83 imon[5438]: imon [ping] Ping Result: IP:192.168.92.1 State:True minrtt:0.571 avgrtt:0.579 maxrtt:0.587 loss:0.0 jitter:0.016
```

## Log output from an 'updown' instance
```
Apr 30 13:32:49 p83 imon[5441]: imon [updown] Starting
Apr 30 13:32:49 p83 imon[5441]: imon [updown] Version V2.90
Apr 30 13:32:49 p83 imon[5441]: imon [updown] Command line: /usr/local/bin/imon --instance updown
Apr 30 13:32:49 p83 imon[5441]: imon [updown] Configuration file /etc/default/imon-updown
Apr 30 13:32:49 p83 imon[5441]: imon [updown] ** [global] **
Apr 30 13:32:49 p83 imon[5441]: imon [updown]     action
Apr 30 13:32:49 p83 imon[5441]: imon [updown]     datefmt           %Y-%m-%d %H:%M:%S
Apr 30 13:32:49 p83 imon[5441]: imon [updown]     instance          updown
Apr 30 13:32:49 p83 imon[5441]: imon [updown]     note              updown only
Apr 30 13:32:49 p83 imon[5441]: imon [updown]     imon-configure-version V1.0
Apr 30 13:32:49 p83 imon[5441]: imon [updown]     imon-configure-created 2022-04-30 12:39:09
Apr 30 13:32:49 p83 imon[5441]: imon [updown] ** [ddns] **
Apr 30 13:32:49 p83 imon[5441]: imon [updown]     enable            False
Apr 30 13:32:49 p83 imon[5441]: imon [updown]     interval          10
Apr 30 13:32:49 p83 imon[5441]: imon [updown]     pingcount         2
Apr 30 13:32:49 p83 imon[5441]: imon [updown]     pingwait          1
Apr 30 13:32:49 p83 imon[5441]: imon [updown] ** [updown] **
Apr 30 13:32:49 p83 imon[5441]: imon [updown]     enable            True
Apr 30 13:32:49 p83 imon[5441]: imon [updown]     interval          5.0
Apr 30 13:32:49 p83 imon[5441]: imon [updown]     pingcount         2
Apr 30 13:32:49 p83 imon[5441]: imon [updown]     pingwait          1
Apr 30 13:32:49 p83 imon[5441]: imon [updown]     monitorip         192.168.42.1
Apr 30 13:32:49 p83 imon[5441]: imon [updown]     addping           192.168.92.1
Apr 30 13:32:49 p83 imon[5441]: imon [updown]     dnsserver
Apr 30 13:32:49 p83 imon[5441]: imon [updown]     dnslookup         somehost.somedomain.com
Apr 30 13:32:49 p83 imon[5441]: imon [updown] ** [failover] **
Apr 30 13:32:49 p83 imon[5441]: imon [updown]     enable            False
Apr 30 13:32:49 p83 imon[5441]: imon [updown]     interval          10
Apr 30 13:32:49 p83 imon[5441]: imon [updown]     pingcount         2
Apr 30 13:32:49 p83 imon[5441]: imon [updown]     pingwait          1
Apr 30 13:32:49 p83 imon[5441]: imon [updown]     prefer-primary    False
Apr 30 13:32:49 p83 imon[5441]: imon [updown]     metric            201
Apr 30 13:32:49 p83 imon[5441]: imon [updown]     primary-if
Apr 30 13:32:49 p83 imon[5441]: imon [updown]     primary-name
Apr 30 13:32:49 p83 imon[5441]: imon [updown]     primary-gw
Apr 30 13:32:49 p83 imon[5441]: imon [updown]     primary-ping
Apr 30 13:32:49 p83 imon[5441]: imon [updown]     primary-postping
Apr 30 13:32:49 p83 imon[5441]: imon [updown]     standby-if
Apr 30 13:32:49 p83 imon[5441]: imon [updown]     standby-name
Apr 30 13:32:49 p83 imon[5441]: imon [updown]     standby-gw
Apr 30 13:32:49 p83 imon[5441]: imon [updown]     standby-ping
Apr 30 13:32:49 p83 imon[5441]: imon [updown]     standby-postping
Apr 30 13:32:49 p83 imon[5441]: imon [updown] ** [ping] **
Apr 30 13:32:49 p83 imon[5441]: imon [updown]     enable            False
Apr 30 13:32:49 p83 imon[5441]: imon [updown]     interval          10
Apr 30 13:32:49 p83 imon[5441]: imon [updown]     pingcount         2
Apr 30 13:32:49 p83 imon[5441]: imon [updown]     pingwait          1
Apr 30 13:32:49 p83 imon[5441]: imon [updown]     monitorip
Apr 30 13:32:49 p83 imon[5441]: imon [updown] Start Updown Monitor for IP Address 192.168.42.1
Apr 30 13:32:50 p83 imon[5441]: imon [updown] Monitored IP 192.168.42.1 online
Apr 30 13:32:50 p83 imon[5441]: imon [updown] Secondary IP 192.168.92.1 online
Apr 30 13:33:11 p83 imon[5441]: imon [updown] Monitored IP 192.168.42.1 offline
Apr 30 13:33:12 p83 imon[5441]: imon [updown] Secondary IP 192.168.92.1 online
Apr 30 13:33:22 p83 imon[5441]: imon [updown] Monitored IP 192.168.42.1 online
Apr 30 13:33:22 p83 imon[5441]: imon [updown] Outage Duration: 0 days 0 hours, 0 minutes 10 seconds
Apr 30 13:33:22 p83 imon[5441]: imon [updown] Secondary IP 192.168.92.1 online
```

## Log output from a 'failover' instance
```
Apr 30 13:33:35 p83 imon[5446]: imon [failover] Starting
Apr 30 13:33:35 p83 imon[5446]: imon [failover] Version V2.90
Apr 30 13:33:35 p83 imon[5446]: imon [failover] Command line: /usr/local/bin/imon --instance failover
Apr 30 13:33:35 p83 imon[5446]: imon [failover] Configuration file /etc/default/imon-failover
Apr 30 13:33:35 p83 imon[5446]: imon [failover] ** [global] **
Apr 30 13:33:35 p83 imon[5446]: imon [failover]     action
Apr 30 13:33:35 p83 imon[5446]: imon [failover]     datefmt           %Y-%m-%d %H:%M:%S
Apr 30 13:33:35 p83 imon[5446]: imon [failover]     instance          failover
Apr 30 13:33:35 p83 imon[5446]: imon [failover]     note              failover only
Apr 30 13:33:35 p83 imon[5446]: imon [failover]     imon-configure-version V1.0
Apr 30 13:33:35 p83 imon[5446]: imon [failover]     imon-configure-created 2022-04-30 13:04:57
Apr 30 13:33:35 p83 imon[5446]: imon [failover] ** [ddns] **
Apr 30 13:33:35 p83 imon[5446]: imon [failover]     enable            False
Apr 30 13:33:35 p83 imon[5446]: imon [failover]     interval          10
Apr 30 13:33:35 p83 imon[5446]: imon [failover]     pingcount         2
Apr 30 13:33:35 p83 imon[5446]: imon [failover]     pingwait          1
Apr 30 13:33:35 p83 imon[5446]: imon [failover] ** [updown] **
Apr 30 13:33:35 p83 imon[5446]: imon [failover]     enable            False
Apr 30 13:33:35 p83 imon[5446]: imon [failover]     interval          10
Apr 30 13:33:35 p83 imon[5446]: imon [failover]     pingcount         2
Apr 30 13:33:35 p83 imon[5446]: imon [failover]     pingwait          1
Apr 30 13:33:35 p83 imon[5446]: imon [failover]     monitorip
Apr 30 13:33:35 p83 imon[5446]: imon [failover]     addping
Apr 30 13:33:35 p83 imon[5446]: imon [failover]     dnsserver
Apr 30 13:33:35 p83 imon[5446]: imon [failover]     dnslookup
Apr 30 13:33:35 p83 imon[5446]: imon [failover] ** [failover] **
Apr 30 13:33:35 p83 imon[5446]: imon [failover]     enable            True
Apr 30 13:33:35 p83 imon[5446]: imon [failover]     interval          2.0
Apr 30 13:33:35 p83 imon[5446]: imon [failover]     pingcount         2
Apr 30 13:33:35 p83 imon[5446]: imon [failover]     pingwait          1
Apr 30 13:33:35 p83 imon[5446]: imon [failover]     prefer-primary    False
Apr 30 13:33:35 p83 imon[5446]: imon [failover]     metric            201
Apr 30 13:33:35 p83 imon[5446]: imon [failover]     primary-if        enxa0cec8003294
Apr 30 13:33:35 p83 imon[5446]: imon [failover]     primary-name      pnet
Apr 30 13:33:35 p83 imon[5446]: imon [failover]     primary-gw        192.168.42.1
Apr 30 13:33:35 p83 imon[5446]: imon [failover]     primary-ping
Apr 30 13:33:35 p83 imon[5446]: imon [failover]     primary-postping
Apr 30 13:33:35 p83 imon[5446]: imon [failover]     standby-if        enxa0cec80380a9
Apr 30 13:33:35 p83 imon[5446]: imon [failover]     standby-name      snet
Apr 30 13:33:35 p83 imon[5446]: imon [failover]     standby-gw        192.168.62.1
Apr 30 13:33:35 p83 imon[5446]: imon [failover]     standby-ping
Apr 30 13:33:35 p83 imon[5446]: imon [failover]     standby-postping
Apr 30 13:33:35 p83 imon[5446]: imon [failover] ** [ping] **
Apr 30 13:33:35 p83 imon[5446]: imon [failover]     enable            False
Apr 30 13:33:35 p83 imon[5446]: imon [failover]     interval          10
Apr 30 13:33:35 p83 imon[5446]: imon [failover]     pingcount         2
Apr 30 13:33:35 p83 imon[5446]: imon [failover]     pingwait          1
Apr 30 13:33:35 p83 imon[5446]: imon [failover]     monitorip
Apr 30 13:33:35 p83 imon[5446]: imon [failover] Start Network Failover Monitor
Apr 30 13:33:36 p83 imon[5446]: imon [failover] Network Failover Initial State for Primary Network pnet (enxa0cec8003294): online
Apr 30 13:33:36 p83 imon[5446]: imon [failover] Network Failover to Primary Network pnet (enxa0cec8003294)
Apr 30 13:33:36 p83 imon[5446]: imon [failover] Network Failover Primary Route pnet (enxa0cec8003294) is active
Apr 30 13:33:37 p83 imon[5446]: imon [failover] Network Failover Initial State for Standby Network snet (enxa0cec80380a9): online
Apr 30 13:33:55 p83 imon[5446]: imon [failover] Primary Network pnet (enxa0cec8003294) is now offline
Apr 30 13:33:56 p83 imon[5446]: imon [failover] Network Failover to Standby Network snet (enxa0cec80380a9)
Apr 30 13:33:56 p83 imon[5446]: imon [failover] Network Failover Standby Route snet (enxa0cec80380a9) is active
Apr 30 13:34:10 p83 imon[5446]: imon [failover] Standby Network snet (enxa0cec80380a9) is now offline
Apr 30 13:34:18 p83 imon[5446]: imon [failover] Both Primary and Standby Networks are offline
Apr 30 13:34:29 p83 imon[5446]: imon [failover] Primary Network pnet (enxa0cec8003294) is now online
Apr 30 13:34:29 p83 imon[5446]: imon [failover] Primary Network Outage Duration: 0 days 0 hours, 0 minutes 34 seconds
Apr 30 13:34:29 p83 imon[5446]: imon [failover] Network Failover to Primary Network pnet (enxa0cec8003294)
Apr 30 13:34:29 p83 imon[5446]: imon [failover] Network Failover Primary Route pnet (enxa0cec8003294) is active
Apr 30 13:34:36 p83 imon[5446]: imon [failover] Standby Network snet (enxa0cec80380a9) is now online
Apr 30 13:34:36 p83 imon[5446]: imon [failover] Standby Network Outage Duration: 0 days 0 hours, 0 minutes 26 seconds
```
