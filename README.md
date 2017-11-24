# InfinityCushion
ProjectX Development of Infinity Cushion


PROJECT OVERVIEW

  What is Infinity Cushion?

The ‘Infinity Cushion’ embedded project is a device that provides valuable, meaningful analytical data to users based on input over periods of time. The device, implemented as a connected cushion, such that it is used when the user sits down over a given interval of time, uses a combination of sensors over various sensitivities (pizoelectric to force resistors), to analyze motion and deviations in vibrations over the study period for which the person is working. The results from the sensors in the system will be stored and analyzed against functions that are developed to match the greatest regression factor(ex: linear regression plot), and at a given period, when the user desires, providing a well-formed summary and report of their studying pattern and focus over their selected interval, enabling the user to optimize study focus. Such a summary will be deliverable in the form of a human-readable link and/or document. The intended user is a student/studying individual, and the inspiration behind the design’s model is a university student optimizing their studying abilities so that they are able to achieve the greatest level of focus while working at their desk. 
From a software perspective, the data provided from the sensors in the cushion/device as well as the simple input from the button to start/stop studying at the screen will be written to a file, which is then processed immediately by polling it along a predetermined interval that matches the average study period for the particular time. All sensor data will serve as a functional layer of files in our software structure. The data written to a file will then, according to our predetermined interval, be run against the aforementioned functions to signify when the greatest motion over a period of time occurred, periods at which no motion was detected, as well as other minor parameters and oddities based on reasonable assumptions (ex: small motions not considered, as within certain percentage error for general human motion). Such statistical analysis will be ported from the functional layer to the analytical layer of our software structure, and further be transferred as a last step, to our output layer. The statistical data will then be processed into an output file, which the user can access via I/O through either the web or USB and view their respective report, while being able to save their data for future reference. 

  Concept Goal, for Doing Everything

If the Infinity Cushion could go beyond its current state of development for our project, we imagine the product being implemented with higher-level software algorithms developed through health-based research to evaluate any individual’s sitting and focus conditions over a period of time. With the current hardware installed in our device, it is fully capable of having its data run through advanced software that would evaluate the fore mentioned conditions. Furthermore, as with the Internet of Things, we foresee this product being connected to the web in order to have its application monitored over a multi-use system, such as in a university, or a health center. Such data could be collected for statistical and analytical purposes, without the need for lengthy examinations to be conducted by physicians and/or professionals evaluating sitting/comfort levels while focusing. In retrospect, given increased time and resources, we would further enable the Infinity Cushion to have our data run against more advanced software algorithms, as well as connect it to the web for further statistical collaboration and monitoring. 

What Subset does Infinity Cushion Fulfill?

The Infinity Cushions fulfills the subset of a device used for optimization purposes, both for personal use and for use in medical settings. The primary system I/O of the device takes input from the user as they work, essentially functioning as a monitor, while simultaneously processing data over that same period of time. 













SYSTEM DESIGN 

 Overview

The Infinity Cushion’s overall system design can be broken down into the hardware and software level, each of which contain further layers of functions that work together to enable to unit to function as a whole. While designing our layers of hardware, we closely evaluated how the user would interact with the product, and what stress barriers were most susceptible to user interaction, hence identifying weak points in our initial design, which we were able to resolve. At the software level, our system is partitioned across multiple files, each of which serves as a vital component of the products effectiveness. At the core of our software is our data-processing, further which we move onto data output, sensor collaboration, as well as sensor input and user interface. While details of the Infinity Cushion’s software design will be analyzed below, an in-depth analysis of our software is included in the ‘Software’ section of the report. 

Hardware


•	Infinity Cushion
•	Pizoelectric Sensors
•	Force Sensor
•	Omega Connection Shell
•	External I/O Shell
 
Figure #1: Piezoelectric Sensor Individual & Force Sensor Schematic for Placement within Top-Layer of Cushion

