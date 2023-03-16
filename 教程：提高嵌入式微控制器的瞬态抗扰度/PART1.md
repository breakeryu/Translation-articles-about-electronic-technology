

> When it comes to protecting their designs from a variety of transient electrical disturbances, developers of microcontroller-based embedded systems in consumer, industrial, and automotive electronics are caught between the rock and the hard place.
>
> 一直以来，在消费、工业和汽车电子产品中的嵌入式系统微控制器设计上，开发人员面临着的各种的瞬态电气干扰。



> On the one hand, more sophisticated and noise-sensitive microcontrollers (MCUs), with high integration, tighter process requirements and lower voltage requirements are moving into designs that are increasingly hazardous with respect to [**electromagnetic interference (EMI)** ](http://en.wikipedia.org/wiki/Radio_frequency_interference)and [**electrostatic discharge (ESD** )](http://en.wikipedia.org/wiki/Electrostatic_discharge) .
>
> 一方面，更加精密和对噪声敏感，同时有着更高的集成度、更严格的工艺要求和更低的电压要求的微控制器(MCU)被使用到设计中去。这些设计往往是伴随着更危险的电磁干扰(EMI)和静电放电(ESD)。



> On the other, increased competition, as well as market regulatory pressures, are forcing original equipment manufacturers (OEMs) to reduce the cost of their products. As a result of this focus on cost control, implementing the necessary transient immunity protections to prevent application malfunction due to transients on power and signal lines is becoming ever more challenging.
>
> 另一方面，竞争的加剧以及市场监管压力，正迫使设备制造商(OEMs)去降低他们的产品成本。由于对成本控制的结果，防止电源和信号线上瞬态影响导致的应用故障，以实现必要的瞬态保护就变得越来越具有挑战性。



> The impact of increasing MCU sensitivity and low-cost application design is being felt in all markets: consumer, industrial, automotive, etc.  While there are significant differences in the design and use of products for these markets, the susceptibilities induced in all microcontroller-based applications are essentially the same. Typical susceptibilities include unexpected state changes on input pins (reset,interrupt request, or general purpose inputs), corruption of on-chip clock signals, or even damage to the silicon.
>
> 由于MCU的高灵敏度和低成本应用设计需求，在各种市场中都产生了影响，比如：消费、工业、汽车市场。虽然这些市场的产品在设计和使用上存在显著差异，但在所有微控制器的应用中的干扰敏感性上基本是相同的（意思是，使用微控制器设计的应用易受到外部干扰）。典型的干扰因素包括输入引脚(复位引脚、中断请求引脚或通用输入引脚)的意外状态变化、片上时钟信号的损坏，甚至是硅的损坏。

# **The pervasive impact of EMI and ESD transients**

**普遍的EMI和ESD影响**



> In **consumer electronics applications** ,transient immunity is a challenge for both battery powered and AC mains powered products. 
>
> 在消费电子产品中，瞬态抗扰度是电池供电和交流电源供电产品都面临的挑战。
>
> Battery powered products such as keyboards, mice, [remote keyless entry systems](https://www.nxp.com.cn/video/remote-keyless-entry-systems-rke-overview:WBNR-RKE-OVERVIEW-VID), and remote controls are challenged by ensuring the immunity of the application to ESD transients.
>
> 电池供电的产品，如键盘、鼠标、远程无线输入系统和遥控器，面临着这样的挑战：需要确保产品具备对瞬态ESD的免疫能力。



> For example, an ESD directly to the product or to a nearby coupling plane has been seen to assert the reset function of an MCU by temporarily changing the state of the RESET pin.
>
> 例如，一次直接通到产品上或到附近耦合平面上的静电放电过程，可以看到短暂变化的RESET引脚的状态，这说明，静电放电影响了MCU的复位功能。
>
>  In these cases, there is typically a long trace between the RESET pin and an in-circuit programming header that serves as an antenna to receive the ESD energy and couple it to the RESET pin.
>
> 在这些情况下，RESET引脚和内部编程接口之间的长长的导线就作为天线接收了ESD能量并将其耦合到RESET引脚。



> Likewise, an [**electrical fast transient (EFT)**](https://en.wikipedia.org/wiki/Transient_response) injected on the AC power plug of an AC mains powered product can couple to a reset trace by either radiation or conduction resulting in susceptibility.
>
> 同样，交流市电供电产品的电源输入导致的[**电气快速瞬态(EFT)**](https://en.wikipedia.org/wiki/Transient_response)可以通过辐射或传导耦合到复位导线上，从而导致干扰。
>
>  Self-compatibility is also of great concern where the product contains inductive loads (motors,compressors, etc) that are switched.
>
> 当产品包含开关电感负载(电机、压缩机等)时，自兼容性也是非常重要的。



> Since electronics for **industrial applications** is typically powered only from the AC mains, they have similar issues to those of consumer electronics products powered from the AC mains. 
>
> 由于工业应用的电子产品通常仅由交流电源供电，因此它们与由交流电源供电的消费电子产品有相似的问题。
>
> However, these issues are typically more severe than in residential applications due to the presence of heavy machinery(large inductive loads) switching on and off the power distribution system for the factory.
>
> 然而，这些问题通常比在民用中更为严重，因为工厂需要重型机械(大型感性负载)来开启和关闭他们的配电系统。



> The transient immunity issues in **automotive electronics** applications are also similar to consumer electronics applications except for being powered by DC mains. 
>
> 在汽车电子应用中的瞬态抗扰度问题也和在消费类电子应用是相似的，不包括DC供电的应用。
>
> This is because automobiles contain numerous switching inductive loads(alternator, compressor, solenoids, etc) that put transients on the DC mains. 
>
> 这是因为汽车包含许多开关感性负载(交流发电机、压缩机、螺线管等)，这些负载会在DC电源上产生瞬变。
>
> In addition, automotive applications are becoming increasing concerned with ESD.
>
> 此外，汽车应用正越来越关注ESD。



> For example, a new application for MCUs is in remote [tire pressure monitoring systems (TPMS)](https://en.wikipedia.org/wiki/Tire-pressure_monitoring_system). 
>
> 例如，MCU的一个新应用是远程轮胎压力监测系统(TPMS)。
>
> This is a novel innovation but introduces new ESD immunity issues. 
>
> 这是一项新颖的创新，但也带来了新的ESD抗扰问题。
>
> ESD near a TPMS device has been seen to cause both upset and damage. 
>
> TPMS设备附近的ESD会导致干扰和损坏。
>
> Since it is almost impossible to ensure that an automotive technician uses and ESD wrist strap, TPMS and other automotive electronics can easily be exposed to ESD in the ±25kV range during maintenance operations.
>
> 由于几乎不可能确保汽车技术人员使用ESD腕带，因此在维护操作期间，TPMS和其他汽车电子设备很容易暴露在±25kV范围内的ESD中。
>
> For reference, commercial electronics are typically required to be immune to ESD in the ±8kV range.
>
> 作为参考，商用电子设备通常要求在±8kV范围内不受ESD影响。



> To meet the transient immunity challenge as traditional power supply designs and EMI controls are sacrificed for lower cost solutions, the embedded systems designers must employ new techniques and processes to meet the applicable regulatory and market requirements for **[electromagnetic compatibility (EMC)](http://en.wikipedia.org/wiki/Electromagnetic_compatibility)** .
>
> 为了满足抗瞬态扰性的需求，传统的电源设计和EMI控制就牺牲了低成本的解决方案，嵌入式系统设计人员必须采用新的技术和工艺，以满足适用的法规和市场要求的**[电磁兼容性(EMC) ](http://en.wikipedia.org/wiki/Electromagnetic_compatibility)**。



> Achieving transient immunity in a low-cost embedded application can be a difficult and time-consuming process, particularly if not addressed early and often in the design of an application. 
>
> 在低成本嵌入式应用中实现抗瞬态扰性可能是一个困难且耗时的过程，特别是如果在应用设计中没有及早并经常解决这个问题的话。
>
> In addition, making the mistake of not addressing transient protection as close to the AC or DC mains as possible will also adversely affect the complexity of EMC protection.
>
> 此外，产生在尽量靠近交流或直流电源的位置未能够解决瞬态扰性保护的错误，也会进一步对EMC保护的复杂性产生不利的影响。
>
>  The initial design of an embedded application should maximize EMC so that design budgets and production schedules are met without delays at the EMC compliance stage.
>
> 嵌入式应用的初始设计应该最大限度地提高EMC，以便设计预算和生产计划相适应，而不会推迟EMC指标的完成。



However, there are practical hardware design techniques that can be employed to provide cost-effective protection for EFT,ESD and other power line or signal line transients of short duration. In addition, the EFT or ESD performance of a system can be dramatically affected by the choices made in the software architecture and application functionality.

Software techniques should be viewed as a necessary but last line of defense against adverse system reaction to EFT or ESD events. The software can affect how the system will react to a disturbance if it reaches the MCU but the hardware PCB board and system hardware design should diminish or eliminate the disturbance before it reaches the MCU.

Prioritizing the control of transient voltages and currents with hardware techniques is also important from the aspect of minimizing exposure of electrical and electronic components to over-specification conditions that could result in accelerated failure rates or long-term degradation.

# **Defining the problem**

Low cost, microcontroller-based embedded applications are particularly susceptible to performance degradation during ESD and EFT events. This sensitivity to fast rise time transients is to be expected, even for microcontrollers running at relatively low clock frequencies.

This sensitivity is due to the process technologies employed. Today's semiconductor process technologies for low-cost, 8-bit and16-bit MCUs implement transistor gate lengths in the 0.65m to 0.25m range. These gate lengths are capable of generating and responding to signals with rise times in the sub-nanosecond range (or an equivalent bandwidth of greater than 300MHz). As a result, an MCU is quite capable of responding to ESD or EFT signals injected onto its pins.

In addition to the process technology, MCU performance in the presence of an ESD or EFT event is affected by the design of the IC and its package, the design of the printed circuit board (PCB), the software running on the MCU, the design of the system, and the characteristics of the ESD or EFT waveform when it reaches the MCU. The relative impact of each performance driver (where to focus effort for maximum effect) is shown in the pie chart in **Figure 1, below.**

![f1](https://img2023.cnblogs.com/blog/1423856/202303/1423856-20230315214931805-918401623.png)

Several facets of IC design other than physical gate length can affect MCU performance during transients. These include the composition of ESD suppression devices on input/output (I/O) pins and the layout of I/O pin structures. ESD devices range from simple diodes to complex active filters. Power supply rejection is accomplished through internal capacitance and careful routing on the die. Physical separation of pin inputs from active circuitry is a proven method to reduce transient effects but at a greater cost penalty due to die size impact.

The choice of MCU package can also affect immunity performance. The package type can have a great influence on PCB layout and composition. Surface-mount MCUs generally have smaller footprints than through-hole packages. This can reduce overall PCB dimensions and increase routing density, but it can also provide more space to implement board-level suppression techniques.

# **Areas of MCU Vulnerability**

Considering that most MCUs are specified and designed to generate and respond to signals with rise times comparable to ESD and EFT events,vulnerability to these events should be expected. Areas of MCU's typically vulnerable to ESD and EFT stresses include:

1)** Power and ground pins

**2)** Edge sensitive digital inputs

3)** High frequency digitalinputs

\4) Analog inputs

**5)** Clock (oscillator) pins

6)** Substrate injection

\7) General purpose I/O (GPIO) with multiplexed pin functions

**8)** ESD protection circuitry

