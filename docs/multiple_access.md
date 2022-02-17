
# Multiple Access
- Data link layer divided into two functionality-oriented sublayers
- Data link control


## Multiple access protocols:

### Random access protocols (4 ta)
- Aloha
- CSMA
- CSMA /CD
- CSMA/CA
## Controlled access protocols (RPT)
- Reservation
- Polling
- Token passing

## Channelization protocols(FTC)
- FDMA
- TDMA
- CDMA

## Random Access/Contention Method
- No station is superior to another station
- There is  no master and slave.
- None is assigned the control over another
- No station permits/does not permit another one to send
- At each instance, a station which has data to send Uses a procedure Defined by the protocol To make a decision on whether or not to send.

## PURE ALOHA
- no sensor for collision
- Sender sends frames, if a sent frame collides with other frames of another sender then no acknowledgement would be received for the collided frames, they need to be resent.
- Only frame 1.1 and frame 3.2 will be sent successfully, so for them ack would be received
- But for others there will be no acknowledgement

## Procedure for pure ALOHA protocol
<pre>
Here at first K= first attempt =0
Send the frame
Then for sending + receiving - wait time to out time -> 2*Tp
Ack received -> yes -> success
No -> next attempt (K=K+1)
If K>Kmax ( maximum attempt number )
Then abort
Else 
Choose a random number R = bet^n 0 to 2^k-1
Wait tb time = back off time = waiting time until an ack arrives(random time duration)	= R * Tp ( max propagation time ) = R * Tfr ( average transmission time for a frame )
Then send the frame again
</pre>

<pre>
The stations on a wireless ALOHA network are a maximum of 600 km apart. If we assume that signals propagate at 3 × 10^8 m/s,  we find 
v=d/t -> t=d/v 
       Tp = (600 × 10^3) / (3 × 10^8) = 2 ms. 
Now we can find the value of TB for different values of K .
a. For K = 1, the range is {0, 1}. The station needs to
     generate a random number with a value of 0 or 1. This
     means that TB is either 
     = R * Tp = 0 ms (0 × 2) or
     = R * Tp = 2 ms (1 × 2),
     based on the outcome of the random variable.

b. For K = 2, the range is {0, 1, 2, 3}. This means that TB
     can be 0, 2, 4, or 6 ms, 
based on the outcome of the random variable.

c. For K = 3, the range is {0, 1, 2, 3, 4, 5, 6, 7}. This
     means that TB can be 0, 2, 4, . . . , 14 ms, 
based on the outcome of the random variable.

d. We need to mention that if K > 10, it is normally set to 10.
</pre>

## Vulnerable time for pure ALOHA

- The vulnerable time is in which there is a possibility of collision. We assume that the stations send fixed-length frames with each frame taking Tfr S to send. The following figure shows the vulnerable time for station A.

- Station A sends a frame at time t. Now imagine station B has already sent a frame between t - Tfr and t. This leads to a collision between the frames from station A and station B. The end of B's frame collides with the beginning of A's frame. On the other hand, suppose that station C sends a frame between t and t + Tfr . Here, there is a collision between frames from station A and station C. The beginning of C's frame collides with the end of A's frame.

<pre>
A pure ALOHA network transmits 200-bit frames on a shared channel of 200 kbps.What is the requirement to make this frame collision-free?
200*10^3 bits per 1 second
200 bits = 200/200*10^3 = 1 ms
Average frame transmission time Tfr= 1ms
vulnerable time is  2 × 1 ms = 2 ms.
Let's assume station A starts sending a frame at time t.
So station B cannot start sending a frame from t-1  to t
Or station C cannot start sending a frame from t to t+1
Or Station D cannot start sending a frame during 1 ms period when A is sending. 
</pre>

## Throughput for pure Aloha
The throughput for pure ALOHA is S = G × e^ −2G  .
The maximum throughput Smax = 0.184 when G= (1/2)

<pre>
A pure ALOHA network transmits 200-bit frames on a shared channel of 200 kbps. What is the throughput if the system (all stations together) produces
a. 1000 frames per second    b. 500 frames per second
c. 250 frames per second.

