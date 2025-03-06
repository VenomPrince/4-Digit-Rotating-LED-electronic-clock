20 October, 2024 
Contents
List of abbreviations	2
1	Introduction	3
2	Project Overview	4
3	Materials and Methods	4
3.1	Prior knowledge	4
3.2	Chosen components	4
3.3	Proof of concept	4
4	Workflow	5
4.1	Early design modification	6
4.2	Multisim Design	7
4.3	Breadboard prototype	12
4.4	PCB Design	14
4.5	PCB Milling	16
4.6	Soldering	17
5	Results	19
6	Summary	19






Figures
Figure 1 The counter (74LS160), Decoder (74LS47) and the 7-segment chain.	7
Figure 2. The 555-Timer diagram.	8
Figure 3. The Led logic	9
Figure 4. The counter for the LEDs.	10
Figure 5. The final multisim schematic before PCB development.	11
Figure 6. Breadboard Working Prototype	12
Figure 7. PCB schematic in Ultiboard.	16
Figure 8. PCB Front After Soldering	18
Figure 9. PCB Back After Soldering	18

List of abbreviations 
PCB: 	Printed Circuit Board. 




 
Introduction
Digital clocks are important devices used in day-to-day applications, from domestic appliances to commercial systems. Nearly anything requiring time measurement can use a digital clock. They have become widely used due to their accurate timekeeping and are now virtually everywhere in modern technology. This thesis will explore and create a 4-digit LED clock with logic gates to act as an example of how basic electronic components work together so that we can construct practical devices which depend on accurate timing.

The purpose of this project is to build a 4-digit real time clock that counts seconds, minutes & hours and accurately displays the same on four-segment display. It does not use a microcontroller but is entirely implemented using digital logic gates to emphasize the fundamentals of digital circuit design. As such, the project seeks to examine time keeping as a concept in addition to signal processing and digital electronics generally.
This thesis will look at the workflow of the project, starting with initial design to prototyping and final PCB development. The article outlines each stage of the project's component by selection and schematic design through PCB layout. We will also walk through some of the problems we came during development, wiring issues and parts compatibility.
The project is useful in practical application since it carries out the designing of electronics and brings a new light on the ethics of logic gates in the field of technology. Outputs from this project will enable the creation of more advanced digital systems while stimulating new projects in electronic engineering.
 
Project Overview
This project focused on the design, development, and prototyping of a 4-digit rotating LED clock. The process included the creation of an electronic schematic, the design of a printed circuit board (PCB), the selection of components, and the subsequent assembly and testing of the system. The clock integrates real-time clock functionality and employs a 555 timer, 74LS counters, and a 7-segment LED display. Key challenges encountered during the project involved optimizing the design and ensuring accurate timekeeping.
Materials and Methods
Prior knowledge
The foundational knowledge applied in this project was primarily derived from previous studies and personal hobbies. Essential skills, including analog design, Multisim simulation, and PCB design, had been acquired prior to the commencement of the project.
Chosen components
An analog design approach was selected due to the prevalence of digital microcontroller-based variants of similar projects in real-world applications. The use of traditional analog components and logic gates provides a unique perspective, offering a refreshing alternative to an otherwise common design. 
Proof of concept
This project was intended to design and develop a fully functional 4-digit rotating LED electronic clock with key features such as the real-time clock, adjustable brightness, and temperature sensing. The key tasks involved: to build an electronics schematic, design a PCB, choose the appropriate components, and put an operating prototype together.

For this, the clock was supposed to show time through four 7-segment displays. It would also grant the user control over setting the time through direct hour and second settings using buttons. Other features included in the design were a rotating LED display for its unique visual depiction of time. For further enhancement of the created gadget, we intended to incorporate automatic brightness adjustment mechanisms depending on the conditions of lighting, as well as embed temperature-sensing capabilities.

It was to be designed based on a 555 timer for the clock pulses, a counter 74HC160N for the timekeeping functions, and a decoder 74LS47N to drive the 7-segment displays. Besides, we were to incorporate several ICs for performing the logic operations and some for control. Phases to be followed for this project would include: breadboard prototype, PCB design and milling, assembling and testing of the full system.