Some MCUs have multiple power and ground pins to isolate high speed digital functions from low speed or noisy analog functions. These supply pins should be filtered appropriately to prevent disturbances in one area from affecting another.

Low cost MCUs may only have a single set of power and ground pins,which makes isolation difficult, and makes filtering more important. It is easy to understand that a transient that gets propagated to a supply line can also disrupt internal circuitry that has no direct route to the pin that was disturbed.

Edge sensitive inputs are particularly vulnerable to transients. These inputs are usually timer or external interrupt inputs. Even with external low pass filtering a sufficiently large pulse can inject enough energy into the input area to disrupt MCU operation. Pulses that don't disrupt the MCU can still be seen as glitches by the MCU. (*A software technique to filter out glitches is discussed later in this series* ).

![img](https://img2023.cnblogs.com/blog/1423856/202303/1423856-20230315214941704-1802580139.png)

High speed digital inputs, such as clock and data inputs, are less likely to have [**low pass filtering**](http://en.wikipedia.org/wiki/Low_pass_filter) and consequently can register transients as valid data pulses (**see Figure 2, above)** . External isolation techniques are necessary to eliminate this vulnerability.

Analog inputs are generally lower impedance than digital inputs and can suffer physical damage if not protected during ESD and EFT transients. However, on most MCUs the analog inputs are multiplexed with general purpose I/O pins and have a small sampling window in which the lower input impedance is active. A transient appearing in an analog input pin during an analog to digital conversion will result in distorted data due to the signal disruption. Effective software filtering techniques exist to mitigate this vulnerability.

Most MCUs have a built-in oscillator amplifier so that an external crystal or resonator is all that is needed to ensure a stable high frequency system clock. The oscillator pins can pass noise pulses as valid clock edges and are considered to be the most vulnerable inputs to the system. Appropriate PCB layout is the preferred method to eliminate this risk.

![f3](https://img2023.cnblogs.com/blog/1423856/202303/1423856-20230315215012522-2031200219.png)

As shown in **Figure 3 above** ,transients can travel from the point of entry and affect circuits via several paths. System input signals that exceed the power rails of the MCU will inject current into the I/O pin structure as soon as the signal level exceeds the ESD protection diode's forward voltage.

The I/O pin structure and on chip ESD protection network can dissipate small amounts of injected energy. However, if the injected current is greater than the local circuit can handle, this excessive current can find alternate paths through the supply rails or substrate to disrupt other circuitry. Current injection is generally minimized by using series resistors.

General purpose MCUs have I/O ports that can have more that one function multiplexed on a single pin. An electrical disturbance that causes enough energy to disrupt digital logic can also affect the control circuitry that selects the pin function. The resulting fault could change the pin state, the pin directionality, or the pin function.

Vulnerability is particularly troublesome for general purpose MCUs that are designed to meet the needs of many applications. For these MCUs, it is impractical or impossible to harden all vulnerable areas without adversely affecting functional performance in at least some applications.

Application-specific MCUs can be hardened with greater success, but some vulnerability will continue to exist if the operational frequency or bandwidth of the MCU overlaps the bandwidth of the ESD and EFT signals.

# **MCU Immunity Performance Classification**

The immunity performance for integrated circuits is typically classified into one of four categories as specified in [**IEC 62132-1**](http://webstore.iec.ch/webstore/webstore.nsf/artnum/035451) and shown in **Table 1 below** .

The classification applied is determined by the performance of the integrated circuit in the presence of the disturbance signal (i.e the ESD or EFT waveform). This performance is dependent on the type of integrated circuit and its functional and parametric operation as documented in its data sheet.

![t1](https://img2023.cnblogs.com/blog/1423856/202303/1423856-20230315215045532-1160321108.png)

**Class A performance** is the most desirable and is often required for safety-critical applications. Of course, this level of performance is difficult to ensure without taking proper steps in the design of the application. This is because any transient appearing at a pin that can be processed by the input circuitry has the potential for being interpreted as data and corrupting program execution.

**Class B performance** is considered acceptable for most applications where the main requirement is for no user intervention to recover nor malperformance. **Class C performance** can be acceptable for particular applications where operator intervention is not an issue, or where an external watchdog or supervisory circuit is used. **Class D performance** is not acceptable.

**MCU Failure Modes**
For MCUs, performance degradation can take many forms. Common forms oftemporary degradation include but are not limited to reset, latch-up,memory corruption, and code runaway.

MCUs with internal reset circuits can generally resume operation without operator involvement if the fault is an unexpected reset orcode runaway that is caught by a watchdog timer.

Recovery from latch-up and volatile memory (RAM, DRAM, etc.)corruption requires cycling the power to the system. Non-volatile memory (FLASH, EEPROM, ROM, etc.) corruption requires a more extensive process of re-programming the system, which can be viewed as a temporary MCU degradation if the system can be re-worked, or as a permanent degradation if it cannot be re-worked.

Permanent degradation can include increased leakage current on I/O pins which can affect analog measurements, input impedances, and output drive strength. With increased leakage current, the electronic system may still operate within specification for a while, but it may ultimately fail due to damage from the transient stress. Another type of permanent degradation found in transient environments is blown pins due to an electrical overstress.

# **Impact of MCU Design Trends**

The MCU design trend that particularly impacts transient immunity performance is the drive to continually reduce the minimum gate length of individual field effect transistors (FETs), making them smaller and faster. This trend is the result of market pressure on semiconductor manufacturers to reduce the cost of their products by making die sizes smaller.

The result is that maintaining the immunity performance of MCUs in the face of process technology advances is becoming increasingly difficult. When coupled with continuing cost reductions by OEMs at the application or system level, the immunity problem becomes severe.

MCU designers are challenged to develop better methods to dissipate the energy injected during a transient event. While they would appreciate more area in which to include transient suppression circuits, this is generally not allowed in order to keep the die size and cost to a minimum. Some of the remaining options available to the designer include modifying semiconductor attributes (doping and materials) and changing the vertical structure of the I/O pin.

**Next in Part 2: Hardware Techniques- The basic circuit building blocks**

Ross Carlton has specialized in all aspects of electromagnetic compatibility (EMC) since his graduation from Texas A&M University with a Bachelor of Science in Electrical Engineering in 1985. He has been with [Freescale Semiconductor](http://www.freescale.com/) for the last eight years where he has led the EMC design, test and support of Freescale's 8, 16, and 32-bit microcontroller products. In addition,Ross represents the U.S. as a Technical Expert to [IEC](http://www.iec.org/)Subcommittee 47Aon integrated circuits where he is the project leader for IEC 61967-2,IEC 61967-3 and IEC 62132-2**.** He is currently involved in developing transient immunity test methodologies for standardization.

*The author would like to thank* *Greg Racino and* *John Suchyta,* *8-Bit Applications Engineer at Freescale Semiconductor*  *for their inputs and guidance. Their contributions were critical to ensuring consistent and correct guidance.*

# **References:**

**1.** Ross Carlton, Greg Racino,John Suchyta, Improving the Transient Immunity Performance of Microcontroller-based applications. [Freescale Application Note (AN) 2764)](http://www.freescale.com/files/microcontrollers/doc/app_note/AN2764.pdf).

**2.** IEC 61000-4-2,Electromagnetic compatibility (EMC) – Part 4-2: Testing and measurement techniques – Electrostatic discharge immunity test, [International Electrotechnical Commission](http://www.iec.ch/), 2001. 

**3.** IEC 61000-4-4,Electromagnetic Compatibility (EMC) – Part 4-4: Testing and measurement techniques – Electrical fast transient/burst immunity test,International Electrotechnical Commission, 2001.

**4.** Ronald B. Standler,Protection of Electronic Circuits from Overvoltages, John Wiley &Sons, 1989, pp. 265-283.

**5.** Ken Kundert, “PowerSupply Noise Reduction”, [The Designer's Guide](http://www.designers-guide.com/) , 2004.

**6.** Larry D. Smith,”Decoupling Capacitor Calculations for CMOS Circuits”, [Electrical Performance of Electrical Packages Conference](http://ieeexplore.ieee.org/xpl/RecentIssue.jsp?punumber=6040), Monterey CA,November 1994, Pages 101-105.

**7.** Ronald B. Standler,Protection of Electronic Circuits from Overvoltages, John Wiley &Sons, 1989.

**8.** Clayton Paul, [Introductionto Electromagnetic Compatibility](http://www.wiley.com/WileyCDA/WileyTitle/productCd-0471758140.html), Wiley & Sons, 1992.

**9.** Bernard Keiser,Principles of Electromagnetic Compatibility, Artech House, 1987.

**10.** T.C. Lun, “Designing for Board Level Electromagnetic Compatibility”, [Motorola Application Note (AN) 2321](http://www.freescale.com/files/microcontrollers/doc/app_note/AN2321.pdf).