# MQ-ECN-Experiments
## Software Requirements
To reproduce Figure 7 and 8 of [MQ-ECN paper](http://www.cse.ust.hk/~kaichen/papers/mqecn-nsdi16.pdf), you need following software:
  - [MQ-ECN software prototype](https://github.com/HKUST-SING/MQ-ECN-Software)
  - [A simple traffic generator](https://github.com/HKUST-SING/TrafficGenerator)
  
In addition, you also need to install Linux 3.18x kernel which supports DCTCP. We used 3.18.11 kernel in our experiments. We also provide a [patch](https://github.com/baiwei0427/Latency-Measurement/blob/master/kernel_measurement3.patch) for Linux 3.18.11 kernel which allows users to adjust TCP RTOmin using sysctl.  

## Testbed Setup
In the testbed, 9 servers are connected to a 9-port server-emulated switch. One server acts as the receiver while the rest 8 servers act as the sender. The IP address of the receiver is 192.168.101.1(/24). The IP addresses of senders are 192.168.102.1(/24), 192.168.103.1(/24), ... 192.168.109.1(/24). The server-emulated switch has 9 NICs whose IP addresses are 192.168.101.2(/24), 192.168.102.2(/24), ... 192.168.109.2(/24). To avoid large segments, please disable offloading techniques (e.g., GSO, TSO and GRO) on the server-emulated switch.   

To enable packet forwarding on the server-emulated switch:
```
$ sysctl -w net.ipv4.ip_forward=1
```
To ensure servers on different subnets (e.g., 192.168.101.0/24 and 192.168.102.0/24) can access each other, you need to add some routing entries on servers. For example, at the receiver (192.168.101.1), I add a new routing entry as follows:
```
$ route add -net 192.168.0.0/16 gw 192.168.101.2
```