Solution

a. The frame transmission time is Tfr= 200/200 kbps or 1 ms.

1 second=1000 frames
10^-3 s = 1000 * 10^-3 frames = 1 frame 

G = load = 1 frame per millisecond 

If the system creates 1000 frames per second, this is 1 frame per millisecond. The load is 1. 


S = G× e^−2 G or S = 0.135 (13.5 percent). 
throughput is 1000 × 0.135 = 135 frames. 
    
Only 135 frames out of 1000 will probably survive.


b. The frame transmission time is Tfr= 200/200 kbps or 1 ms.
1 second=500 frames
10^-3 s = 500 * 10^-3 frames = .5 frame 

G = load = 1/2 frame per millisecond 
    If the system creates 500 frames per second, this is
    (1/2) frame per millisecond. The load is (1/2). In this
    case S = G × e^ −2G or S = 0.184 (18.4 percent). This
    means that the throughput is 500 × 0.184 = 92 and that
    only 92 frames out of 500 will probably survive. 

    Note
    that this is the maximum throughput case,
    Percentage wise.

c. The frame transmission time is Tfr= 200/200 kbps or 1 ms.
1 second=250 frames
10^-3 s = 250 * 10^-3 frames = .25 frame 

G = load = 1/4 frame per millisecond 
If the system creates 250 frames per second, this is (1/4)
    frame per millisecond. The load is (1/4). In this case 
    S = G × e^ −2G or S = 0.152 (15.2 percent). This means
    that the throughput is 250 × 0.152 = 38. Only 38
    frames out of 250 will probably survive.

</pre>

## Slotted ALOHA
> Pure ALOHA has a vulnerable time of 2 x Tfr. This is so because there is no rule that defines when the station can send. A station may send soon after another station has started or soon before another station has finished. Slotted ALOHA was invented to improve the efficiency of pure ALOHA.
In slotted ALOHA we divide the time into slots of Tfr s and force the station to send only at the beginning of the time slot.

> Because a station is allowed to send only at the beginning of the synchronized time slot, if a station misses this moment, it must wait until the beginning of the next time slot. This means that the station which started at the beginning of this slot has already finished sending its frame. But, still there is the possibility of collision if two stations try to send at the beginning of the same time slot. However, the vulnerable time is now reduced to one-half, equal to Tfr. figure 14 

## Throughput for slotted Aloha
> The throughput for slotted ALOHA is S = G × e^−G .The maximum throughput Smax = 0.368 when G = 1.


<pre>
A slotted ALOHA  network transmits 200-bit frames on a shared channel of 200 kbps. What is the throughput if the system (all stations together) produces
a. 1000 frames per second    b. 500 frames per second
c. 250 frames per second.

The frame transmission time is 200/200 kbps or 1 ms.
a. If the system creates 1000 frames per second, this is 1
    frame per millisecond. The load is 1. In this case 
    S = G× e^−G or S = 0.368 (36.8 percent). This means
    that the throughput is 1000 × 0.0368 = 368 frames.
    Only 368 frames out of 1000 will probably survive.

b. If the system creates 500 frames per second, this is
    (1/2) frame per millisecond. The load is (1/2). In this
    case S = G × e^−G or S = 0.303 (30.3 percent). This
    means that the throughput is 500 × 0.0303 = 151. 
    Only 151 frames out of 500 will probably survive.

c. If the system creates 250 frames per second, this is (1/4)
    frame per millisecond. The load is (1/4). In this case 
    S = G × e^−G or S = 0.195 (19.5 percent). This means
    that the throughput is 250 × 0.195 = 49. Only 49
    frames out of 250 will probably survive.
</pre>


## CSMA - carrier sense multiple access

## Vulnerable Time of CSMA:

