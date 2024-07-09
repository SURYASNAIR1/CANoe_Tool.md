# CANoe_Tool.md
- Software tool from vector.

- To test and analyse communication network of an ECU and the entire communication network.

- These tool support communications like CAN, Ethernet, FlexRay, LIN etc...

- Vector provides a network interface hardware which has a USB port connects to our computer and 
  other end CAN controller connects to the ECU.

- CANoe transmit and receive messages via USB serial communication with a network interface 
  hardware and that network interface put the msg on the bus receive a message or send it to 
  CANoe.

- We need license to CANoe software, network interface hardware and ECU to complete the set up.

- CANoe creates a virtual environment for creation of ECUs and simulate the network

- SUT: System Under Test
  
- Real-time Area: Just the simulation of test where we will have RX TX messages.

- Analysis Area: Customer will provide the log and we need to process the log and find out the 
  issues that actually occured in the vehicle area or the vehicle testing.

# Basic Terms in latest CANoe version
- Data base/ Data source: CANoe imports all databases (AUTOSAR, FIBEX) to a universak vector data model format.

- ECU/Node/ Participants: Can be used to group commn. end points that are logically associated 
  eg; because they belong to the same ECU, or because they are implemented by the same sw 
  component.

- Frame/PDU/Signal/ Communication object : Commn. object abstract any form of commn. Frames on 
  a particular bus system can still be analyzed.

- Interaction layer/Binding: This binding replaces the interaction layer concept. It links 
  abstrtact commn. objects to concrete bus systems and protocols.

- Simulation setup/ Communication setup: The commn. setup replaces the simulation setup as a 
  central config. hub for all comm. aspects.

- Endpoint: Until now end points of the commn. haven't been distinguished but grouped on ECU 
  level.

# CANoe Analysis
- Receiving data
  
Online or offline analysis is possible

   - Online data: We will be connected to the actual ECU and other parts are simulated in the 
    CANoe and datas are directly fed from the real bus or the real environment.

   - Offline data: will be the log files captured from the vehicle or given by the OEMs, 
     customer. We want to replay that, analyse that are called offline data.

- Processing data
  
Here we can use filters which can be used to specify which data are to be allowed abd which be explicitily filtered out. We can use CAPL scripting and triggering also.

- Representing data

   - Graphical representation of signal charts
 
   - Display or signal values
 
   - We have analysis window, trace window etc...
 
- Logging data

  The messages we want on bus we can log it using CANoe using several formats.

# Basic Feature set in CANoe
- Trace window

- Graphical window

- Simulation setup

- Measurement setup

- Testing in CANoe

- Packet Builder

- Replay Block

- Panel Creation

# Trace window (left top 1st button)
- We can see all bus traffics flowing once we ran the ECU.

- Details view: To display the packet/frame info with details view

- Statistic view: several events can be selected and examined statistically eg: difference in 
   time stamp of the signals (min, max and average stastical analysis)

- Difference view: for direct comparison of different events wg: comaprison of time stamps or 
  signal values

- Predefined filters: here you can activate the filters from a fixed set of events

- Analysis filter: here you can configure stop and pass filter

- Search Button: for performing different kinds of searches(pattern search, context search, 
  text search, condition search)

- Toggle Time mode: to change view between absolute and relative time mode

  - Absolute time mode: the time display will indicate the specific point in time at whcih the 
    message was rxvd.

  - Relative: indicate the time in relation to the preceding message.
 
- Toggle Display mode: To change the display in chronological and fixed position mode

  - Chronological mode: each new row is inserted below the prevoius row and when the window is 
    full it scrolls upward.

  - Fixed position mode: Each message is assigned to a specific line the first time it occurs, 
    and all further messages of the same line

- Activates/ Deactivates the analysis filter

# Graphical window

- In the graphical window symbols (signals, variables, and diagnostic parameters) are 
  displayed graphically in an XY diagram

-  Many functions are available to measure and evaluate the curves. You can read measurements 
   point values using the measurement cursors or difference cursors.

# Simulation window

- In the simulation setup, the overall system is displayed graphically with networks, devices 
  and all network nodes.

- The basis for a control unit simulation is the simulating of its full transmission behavoir

- A reaction, eg; to a particular message, must be programmed

# Testing in CANoe
- An ECU maybe tested by itself, or as a part of network consisting of various ECUs where the 
  object of testing is caleed a System Under Test(SUT)

- CANoe's option are available to the test modules/ test units eg: panels for user interaction 
  or writing of outputs to the write window

# Tool set in CANoe.
- Model Generation Wizard: Using model generation wizard you can automatically generate 
  configurations for remianing bus simulations based on network description.

- ASAP2 Studio Editor 1.8: Using ASAP2 udapter you can update the address and data type info. 
  in an ASAP2 file based on the entries of a Linker MAP file.

- CANdb++ Editor: Using CANdb++ you can create, visulaize and edit CAN databases.

- Vector Security Manager: We can manage and configure security profiles(eg; secoc, 
  diagnostics, authentication) for usage in vector tools.

# Basic CAPL useful keywords

1. To set and get value:
  
   - Node and signal ---> **setSignal**(LightSwich::OnOff,1.0) -form 1
 
   - Channel and signal ---> **setSignal**(CAN1::Status); - form 2 

   - data = **getSignal**(CAN::Status); ---> variable data will have the signal value
 
   - **setServiceSignal**(char qualifier [], double value); --> to get some ip signal value
 
   - **GetServiceSignal**(char qualifier [], diuble& value); --> to get some ip signal value

2. To stop CRC/SQC for fault generation:

   - **TestDisableCRCCalculation** (dbMessage aMessage); --> for CAN/Ethernet AUTOSAR PDU
 
   - **AREthSetProperty** (msg, "UpdateCRCAndLengthOn", 0); --> to stop someip CRC using 
      AUTOSAR Eth IL.dll file.

  - To react to a Message/PDU on Bus or to retrieve any message details from the Bus:
 
     - on Message CAN1.* ---> restrict to CAN
   
     - on ethernetPacket msgChannel1.* ---> for Ethernet packet
     
3. Time difference between 2 signals in script:

   -**timeDiff**
4. 





