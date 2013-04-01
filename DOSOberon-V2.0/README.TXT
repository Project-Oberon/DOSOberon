Oberon (TM) for MS-DOS Systems,  
Version 2.0 , 1. 4. 93     
Copyright (C) 1993 by Institut fuer Computersysteme ETH Zuerich


Introduction

Oberon is both a programming language and an operating environment. It is the 
final outcome of a research project whose aim was an extensible, highly 
integrated and compact  operating platform for single-user personal 
workstations.

The original project was launched and carried out by N. Wirth and J. Gutknecht 
for the Ceres workstation. Ported versions of the Oberon language and system 
are now available for numerous commercial machines, among them MacIntosh, IBM 
RS/6000, DEC station, SPARC station and IBM PC/386 compatibles.                                                                                                                                                                                                           

Literature

The following family of books on Oberon is available from Addison-Wesley 
company:

	The Oberon System- User Guide and Programmer's Manual,
		by M. Reiser

	Programming in Oberon- Steps beyond Modula-2,
		by M. Reiser and N. Wirth

	Project Oberon- The Design of an Operating System
		and Compiler, by N. Wirth and J. Gutknecht                                                                                                                                                                 

MS-DOS Oberon

Oberon for IBM PC/386 compatibles is henceforth called MS-DOS Oberon. Even 
though MS-DOS Oberon is highly congruent with the original system as described 
in the above listed literature, there are some preconditions and 
implementation specialties to know. The following sections summarize these 
points. They also include a summary of principles of operation and an 
installation guide.

Hardware Requirements

	1) Intel 80386DX- or 80386SX-processor
	2) 2 megabytes or more of main memory
	3) mouse with 2 or 3 buttons and driver
	4) VGA-board

Software Requirements

	1) DOS version 3.3 or 5.0 
	2) HIMEM.SYS driver for extended memory access

Disclaimer

Permission to use, copy, modify or distribute this software and its 
documentation for any purpose is hereby granted without fee, provided  that 
the above copyright notice appear in all copies and that both that copyright 
notice and this permission notice appear in supporting documentation, and that 
the name of ETH not be used in advertising or  publicity pertaining to 
distribution of the software without specific, written prior permission.

ETH disclaims all warranties with regard to this software, including all 
implied special, indirect or consequential damages or any damages whatsoever 
resulting from loss of use, data or profits, whether in an action of contract, 
negligence or other tortious action, arising out of or in connection with the 
use or performance of this software.

Contact Address

MS-DOS Oberon
Institute for Computer Systems
ETH Zentrum
CH-8092 Zuerich

E-mail: Oberon@inf.ethz.ch 
E-Fax: +41 1 2519678

Acknowledgement

The MS-DOS Oberon project has partly been supported by IBM research 
laboratory, Rueschlikon Switzerland. It has been carried out by A. R. Disteli.


Principles of Operation and Installation Guide

Mode of Operation

MS-DOS Oberon principally operates in 386 protected mode in high memory above 
1 MB. Below the 1 MB limit are video-RAM, extender, system loader, Oberon 
kernel and the procedure activation stack. The extender handles interrupts and 
DOS system calls. It also bootstraps the Oberon module loader and starts the 
Oberon system.

Restriction

Currently, no other software running in protected mode or V86 mode must be 
installed simultaneously with Oberon. This restriction applies in particular 
to expanded memory managers like EMM386. Also SMARTDRIVE should not be 
installed.

File System

MS-DOS Oberon maintains its own DOS file directory. It contains all Oberon 
files that are created at Oberon run-time. Note that Oberon file names may be 
up to 31 characters long and may contain an arbitrary number of part-
separators ".". Oberon translates such file names internally into aliasing DOS 
file names and maintains a translation table.

In addition, Oberon offers commands System.CopyFromDOS and System.CopyToDOS, 
allowing file copy from arbitrary DOS directories to Oberon and vice versa.

