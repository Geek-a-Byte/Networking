# Networking
## Information Exchange Process

Information flow: The flow of information is from the top layer (usually application layer) down to the physical layer at the information source node; and from the physical layer up to the application later at the destination node as illustrated in the figure below. The information exchange process occurs between peer OSI layers. Each layer in the source system adds control information to data and each layer in the destination system analyzes and removes the control information from that data.

<img src="https://user-images.githubusercontent.com/59027621/148686943-31194bb8-0224-4d39-8854-a620c07a1665.gif" width="300px" height="300px"><img src="https://user-images.githubusercontent.com/59027621/148686980-b9c8bc3b-8835-4abd-b954-29409bded698.gif" width="500px" height="300px">

from figure 2
> System A has data from a software application to send to System B.

> the data is passed to the application layer. 

> The application layer in System A then adds any control information required by the peer layer in system B/ application layer in System B by prepending a header to the data. 

> The resulting information unit (a header and the data) is passed to the presentation layer, which prepends its own header containing control information intended for the presentation layer in System B. 

> The information unit grows in size as each layer prepends its own header (and in some cases a trailer) that contains control information to be used by its peer layer in System B. 

>  At the physical layer, the entire information unit is placed onto the network medium.

> The physical layer in System B receives the information unit and passes it to the data-link layer. The data link layer in System B then reads the control information contained in the header prepended by the data link layer in System A. The header is then removed, and the remainder of the information unit is passed to the network layer.

>  Each layer performs the same actions: 
- The layer reads the header from its peer layer 
- strips it off
- passes the remaining information unit to the next highest layer. 

> After the application layer performs these actions, the data is passed to the recipient software application in System B, in exactly the form in which it was transmitted by the application in System A.

| **Layer Name**                                               | **Work**                                                     |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| **physical layer** (hop to hop delivery of individual bits (1’s and 0’s) (Protocol Data Unit)) | This layer represents the **physical medium** which is carrying the **traffic** between two nodes.<br/>In the case of **Ethernet**, bits are transferred in the form of **electric pulses**.<br />In the case of **Wifi**, bits are transferred in the form of **radio waves**. <br />In the case of **Fiber**, bits are transferred in the form of **pulses of light**. <br />Aside from the physical cable, **Repeaters and Hubs** also operate at this layer. |
| **Data Link Layer**(hop to hop delivery of frames (Protocol Data Unit))<br/>responsible to organize bits into frames and provide them from hop-to-hop. | ****Layer 2 will group together 1’s and 0’s sent from the **physical layer into chunks known as Frames**.<br/>The **Network Interface Card (NIC)** that you plug your **Ethernet wire** into **handles the Layer 2 functionality**. It receives **signals** from the wire, and **transmits** signals on to the wire.<br />Your **WiFi NIC** works the same way, **receiving and transmitting radio waves** which are then interpreted as a series of **1’s and 0’s**.<br />There is an **addressing system** that exists at **Layer 2** known as the **Media Access Control address**, or MAC address. The MAC address uniquely **identifies each individual NIC**. Each NIC is **pre-configured** with a MAC address by the **manufacturer**; in fact, it is sometimes referred to as the **Burned In Address (BIA)**.<br />A **Switch** also operates at this layer. A Switch’s primary responsibility is to facilitate communication **within** **Networks**.**** |
| **Network layer**(host to host/end to end delivery of packets (Protocol Data Unit))<br/>responsible for the delivery of individual packets from source to destination. | **addressing scheme used** - **Internet Protocol address, or the IP Address. logically** identifies **every node** connected to the Internet. <br />It is considered **logical** because an **IP address is not a permanent identification of a computer.** Unlike the MAC address which is considered a physical address, the IP address is not burned into any computer hardware by the manufacturer.<br />Routers are Network Devices that operate at Layer 3 of the OSI model. **A Router’s primary responsibility is to facilitate communication** **between** **Networks**. As such, a Router creates a boundary between two networks. In order to communicate with any device not directly in your network, a router must be used. |
| **transport layer**(process to process or service to service delivery of message/segments (Protocol Data Unit) and error recovery.) | The **Transport layer** of the OSI model is responsible for **distinguishing network streams.**At any given time on a user’s computer there might be an **Internet browser** open, while **music is being streamed**, while a **messenger or chat app is running.** Each of these applications are **sending and receiving data** from the Internet, and all that data is arriving in the form of **1’s and 0’s** on to that computer’s NIC.Something has to exist in order to distinguish which **1’s and 0’s** belong to the messenger or the browser or the streaming music. That “something” is Layer 4:<img src="https://lh3.googleusercontent.com/FQH5li3eUb-hDIISfW0RUFCoxDT4WKLePSng6H8o19v7dFnW4d3zP2JrbSsDcoCBgbJKYCD12zk77TWVzKk5fc27SnFvu8uNjLxyvtgOSJyxW49VuHcSbXa2Cd2mH9ktHf45AATW" width="500px" height="300px"><br />**Layer 4 accomplishes this by using an addressing scheme known as Port Numbers**.Specifically, two methods of distinguishing network streams exist. They are known as the Transmission Control Protocol (TCP), or the User Datagram Protocol (UDP). |
| Session layerResponsible for<br />> **Dialog control and synchronization**.<br /> > To **establish, manage, synchronize and terminate sessions** between **end-user application processes**. | The main functions of the session layer are as follows −<br />**1. Dialog Control<br />**The session layer behaves as a **dialog controller**.<br />It allows **two communication machines** to enter into a dialog.<br />It permits communication in either **half-duplex (one way at a time)** or **full-duplex (two ways at a time)** mode of communication.<br />**2. Synchronization<br />**This layer permits a **process to add checkpoints** which are referred to as **synchronization points** into the **stream of data**.<br />If a system is sending a file of **2500** pages, It is advisable to add **checkpoints after every 100** to ensure that a **100-page unit** is successfully **received and acknowledged** independently.<br />In this case, if a **crash happens during transmission of page number 824;** then retransmission begins on page **801**. There is no need to retransmit pages 1 to 800 pages.<br />**3. Token Management**<br />This layer is also responsible for managing tokens through which it prevents two users attempting the same critical operation. |
| **presentation layer**                                       | responsible for **translation, compression, and encryption**.<br/>The presentation layer is located at the sixth level of the OSI model, it is responsible for the **delivery and formatting of information to the application layer for further processing or display**. This type of service is needed because different computer architectures use different data representations. In contrast to providing transparent data transport at the fifth level, the presentation layer handles all issues related to **data presentation and transport,** including **translation, encryption, and compression**. |
| **application layer**<br />responsible for providing services to the user.Allows access to network resources to application users. | The Application Layer interface directly interacts with applications and provides common web application services. |