> The vulnerable time for CSMA is the propagation time Tp. This is the time needed for a signal to propagate from one end of the medium to the other. When a station sends a frame, and any other station tries to send a frame during this time, a collision will result. But if the first bit of the frame reaches the end of the medium, every station will already have heard the bit and will refrain from sending. The following figure shows the worst case. The leftmost station A sends a frame at time t1 which reaches the rightmost station D at time t1 + Tp. The gray area shows the vulnerable area in time and space.

<pre>
What should a station do if the channel is busy? What should a station do if the channel is idle? Three methods have been devised to answer these questions: 
the 1-persistent method, 
the non persistent method, and 
the p-persistent method. 
</pre>

The following figure shows the behavior of three persistence methods when a station finds a channel busy.
![image](https://user-images.githubusercontent.com/59027621/154421563-3a8b5e20-523e-4cb6-8b05-d707d08ff906.png)

• 1-Persistent: In this method, after the station finds the line idle, it sends its frame immediately (with probability 1). This method has the highest chance of collision because two or more stations may find the line idle and send their frames immediately.

• Nonpersistent: a station that has a frame to send, senses the line. If the line is idle, it sends immediately. If the line is not idle, it waits a random amount of time and then senses the line again. The nonpersistent approach reduces the chance of collision because it is unlikely that two or more stations will wait the same amount of time and retry to send simultaneously. However, this method reduces the efficiency of the network because the medium remains idle when there may be stations with frames to send.

• P-Persistent: The p-persistent method is used if the channel has time slots with a slot duration >= maximum propagation time. The p-persistent approach combines the advantages of the other two strategies. 
reduces the chance of collision
improves efficiency. 

When the station finds the channel 
- busy, it acts as 1 persistent method.
- idle, it follows these steps:
1. With probability outcome<=p, the station can send its frame.
2. With probability outcome>p, the station waits for the beginning of the next time slot and checks the line again.
3. If the line is idle, it goes to step 1.
4. If the line is busy, it acts as though a collision has occurred and uses the back off procedure.

# Carrier Sense Multiple Access with Collision Detection (CSMA/CD) 

> The CSMA method does not specify the procedure following a collision. Carrier sense multiple access with collision detection (CSMA/CD) augments the algorithm to handle the collision.

> In this method, a station monitors the medium after it sends a frame to see if the transmission was successful. If so, the station is finished. If, however, there is a collision, the frame is sent again.

> To better understand CSMA/CD, let us look at the first bits transmitted by the two stations A,C involved in the collision. Although each station continues to send bits in the frame until it detects the collision, we show what happens as the first bits collide. In the following Figure stations A and C are involved in the collision.


• At time t1, station A has executed its persistence procedure and starts sending the bits of its frame.  

• At time t2, station C has not yet sensed the first bit sent by A. Station C executes its persistence procedure and starts sending the bits in its frame, which propagate both to the left and to the right.  

• The collision occurs sometime after time t2', Station C detects a collision at time t3 when it receives the first bit of A's frame. Station C immediately aborts transmission.

• Station A detects collision at time t4 when it receives the first bit of C's frame; it also immediately aborts transmission.

• Looking at the figure, we see that A transmits for the duration t4 – t1. C transmits for the duration t3 - t2. The protocol to work, the length of any frame divided by the bit rate must be more than either of these durations. At time t4, the transmission of A’s frame, though incomplete, is aborted. At time t3, the transmission of C's frame, though incomplete, is aborted.

# Minimum Size of frame in CSMA/CD
For CSMA/CD to work, we need a restriction on the frame size. Before sending the last bit of the frame, the sending station must detect a collision, if any, and abort the transmission.
This is so because the station, once the entire frame is sent, does not keep a copy of the frame and does not monitor the line for collision detection. Therefore, the frame transmission time Tfr must be at least two times the maximum propagation time Tp.

To understand the reason, let us think about the worst-case scenario: the signal from the first takes time Tp to reach the second and the effect of the collision takes another time Tp to reach the first. So the requirement is that the first station must still be transmitting after 2Tp .

<pre>
A network using CSMA/CD has a bandwidth of 10 Mbps. If the maximum propagation time (including the delays in the devices and ignoring the time needed to send a jamming signal, as we see later) is 25.6 μs, what is the minimum size of the frame?

Solution
The frame transmission time is Tfr = 2 × Tp = 51.2 μs. This means, in the worst case, a station needs to transmit for a period of 51.2 μs to detect the collision. The minimum size of the frame is 10 Mbps × 51.2 μs = 512 bits or 64 bytes. This is actually the minimum size of the frame for Standard Ethernet.
</pre>

## Flowchart CSMA/CD
![image](https://user-images.githubusercontent.com/59027621/154421921-f5239f2d-c3b2-43a0-be8c-9977cc057049.png)

• The first difference is the addition of the persistence process. We need to sense the channel before we start sending the frame by using one of the persistence processes we discussed previously (nonpersistent, I-persistent, or p-persistent).

• The second difference is the frame transmission. In ALOHA, we first transmit the entire frame and then wait for an acknowledgment. In CSMA/CD, transmission and collision detection is a continuous process. We constantly monitor in order to detect one of two conditions: either transmission is finished or a collision is detected. Either event stops transmission.


## Energy Level:
![image](https://user-images.githubusercontent.com/59027621/154422210-f9c877d9-322b-4134-8d25-6c11de4e6b9a.png)

> We can say that the level of energy in a channel can have three values: zero, normal, and abnormal. At the zero level, the channel is idle. At the normal level, a station has successfully captured the channel and is sending its frame. At the abnormal level, there is a collision and the level of the energy is twice the normal level. A station that has a frame to send or is sending a frame needs to monitor the energy level to determine if the channel is idle, busy, or in collision mode.

# CSMA/CA - collision avoidance
- In CSMA/CA, the IFS can also be used to define the priority of a station or a frame.
- IFS - interframe space delay ghotay

> In CSMA/CA, if the station finds the channel busy, it does not restart the timer of the contention window;
it stops the timer and restarts it when the channel becomes idle.
Contention window - terminal random slot diye dibe


## Timing in CSMA/CA
![image](https://user-images.githubusercontent.com/59027621/154422247-8ff5495f-07ab-4d01-af0c-7e15fa23ed79.png)

## The algorithm of CSMA/CA is:
- When a frame is ready, the transmitting station checks whether the channel is idle or busy.
- If the channel is busy, the station waits until the channel becomes idle.
- If the channel is idle, the station waits for an Inter-frame gap (IFG) amount of time and then sends the frame.
- After sending the frame, it sets a timer.
- The station then waits for acknowledgement from the receiver. If it receives the acknowledgement before expiry of timer, it marks a successful transmission.
- Otherwise, it waits for a back-off time period and restarts the algorithm. (after checking if K>15 in diagram)
- Here K= backoff parameter

![image](https://user-images.githubusercontent.com/59027621/154422571-4efb46fb-b5e4-4a46-8a79-bd5d0d289068.png)


# Controlled Access
In controlled access, the stations consult one another to find which station has the right to send. A station cannot send unless it has been authorized by other stations. We discuss three popular controlled-access methods. Reservation, Polling and Token passing


1. Reservation:

- In the reservation method, a station needs to make a reservation before sending data. 
- Time is divided into intervals.
- In each interval, a reservation frame precedes the data frames sent in that interval.
- If there are N stations in the system, there are exactly N reservation mini slots in the reservation frame. 
- Each minislot belongs to a station. 
- When a station needs to send a data frame, it makes a reservation in its own minislot. 
- The stations that have made reservations can send their data frames after the reservation frame.

The following figure shows a situation with five stations and a five-minislot reservation frame. 
![image](https://user-images.githubusercontent.com/59027621/154422516-2389dbd8-6aa7-4448-8a21-0db64b3b86fe.png)

- In the first interval, only stations 1, 3, and 4 have made reservations.
- In the second interval, only station 1 has made a reservation.

2. Polling Method
- Polling works with topologies in which one device is designated as a primary station and the other devices are secondary stations. All data exchanges must be made through the primary device even when the ultimate destination is a secondary device.
- The primary device controls the link; the secondary devices follow its instructions.
- It is up to the primary device to determine which device is allowed to use the channel at a given time. 
- The primary device, therefore, is always the initiator of a session. Consider the following figure.
![image](https://user-images.githubusercontent.com/59027621/154422740-860021f4-310f-4551-bc63-1576fc6ffaae.png)

- If the primary wants to receive data, it asks the secondaries if they have anything to send, this is called poll function. 
- If the primary wants to send data, it tells the secondary to get ready to receive; this is called the select function.

## Select:
> The select function is used whenever the primary device has something to send. If it has something to send, the primary device sends it. It has to know whether the target device is prepared to receive or not. So the primary must alert the secondary to the upcoming transmission and wait for an acknowledgment of the secondary's ready status. Before sending data, the primary creates and transmits a select (SEL) frame, one field of which includes the address of the intended secondary.
 
## Poll:

> The poll function is used by the primary device to solicit transmissions from the secondary devices. 

> When the primary is ready to receive data, it must ask (poll) each device in turn if it has anything to send. When the first secondary is approached, it responds either with a NAK frame if it has nothing to send or with data (in the form of a data frame) if it does. If the response is negative (a NAK frame), then the primary polls the next secondary in the same manner until it finds one with data to send. When the response is positive (a data frame), the primary reads the frame and returns an acknowledgment (ACK frame), verifying its receipt.


3. Token Passing:
> In the token-passing method, the stations in a network are organized in a logical ring. In other words, for each station, there is a predecessor and a successor. The predecessor is the station which is logically before the station in the ring; the successor is the station which is after the station in the ring. The current station is the one that is accessing the channel now. The right to this access has been passed from the predecessor to the current station. The right will be passed to the successor when the current station has no more data to send.
 
> In this method, a special packet called a token circulates through the ring. The possession of the token gives the station the right to access the channel and send its data. When a station has some data to send, it waits until it receives the token from its predecessor. It then holds the token and sends its data. When the station has no more data to send, it releases the token, passing it to the next logical station in the ring. The station cannot send data until it receives the token again in the next round.
 
> Token management is needed for this access method.

> Stations must be limited in the time they can have possession of the token. The token must be monitored to ensure it has not been lost or destroyed. For example, if a station that is holding the token fails, the token will disappear from the network. 
Another function of token management is to assign priorities to the stations and to the types of data being transmitted. 
And finally, token management is needed to make low- priority stations release the token to high priority stations.

## Logical Ring:
> In a token-passing network, stations do not have to be physically connected in a ring; the ring can be a logical one. The following figure shows four different physical topologies that can create a logical ring.
 
## In the physical ring topology
- when a station sends the token to its successor, the token cannot be seen by other stations; the successor is the next one in line. This means that the token does not have to have the address of the next successor. The problem with this topology is that if one of the links-the medium between two adjacent stations fails, the whole system fails.

## The dual ring topology 
- uses a second (auxiliary) ring which operates in the reverse direction compared with the main ring. The second ring is for emergencies only. 
- If one of the links in the main ring fails, the system automatically combines the two rings to form a temporary ring. 
- After the failed link is restored, the auxiliary ring becomes idle again.

## In the bus ring topology, also called a token bus, 
- the stations are connected to a single cable called a bus. They, however, make a logical ring, because each station knows the address of its successor (and also predecessor for token management purposes). a station sends its data, releases the token, inserts the address of its successor in the token. 
- Only the station with the address matching the destination address of the token gets the token to access the shared media. 
- The Token Bus LAN, standardized by IEEE, uses this topology.

## In a star ring topology, the physical topology is a star. 
- There is a hub- acts as the connector. 
- The wiring inside the hub makes the ring
- The stations are connected to this ring through the two wire connections. 
- This topology makes the network less prone to failure because if a link goes down, it will be bypassed by the hub and the rest of the stations can operate. 
- Also adding and removing stations from the ring is easier. 
- This topology is still used in the Token Ring LAN designed by IBM.
