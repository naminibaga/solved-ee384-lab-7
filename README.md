Download Link: https://assignmentchef.com/product/solved-ee384-lab-7
<br>
<strong>Materials: </strong>

<ul>

 <li>Time Domain P410 radar  MRM RET software</li>

 <li>USB 2.0 A to Micro-B cable.</li>

</ul>

<strong>Introduction: </strong>

In this laboratory you will be introduced to the Time Domain PulsON 410 ultra wideband (UWB) module.  This module can be used for communications and ranging, but for this experiment the P410 will be used as a radar device.

Radar is an electromagnetic phenomenon that is used for the detection and location of reflecting objects.  Various forms of radar are possible including frequency modulated continuous wave (FMCW), Doppler, pulsed, monostatic, bistatic, phased array, etc.  The device we will use is a monostatic pulsed radar.

The basic principle of pulsed radar will be illustrated in this lab.  A transmitter generates an electromagnetic pulse, which is radiated into space by the transmit antenna.  A portion of this radiated energy is intercepted by the target and reradiated in many directions.  Some of this reradiated energy is directed back towards the radar where it is collected by the receive antenna.  By processing these signals we can determine not only the distance or range to the target, but also other information about the target and its motion.

The most basic calculation made from a radar signal is the range to the target.  Suppose the time the signal was emitted from the antenna is known and the radar determines when the received pulse is detected.  The time difference  is the time in seconds it took the signal to travel from the radar to the target and return.  Since electromagnetic waves travel in space at a constant speed of <em>c</em>=3 × 10<sup>8</sup> m/s, then the distance to the target is

.

The P410 unit is different than typical radar systems.  It transmits a sequence of short duration, low duty cycle, low energy RF pulses.  Thousands of these very low energy pulses are processed coherently, which allows the energy to be effectively summed to produce a received waveform of sufficient signal energy, even though any single transmitted pulse energy is extremely small. Thus operation of the P410 is safe even in close contact with people in indoor environments.  In fact the radiated power of this radar is less than 50 microWatts (-13dBm) at full power, which is less than 1/2000 the maximum radiated power of a typical mobile phone, which may reach 125 milliWatts (+21dBm.)

The transmitted pulses are less than 1 nano-second in duration.  The short duration of the pulse gives a resulting waveform with 2.2 GHz of bandwidth with a center frequency of 4.2 GHz.  A sample pulse in both the time domain and frequency domain is shown below:




Systems characterized by having an RF bandwidth that is greater than 25% of its center frequency are considered Ultra Wideband (UWB) systems.  In contrast most data communication systems are narrowband – their time domain plot would look like a continuous sinusoid, and their frequency domain a spike at a single frequency. The large bandwidth/short pulse of UWB provides several useful properties for an indoor radar system including:

<ul>

 <li>Robust performance in the face of multipath. Narrowband (aka continuous wave) signals, often used for data communications such as WiFi, Bluetooth, Zigbee, etc., are unable to resolve multipath because their effective pulse lengths are simply too long, in essence overlapping direct and reflected long pulses to the extent they cannot be effectively differentiated.</li>

 <li>The ability for pulsed radars to reject clutter, attain high spatial resolution and discriminate between targets in close proximity to each other. The P410 offers a resolution of about 4 inches, which means that the radar can detect quite small targets and discriminate between targets that are close together.</li>

</ul>

We will be exploring these properties further during this course.

<strong>Experiment: </strong>

For this experiment we will be exploring the operation of the P410 unit, which is referred to as the Monostatic Radar Module (MRM) and the MRM Reconfiguration and Evaluation Tool (MRM RET) software.

<ol>

 <li>System power-up:

  <ol>

   <li>Connect the MRM to the computer with the USB cable.</li>

   <li>Apply power to the MRM with the provided power cord. Once the MRM is powered, the amber power LED on the bottom will turn on and remain lit with a steady glow. Approximately 10 seconds later the green status LED on the top will turn on and remain lit with a steady glow (this LED will toggle on/ off each time a scan is produced).</li>

  </ol></li>

 <li>Launch the MRM RET Application:

  <ol start="410">

   <li>Double click on the MRM RET icon. At this point, the MRM RET will set the USB button and indicate which COM port is connected to the P410. If the connection is successful, click the <strong>connect</strong> The main operating window will open. Several messages should appear in the status window at the bottom screen. The final line should read “Received MRM-GET-STATUSINFO-CONFIRM”.</li>

   <li>At this stage you have established that the PC and the MRM are communicating.</li>

  </ol></li>

 <li>Explore the MRM RET application:</li>

</ol>