<img src="https://user-images.githubusercontent.com/59027621/148687562-9c3302cb-def9-4507-b2d4-acd71f2a6520.png" width="400px" height="300px"><img src="https://user-images.githubusercontent.com/59027621/148687565-eecd21ed-89d6-4796-a765-39120ee5ac7e.png" width="500px" height="300px">






| **OSI Model**                                                | **TCP/IP model**                                             |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| It is developed by ISO (International Standard Organization) | It is developed by ARPANET (Advanced Research Project Agency Network). |
| OSI model provides a clear distinction between interfaces, services, and protocols. | TCP/IP doesn’t have any clear distinguishing points between services, interfaces, and protocols. |
| OSI refers to Open Systems Interconnection.                  | TCP refers to Transmission Control Protocol.                 |
| OSI uses the network layer to define routing standards and protocols. | TCP/IP uses only the Internet layer.                         |
| OSI follows a vertical approach.                             | TCP/IP follows a horizontal approach.                        |
| OSI layers have seven layers.                                | TCP/IP has four layers.                                      |
| OSI model, the transport layer is only connection-oriented.  | A layer of the TCP/IP model is both connection-oriented and connectionless. |
| In the OSI model, the data link layer and physical are separate layers. | In TCP, physical and data link are both combined as a single host-to-network layer. |
| Session and presentation layers are not a part of the TCP model. | There is no session and presentation layer in TCP model.     |
| The minimum size of the OSI header is 5 bytes.               | Minimum header size is 20 bytes.                             |