Template:  System.CopyFromDOS a:/MyDir/Filename.Ext => Oberonname~

Diskettes

Data transfer from and to diskettes is supported by module Backup. Data on 
Oberon diskettes are stored in a private format that supports full Oberon file 
names. Use commands SetDriveA and SetDriveB to set the current drive.

Keyboard

The following table shows how to generate special characters under Oberon 
control.

special character	key

mark viewer	F1	(* Setup *)
no scroll	F2	(* used in program Draw *)
double s	F7
escape	ESC

ae	ctrl-a
oe	ctrl-o
ue	ctrl-u
Ae	F8
Oe	F9
Ue	F10

ctrl-shift-del	ctrl-break	(* keyboard interrupt *)

If the appropriate keyboard driver is installed, ae, oe, ue, Ae, Oe, Ue and 
double-s can also be typed directly.

Mouse

The standard Oberon user interface is based on a 3-button mouse and on the 
following interpretation of button clicks:

Primary clicks:

    left: set caret
    middle: execute
    right: select

Interclicks while selecting (holding down the right button):

   left: delete selected data 
   middle: copy selected data to caret
   left & middle: undo interclick

Alternatively, interclicking left/middle can be replaced by pressing ctrl-
key/alt-key on the keyboard.

Preverably install a Logitech Mouse Driver V6.0 (Included in this release 
named MOUSE.COM). MS-DOS Oberon also supports a 2-button mouse. In this case, 
the left button subsumes the functions execute and set caret. To switch from 
execute to set caret, keep the mouse still and the button pressed for ca. 0.5 
sec.

Display

MS-DOS Oberon by default assumes a VGA display interface with a resolution of 
640 * 480 * 16. However, support is also provided for the ET4000 Super-VGA 
standard with a resolution of 1024 * 768 * 256. In order to activate the Super-
VGA support, simply open ET4000.Tool, execute the renaming command and restart 
Oberon.

Printing

DOS-Oberon currently supports Postscript and HP PCL printing. To that purpose, 
different drivers are available: The HP500 printer family and Postscript. 
These drivers assume that an appropriate printer device is connected to one of 
the parallel ports LPT1 or LPT2 or the serial ports COM1 or COM2 with 9600 
baud for Postscript printers and 19200 baud for HP printers. If no suitable 
printer is installed, a printfile (Document.Print) is generated on the local 
disk. Simply open Printer.Tool in Oberon, execute the renaming command and 
restart Oberon.


System Installation and Operation

The installation kit consists of the following files:

	name                contents

	README.TXT    this description
	SYSTEM.EXE     Oberon system in compressed form (selfextracting file)
	CHANGES.TXT   Changes since the last release

to install Oberon

	1) assert FILES = 64 in CONFIG.SYS
	2) create new directory
	3) copy SYSTEM.EXE into new directory
	4) execute SYSTEM.EXE

to load and start Oberon

	5) install mouse driver
	6) set directory containing the Oberon system to current directory
	7) execute START command

System Exit

	8) Activate command System.Quit

Getting started with Oberon

The above mentioned book The Oberon System- User Guide and Programmer's Manual 
is a complete and comprehensive guide to the basic Oberon system. In addition, 
online documentation is included in the installation kit, as well as some sample
source code files. See the different tools for prepared opening commands.                         


List of installed Oberon packages

 Program packages

	Basic system
	Compiler
	Edit	program editor
	Paint	picture editor
	
	Write	text editor                  
	Draw	graphic editor                                         

Program samples in source form

	Biorhythm.Mod	calculates biorythm
	RandomNumbers.Mod	generates good random numbers
	IFS.Mod	generates fractal fern graphic

Online documentation

	ReadMe.Text	this text
	OberonGuide.Text                                                             

Fonts

	Courier	monospace font
	Syntax	proportional text font
	Elektra	general symbols
	Math	mathematical symbols

