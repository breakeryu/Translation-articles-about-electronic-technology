The hardware design techniques employed for an application will establish the base line immunity performance. The purpose of hardware techniques is to reduce the level or frequency content of immunity signals below that needed to cause performance degradation or long-term microcontroller (MCU) reliability problems.

Hardware techniques should be maximized to ensure desired [**electromagnetic compatibility (EMC)**](http://en.wikipedia.org/wiki/Electromagnetic_Compatibility)performance before attempting any software techniques. This is important because software techniques do not reduce the level of immunity signals to which the MCU is exposed ” they only reduce the impact of these signals on system operation. Even though the application performance may not be degraded, exposure to immunity signals can adversely affect long-term reliability.

In order to produce an application that meets both the mandated EMC requirements and minimizes cost, the design process must be both methodical and iterative. Rigorous system and PCB design method ology's are required to ensure quality and consistency in the design process. Without such methodologies, achieving EMC compliance will be accidental and unrepeatable. The design process must also be iterative to ensure the best possible system design and PCB layout at the lowest cost.

A design that minimizes cost cannot be completed properly in one pass ” regardless of the quality of personnel or tools. An EMC-compliant, low-cost application is the result of close and consistent collaboration between the EMC engineer and all other engineering disciplines (*i.e. “electrical engineers, mechanical engineers, PCB layout engineers, etc* ).

**Building Blocks of Transient Suppression and Control**
Components used to suppress or control transients can be grouped into two main categories: **1)** components that shunt transient currents (*voltage limiters* ), and **2)** components that block transient currents (*current limiters* ).

Note that depending on the rise time (*frequency bandwidth* ) of the transient, a component may function as either a shunt or a block. For instance, at a slow rise time (low frequency bandwidth) an inductor will have little impedance (a shunt). At faster rise times (higher frequency bandwidth), an inductor will have greater impedance (*ablock* ).

As a result, transient suppression components must be carefully selected for the optimal operating conditions. The actual performanceof the component in the application will depend on the radio frequency(RF) characteristics of the component and the physical geometry of theboard layout.

**Resistors.** A ***\*series resistor between two nodescan provide inexpensive and effective transient protection. Resistancecan be used to create low-pass filters and to decouple power domains.\****

In these applications, a series resistor is used to block or limittransients with frequency- independent resistance. Series resistance isprimarily suited to protecting digital or analog signals that carry lowcurrents and can accept a modest voltage drop (*across the seriesresistance* ). Typically, wire wound or carbon compositionresistors areused due to their ability to survive large transient currents.

Important characteristics to consider when selecting resistors arethe steady-state maximum power rating, maximum working voltage, anddielectric withstand voltage. The parasitic shunt capacitance andseries inductance of a resistor do not require special consideration intransient protection applications.

**Capacitors.** Capacitors are used in a variety of transient protection roles:bypassing or charge storage (*as alimiter of voltage variations* ) andpower decoupling (*as a shunt elementin a low-pass filter or a serieselement in a high-pass filter* ).