![osi vs tcp2](https://user-images.githubusercontent.com/59027621/148687936-b96520f5-c5d1-4729-bb54-b5b3c619dfa1.png)




## ADDRESSING

| Four levels of addresses | employing the TCP/IP protocols                               |
| ------------------------ | ------------------------------------------------------------ |
| physical                 | Underlying physical networks in the physical +data link layer. |
| logical                  | Ip and other protocols under network layer                   |
| port                     | SCTP, TCP, UDP protocols under transport layer               |
| specific                 | Processes under application layer                            |


![hrllo](https://user-images.githubusercontent.com/59027621/148687707-0633dcac-0847-4a80-90b4-c90172055dc3.jpg)


> A part of an internet with \two routers connecting three LANs. 
> Each device (computer or router) has a pair of addresses (logical and physical) for each connection. 
> In this case, each computer is connected to only one link and therefore has only one pair of addresses. 
> Each router, however, is connected to three networks (only two are shown in the figure). So each router has three pairs of addresses, one for each connection. 

> The computer with logical address A and physical address 10 needs to send a packet to the computer with logical address P and physical address 95. 

> The sender encapsulates its data in a packet at the network layer and adds two logical addresses (A and P). The network layer, however, needs to find the physical address of the next hop before the packet can be delivered.
 
> The network layer consults its routing table and finds the logical address of the next hop (router 1) to be F.
 
> Another protocol, Address Resolution Protocol (ARP) finds the physical address of router 1 (20) that corresponds to its logical address(F). Now the network layer passes this address to the data link layer, which in turn, encapsulates the packet with physical destination address 20 and physical source address 10. 

> Router 1 decapsulates the packet from the frame to read the logical destination address P. Since the logical destination address(P) does not match the router’s logical address(F), the router knows that the packet needs to be forwarded. 

> The router consults its routing table and ARP to find the physical destination address of the next hop (router 2), creates a new frame, encapsulates the packet, and sends it to router 2.

> Note the physical addresses in the frame. The source physical address changes from 10 to 99. The destination physical address changes from 20 (router 1 physical address) to 33 (router 2 physical address).
 
> The logical source and destination addresses must remain the same; otherwise the packet will be lost. At router 2 we have a similar scenario. The physical addresses are changed, and a new frame is sent to the destination computer. 

> When the frame reaches the destination, the packet is decapsulated. The destination logical address P matches the logical address of the computer. 

> The data are decapsulated from the packet and delivered to the upper layer. Note that although physical addresses will change from hop to hop, logical addresses remain the same from the source to destination.


![hrllo2](https://user-images.githubusercontent.com/59027621/148687740-748b8f06-7aa0-4351-b2d5-153939fb9289.jpg)

To show that data from process a needs to be delivered to process j, and not k, the transport layer encapsulates data from the application layer in a packet and adds two port addresses (a and j), source and destination. The packet from the transport layer is then encapsulated in another packet at the network layer with logical source and destination addresses (A and P). Finally, this packet is encapsulated in a frame with the physical source and destination addresses of the next hop. We have not shown the physical addresses because they change from hop to hop inside the cloud designated as the Internet. Note that although physical addresses change from hop to hop, logical and port addresses remain the same from the source to destination. 


A port address is a 16-bit address represented by one decimal number as shown.753—A port address is a 16-bit address represented by one decimal number as shown.

Service primitives :
Lcrsd




![service primitives](https://user-images.githubusercontent.com/59027621/148687797-1bcb2115-adbc-4701-ab34-b218798591ee.jpg)

![all layers](https://user-images.githubusercontent.com/59027621/148687958-92935135-abbb-4524-8bd0-fe0fdf8ab789.jpg)



Twisted pairs are made up of two insulated copper wires that are twisted together. The twisting is done to help cancel exterior electromagnetic interference. Crosstalk interference can come from other pairs within a cable


# MOBILE NETWORK

Cellular telephony is designed to provide communications between two moving units, called mobile stations (MSs), or one mobile unit and one stationary unit, often called a land unit. 

## Why Wireless is needed?
- Mobile communications is needed
- Terrain makes wired communication difficult
- Communications must be set up quickly
- Communications must be installed at low cost
- Same information must be broadcast to many locations

## Disadvantages of Wireless?
- More susceptible to interference, noise, signal loss, eavesdropping
- Generally lower data rate than wired
- Frequencies interfere in close proximity
- Less connection stability

## Cellular Network Organization

- Multiple low power transmitters (100w or less)
- Area divided into cells
- Each with own antenna
- Each with own range of frequencies
- Served by base station
- Transmitter, receiver, control unit
- Adjacent cells on different frequencies to avoid crosstalk

## Shape of Cells

#### Square
- Width d cell has four neighbors at distance d and four at distance  root(2)*d
- Better if all adjacent antennas equidistant
- Simplifies choosing and switching to new antenna

![square](https://user-images.githubusercontent.com/59027621/148688099-754a4a14-03f2-4654-8013-d83dfc0722ec.png)

#### Hexagon
- Provides equidistant antennas
- Radius defined as radius of circum-circle(jeita oi hexagon er shob vertex ke touch kore ekta circle)
- Distance from center to vertex equals length of side (polygon er ekta side er length)
- Distance between centers of cells radius R is root(3)* R (calc yourself)
- Not always precise hexagons
- Topographical limitations
- Local signal propagation conditions
- Location of antennas

![hexagonal](https://user-images.githubusercontent.com/59027621/148688104-f2a1eedf-6574-4d39-b099-7fd19738e917.png)
<pre>
Cell Splitting
Cell splitting is a means of increasing the capacity of a cellular system by subdividing or splitting cells into two or more smaller cells.
Cell splitting is the process of subdividing a congested cell into smaller cells, each with its own base station and a corresponding reduction in antenna height and transmitter power. Cell splitting increases the capacity of a cellular system since it increases the number of times that channels are reused. By defining new cells which have a smaller radius than the original cells and by installing these smaller cells (called microcells) between the existing cells, capacity increases due to the additional number of channels per unit area [8].
The consequence of the cell splitting is that the frequency assignment has to be done again, which affects the neighboring cells. It also increases the handoff rate because the cells are now smaller and a mobile is likely to cross cell boundaries more often compared with the case when the cells are big. Because of altered signaling conditions, this also affects the traffic in control channels [9]

What is Cell Splitting?
As the number of users increases, so does the interference, thereby affecting the capacity of the cellular system. One immediate solution to this problem is to subdivide a cell into two or more smaller cells. This method is called cell splitting. So, it is a process by which an area of a cell or an independent coverage area of a cellular system is divided into more cell areas, while each cell has its own base station and a subsequent cutback in antenna height and transmitter power.

What it basically does is – it splits the cells in areas of high usage into multiple smaller cells called microcells. So, it would require additional BSs to be established at the site of each new cell that has been installed in order to increase the capacity in congested areas. So, the purpose of cell splitting is to increase the capacity of a channel and improve the availability and reliability of cellular telephone networks, providing an increase in the degree of frequency reuse.

What is Cell Sectoring?
One way to increase the capacity of a cellular network to make up for the increasing number of subscribers is to replace the omni-directional antenna at the base station with a number of directional antennas. This method is called cell sectoring. It is a very common technique used in macro cellular systems to improve the performance against co-channel interference, wherein each cell is subdivided into radial sectors with directional BS antennas.

In practical terms, a number of sector-ed antennas are mounted on a single microwave tower located at the center of the cell, and a subsequent number of antennas are installed to cover the full 360 degrees of the cell. The number of cells in a specific cluster is decreased in cell sectoring, and the separation between co-channels is decreased. So, cell sectoring basically refers to the method of decreasing co-channel interference to increase the cellular system capacity by using directional antennas for each sector within a cell.

Overview of cellular system
Base station/BS/BTS(Base transceiver station)/tower/BSS
Phone is strongly connected to the tower of the cell, which it is currently in.
Whenever anyone calls, a request is sent through BTS to MTSO.
MTSO will broadcast the request msg to every cell
The called person’s cell tower will give a reply msg to MTSO
MTSO then would assign voice channels to both the caller and the called.
Thus the call establishes
MTSO will connect the caller if he goes to another cell while on calling. BTS will change automatically. It is soft handoff

Typical Call in SIngle MTSO area

Mobile unit initialization (monitor for strongest signal)
Scan and select the strongest setup control channel
Automatically selected BS(nearest although not alwaysc ) antenna of cell
Handshake to identify user and register location
Scan repeated to allow for movement - as change of cell occurs
Mobile unit monitors for pages
Mobile originated call (Request for connection)
Check whether the setup channel is free or not
Send number on pre selected channel
Paging
MTSO attempts to connect to mobile unit
Paging message sent to BSs depending on called mobile number
Paging signal transmitted on setup channel
Call accepted
Mobile unit recognizes the number on setup channel 
Responds to BS which sends response to MTSO
MTSO sets up circuit between calling and called BTSs
MTSO selects available traffic channel within the cells and notifies BSs
BSs notify mobile unit of the channel
Ongoing call
Voice and data exchanged through respective MTSO and BSc
Handoff
Mobile unit moves out of range of cell into range of another cell
Traffic channel changes to one assigned to new BS - without interruption of service to user

Call blocking
During mobile initiated call stage, if all traffic channels busy 
mobile tries again
After number of fails, busy tone returned.

Call termination
User hangs up
MTSO informed
Traffic channels at two BSs released

Call drop
BS cannot maintain required signal strength
Traffic channel dropped
MTSO informed


Calls to/from fixed and remote mobile subscriber
MTSO connects to PSTN
MTSO can connect mobile user and fixed subscriber via PSTN
MTSO can connect to remote MTSO via PSTN or via dedicated lines
Can connect mobile user in its area and remote mobile user

GSM Layout
MSC - Mobile Switching Center
BSC - Base Station Controller
BTS - Base transceiver 
VLR - Visitor Location Register
HLR - Home Location Register
AUC - Authentication Center
EIR - Equipment Identity Register



WAP
Wireless application protocol
Universal
Open standard
Provide mobile users access to information services, including internet and web
TCP/IP, HTTP, HTML, XML


## Trilateration

Trilateration involves measuring distances.
Trilateration Measures Distance, Not Angles
How does the GPS system pinpoint your location using trilateration?
Using a simple two-dimensional example, let’s imagine we have three GPS satellites each with a known position in space.

Really, all that satellites do is broadcast a signal for your GPS receiver to pick up with a specific time and distance.
For example, the first satellite broadcasts a signal that eventually hits your GPS receiver. We don’t know the angle, but we do know the distance. That’s why this distance forms a circle equal in all directions.
This means that your GPS position could be anywhere on this circle at this specific radius.

What happens when your GPS receives a second signal?
Again, this distance is equally broadcasted in all directions until it hits your GPS receiver. This means that the distance could be anywhere on that circle.
But this time, we have two known distances from two satellites. With two signals, the precise position could be any of the two points where the circles intersect.

Because we have a third satellite, it reveals your true location where all three circles intersect.
Using three distances, trilateration can pinpoint a precise location. Each satellite is at the center of a sphere and where they all intersect is the position of the GPS receiver.
As the position of the GPS receiver moves, the radius of each circle (distance) will also change.

But the reality is in our three-dimensional world that GPS satellites broadcast signals as a sphere.
Each satellite is at the center of a sphere.
Where all spheres intersect determines the position of the GPS receiver.

## Multiple Access

Multiple Access

Data link layer divided into two functionality-oriented sublayers
Data link control
Multiple access resolution

Amar shared channel ke multiple device er shathe connection dite hobe
Multiple access protocols:



Random access protocols (4 ta)
Aloha
CSMA
CSMA /CD
CSMA/CA
Controlled access protocols (RPT)
Reservation
Polling
Token passing
Channelization protocols(FTC)
FDMA
TDMA
CDMA

Random Access/Contention Method
No station is superior to another station
There is  no master and slave.
None is assigned the control over another
No station permits/does not permit another one to send
At each instance, a station which has data to send
Uses a procedure 
Defined by the protocol
To make a decision on whether or not to send.


Slide 12.5 PURE ALOHA
no sensor for collision
Sender sends frames, if a sent frame collides with other frames of another sender then no acknowledgement would be received for the collided frames, they need to be resent.
Only frame 1.1 and frame 3.2 will be sent successfully, so for them ack would be received
But for others there will be no acknowledgement
Procedure for pure ALOHA protocol

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
________________________________________________________
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





 We communicate with BTS while phone communication -> multiplexing
Then all BTS finally sends -> multiple access

Vulnerable time for pure ALOHA

The vulnerable time is in which there is a possibility of collision. We assume that the stations send fixed-length frames with each frame taking Tfr S to send. The following figure shows the vulnerable time for station A.

Station A sends a frame at time t. Now imagine station B has already sent a frame between t - Tfr and t. This leads to a collision between the frames from station A and station B. The end of B's frame collides with the beginning of A's frame. On the other hand, suppose that station C sends a frame between t and t + Tfr . Here, there is a collision between frames from station A and station C. The beginning of C's frame collides with the end of A's frame.

A pure ALOHA network transmits 200-bit frames on a shared channel of 200 kbps.What is the requirement to make this frame collision-free?
200*10^3 bits per 1 second
200 bits = 200/200*10^3 = 1 ms
Average frame transmission time Tfr= 1ms
vulnerable time is  2 × 1 ms = 2 ms.
Let's assume station A starts sending a frame at time t.
So station B cannot start sending a frame from t-1  to t
Or station C cannot start sending a frame from t to t+1
Or Station D cannot start sending a frame during 1 ms period when A is sending. 

The throughput for pure ALOHA is S = G × e^ −2G  .
The maximum throughput Smax = 0.184 when G= (1/2)

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

Slotted ALOHA
Pure ALOHA has a vulnerable time of 2 x Tfr. This is so because there is no rule that defines when the station can send. A station may send soon after another station has started or soon before another station has finished. Slotted ALOHA was invented to improve the efficiency of pure ALOHA.
In slotted ALOHA we divide the time into slots of Tfr s and force the station to send only at the beginning of the time slot.

Because a station is allowed to send only at the beginning of the synchronized time slot, if a station misses this moment, it must wait until the beginning of the next time slot. This means that the station which started at the beginning of this slot has already finished sending its frame. But, still there is the possibility of collision if two stations try to send at the beginning of the same time slot. However, the vulnerable time is now reduced to one-half, equal to Tfr. figure 14 

The throughput for slotted ALOHA is S = G × e^−G .
The maximum throughput Smax = 0.368 when G = 1.



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
CSMA - carrier sense multiple access
19 slide baad




Vulnerable Time:

The vulnerable time for CSMA is the propagation time Tp. This is the time needed for a signal to propagate from one end of the medium to the other. When a station sends a frame, and any other station tries to send a frame during this time, a collision will result. But if the first bit of the frame reaches the end of the medium, every station will already have heard the bit and will refrain from sending. The following figure shows the worst case. The leftmost station A sends a frame at time t1 which reaches the rightmost station D at time t1 + Tp. The gray area shows the vulnerable area in time and space.



What should a station do if the channel is busy? What should a station do if the channel is idle? Three methods have been devised to answer these questions: 
the 1-persistent method, 
the non persistent method, and 
the p-persistent method. 


The following figure shows the behavior of three persistence methods when a station finds a channel busy.

 

• 1-Persistent: In this method, after the station finds the line idle, it sends its frame immediately (with probability 1). This method has the highest chance of collision because two or more stations may find the line idle and send their frames immediately.

• Nonpersistent: a station that has a frame to send, senses the line. If the line is idle, it sends immediately. If the line is not idle, it waits a random amount of time and then senses the line again. The nonpersistent approach reduces the chance of collision because it is unlikely that two or more stations will wait the same amount of time and retry to send simultaneously. However, this method reduces the efficiency of the network because the medium remains idle when there may be stations with frames to send.

• P-Persistent: The p-persistent method is used if the channel has time slots with a slot duration >= maximum propagation time. The p-persistent approach combines the advantages of the other two strategies. 
reduces the chance of collision
improves efficiency. 

When the station finds the channel 
busy, it acts as 1 persistent method.
idle, it follows these steps:
1. With probability outcome<=p, the station can send its frame.
2. With probability outcome>p, the station waits for the beginning of the next time slot and checks the line again.
3. If the line is idle, it goes to step 1.
4. If the line is busy, it acts as though a collision has occurred and uses the back off procedure.

Carrier Sense Multiple Access with Collision Detection (CSMA/CD) 

The CSMA method does not specify the procedure following a collision. Carrier sense multiple access with collision detection (CSMA/CD) augments the algorithm to handle the collision.
In this method, a station monitors the medium after it sends a frame to see if the transmission was successful. If so, the station is finished. If, however, there is a collision, the frame is sent again.
 To better understand CSMA/CD, let us look at the first bits transmitted by the two stations A,C involved in the collision. Although each station continues to send bits in the frame until it detects the collision, we show what happens as the first bits collide. In the following Figure stations A and C are involved in the collision.


• At time t1, station A has executed its persistence procedure and starts sending the bits of its frame.  

 • At time t2, station C has not yet sensed the first bit sent by A. Station C executes its persistence procedure and starts sending the bits in its frame, which propagate both to the left and to the right.  

• The collision occurs sometime after time t2', Station C detects a collision at time t3 when it receives the first bit of A's frame. Station C immediately aborts transmission.

• Station A detects collision at time t4 when it receives the first bit of C's frame; it also immediately aborts transmission.

 • Looking at the figure, we see that A transmits for the duration t4 – t1. C transmits for the duration t3 - t2. The protocol to work, the length of any frame divided by the bit rate must be more than either of these durations. At time t4, the transmission of A’s frame, though incomplete, is aborted. At time t3, the transmission of C's frame, though incomplete, is aborted.

Minimum Time
For CSMA/CD to work, we need a restriction on the frame size. Before sending the last bit of the frame, the sending station must detect a collision, if any, and abort the transmission.
This is so because the station, once the entire frame is sent, does not keep a copy of the frame and does not monitor the line for collision detection. Therefore, the frame transmission time Tfr must be at least two times the maximum propagation time Tp.

To understand the reason, let us think about the worst-case scenario: the signal from the first takes time Tp to reach the second and the effect of the collision takes another time Tp to reach the first. So the requirement is that the first station must still be transmitting after 2Tp .

########## A network using CSMA/CD has a bandwidth of 10 Mbps. If the maximum propagation time (including the delays in the devices and ignoring the time needed to send a jamming signal, as we see later) is 25.6 μs, what is the minimum size of the frame?

Solution
The frame transmission time is Tfr = 2 × Tp = 51.2 μs. This means, in the worst case, a station needs to transmit for a period of 51.2 μs to detect the collision. The minimum size of the frame is 10 Mbps × 51.2 μs = 512 bits or 64 bytes. This is actually the minimum size of the frame for Standard Ethernet.


• The first difference is the addition of the persistence process. We need to sense the channel before we start sending the frame by using one of the persistence processes we discussed previously (nonpersistent, I-persistent, or p-persistent).

• The second difference is the frame transmission. In ALOHA, we first transmit the entire frame and then wait for an acknowledgment. In CSMA/CD, transmission and collision detection is a continuous process. We constantly monitor in order to detect one of two conditions: either transmission is finished or a collision is detected. Either event stops transmission.


Energy Level:

We can say that the level of energy in a channel can have three values: zero, normal, and abnormal. At the zero level, the channel is idle. At the normal level, a station has successfully captured the channel and is sending its frame. At the abnormal level, there is a collision and the level of the energy is twice the normal level. A station that has a frame to send or is sending a frame needs to monitor the energy level to determine if the channel is idle, busy, or in collision mode.



CSMA/CA - collision avoidance
In CSMA/CA, the IFS can also be used to define the priority of a station or a frame.
IFS - interframe space delay ghotay

In CSMA/CA, if the station finds the channel busy, it does not restart the timer of the contention window;
it stops the timer and restarts it when the channel becomes idle.
Contention window - terminal random slot diye dibe


Timing in CSMA/CA




The algorithm of CSMA/CA is:

When a frame is ready, the transmitting station checks whether the channel is idle or busy.

If the channel is busy, the station waits until the channel becomes idle.

If the channel is idle, the station waits for an Inter-frame gap (IFG) amount of time and then sends the frame.

After sending the frame, it sets a timer.

The station then waits for acknowledgement from the receiver. If it receives the acknowledgement before expiry of timer, it marks a successful transmission.

Otherwise, it waits for a back-off time period and restarts the algorithm. (after checking if K>15 in diagram)
Here K= backoff parameter


Controlled Access
In controlled access, the stations consult one another to find which station has the right to send. A station cannot send unless it has been authorized by other stations. We discuss three popular controlled-access methods. Reservation, Polling and Token passing


1. Reservation:

In the reservation method, 
a station needs to make a reservation before sending data. 
Time is divided into intervals.
In each interval, a reservation frame precedes the data frames sent in that interval.
If there are N stations in the system, there are exactly N reservation mini slots in the reservation frame. 
Each minislot belongs to a station. 
When a station needs to send a data frame, it makes a reservation in its own minislot. 
The stations that have made reservations can send their data frames after the reservation frame.
The following figure shows a situation with five stations and a five-minislot reservation frame. 
In the first interval, only stations 1, 3, and 4 have made reservations.
In the second interval, only station 1 has made a reservation.

2. Polling Method
Polling works with topologies in which one device is designated as a primary station and the other devices are secondary stations. All data exchanges must be made through the primary device even when the ultimate destination is a secondary device.
The primary device controls the link; 
the secondary devices follow its instructions.
It is up to the primary device to determine which device is allowed to use the channel at a given time. 
The primary device, therefore, is always the initiator of a session. Consider the following figure.

If the primary wants to receive data, it asks the secondaries if they have anything to send, this is called poll function. 
If the primary wants to send data, it tells the secondary to get ready to receive; this is called the select function.

Select:
The select function is used whenever the primary device has something to send. If it has something to send, the primary device sends it. It has to know whether the target device is prepared to receive or not. So the primary must alert the secondary to the upcoming transmission and wait for an acknowledgment of the secondary's ready status. Before sending data, the primary creates and transmits a select (SEL) frame, one field of which includes the address of the intended secondary.


Poll:

The poll function is used by the primary device to solicit transmissions from the secondary devices. 

When the primary is ready to receive data, it must ask (poll) each device in turn if it has anything to send. When the first secondary is approached, it responds either with a NAK frame if it has nothing to send or with data (in the form of a data frame) if it does. If the response is negative (a NAK frame), then the primary polls the next secondary in the same manner until it finds one with data to send. When the response is positive (a data frame), the primary reads the frame and returns an acknowledgment (ACK frame), verifying its receipt.


3. Token Passing:
In the token-passing method, the stations in a network are organized in a logical ring. In other words, for each station, there is a predecessor and a successor. The predecessor is the station which is logically before the station in the ring; the successor is the station which is after the station in the ring. The current station is the one that is accessing the channel now. The right to this access has been passed from the predecessor to the current station. The right will be passed to the successor when the current station has no more data to send.
 
In this method, a special packet called a token circulates through the ring. The possession of the token gives the station the right to access the channel and send its data. When a station has some data to send, it waits until it receives the token from its predecessor. It then holds the token and sends its data. When the station has no more data to send, it releases the token, passing it to the next logical station in the ring. The station cannot send data until it receives the token again in the next round.
 
Token management is needed for this access method.
Stations must be limited in the time they can have possession of the token. The token must be monitored to ensure it has not been lost or destroyed. For example, if a station that is holding the token fails, the token will disappear from the network. 
Another function of token management is to assign priorities to the stations and to the types of data being transmitted. 
And finally, token management is needed to make low- priority stations release the token to high priority stations.
Logical Ring:
In a token-passing network, stations do not have to be physically connected in a ring; the ring can be a logical one. The following figure shows four different physical topologies that can create a logical ring.
 
 
 
• In the physical ring topology
when a station sends the token to its successor, the token cannot be seen by other stations; the successor is the next one in line. This means that the token does not have to have the address of the next successor. The problem with this topology is that if one of the links-the medium between two adjacent stations fails, the whole system fails.
• The dual ring topology uses a second (auxiliary) ring which operates in the reverse direction compared with the main ring. The second ring is for emergencies only. 
If one of the links in the main ring fails, the system automatically combines the two rings to form a temporary ring. 
After the failed link is restored, the auxiliary ring becomes idle again.
• In the bus ring topology, also called a token bus, the stations are connected to a single cable called a bus. They, however, make a logical ring, because each station knows the address of its successor (and also predecessor for token management purposes). a station 
sends its data 
releases the token 
inserts the address of its successor in the token. 
Only the station with the address matching the destination address of the token gets the token to access the shared media. 
The Token Bus LAN, standardized by IEEE, uses this topology.
• In a star ring topology, the physical topology is a star. 
There is a hub- acts as the connector. 
The wiring inside the hub makes the ring
The stations are connected to this ring through the two wire connections. 
This topology makes the network less prone to failure because if a link goes down, it will be bypassed by the hub and the rest of the stations can operate. 
Also adding and removing stations from the ring is easier. 
This topology is still used in the Token Ring LAN designed by IBM.



## Error correction and detection

There are many reasons such as noise, cross-talk etc. which may help data to get corrupted during transmission.
Data-link layer uses some error control mechanism to ensure that frames (data bit streams) are transmitted with a certain level of accuracy.

Redundancy
Central concept to detect + correct errors
Extra bit/bits with data
Added by sender
Removed by receiver

Detection
Looking only if any error has occurred

Correction
More difficult than detection
Exact number of corrupted bits are required along their location

Forward Error Correction
Receiver tries to guess the msg from redundant bits
Possible when errors is small

Retransmission
Receiver detects the error and asks the sender to resend
Resending is repeated until the arrival of error-free msg

Parity Check for Detection 
One extra bit is sent along with the original bits to make the number of 1s either 
even in case of even parity, or 
odd in case of odd parity.
The sender while creating a frame counts the number of 1s in it. For example, if 
Even parity is used and the number of 1s is even then one bit with value 0 is added. 
This way the number of 1s remains even. 
If the number of 1s is odd, to make it even a bit with value 1 is added. 


The receiver simply counts the number of 1s in a frame. If the count of 1s is 
Even and even parity is used, the frame is considered to be not-corrupted and is accepted. 
If a single bit flips in transit, the receiver can detect it by counting the number of 1s. 
But when more than one bit are erroneous, then it is very hard for the receiver to detect the error.


Checksum for Detection 

Cyclic Redundancy Check (CRC) for Detection
This technique involves binary division of the data bits being sent. 
The divisor is generated using polynomials. 
The sender performs a division operation on the bits being sent and calculates the remainder. 
Before sending the actual bits, the sender adds the remainder at the end of the actual bits. 
Actual data bits plus the remainder is called a codeword. 

Block Coding
Redundancy is achieved through various coding schemes
Coding schemes may be block coding or convolution coding
In block coding, message is divided into blocks
Each blocks of k bits is called datawords
Redundant r bits are added with each block where n=k+r
Resulting n-bit blocks are called codewords
Block coding process is one-to-one

codeword = n bits
data bits = k bits
check bits = r bits. 
Then 
n = 2^r -1 and k = n-r

## Guided media/Wired Media/Bounded Media
provide a conduit from one device to another, 
twisted-pair cable, coaxial cable, and fiber-optic cable.
It is defined as the physical medium through which the signals are transmitted.

There are 3 major types of Guided Media: 
(i) Twisted Pair Cable – 
Twisted pair is a physical media made up of a pair of insulated copper wires twisted with each other.
The twisting is done to help cancel exterior electromagnetic interference.
Crosstalk interference can come from other pairs within a cable.
The degree of reduction in noise interference is determined by the no of turns/foot. Increasing the number of turns per foot decreases noise interference.

Twisted Pair is of two types: 
Unshielded Twisted Pair (UTP): 
consists of two insulated copper wires twisted around one another. 
This type of cable has the ability to block interference and 
does not depend on a physical shield for this purpose.
UTP performance : attenuation is inversely proportional to diameter
 
Shielded Twisted Pair (STP):
This type of cable consists of a special jacket (a copper braid covering or a foil shield) to block external interference. 

Coaxial Cable
outer plastic covering containing an insulation layer made of PVC/Teflon
2 parallel conductors each having a separate insulated protection cover. 
The coaxial cable transmits information in two modes: 
Baseband transmission: process of transmitting a single signal at high speed.
Broadband transmission: process of transmitting multiple signals simultaneously.

Optical Fiber Cable  
- uses electrical signals for communication.
- uses the concept of reflection of light through a core made up of glass or plastic.
- The core is surrounded by a less dense glass or plastic covering called the cladding.
- holds the optical fibers coated in plastic that are used to send the data by pulses of light.
- The plastic coating protects the optical fibers from heat, cold, electromagnetic interference from other types of wiring.

Basic elements of Fibre optic cable:

Core:
narrow strand of glass or plastic 
light transmission area 
The more the area of the core, the more light will be transmitted
 
Cladding:  
concentric layer of glass 
The main functionality is to provide the lower refractive index at the core interface to cause the reflection within the core so that the light waves are transmitted through the fiber.

Jacket: 
protective coating consisting of plastic 
preserves the fiber strength 
absorbs shock and 
Provides extra fiber protection.

Propagation modes of optical fiber:

1. On the basis of the Number of Modes:

(a). Single-mode fiber optic cable:
small diametral core that allows only one mode of light to propagate.
Because of this, the number of light reflections decreases, lowering attenuation and creating the ability for the signal to travel further. 
high cladding diameter (70um) and 
The difference between the refractive index of core and cladding is very small.
There is no dispersion i.e. no degradation of the signal during traveling through the fiber. 

(b). Multi-mode fiber:
has a large diametral core that allows multiple modes of light to propagate. 
Because of this, the number of light reflections increases, creating the ability for more data to pass through at a given time. 
There is signal degradation due to multimode dispersion. 
Because of the high dispersion and attenuation rate with this type of fiber, the quality of the signal is reduced over long distances. 
The diameter of the cladding is (70um). 
The relative refractive index difference is also greater than single mode fiber.
There are two categories on the basis of Multi-mode fiber i.e. Step Index Fiber and Graded Index Fiber. Basically these are categories under the types of optical fiber on the basis of Refractive Index.

2. On the basis of Refractive Index:

(a). Step-index optical fiber:
Due to its large core, some of the light rays that make up the digital pulse may travel a direct route, whereas others zigzag as they bounce off the cladding. These alternate paths cause the different groups of light rays, referred to as modes, to arrive separately at the receiving point. 
The pulse, an aggregate of different modes, begins to spread out, losing its well-defined shape. 
The need to leave spacing between pulses to prevent overlapping, limits the amount of information that can be sent. 
The refractive index of the core and cladding is constant. 
The rays of light propagate through it in the form of meridional rays which cross the fiber axis during every reflection at the core-cladding boundary.

(b). Graded index optical fiber:
Contains a core in which the refractive index decreases gradually from the center axis out toward the cladding. 
The higher refractive index at the center makes the light rays moving down the axis advance more slowly than those near the cladding.
Due to the graded index, light in the core curves helically rather than zigzag off the cladding, reducing its travel distance. 
The shortened path and the higher speed allow light at the periphery to arrive at a receiver at about the same time as the slow but straight rays in the core axis. 
The result: digital pulse suffers less dispersion. 
The cladding has a uniform refractive index. 
The light rays propagate through it in the form of skew rays or helical rays.


</pre>

