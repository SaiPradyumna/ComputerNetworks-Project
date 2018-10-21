# ComputerNetworks-Project (CO300)

## SIM-21:  Implementing Hoe’s Modification to Slow Start

### Statement:

It proposes changes to improve the startup behavior of the congestion control scheme.
Changes proposed include using an estimated value instead of default value for the slow start
threshold at start-up, and modifying the Fast Retransmit algorithm.

## Members :
* Sai Pradyumna(16CO220) 
* Lokesh Manideep(16CO213)
* Prasanth Sagar(16CO225) kpsagar1999@gmail.com
 
 ## Abstract
 ### Improving the Start-up Behavior of a Congestion Control Scheme for TCP
 Changes to congestion control scheme in current tcp implementations to improve its behaviour during the startup period of TCP connection.
 The control scheme uses SlowStart,Fast Retransmission and Fast recovery algorithms.
 During Startup period because a TCP sender starts with default parameters it often ends up sending too many packets and too fast,leading to multiple losses of packets from the same window.The recovery from losses during this startup period is often unnecessarily time consuming.
 The current Fast Retransmit algorithm, when multiple packets in the same window are lost, only one of the packet losses may be recovered by each Fast Retransmit; the rest are often recovered by Slow-start after a usually lengthy retransmission timeout.
 We make changes to the Fast Retransmit algorithm so that it can quickly recover from multiple packet losses without waiting unnecessarily for the timeout and in slow start instead of using default value for sshtresh we use better initial value to curtail the surge of packets
 
 ## Objective
 --To improve tcp performance
 As we knew that initial value of 'ssthresh' is critical.One way is to find a better value of ssthresh so that we can avoid large surge of packet that leads to multiple packet losses, ie ,we can avoid this thing .so we need to find an estimate of the threshold at which the sender is closely approaching the full network capacity and thus should slow down and probe remaining capacity.
 
 ## Congestion Control Scheme
 
 Slow Start Phase : exponential increment – In this phase after every RTT the congestion window size increments exponentially.
 
 Congestion Avoidance Phase : additive increment – This phase starts after the threshold value also denoted as ssthresh. The size of cwnd(congestion window) increases additive. After each RTT cwnd = cwnd + 1.

Congestion Detection Phase : multiplicative decrement – If congestion occurs, the congestion window size is decreased. The only way a sender can guess that congestion has occurred is the need to retransmit a segment. Retransmission is needed to recover a missing packet which is assumed to have been dropped by a router due to congestion. Retransmission can occur in one of two cases: when the RTO timer times out or when three duplicate ACKs are received.
 
 Case 1 : Retransmission due to Timeout – In this case congestion possibility is high.
    (a) ssthresh is reduced to half of the current window size.
    (b) set cwnd = 1
    (c) start with slow start phase again.

Case 2 : Retransmission due to 3 Acknowledgement Duplicates – In this case congestion possibility is less.
    (a) ssthresh value reduces to half of the current window size.
    (b) set cwnd= ssthresh
    (c) start with congestion avoidance phase 
   
 ## Reference 
 
         http://dl.acm.org/citation.cfm?id=248180
 
         J. C. Hoe, “Improving the Start up Behaviour of a Congestion Control Scheme for TCP” Proceedings of ACM SIGCOMM.

