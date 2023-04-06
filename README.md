Archived here: https://www.hpcalc.org/details/4301


==============================================================================
=============== Hewlett Packard 49G Keyboard Hardware Note ===================
============================= Version 0.2 ====================================
==============================================================================

Version 0.2 - April 3, 2003.
Version 0.1 - October 1, 2000.

------------------------------------------------------------------------------
DISCLAIMER:

The following information is in no way official, it is the result of my
analisys of an HP49 circuit, and it can be absolutly wrong, or full of errors.
Use the information AT YOU OWN RISK!, there are NO WARRANTIES!, if you
damage your calculator in any way or loose any information, it is your
SOLE RESPONSIBILITY!
 
You are free to use this file for non-comercial purposes provided that
no changes are made to it, and that this and other copyright notices are kept.
------------------------------------------------------------------------------

0. INTRODUCTION 
---------------

As many of you know, the 49G calculator is an improvement of the 48G series
in many aspects, such as memory, software and hardware.

For those of you who are interested in the hardware of the 49G and are
courious about the keyboard pin assignments, they are provided below.

The calculator viewed from the back of the PCB. So the xtal (crystal
oscillator) is oriented to the left side.

 From left to right:

 PIN  NAME	 LINE IN-reg	 LINE OUT-reg
 ---------	 -----------	 ------------
  1   Vcc	  A1  0001	  Y1  001
  2   ON	  A2  0002	  Y2  002
  3   Y8	  A3  0004	  Y3  004
  4   Y5	  A4  0008	  Y4  008
  5   A1	  A5  0010	  Y5  010
  6   A2	  A6  0020	  Y6  020
  7   Y3	  A7  0040	  Y7  040
  8   Y3	  A8  0080	  Y8  080
  9   A8
  10  A3
  11  A4
  12  Y2
  13  Y6
  14  A7
  15  A6
  16  Y1
  17  A5
  18  Y7

1. USING THE LINES
------------------

 1.1 Using Saturn assembly
 -------------------------

 To check if a key is being pressed we must first set the OUT register
 (see next table) and then read the IN register through the CINRTN fuction
 (this is because the C=IN must be executed on an odd memory adress due to
 a bug). We read the value of IN and check if the bit (see next table) is
 set. We can read up to 8 keys at the same time.

  KEY    OUT   IN	  KEY    OUT   IN
  ----------------	  ----------------
  F1     020  0001	  EEX    010  0010
  F2     020  0002	  +/-    008  0010
  F3     020  0004	  X KEY  004  0010
  F4     020  0008	  1/X    002  0010
  F5     020  0010	  / KEY  001  0010
  F6     020  0020	  ALPHA  080  0008
  APPS   020  0080	  7 KEY  008  0008
  MODE   010  0080	  8 KEY  004  0008
  TOOL   008  0080	  9 KEY  002  0008
  VAR    004  0080	  * KEY  001  0008
  STO    002  0080	  L SHFT 080  0004
  NXT    001  0080	  4 KEY  008  0004
  U-ARW  040  0008	  5 KEY  004  0004
  L-ARW  040  0004	  6 KEY  002  0004
  R-ARW  040  0001	  - KEY  001  0004
  D-ARW  040  0002	  R SHFT 080  0002
  HIST   010  0040	  1 KEY  008  0002
  CAT    008  0040	  2 KEY  004  0002
  EQW    004  0040	  3 KEY  002  0002
  SYMB   002  0040	  + KEY  001  0002
  DROP   001  0040	  ON     ANY  8000
  Y^X    010  0020	  0 KEY  008  0001
  SQRT   008  0020	  . KEY  004  0001
  SIN    004  0020	  SPC    002  0001
  COS    002  0020	  ENTER  001  0001
  TAN    001  0020

 1.2 Using direct hardware
 -------------------------

 The OUT lines use TTL.
 To use the IN lines you must connect one them using an 8 Kohm resistor
 to an OUT line, this IN-OUT connection produces the key defined in the
 previous table.
 In case you want connect more than one IN line to a OUT line, you must
 connect the IN lines each one with a 2 Kohm - 4 Kohm resistor between them.

----------------------------------------
"True greatness is only found in simple things".

Igor Sylvester
Massachusetts Institute of Technology
Cambridge, MA
ias@mit.edu.