Each MRM RET window is divided into two main areas, the tab control and action area. The bottom part of the window contains the action area which provides scrolling text indication of every message sent to and received from the MRM.  The tab control is the upper area and provides access to seven selectable tab pages. A brief description of each of them is provided below:

          <strong>Configuration Tab:</strong> This tab shows the MRM’s current configuration parameters. It provides the user with an easy method for reading and writing the seven essential configuration parameters. These parameters are:

<ul>

 <li><strong>Node ID</strong>: It is a three-digit number which represents the MRM’s ID. It is labeled on the RF shield below the PulsON logo on the MRM unit.</li>

 <li><strong>Pulse Integration Index</strong>: It is an integer representing the number of pulse frames that are integrated to produce a scan. Increasing the pulse integration index allows integrating more frames and thereby improves the received SNR. Each time the integration is doubled, the SNR of the received signal will improve by 3 dB at the cost of increasing the amount of time it takes to produce a scan.</li>

 <li><strong>Antenna Mode</strong>: The MRM RF frontend hardware can support two antenna configurations.</li>

 <li><strong>Code Channel</strong>: When operating two or more MRM’s in the same vicinity, the user must take care to insure that the units are operating on different code channels.</li>

</ul>

Code channels are numbered from 0-255.  Your unit will need to be set to the channel listed at your station so that all units in the room are on different channels.

<ul>

 <li><strong>Transmit Gain</strong>: When set to zero, the unit will transmit at the minimum power supported by the MRM.</li>

 <li><strong>Scan Start</strong>: This is the starting time of the first data point in the scan.</li>

 <li><strong>Scan Stop</strong>: This is the starting time of the last data point in the scan.</li>

 <li><strong>Message ID</strong>: This parameter provides tracking number for all messages.</li>

 <li><strong>Persist</strong>: If the persist flag is set to a 1, then any configuration change will be maintained through a power down. If set to 0 the changes are not maintained.  For this lab please adjust configuration settings with Persist=0, unless otherwise specified.</li>

 <li><strong>Get configuration</strong> and <strong>set configuration</strong> buttons are used to read and write the MRM configuration parameters.</li>

 <li>The <strong>load from file</strong>/ <strong>save to file</strong> buttons retrieves / stores the configuration parameters from / to files on the PC.  The factory default settings can be loaded from the file “MRM Factory Defaults.ret” located in the default MRM RET directory selected at installation.</li>

</ul>

<ul>

 <li><strong>Control Tab:</strong> This tab is used to initiate and stop radar scans. Radar scans can be started and stopped by clicking on either the <strong>start scanning</strong> or <strong>stop scanning</strong> When <strong>start scanning</strong> is selected, the message ID number will be set equal to the present message ID number and scanning will begin. By selecting the <strong>continuous</strong> option, the user is requesting that the scans be generated indefinitely at an interval defined in the contents of “Interval” box. By selecting the <strong>count</strong> option, the user is requesting that the MRM produce the number of scans indicated in the count field.</li>

 <li><strong>Scan Tab:</strong> This tab is used to view scan details as well as a plot of raw and processed data. The scan information boxes are

  <ul>

   <li>Time since last scan: This is the difference in time between the current scan and the previous one.</li>

   <li>First detection: This is an approximate measurement of the distance, in meters, from the scan start point to the first detection. This distance is computed using the following equation:</li>

  </ul></li>

</ul>

distance=(detection time (ps)-scan start (ps))×10<sup>−12</sup>(sec/ps)×3×10<sup>8</sup>(m/s)

<ul>

 <li>Display Options: The user can select which waveform scans are to be displayed by putting a check mark in the indicated box.</li>

 <li>Scan Data Plot: This is a plot of radar scan amplitude or reflectivity as a function of time. The horizontal scan uses the scan start value as the origin and sets that maximum so that it includes the scan stop value.</li>

</ul>




<ul>

 <li><strong>MRM Server Tab:</strong> The MRM server is a separate and independent Windows service that is installed when the MRM RET is installed. When MRM RET is connected to this service, the MRM server will intercept raw data being sent by the MRM to MRM RET, filter the data, and produce a detection list. If the MRM server task is not connected, then MRM RET will receive only the raw data scans. The objective of filtering and detection is to allow the user to sense the items or motions of interest. In this tab, if you check the <strong>Detection List</strong>, then the detection data will be passed from the MRM server to MRM RET, enabling the display of MRM detection list.</li>

</ul>

For the <strong>Threshold Mult</strong>, the value selected will set the sensitivity of the detector, where the value is between 1 and 255. Using small numbers will make the system very sensitive to changes.

