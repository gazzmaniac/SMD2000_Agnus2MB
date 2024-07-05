# SMD2000_Agnus2MB
SMD 2000 2 MB SMD Agnus Card

This is the 2 MB SMD Agnus card for the SMD2000 "BUSHFIRE" project, a mini-DTX sized Amiga 2000.  
Official project information can be found at Amiga Retro Brisbane projects page:
https://www.amigaretro.com/projects/

This card is for constructors who wish to use a 2 MB 8375 Agnus from an A500+ or A600.  Not all 8375s will work!!!! See notes on Agnus revisions below.

If you intend to use a 1 MB or 512 kB Agnus from an Amiga 500 or Amiga 2000: 8370; 8371; 8372A; and certain 8375s, build a 1 MB card.  

There are two other Agnus cards to choose from; a 1 MB card that uses the TTH ram from the Amiga, and one which uses SMD ram (not yet released).  The 1 MB TTH version is probably the easiest to get working but it is too tall for the ML09 case.

2 MB Agnus card: https://github.com/gazzmaniac/SMD2000_Agnus2MB 

1 MB SMD Agnus card: https://github.com/gazzmaniac/Agnus_1MB 

1 MB TTH Agnus card: https://github.com/gazzmaniac/Agnus_1MB_TTH


## Licensing
Design is open source hardware.
1. Any and all derivative designs must also be open source.
2. No person, business, or other entity associated with this design shall be liable for any damages incurred by anyone as a result of using this design.  If you do not accept this condition do not build the project.
3. Free for private use by anyone.
4. Free for anyone to make for sale by anyone.
5. CERN Open Hardware Licence Version 2 - Strongly Reciprocal CERN-OHL-S) license applies, subject to conditions 1-4 above.
6. Any portions of this design from other projects shall be licensed according to their respective licenses if their licenses are not compatible with CERN-OHL-S or the conditions above.
7. All Other Rights Reserved.

## Requirements
To make a complete SMD2000 you also need to build a motherboard and a CPU card.  They are documented separately.

Motherboard: https://github.com/gazzmaniac/SMD2000/ 

Basic CPU card: https://github.com/gazzmaniac/SMD2000_cpu-card

The SMD2000 project requires a donor Amiga, either an A500, A500+, A2000, or A600 plus a Gary.

If you intend to use the Kicad files you will need the SMD2000 symbol and footprint libraries.  They are included in the SMD2000 motherboard package.  You will probably need to change the path in Kicad.

## Notes and Eratta
Forgot to take the gap between the CD Rom and the top of the case into account so this card (and its 1 MB counterpart) are too tall to fit under the CD Rom in the ML09 case.  Revision is coming.

This card is essentially the onboard and trapdoor expansion ram from the in the A500+ but with 16x256 SMD ram chips instead of 4x256 TTH chips.  Component numbering sometimes follows the A500+ rather than the A2000.

SN74F139 for U32 is no longer sold.  This has been substituted to CD74AC139 (TI) or MC74AC139 (OnSemi) as these chips have similar propagation delay to the SN74F139.  Prototype uses the CD74AC139 and it seems stable.  Remember to take ESD precautions as this is a CMOS device.

X1, the 28.37516 oscillator (for PAL systems) is difficult to find new.  Most constructors will probably use the one from the donor board.  I had success buying them from AliExpress, testing with the frequency function on the oscilloscope gave values of 28.3752 which is correct to the limits of accuracy of the scope.  

RAM is 256k x16 SOJ-40, e.g. HYB514171BJ-60.  It's no longer in production but easy to find on eBay or AliExpress.

There's a Commodoreism with the DRD bus on the A500+ not arranged so bit 0 on the bus goes to bit 0 on the ram chip and so on, and for some reason the NC pin is connected to _RAS.  There's no functional difference so the SMD2000 is wired sensibly same as the A2000, with DRD0 going to D0 on the ram and so on.

The A & DRD Buses on the A2000 do not have pullup resistors on the A200 but do on the A500+.  The SMD2000 does not have them either and there seems to be no problem.

## Jumpers
J101 is the same as JP2 in A500+.  It probably shouldn't be changed since you have 2 mb ram fitted.
JP3 from A500+ (swaps lower and upper ram banks) has been removed.  
JP4 is the same as J4 on A500+, it bypasses U32 CAS multiplexing.  Name has been changed slightly to conform with Kicad rules.  It'd be stupid to close this jumper, if you're going to the effort of using a $200 2 MB Agnus you're not going to try and save $5 and only use 1 MB ram.

## Notes about Agnus revisions
This board is designed for the 2 MB 8375 Agnus from the A500+ and A600 only.  NOT ALL 8375s will work!!!!

1 MB and 512 kb Agnus from A500/A2000 (8370, 8371, 8372A) and 2 MB Agnus from A3000 (8372AB and 8372B) have a different pinout and WILL NOT WORK.  Build one of the 1 MB Agnus Boards if you have one of them.

The 8375 Agnus ICs are not all the same.  Only Agnus with the following Commodore part numbers have the correct pinout:
390544-01, 318069-10 (PAL)
390544-02, 318069-11 (NTSC)

All the rest are the same pinout as the 1 MB Agnus.

## References
Amiga A500/A2000 Technical Reference Manual

A2000 and A500+ schematics (Commodore scanned and Amigawiki.org vector)

Agnus Revision Information:

https://www.amigawiki.org/lib/exe/fetch.php?media=de:parts:agnus_reworks.pdf

https://bigbookofamigahardware.com/bboah/product.aspx?id=1478

Datasheet for HYB514256B (4x256kbit RAM) and HYB514171BJ-60 (16x256kbit RAM)

Various component data sheets.  Refer component metadata.
