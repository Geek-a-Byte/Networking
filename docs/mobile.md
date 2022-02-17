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

# Cell Splitting
> Cell splitting is a means of increasing the capacity of a cellular system by subdividing or splitting cells into two or more smaller cells.

> Cell splitting is the process of subdividing a congested cell into smaller cells, each with its own base station and a corresponding reduction in antenna height and transmitter power. Cell splitting increases the capacity of a cellular system since it increases the number of times that channels are reused. By defining new cells which have a smaller radius than the original cells and by installing these smaller cells (called microcells) between the existing cells, capacity increases due to the additional number of channels per unit area [8].

> The consequence of the cell splitting is that the frequency assignment has to be done again, which affects the neighboring cells. It also increases the handoff rate because the cells are now smaller and a mobile is likely to cross cell boundaries more often compared with the case when the cells are big. Because of altered signaling conditions, this also affects the traffic in control channels [9]

# What is Cell Splitting?
> As the number of users increases, so does the interference, thereby affecting the capacity of the cellular system. One immediate solution to this problem is to subdivide a cell into two or more smaller cells. This method is called cell splitting. 

> So, it is a process by which an area of a cell or an independent coverage area of a cellular system is divided into more cell areas, while each cell has its own base station and a subsequent cutback in antenna height and transmitter power.

> What it basically does is – it splits the cells in areas of high usage into multiple smaller cells called microcells. So, it would require additional BSs to be established at the site of each new cell that has been installed in order to increase the capacity in congested areas. So, the purpose of cell splitting is to increase the capacity of a channel and improve the availability and reliability of cellular telephone networks, providing an increase in the degree of frequency reuse.

# What is Cell Sectoring?

> One way to increase the capacity of a cellular network to make up for the increasing number of subscribers is to replace the omni-directional antenna at the base station with a number of directional antennas. This method is called cell sectoring. It is a very common technique used in macro cellular systems to improve the performance against co-channel interference, wherein each cell is subdivided into radial sectors with directional BS antennas.

> In practical terms, a number of sector-ed antennas are mounted on a single microwave tower located at the center of the cell, and a subsequent number of antennas are installed to cover the full 360 degrees of the cell. The number of cells in a specific cluster is decreased in cell sectoring, and the separation between co-channels is decreased. So, cell sectoring basically refers to the method of decreasing co-channel interference to increase the cellular system capacity by using directional antennas for each sector within a cell.

# Overview of cellular system
- Base station/BS/BTS(Base transceiver station)/tower/BSS
- Phone is strongly connected to the tower of the cell, which it is currently in.
- Whenever anyone calls, a request is sent through BTS to MTSO.
- MTSO will broadcast the request msg to every cell
- The called person’s cell tower will give a reply msg to MTSO
- MTSO then would assign voice channels to both the caller and the called.
- Thus the call establishes
- MTSO will connect the caller if he goes to another cell while on calling. BTS will change automatically. It is soft handoff

# Typical Call in SIngle MTSO area
## Mobile unit initialization (monitor for strongest signal)
- Scan and select the strongest setup control channel
- Automatically selected BS(nearest although not alwaysc ) antenna of cell
- Handshake to identify user and register location
- Scan repeated to allow for movement - as change of cell occurs
- Mobile unit monitors for pages
- Mobile originated call (Request for connection)
- Check whether the setup channel is free or not
- Send number on pre selected channel

## Paging
- MTSO attempts to connect to mobile unit
- Paging message sent to BSs depending on called mobile number
- Paging signal transmitted on setup channel

## Call accepted
- Mobile unit recognizes the number on setup channel 
- Responds to BS which sends response to MTSO
- MTSO sets up circuit between calling and called BTSs
- MTSO selects available traffic channel within the cells and notifies BSs
- BSs notify mobile unit of the channel

## Ongoing call
- Voice and data exchanged through respective MTSO and BSc
- Handoff
- Mobile unit moves out of range of cell into range of another cell
- Traffic channel changes to one assigned to new BS - without interruption of service to user

## Call blocking
- During mobile initiated call stage, if all traffic channels busy 
- mobile tries again
- After number of fails, busy tone returned.

## Call termination
- User hangs up
- MTSO informed
- Traffic channels at two BSs released

## Call drop
- BS cannot maintain required signal strength
- Traffic channel dropped
- MTSO informed

## Calls to/from fixed and remote mobile subscriber
- MTSO connects to PSTN
- MTSO can connect mobile user and fixed subscriber via PSTN
- MTSO can connect to remote MTSO via PSTN or via dedicated lines
- Can connect mobile user in its area and remote mobile user

# GSM Layout
- MSC - Mobile Switching Center
- BSC - Base Station Controller
- BTS - Base transceiver 
- VLR - Visitor Location Register
- HLR - Home Location Register
- AUC - Authentication Center
- EIR - Equipment Identity Register

## WAP Wireless application protocol
- Universal
- Open standard
- Provide mobile users access to information services, including internet and web TCP/IP, HTTP, HTML, XML
