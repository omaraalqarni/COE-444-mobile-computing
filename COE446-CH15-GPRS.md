# CH 15: General Packet Radio Service (GPRS)

- GPRS is a service carrier that improved GSM wireless access to packet data networks
- Channels are taken from the available channels in the cell are three types:
  1. **Class A terminals**: operates GSM and GPRS
  2. **Class B terminals**: can monitor all services. But, operates GSM and GPRS
  3. **Class C terminals**: operates GPRS ONLY
- No store and forward services

------

### GSM Architecture

- **GPRS Support nodes (GSN)**: new network entities that has two types

  1. **Serving GPRS Support Node (SGSN):** is a router that is responsible for:
     1. Delivery of the packets to the MS. and from the MS to the internet
     2. Mobility and location management
     3. Authentication and billing
     4. location info of the users
  2. **Gateway GPRS Support Node (GGSN):** A logical interface to the internet
     - maintains routing information related to an MS, so that it can route packets to the SGSN servicing the MS
     - analyze the PDN address of the MS and converts it to the corresponding IMSI

  ------

  ### 2.5G Architecture 

![Screenshot 2022-12-28 at 2.13.37 AM](/Users/omar/Documents/221 Finals/COE446/assets/Screenshot 2022-12-28 at 2.13.37 AM.png)

![Screenshot 2022-12-28 at 2.14.06 AM](/Users/omar/Documents/221 Finals/COE446/assets/Screenshot 2022-12-28 at 2.14.06 AM.png)

------

### GPRS Architecture

- **Packet Control Unit (PCU)**: is the core unit to segregate between GSM and GPRS traffic

- **Border Gateway (BG)**: is a router which interfaces different operators GPRS networks
  - The connection between two border gateways is called GPRS tunnel.
  - It is more secure to transfer data between two operators using their own PLMN networks through a direct connection rather than via the public Internet which is less secure
  - For this both operators need to agree to provide such connectivity and terms and conditions including charging terms
  - **Charging Gateway(CG)**: to charge for the use of the network

------

##### Steps for the registeration of the Mobile Node

1. An MS must register itself to a GPRS network
2. GPRS attach
3. GPRS detach
   - Detach can be initialized by either the MS or the network

------

##### Session management

- After a successful attach, MS gets one or more of Packet Data Protocol **PDP** address. This address is unique for a single session
- **PDP address consists of:**
  1. PDP type, such as IPv4
  2. PDP address assigned to the MS
  3. Requested Qos
  4. address of the corresponding GGSN
- The PDP context is stored in the MS, SGSN and GGSN

------

##### PDP protocol allocation

Either

- Static: Assigned by the network operation of the user's home PLMN
- Dynamic: Assigned by corresponding GGSN

![Screenshot 2022-12-28 at 3.01.59 AM](/Users/omar/Documents/221 Finals/COE446/assets/Screenshot 2022-12-28 at 3.01.59 AM.png)



------



## Location Management 

- MS frequently sends location update to inform the SGSN
- The location update frequency is dependent on the state of the MS
- It depends on 3 things:
  1. **Idle state**: MS is not reachable. and all the PDP contexts are deleted
  2. **Standby state**: movement cross router area is updated to the SGSN but not to across the cells
  3. **Ready state**: every movement of the MS is told to the SGSN
- Routing area updates that are in the **STANDBY state** has two types:
  - **Intra-SGSN RA Update**: The SGSN already has the PDP context and user profile. a new **TMSI** is issued as part of routing arae update, “accept” and the HLR (GR) need not to be updated
  - **Inter-SGSN RA Update**: the new RA is serviced by a new SGSN. The new SGSN requests the old SGSN to send the PDP contexts of the MS. The new SGSN informs the home GGSN, the GR and other GGSNs about the user's new routing context

> **TMSI**: Temporary Mobile Subscriber Identity

------

### Handoff

1. When a MS changes a routing area (RA), it sends an RA update request containing the cell identity and the identity of previous routing area, to the new SGSN
2. If that is an intra-SGSN, routing area update is also possible when the same SGSN serves the new RA. The new SGSN asks the old SGSN to provide the routing context (GGSN address and tunneling information) of the MS
3. The new SGSN then updates the GGSN of the home network with the new SGSN address and new tunneling information

- The new SGSN also updates the HLR

- The HLR cancels the MT information context in the old SGSN and

  loads the subscriber data to the new SGSN

- The new SGSN acknowledges the MS

- The previous SGSN is requested to transmit undelivered data to the new SGSN

------

##### Multislot operation

GPRS allows a mobile to transmit data in up to 8 Packet Data Channels (PDCHs) (eight-slot operation)

- In comparison with single-slot GSM
  - Higher delay at higher load
  - Low blocking rate
  - Improved Throughput