<ul>

 <li><strong>Status Info Tab:</strong> This tab is used to report the MRM status information. It provides the uploaded software and hardware version numbers as well as the MRM board temperature.

  <ul>

   <li><strong>BIT</strong> stands for “Built-in Test” and will return “0” under normal operation. Otherwise, some sort of failure exists.</li>

   <li><strong>Temperature:</strong> This is the temperature of the sensor mounted on the PCB board.</li>

  </ul></li>

 <li><strong>Logging Tab:</strong> This supports data collection and post processing analysis. The log file is a comma-separated variable ASCII.csv text file. Log files will be stored in the directory indicated in the “Directory” field.</li>

 <li><strong>Sleep Mode Tab:</strong> This tab supports operation in various sleep modes.</li>

</ul>




<ol start="4">

 <li>Set the MRM configuration to the factory default values

  <ol>

   <li>Go to <strong>Load From File</strong> under the <strong>Configuration Tab</strong> and open <em>MRM Factory </em></li>

  </ol></li>

</ol>

<em>Defaults.ret</em> from the <em>Time DomainMRM Reconfig &amp; Eval Tool (RET)</em>  folder.

<ol>

 <li>Change <strong>Code Channel</strong> to the value indicated at your station (station number on your PC).</li>

 <li>Select <strong>Set Configuration</strong></li>

 <li>Select <strong>Get Configuration</strong> to determine the configuration of the MRM</li>

 <li>Record the values of the Pulse Integration Index, Transmit Gain, Scan Start, and Scan Stop</li>

</ol>

<ol start="5">

 <li>Start scanning

  <ol>

   <li>Go to the <strong>Control Tab</strong> and select <strong>Continuous</strong></li>

   <li>Press <strong>Start Scanning</strong></li>

  </ol></li>

 <li>Observe the scan

  <ol>

   <li>Go to the <strong>Scan Tab. </strong>MRM RET provides some signal processing capabilities, but to begin with, uncheck all but the <strong>Raw</strong> display option.</li>

   <li>Stand as far back from the MRM as possible and slowly walk towards the MRM<strong>. </strong>Observe the signal waveform as you do this.  Notice that as you get close to the MRM, the signal becomes saturated.  Record the peak signal value.</li>

   <li>Repeat this procedure with each of the display options checked.</li>

  </ol></li>

 <li>Reconfigure the MRM by setting the <strong>Transmit Gain</strong> to 0. Remember you must <strong>Set Configuration</strong> for the changes to take place on the MRM.  Every time a set configuration command is sent, the MRM automatically stops sending scans, so you will have to restart scanning.  Repeat step 6.</li>

 <li>Change the <strong>Pulse Integration Index</strong> to 8. Repeat step 6.  How does this change affect your signal strength?</li>

 <li>Log data to a file.

  <ol>

   <li>Under the <strong>Control Tab</strong>, <strong>Stop Scanning</strong></li>

   <li>Under the <strong>Logging Tab</strong>, select where to store your log file.</li>

   <li>Under the <strong>Control Tab</strong> set the <strong>Count</strong> to 10 to record 10 scans.</li>

   <li><strong>Start Scanning</strong>.</li>

   <li>Under the <strong>Logging Tab</strong>, <strong>Stop Logging</strong>.</li>

  </ol></li>

 <li>The log file is a .csv file and can be opened in Excel. Do this and notice that the first few rows of the file contain the configuration parameters.  The data values start about row 8 column Q.</li>

 <li>The log file can also be opened in Matlab which will allow us to process the data using</li>

</ol>

Matlab’s capabilities and tool boxes.

<ol>

 <li>Open <strong>m</strong> in Matlab. This m file prompts for the log file name, and then calls the function <strong>readMrmRetLog</strong> which reads the log file and parses the data into structures.</li>

 <li>Run this code and open your log file when prompted. The plot should be the same as seen in MRM RET, but with the x-axis in distance (meters) rather than time (picoseconds.)</li>

</ol>

<strong>Questions and Further Explorations: </strong>

<ol>

 <li>Consider Appendix C of the MRM RET Users Guide. Determine the power in Watts at the transmit antenna port for a transmit gain setting of 63 and of 0.</li>

 <li>In the MRMplotter.m code, explain how Rbin vector (the x-axis for your plots) was constructed. Where does Tbin come from? (Hint: see the MRM RET Users Guide)</li>

 <li>Modify MRMplotter.m to produce plots of the bandpass and motion filtered data.</li>

 <li>Modify MRMplotter.m to overlay all of the raw scans on one plot. Comment on the differences in the scans and what would cause the differences.</li>

</ol>

<strong>Turn in: </strong>

<strong>4e, 6b, 7, 8, Plots from MRM Plotter for raw, match filter and band filter data. </strong>


