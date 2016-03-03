# MQ-ECN-Experiments
## Software Requirements
To reproduce Figure 7 and 8 of [MQ-ECN paper](http://www.cse.ust.hk/~kaichen/papers/mqecn-nsdi16.pdf), you need following softwares:
  - [MQ-ECN software prototype](https://github.com/HKUST-SING/MQ-ECN-Software)
  - [A simple traffic generator](https://github.com/HKUST-SING/TrafficGenerator)
  
In addition, you also need to install Linux 3.18x kernel which supports DCTCP. We used 3.18.11 kernel in our experiments. We also provide a [patch](https://github.com/baiwei0427/Latency-Measurement/blob/master/kernel_measurement3.patch) for Linux 3.18.11 kernel which allows users to adjust TCP RTOmin using sysctl.  