However, its development process was plagued by setbacks, mainly in designing and milling the PCB, necessitating successive redesigns and adjustments, as explained in further sections.
Workflow
In the following subchapters, each stage of the project development is explored in chronological order. The project consists of multiple separate development phases, starting from the design and ultimately ending with the finished product. 
Early design modification
The initial design of the clock was intended to feature a total of 60 LED indicators, with 12 LEDs representing the hours and 48 LEDs representing the minutes, similar to a traditional analog clock. However, upon evaluating the anticipated complexity of the circuit, it was decided to exclude the 48-minute LEDs. This modification was made to prevent the PCB from becoming excessively complex and costly to manufacture.
 
Multisim Design 
The design process started with the assessment of required components needed for the operational core logic. After the components were chosen, the next step was to build the circuit. 
The complexity of the ultimate design steered the design process to be created and tested in ‘blocks’ — e.g. 
First, the decade counters and their logic were implemented and tested with a virtual clock signal generator. Afterward, the working counters were connected to the 7-segment display decoders and then the decoders were connected to the actual 7-segment displays (Figure 1). 
 
Figure 1 The counter (74LS160), Decoder (74LS47) and the 7-segment chain.

Finally, the digital Multisim signal generator was replaced by an actual 555-timer block circuit (Figure 2). The resistors R1, R2 and capacitor C2 were used for setting the oscillation frequency of the 555-timer to around 1Hz. The C1 capacitor was added to provide extra stability to the system.
The formula used for the oscillation frequency calculation is: 