As seen in the schematic above, the Infinity Cushion’s interior shell contains a series of circuitry components that are all implemented together within the top layer of the cushion’s interior padding. Enabling the sensors to function accurately while inside the cushion proved to be difficult to maintain without sufficient static protection. We custom-made and developed our own protecting shielding for our circuitry, printing it out through the use of 3-D Printers, to protect all of our circuitry from the effects of static charge caused by prolonged use of the cushion by the user. 

The cushion itself is a high-quality cushion developed by Upper Echelon Products, and was custom ordered to ensure proper access to the cushion’s interior. Furthermore, the cushion’s ergonomic design makes it comfortable to use, while also serving its technical functionality. 

The piezoelectric circuitry within the Infinity Cushion is connected, using Opamps, to the Omega board and requires its own custom soldering and power source, provided through a 9V battery. Four sensors are present within the cushion itself, positioned at symmetric positions relative to the surface area in order to result in the most accurate approximation of the motion of the user. A high-sensitivity force cushion is positioned at the center of the cushion to differentiate between a user positioned on the cushion, and an arbitrary object, which may have been placed on the seat – a realistic assumption for the use of a cushion on a seat. 

The Infinity Cushion further features an external shell, which holds both the Omega board as well as the input/output hardware for the product. The external shell is a plastic enclosure which is connected to the cushion through external wiring. Within the enclosure is the Omega board, as well as the Omega OLED Display and button, which is used to take input from the user to press the button at the point when they wish to begin studying. This display is used as a source of input confirmation for the user, indicating to them when the cushion is recording their performance, and when they wish to output their overall report. 

Software

Similar to the hardware structural design, the software design for the Infinity Cushion follows a multi-shell model as seen in Figure #2 in the ‘Software Design’ section. All of the code used for both data processing and I/O for the system was worked on collaboratively through the pull/merge process on GitHub, so that we were able to review and edit each other’s work in real-time. Further details regarding the specific software components and the structure of code within each respective program is included in the ‘Software Design’ section. 


  
•	Sensor Input File
•	Logging Files
•	Data Processing Files


The sensor input file is primarily responsible for taking sensor input, as it connects to the Omega board and saving such information over a buffer period – an application specific to our product’s functionality. Furthermore, in order to process our data as fast and simply as possible, the sensor input taken in from the five connected sensors is converted into a custom ‘char’, through which we have encoded our HIGH/LOW values for each sensor to be logged and processed. 

The software for the Infinity Cushion includes two separate logging files, for sensor logging and function logging, respectively. The purpose of the sensor logging is so that in case of error, or in that of a period of time, the status of each sensor is displayed so that it can be reference later for reviewing and/or debugging purposes. The function logging file is responsible for taking our custom ‘char’ from the sensor input, and processing it over a selected buffer period, which we have maximized in order to allow for the maximum rate of data processing. 

The data processing files for the Infinity Cushion serve the purpose of taking our inputted values and inputting them into our statistical functions, which develop historical records for the sensor values over time, as well as process a report for the data. We implement graphics through the use of data-displaying and use integration to find the area between curves for the average sensor values over time. 





SOFTWARE DESIGN


 



TESTING

Quality Assurance & Data Accuracy

Testing sensor input and especially calibrating output to have meaningful results proves to be an extremely challenging task for any physical ‘smart’ product. Likewise, the Infinity Cushion required extensive calibration and sensor testing for each individual component and facet of its use in order to result in accurate, meaningful data being outputted to the user. 

3-Way Communication Compatibility Assurance

Based on the previous project development experience of our team member, Jason Antao, we employed a 3-Way Communication Compatibility Assurance technique for all aspects of our project design. By deploying all software and schematics to all members of the group to see, and requiring confirmation from all members towards the accuracy of each component, we effectively prevented compatibility issues between our individual work from occurring later on in the build-stage. 



























SOURCE CODE

END OF OFFICIAL PROJECT PROPOSAL. 

Please note that this document is the Official Project Proposal for the ECE150-001 Final Project. All details and sources for parts have been cross-checked for greatest availability and lowest relative cost. All changes from the Initial Project Proposal to this document reflect a combination of the feedback we received via Dropbox as well as discussion with our group and Prof. Ward. 