In either role, the capacitor can be used to effectively shunt fasttransients of limited energy, such as [**ESD**](http://en.wikipedia.org/wiki/Electrostatic_discharge) or [**EFT** .](http://en.wikipedia.org/wiki/Transient#Electrical_engineering) Capacitors are notpractical for shunting larger transient currents created by lightning,surge, or switching large, inductive loads.

Important characteristics to consider when selecting capacitors arethe maximum DC voltage rating, parasitic inductance, parasiticresistance, and over-voltage failure mechanism. When used in conditionswhere the maximum voltage rating may be exceeded, capacitors should beof the self-healing type, such as the metalized polyester filmcapacitor.

**Ferrite Beadsand Inductors.** Ferrite beads and inductors are used to decouplepower domains by creating [**low-pass filters**](http://en.wikipedia.org/wiki/Low-pass_filters). In theseapplications, a series ferrite bead or inductor is used to block orlimit transients with frequency-dependent impedance.

**Series inductance** isprimarily suited to protecting power lines and digital or analogsignals that carry high currents or cannot accept the voltage dropimposed by a series resistance. In general, ferrite beads are preferredbecause of their lossy nature.

As a result, introducing damaging resonances into the powerdistribution network is less likely. Important characteristics toconsider when selecting ferrite beads or inductors are the maximum DCcurrent rating, parasitic resistance, [**permeability**](http://en.wikipedia.org/wiki/Permeability_(electromagnetism)) of the ferritematerial, DC resistance, and [**parasitic inter-winding capacitance**](http://en.wikipedia.org/wiki/Parasitic_capacitance)in the case of wound inductors.

**Common-modeChokes** *.* Common-modechokes present a large inductance in series with common-mode sourcesand small or negligible inductance in series with differential-modesources. These inductances suppress common-mode signals while having anegligible effect on power frequency differential-mode signals. As aresult, the common-mode choke is one of the most effective transientprotection components.

When used with capacitors to form a low-pass filter, common-modechokes can be even more effective. Important characteristics toconsider when selecting a common-mode choke are the maximumdifferential-mode DC current rating, common-mode inductance,differential-mode inductance, and DC resistance.

**Filters** .Filters are used to achieve greater performance than single capacitiveor inductive components. Filters utilize multiple capacitive andinductive components that are specifically selected to achieve thedesired performance.

**TransientVoltage Suppressors.** The transient voltage suppressor (TVS) isused to control and limit the voltage developed across any two, ormore, terminals. The TVS accomplishes this task by clamping the voltagelevel and diverting transient currents from sensitive circuitry when atrigger voltage is reached.

TVS devices tend to have response times in inverse proportion totheir current handling capability. As a result, two devices (one withslow response and high current capability and one with fast responsebut low current capability) are often required to achieve the desiredprotection level.

TVS devices can be utilized to suppress transients on the AC mains,DC mains, and other power supply systems. They can also be used toclamp transient voltages generated by the switching of inductive loadswithin as application.

**Varistors.** The varistor (or voltage-variable resistor) is a non-linear,symmetrical, bipolar device that dissipates energy into a solid, bulkmaterial such as a metal oxide in the case of the common [**metal oxide varistor (MOV)**](http://en.wikipedia.org/wiki/Metal_oxide_varistor). As aresult, the varistor will effectively clamp both positive and negativehigh current transients.

The one issue with varistors is that the actual trigger voltage canvary widely from the specified value. Transient protection designsemploying varistors will need to accommodate this characteristic.Currently, MOVs are the best of the available non-linear devices forthe protection of electronics from transient voltages propagating onthe AC mains.

**Avalanche andZener Diodes.** The avalanche and zener diodes are silicon diodesintended for operation in the reverse breakdown mode. The primarydifference between these two diodes is the mechanism of reversebreakdown: avalanche or zener. Typically, the zener diodes have areverse breakdown voltage of less than 5V while diodes with reversebreakdown voltages of more than 8V use the avalanche mechanism.

**Implementing the Solution**
The available building blocks for transient suppression and controlmust be selected, assembled and implemented properly to ensure aneffective solution. The choice of building block(s) and implementationsmust be determined on a case-by-case basis to work under the applicableconstraints.

The constraints that most often limit or challenge the EMC designerinclude the functionality of the application, low-cost printed circuitboard technologies, packaging (industrial design), bill of materialslimitations, and the manufacturing process.

Now that we have a good understanding of the nature of the problemsfacing developers with respect to transient immunity and some of thebasic building blocks that can be used to enhance immunity, it is nowtime to apply this knowledge to the overall hardware and softwareaspects of your embedded design. That is the topic of Part 3 in thisseries.

<>To read Part 1 in this series, go to “[Definingthe problem](http://www.embedded.com/showArticle.jhtml?articleID=194300451).”<>
Next in Part 3: **System Power &Signal Entry considerations**

*Ross Carlton has specialized inall aspects of electromagnetic compatibility (EMC) since his graduationfrom Texas A&M University with a Bachelor of Science in ElectricalEngineering in 1985. He has been with [Freescale Semiconductor](http://www.freescale.com/) for thelast eight years where he has led the EMC design, test and support ofFreescale's 8, 16, and 32-bit microcontroller products. In addition,Ross represents the U.S. as a Technical Expert to [IEC](http://www.iec.org/)Subcommittee 47Aon integrated circuits where he is the project leader for IEC 61967-2,IEC 61967-3 and IEC 62132-2**.** Heis currentlyinvolved in developing transient immunity test methodologies forstandardization.*

*Theauthor would like to thank* *GregRacino as well as* *JohnSuchyta,* *8-Bit ApplicationsEngineer at FreescaleSemiconductor*  *for theirinputs and guidance. Their contributions were critical toensuring consistent and correct guidance.*

**References:**
**1.** Ross Carlton, Greg Racino,John Suchyta, Improving the Transient Immunity Performance ofMicrocontroller-based applications. [FreescaleApplication Note (AN) 2764)](http://www.freescale.com/files/microcontrollers/doc/app_note/AN2764.pdf).

**2.** IEC 61000-4-2,Electromagnetic compatibility (EMC) – Part 4-2: Testing and measurementtechniques – Electrostatic discharge immunity test, [InternationalElectrotechnical Commission](http://www.iec.ch/), 2001. 

**3.** IEC 61000-4-4,Electromagnetic Compatibility (EMC) – Part 4-4: Testing and measurementtechniques – Electrical fast transient/burst immunity test,International Electrotechnical Commission, 2001.

**4.** Ronald B. Standler,Protection of Electronic Circuits from Overvoltages, John Wiley &Sons, 1989, pp. 265-283.

**5.** Ken Kundert, “PowerSupply Noise Reduction”, [The Designer's Guide](http://www.designers-guide.com/) ,2004.

**6.** Larry D. Smith,”Decoupling Capacitor Calculations for CMOS Circuits”, [ElectricalPerformance of Electrical Packages Conference](http://ieeexplore.ieee.org/xpl/RecentIssue.jsp?punumber=6040), Monterey CA,November 1994, Pages 101-105.

**7.** Ronald B. Standler,Protection of Electronic Circuits from Overvoltages, John Wiley &Sons, 1989.

**8.** Clayton Paul, [Introductionto Electromagnetic Compatibility](http://www.wiley.com/WileyCDA/WileyTitle/productCd-0471758140.html), Wiley & Sons, 1992.

**9.** Bernard Keiser,Principles of Electromagnetic Compatibility, Artech House, 1987.

**10.** T.C. Lun, “Designing forBoard Level Electromagnetic Compatibility”, [MotorolaApplication Note (AN) 2321](http://www.freescale.com/files/microcontrollers/doc/app_note/AN2321.pdf).