█(f=1.44/█((R_1+2R_2 ) C_█(1) )  #(1)#)

 
Figure 2. The 555-Timer diagram. 
 
When the counting logic was complete, a separate logic was implemented for the 12-hour indicator LEDs (as seen in Figure 3). 

 
Figure 3. The Led logic
 

Then another counter was made to count hours from 1 to 12, to which output’s the led logic gates were connected (Figure 4). The input signal was split from the hour indicator of the main circuit, ensuring the synchronous operation of the analog and digital displays. 

 
Figure 4. The counter for the LEDs.
 
The final circuit is shown in Figure 5. This marked the completion of the Multisim design phase and from here the project progressed to the PCB development. 

 
Figure 5. The final multisim schematic before PCB development.
 

Breadboard prototype
We successfully developed a breadboard prototype for the 4-digit 7-segment LED clock, featuring displays to show the time and buttons to adjust hours and seconds. The design initially used the 74LS160N as the counter but was switched to the 74HC160N due to performance and availability. A 555 timer provided clock pulses to the 74HC160N, which was connected to a 74LS47N decoder/driver to control the displays. Additional logic operations were handled by ICs like the 7404N and 7400N. Despite the dense wiring typical of breadboard prototypes, the core functionality of the clock worked as expected, though the planned 12 LEDs for extra features were not implemented at this stage.
Below are some images of the breadboard prototype, displaying the wiring
setup and how the 7-segment displays were connected:
 
Figure 6. Breadboard Working Prototype


  

PCB Design
The PCB for the 4-digit 7-segment LED clock was initially designed as a 4-layer variant in Ultiboard. However, due to limitations with the campus milling machine, the design had to be redone as a 2-layer board. After milling the first board, several issues arose that required a complete redesign. 
Upon receiving the first PCB, we found multiple critical flaws:
Trace Width Issues: The traces were much too narrow at places within the circuit, having made them fragile enough to break during its operation.
Incorrect Footprints for the 7-Segment Display: Certain component footprints, especially for the 7-segment displays, did not match the actual components, making it difficult to assemble the board correctly.
Via Hole Problems: Many via holes, which are crucial for connecting different layers, were either too small or incorrectly aligned. The copper plating inside these holes was rubbed off, making the connections between layers incomplete or non-functional.
These issues were further aggravated because the initial design needed to be downgraded from a 4-layer to a 2-layer PCB to accommodate the campus milling machine. This introduced extra challenges, particularly in routing signals and maintaining proper connections between components.
After identifying these problems, the task of redesigning the PCB was undertaken to ensure full compatibility with the milling machine. Although the design had already been converted to a 2-layer format, further modifications were necessary to address the issues. This included several major changes:
 

Changing Trace Widths: We adjusted the trace widths to meet the minimum requirement specified by the campus milling machine for the strongest, most reliable connections.
Changing Component Footprints: The footprints for the 7-segment display and other components were revised to align with the actual sizes of the parts.
Increasing Components Sizes: We manually resized 100 via holes to make them drill and plate correctly when milling.
Throughout the redesign, we encountered frequent crashes with Ultiboard, which slowed down progress. We had to redo many of the routing paths and manually adjust the footprints and via sizes multiple times. Despite these setbacks, we eventually produced a functional 2-layer PCB design suitable for milling.
Once the final adjustments were made, the redesigned PCB was successfully milled using the campus device and proved to be functional for the next phase of the project.
 
 Figure 7. PCB schematic in Ultiboard.



PCB Milling
Milling was conducted with the assistance of campus staff. Due to the milling machine's limitation to working with 2-layer boards, the original 4-layer design was adapted to fit these constraints.
Several challenges were encountered during the milling process. Although the final PCB design had been optimized, the machine's limitations affected the accuracy of certain elements, particularly the via holes. Some via holes were either misplaced or too small, and in many cases, the copper lining within these holes was insufficient. As a result, most connections had to be manually corrected during assembly, which further complicated the soldering process.


Soldering
The soldering process for the final version of the PCB presented several challenges that hindered the completion of the project. The complexity of routing contributed significantly to these difficulties, as the design had been downgraded from a 4-layer to a 2-layer PCB, leading to numerous connections that required soldering:
Excessive Via Holes: The design featured numerous via holes, and issues during the milling process caused some of these vias not to connect properly within the board. Manual soldering was necessary to bridge these connections, which further complicated the process and increased the risk of errors.
Small Via Holes: Several via holes were too small, resulting in damage to the internal copper lining during milling. Circuits associated with these vias were either weak or nonfunctional, necessitating the addition of external jumpers or manual re-soldering of specific points.
Narrow Trace Widths: The narrow traces on the PCB also posed challenges during soldering. Achieving precise soldering was critical, resulting in a time-consuming process that often required multiple attempts.
Due to these combined issues, the soldering process took significantly longer than anticipated and was prone to errors, compromising the structural reliability of the final circuit. Despite efforts to manually address these challenges, they ultimately hindered the project's completion.
 
Figure 8. PCB Front After Soldering
 
Figure 9. PCB Back After Soldering
 
Results
The project results ended in schedule and as planned in every area before the PCB printing and Soldering. The most time-consuming problems were encountered, and reiterations happened during the soldering stage, as the PCB had to basically be redesigned and reprinted and soldered. 
Ultimately the concrete results include a fully working clock assembled on a breadboard. A couple of PCBs were printed, but unfortunately neither of them worked as intended. 
Summary
The objective of this project was to develop a functional digital/analog clock utilizing 74LS components and logic gates.
The design process began with the creation of the logic and schematic entirely from scratch in Multisim, which was then transferred to Ultiboard for PCB design and fabrication. In parallel with the Multisim schematic, a breadboard prototype was developed to verify the circuit’s operation in a real-world environment.
A fully functional breadboard prototype was successfully completed. However, the PCB did not function as intended after assembly, and due to time constraints, further troubleshooting could not be conducted. Despite this setback, the project goals were achieved to a satisfactory extent, though the PCB-related tasks could have been executed more effectively.
The project provided valuable insight into the complexities and demands of PCB development, with lessons learned that will be beneficial for future endeavors. The clock is likely to be revisited in future projects, where the knowledge gained from this experience will be applied. Key takeaways include the importance of time allocation for each development phase, anticipation of potential challenges, and effective problem-solving strategies.
