# Goom VCF

Goom is yet another Moog style transistor ladder VCF for Eurorack. It's setup to be a fairly shallow 14hp module.

This is mainly a re-layout of [Yves Usson's](http://yusynth.net/) [YuSynth MiniMoog VCF](http://yusynth.net/Modular/index_en.html). A few substitions of really super obsolete componetns with only somewhat obsolete components were made. Everything is through-hole mount, I haven't made the leap to SMT yet. There's similar designs using SMT devices out there; just search for "minimoog transistor ladder filter eurorack".

The original design was for a 5U modular synth because that's what Yves was building. You can still [buy the YuSynth PCB](https://www.soundtronics.co.uk/yusynth-diy-synth/) and adapt it to Eurorack power and figure out how to attach it to a front panel but it's really designed to be a MOTM module. 

This used three matched pairs of <a href="https://github.com/crankery/goom/blob/main/Documents/BC547.pdf" target="_blank">BC547C NPN transistors</a>, a [BC557C PNP transistor](Documents/BC557C.pdf), a [TL072 op-amp](Documents/tl072h.pdf) and two [CA3046N transistor arrays](Documents/CA3046N.pdf). Of these components, the CA3056 and TL072 are still readily available. There's a clear substition for the transistors as well as a possible better option. The original design was for $\pm15V$; Yves suggests some resistor value changes for Eurorack's $\pm12V$ power. Matching transistors is still possible in this day and age but I felt like it was a pain so I decided to try out another option.

## Changes from YuSynth Design

You can still easily obtain BC5x7 transistors but I happened to have a bunch of 2N3904 and 2N3906 transistors on hand so I elected to use those. Then I decided trying to match pairs of them was a pain. Knowing the [Alfa RPAR AS394](https://www.alfarzpp.lv/eng/sc/AS394CH.pdf) matched transistor pair IC was available, I decided to try that out.
I've left the discrete transistor pads on the PCB.

The 2N3904 is standing in for the BC557, 2N3096 for the BC547N transistors.

Since the AS394 has internal diodes coming off the emitters, I've included pads for 2N4148 diodes on the optional discrete transistor pads. Again, 2N2148 was selected because I had them on hand.

## Design Constraints

The PCB is 100mm in the long dimension which makes it pretty darned cheap to order from [PCBWay](https://www.pcbway.com/). It is 70.8mm wide which [Doepfer says is 14hp](https://doepfer.de/a100_man/a100m_e.htm).

I elected to exclusively use through-hole components and PCB mount vertical potentiometers and jacks. Because some of these components are taller than the jacks and pots most of the components are on the opposite side of the PCB from the components that protrude from the front panel.

The potentiometers used are Alpha RD901F style 9mm vertical PCB mount with 6.35mm (1/4") round shafts and threaded collar to attach the front panel. The 10KΩ anti-log taper potentiometer was not available in this style so I used the RD901F which has a 6mm 18 tooth plastic shaft for resonance/emphasis. The jacks are PJ301BM 3.5mm switched tip mono jacks.

## Parts Sourcing

Most of the hardware and the discrete components were obtained from [Tayda](https://www.taydaelectronics.com/). The AS394 ICs are from [Cabintech](https://cabintechglobal.com/). The CA3056 and TL072 ICs came from AliExpress.

# Design

I started out by re-drawing the original design in [KiCad](https://www.kicad.org).

![YuSynth Schematic](http://yusynth.net/Modular/Commun/MOOGVCF/Moogfilter-sch.jpg)

## To Do

- [ ] A note on the schematic `** resistor valus to be adjusted to adapt to input and output levels` which applies to R5 and R32. Not sure what the appropriate values are for Eurorack levels and this isn't discussed anywhere on the page
- [ ] The references are different in the KiCad schematic vs the original. Make them match
- [ ] The BOM says `47nF matched to 1%` for C4-7, not sure how to go about that

## Changes From Original

- R24, R27, R26 value changed for $\pm12V$
- Eliminated the MOTM power connection and switched all the $\pm15V$ to $\pm12V$
- Added a Eurorack 10 pin header power connector
- Switched the 3 x 100KΩ resistors to a 4 pin resistor network
- Switched the 4 x 470Ω resistors to an 8 pin isolated resistor pack 
- Added diodes off the matched transitor emitters as per the AS394's internals
- Added optional AS394 ICs to replace the matched transistors

# Front Panel

I'm trying to put the edge cuts for the panel, including jack and pot holes on a user layer. The graphics for the front panel are on another one.

## To Do

- [ ] determine how one goes about exporting a document to send to a service to get panels cut and drilled
- [ ] in the meantime, determine how to export the panel edge cuts layer to a pdf so the holes can be accurately drilled by hand in a blank panel
- [ ] determine how to go about exporting the graphics layer and doing some sort of acid etching process or something
