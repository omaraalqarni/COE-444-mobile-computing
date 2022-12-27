# CH 14: GSM



### GSM regestration steps:

1. When the MS is turned on, it needs to establish a new connection or possibly a new registeration
2. If the MS is not in the same location before, it needs to initiate a new registeration
3. In the first four steps, a radio channel is established for communication between MS and BSS
4. The next four steps, the NSS authenticates the MS
5. The next three steps, a Temporary Mobile Subscriber Identity **TMSI** is assigned, and adjustments are done on the VLR and HLR
6. The temporary radio channel is released. and transmission start over a traffic channel

![Screenshot 2022-12-28 at 1.07.41 AM](/Users/omar/Documents/221 Finals/COE446/assets/Screenshot 2022-12-28 at 1.07.41 AM.png)

------

### Mobile initiated call

1. The first five steps are the same as registeration
2. The next two steps are for encryption to protect against eavesdropping
3. The rest of the steps are similar to those in wired networks except that we have an additional traffic channel assignment procedure

![Screenshot 2022-12-28 at 1.14.20 AM](/Users/omar/Documents/221 Finals/COE446/assets/Screenshot 2022-12-28 at 1.14.20 AM.png)



![Screenshot 2022-12-28 at 1.15.51 AM](/Users/omar/Desktop/Screenshot 2022-12-28 at 1.15.51 AM.png)

​	

------

##### GSM Bands

It has:

1. 850 MHz, 900 MHz, 1800 MHz and 1900 MHz
2. Dual-band 850/900 MHz
3. Tri-Band 900/1800/1900 MHz
4. Quad-band 850/900/1800/1900 MHz

- 25 MHz for each direction divided into 124 channels of 200 kHz with 100 kHz band at the two edges
   - **124 channels * 200 kHz + 200 kHz = 25,000 kHz = 25 MHz**

- Each carrier supports 8 time slots for TDMA operation
- Data rate carrier is 270.833 𝑘𝑏𝑝𝑠 
- duration of each bit is ( 1/data rate ) = 3.69 𝜇𝑠
- The user transmission packet burst is fixed at
   577 𝜇𝑠, which accommodates information bits and a time gap between the packets for duration equivalent to 156.25 𝑏𝑖𝑡𝑠 times the bit duration of 3.69𝜇𝑠

------

#### Normal burst

![Screenshot 2022-12-28 at 1.29.47 AM](/Users/omar/Documents/221 Finals/COE446/assets/Screenshot 2022-12-28 at 1.29.47 AM.png)

- 3 bits (zeros) TBs at the beginning and the end of the packet **to cover the uncertainty period ramp on and off the radiated power and initiate the convolutional decoding of the data**

- Equivalent to 8.25 bits for GP
- Two sets of 58 bits (encrypted), includes two flags bits at the end of each part of the data
- 26 bits training sequence, is used to train the adaptive equalizer at the receiver
  - Because the channel behavior is constantly changing during the transmission of the packet, the most effective place for the training of the equalizer is in the middle of the burst

------

##### Frequency Correction Burst

![Screenshot 2022-12-28 at 1.31.32 AM](/Users/omar/Documents/221 Finals/COE446/assets/Screenshot 2022-12-28 at 1.31.32 AM.png)

- **TB:** three bits at the beginning and the end of the packet
- The rest of the packets contains all zeros to allow simple transmission of the carrier frequency without any modulated info
- Equivalent to 8.25 bits for GP
- The BS broadcast the **Fixed Bit** and MTs use it to synchronize with the master clock in the system

------

##### Syncronization Burst

![Screenshot 2022-12-28 at 1.35.25 AM](/Users/omar/Documents/221 Finals/COE446/assets/Screenshot 2022-12-28 at 1.35.25 AM.png)

- **TB:** three bits at the beginning and the end of the packet
- **Encrypted Bits:** 2*39 bits coded data are used for the specific task of identifying the network
- Equivalent to 8.25 bits for GP
- The BS broadcast the SB and MTs use it for initial training of the equalizer as well as in initial learning of the network identity and to synchronize time slots.

------

###### Random Access Burst

![Screenshot 2022-12-28 at 1.38.18 AM](/Users/omar/Documents/221 Finals/COE446/assets/Screenshot 2022-12-28 at 1.38.18 AM.png)

- Long start-up and synchronization sequence is used to initiate the equalizer
- Long GP to allow rough calculation of the distance of the MT from the BTS
- The RAB is used by MTs to access the BS as it registers to the network

------

### Interleaving traffic frames onto TDMA GSM frame in the air

- The user traffic data arrives in frames of length 456 bits

- They are interleaved into the transmitted normal bursts in blocks of 57 bits plus one flag bit

- The purpose of interleaving is to improve the performance for the users by distributing the effects of fade hits among several users

- The 456 bits are produced every 20 𝑚𝑠

  

