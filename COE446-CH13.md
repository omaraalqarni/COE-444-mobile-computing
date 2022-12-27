# CH 13: Power control



- Power control enhances battery life of the MSs
- In order to reduce interference and maximize the battery life, there is a need for the wireless network to keep track of 
  - the radio resources
  - signal strength
  - and other associated information related to communication between an MS and neighboring BSs

### Power control definition 

###### It means the algorithms, protocols, and techniques that are employed to dynamically adjust the transmit power of both MSs and BSs

------

#### Open loop power control

- implemented in the uplink
- MT measures the quality of a refrence channel from the BS using RSS or BER
- If the RSS is above a certail threshold, the mobile will reduce power and vice versa

###### Disadvantage of open loop:

- Depends only on the MS **Mobile station**

- No feedback from BS **Base station**

- **Not accurate like Closed loop, but can react quickly when the signal fluctuates**

  

1.  the decision is based on the measurements of the downlink

2.  The channels are not related. **if the uplink channel has a good signal it doesn't mean that the downlink has a good signal too **

3.  There may be a delay before implementing the power control

4.  In TDMA (**Time division Multiple Access**), the MS reception and transmition times are different. and it will cause a time lag

   ------

   #### Closed loop power control

   - Adjust the signal strength in reverse channel based on a metric of performance
   - BS makes signal power adjustments and communicates to the MS on ctrl channel

   

   - fixes the quality concern by implementing a feedback mechanism between the BS and the MS
   - The BS measures the quality of the signal with the MS and sends through the downlink what actions the MS should do
   - Closed loop power ctrl can be used to ctrl the **transmit signal** of the BS 

   ------

   ##### Open loop power ctrl in **IS-95 CDMA**

   - power ctrl is very important because of the near-far effect

     WHY?

     - since all the voice channels occupy the same **time and frequency slots**, the recieved signals from all users must have the same RSS to be detected correctly.

       **Therefore, an MS that transmits at large power unnecessarily, will jam the signal of the other MSs **

   

   ###### How the open loop operates in IS-95 CDMA?

   1. A mobile terminal must use less power if it is close to the BS. Because its signal suffers a smaller path-loss. 

   2. mobile terminals that are further must use higher power to overcome signal loss

   3. After powerup, MS changes its transmit power based on the *total* power recieved from the BS on the forward channel

   4. BSs are not involved in the power ctrl mechanism

   5. The **pilot channel** on the forward path determines the transmit power of the MS

   6. **If the pilot channel transmits strong signal, the MS must transmit back a weak signal and vice versa**

      ------

   ##### Closed loop in GSM

   its steps:

   1. MS measures the RSS of up to 6 neighbouring BSs and transmits the data to its BTS **Base transceiver System**
   2. The BTS also, measures the RSS, signal quality and distance to each of the mobile terminal in its serving area
   3. From the measured values, BTS sends the MS through a five-bit field the minimum signal power it should use
   4. The power ctrl is performed in the steps of 2dB 

   ------

   - The open loop and closed loop are used to ctrl the transmit power on the BS and MS side using SSR or BER algos
   - **The goal of all power ctrl is to uniformly render the SIR of all users to a value, which is usually the maximum SIR in the system**
   - We optimize it using two approaches, **Centralized and distributed**

   ------

   ###### Centralized Power CTRL

   - A central controller in MSC or BSC has the full info of the radio links in the system
   - Thetransmit powers, received powers, SIRs, and BERs for all mobile terminal BS combinations are known to this centralized controller
   - It is hard to implement because the centralized controller has to dynamically keep track of all the links in the system and compute the transmit power for each MS

   ------

   ###### Distributed power CTRL

   - MS adjust its power in a discrete step
   - It is assumed that the MSs adjust their power synchronously
   - Power adjustments in the MSs result in the transmit powers iteratively converging to the optimum power control solution
   -  **In theory:** this should result in all the mobile terminals having the same SIR as in the CPC scheme after a number of adjustments
   - **In practice:** the adjustment to the power levels is also discrete (in steps of a few dB)

   ------

   ###### Power adjustment levels in wireless networks:

   - **In GSM**: each mobile terminal is required to increase/decrease its power level by 2dB, depending on the message sent by the BTS
   - **In CDMA**: mobile terminals can change power levels in 1dB steps
   - **In IS-95 standard**: the mobile terminal can change the power in 4dB steps in response to a command from the BSs in 20ms

   ------

   ##### Power consumption from most to least:

   1. Transmission process
   2. Reception process
   3. Standby process

   ------

   ##### Discontinuous Transmission and Repetition at Lower Transmit Powers

   ###### **Voice Activity Detector (VAD)**

   - In old telephones, some amount will be transmitted wether the person is speaking or not
   - **With VAD**, The MS can behave differently when no voice activity is detected
   - VAD does not transmit any signal when the person is not speaking 
   - a second alternative is to repeat data, but at a far lower signal power than usual
   - It ensures that data is transmitted all the time, but the total power consumed corresponds to only that data which was actually generated by speech

   

   ###### Problems with VAD

   - If it is not working correctly, it can decrease the quality of the voice signal and the conversation quality

   

   ###### Sleep Modes:

   

   

   