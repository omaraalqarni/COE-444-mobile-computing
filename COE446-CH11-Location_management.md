#  CH11: Location Management

-  Involves tracking of the location of MT

- If the MT moves during the course of a conversation, the step taken to handle the continuity of conversation is called handoff

- Routers will use the destination address to deliver the packet

- Locating the dest is done before the packets are sent to the dest

- Location management has three parts:

  1. Location updates

  2. Paging

  3. Location information dissemination

     

  ###### Location Updates: messages sent by the MT regarding its location to the fixed network

  - Everytime the MT makes an update to a new location. a database in the fixed part has to be updated.
  - updates are **periodic**, there will be some uncertainty in the location of MT

  

  ###### Paging: used by the network to deliver a message to the MT

  - The network have to page the MT in a group of cells
  - The paged terminal will respond through the point of access that is providing coverage in its cell, which will enable the network to locate accurately the MT.
  - To init paging, a calling or message will trigger a location request from a fixed network
  - The fixed network will access db that has the latest location of the MT. Then, generate paging request and deliver

  ###### 

  ###### Location info dissemination: the procedure that is required to store and distribute the location info related to the MT

  - Location management is the trade off between the cost, number, and the frequency of location updates and the paging cost
  - **Location update algorithms:**
    1. Static: The topology of the cellular network decides when to init the location updates
    2. Dynamic: the mobility of the user and the pattern of calls determines when to init location updates
  - **Most of the cellular networks use static location updates, which is a group of cell assigned a Location Area (LA) identifiers**
  - Each base station **BS** in the **LA** broadcasts this identification number periodically over control channels
  - MT is required to listen all the time to the control channel for the LA id
  - when LA changes, MT will make an update to the location by sending a message with new ID to the db containing its location
  - if there is an incoming message paging will be performed.
  - The MT usually responds and communication can be established
  - **Location update in GSM**: **LA** consists of a group of cells controlled by a Base Station Controller **BSC**
  - **MT performs location updates in these circumstances**:
    1. when powering up, to compare the **LA** ID
    2. when MT crosses the LA. 
    3. After a period of time determined by the network. since it is costly to have the MT in the LA for long time

  

  ###### Problem of Static LA identifier

  - If the MT is frequently switching between LAs. there will be a ping pong effect.

  ###### Solution:

  - have dwell timer that persists without location updates to ensure location updates are worthy
    - Types of the timers:
      1. Distance based: the location update is performed after crossing a certain number of cells
      2. Timer based: updated after a certain time has elapsed

------

##### Dynamic update algorithm

- dynamic location updates are either:

  - **state-based**: the MT makes the decision of when to update based on his **current state info**

    State information includes: time elapsed, distance traveled, number of LA crossed and calls recieved

    or

  -  **user-profile-based**: maintains a sequencial list of LAs that the MT may be located in at different points of time based on the history of the MT

------

###### Paging Schemes

- it is done by broadcasting a message in a cell or group of cells till it reaches the MT and gets a response

- paging only the cell that contains the MT reduces the cost

- It is impossible to locate the MT accurately when the cost has to be kept low

  **1. Blancket paging**: paging the MT in all the cells with LA simultaneously

  **2. Closest-Cell-First**: paging the cell where the MT was last seen, then paging the cells that are equidistant from this cell in each paging cycle

- Paging is performed according to the location updates

- A timer is used to tell if the MT is unreachable in a cycle

###### Paging Schemes performance:

- Blanket polling provides **the lowest delay at small loads**
- Sequencial paging provides **higher paging request rate when there are several incoming calls to an area**

------

###### Location Dissemination

- **Anchor:** is a fixed network with known location and address to handle incoming calls to MT and  can obtain info about him **(MT)**

- The info that the anchor has is the MT location and the routing info

- Multiple anchors are implemented to avoid congestion and call failures

- Every MT is associated with **home network** and **home db**

- **Home database** keeps track of the **MT's profile**

- the location of the MT is located by the visiting network where the MT is located

- Visiting db keeps track of the MT in its service area

- The home and visiting DBs communicate with each other to authenticate and update each other

  

**Location dissemination in GSM**

- the home and visiting DBs are called **Home Location Register (HLR)** and **Visiting Location Register (VLR)**
- When MT finds a change in LA ID, it sends a location update message through its BS to the MSC
- The MSC sends the VLR the location update. Which then contacts its HLR via location registeration message **only when it has no info about the MT**
- The HLR then authenticates the location, updates its own DB. and send to the VLR to cancel the registeration there



------

###### Handoff management

> Reminder: handoff is a way to handle the communication when the MT is moving

- Persisting with the BS as long as possible to avoid the ping pong effect
- if the handoff is delayed, a weak signal persists unnecessarily, to result a bad QoS
- handoff has multiple events that includes **rerouting the connection and reregistering to the new point of access **
- Handoff has an impacct on traffic matching and traffic density on a single BS
- Handoff has two steps:
  1. **Handoff decision and initiation**: determines if handoff is required
  2. the rest of the network is aware of the handoff. So, the connection is restructured to the new location
- **An anchor must be involved in the handoff similar to the location management**



**Issues with the handoff**

- two categories of issues in handoff management are:
  1. **Architectural issues:** related to the methodology, control, and software/hardware
  2. **Handoff decision time**: the types of metrics used by algorithms, and performance evaluation methodologies



- عاند تفكيرك

