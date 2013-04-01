System 3, Release 2.0, MS-DOS Version, May 5, 1995
Copyright (C) 1995 by Institut fuer Computersysteme ETH Zuerich

Table of Contents 
=================
 
 1.) Introduction
 2.) Literature 
 3.) MS-DOS Oberon
 4.) Hardware Requirements  
 5.) Software Requirements
 6.) Available Packages
 7.) Principles of Operation
 8.) Implementation Restriction
 9.) File System
10.) Diskette Support
11.) Keyboard
12.) Mouse
13.) Display
14.) Printing
15.) System Installation and Operation
16.) System Exit
17.) Getting Started with Oberon
18.) Contact Address
19.) Acknowledgement
20.) Disclaimer
21.) Changes since Previous Release

1.) Introduction
================

Oberon is both the name of a programming language and of an operating
environment. It is the final outcome of a research project whose aim was
an extensible, highly integrated and compact operating platform for
single-user personal workstations.

The original project was launched and carried out by N. Wirth and 
J. Gutknecht for the Ceres workstation. Ported versions of the Oberon 
language and system are now available for numerous commercial machines, 
among them MacIntosh, IBM RS/6000, DEC station, SPARC station and 
IBM PC/386/486 compatibles.

System 3 is an object-oriented evolution of the original Oberon system. 
It supports a generic mechanism for the management of visual and abstract
end-user objects. Gadgets (TM) is a graphical user interface (GUI) 
framework that has been specifically designed for System 3.

2.) Literature
==============

The following books on Oberon are currently available:

The Oberon System- User Guide and Programmer's Manual,
by M. Reiser, Addison-Wesley.

Programming in Oberon- Steps beyond Modula-2,
by M. Reiser and N. Wirth, Addison-Wesley.

Project Oberon- The Design of an Operating System and Compiler, 
by N. Wirth and J. Gutknecht, Addison-Wesley.

Objektorientierte Programmierung in Oberon-2,
by H. P. M”ssenb”ck, Springer Verlag

3.) MS-DOS Oberon
=================

The MS-DOS version of Oberon for IBM PC/386 & /486 compatibles is henceforth 
called MS-DOS Oberon. Although MS-DOS Oberon is highly congruent with the 
original system as described in the above listed literature, there are some 
preconditions and implementation specialties to know about. These points
are summarized in the following sections. Also included are a summary of 
principles of operation, an installation guide and a list of changes.

4.) Hardware Requirements
=========================

1) Intel 80386SX/DX-, 80486- or Pentium processor
2) 2 MB of main memory (4 MB for Gadgets toolkit)
3) Mouse (3 buttons recommendable)
4) VGA- or SVGA-interface
5) Ethernet interface (for network applications only)

5.) Software Requirements
=========================

1) DOS version 5.0 or higher
2) HIMEM.SYS driver for extended memory access
3) Mouse driver

6.) Available Packages
======================

SYSTEM.EXE    Basic MS-DOS Oberon System 3 & Simple Simulation Case Study 
DEVELOP.EXE   Development tools, including assembler & debugger
GADGETS.EXE   Gadgets GUI framework
EDITORS.EXE   Includes Leda with TrueType (demo version), ET, Draw 
NET.EXE       Net tools, including e-mail, Telnet, FTP, WWW, Teletext
DOCU.EXE      Full online documentation & tutorial

7.) Principles of Operation
===========================

MS-DOS Oberon principally operates in 386 protected mode in high memory above
1 MB. Below the 1 MB limit are video-RAM, extender, system loader, Oberon
kernel and the procedure activation stack. The extender handles interrupts 
and DOS system calls. It also bootstraps the Oberon module loader and 
starts the Oberon system.

8.) Implementation Restriction
==============================

With this MS-DOS Oberon version, no other software running in protected mode 
or V86 mode must be installed simultaneously with Oberon. This restriction 
in particular applies to expanded memory managers like EMM386. Also, 
SMARTDRIVE and SHARE should not be installed.

9.) File System
===============

MS-DOS Oberon maintains its own DOS file directory containing all Oberon
files that are created at Oberon run-time. Oberon file names may be up to
31 characters long and may contain an arbitrary number of part-separators 
".".

In addition, Oberon offers commands System.CopyFromDOS and System.CopyToDOS,
allowing file copy from arbitrary DOS directories to Oberon and vice versa.

Template: System.CopyFromDOS a:/MyDir/Filename.Ext => Oberonname~

10.) Diskette Support
=====================

Data transfer from and to diskettes is supported by the Backup tool.
This tool supports two different formats: Standard DOS and Oberon.
Use any standard DOS formatter or the Backup.Format command
to format both standard DOS and Oberon diskettes. Option /H
is used for high-density formatting. Use Backup.InitOberon
to initialize Oberon diskettes.

Text conversion from Oberon to DOS and vice versa is provided
by the commands Miscellaneous.MakeDOSText and
Miscellaneous.MakeOberonText respectively.

The current drive can be defined by a call of Backup.SetDriveA
or Backup.SetDriveB.

11.) Keyboard
=============

The following table shows how to generate special characters under Oberon
control.

function        key

mark viewer     F1 (* Setup *)
no scroll       F2 (* used in program Draw *)
Break           F4

screen off/on   F5
invert screen   F6
reset screen    F7

double-s        ctrl-s
escape          ESC

ae               ctrl-a
oe               ctrl-o
ue               ctrl-u
Ae               alt-a
Oe               alt-o
Ue               alt-u

ctrl-shift-del  ctrl-break              (* keyboard interrupt *)
System.Quit     ctrl-F10                (* Shortcut *)

If the appropriate keyboard driver is installed, ae, oe, ue, Ae, Oe,Ue and
double-s can also be typed directly.

12.) Mouse
==========

The standard Oberon user interface is based on a 3-button mouse and on 
the following interpretation of button clicks:

Primary clicks:

left:   set caret
middle: execute
right:  select

Interclicks while selecting (holding down the right button):

left:    delete selected data 
middle:  copy selected data to caret
left & middle: undo interclick

MS-DOS Oberon also supports a 2-button mouse. In this case, the middle button
is assigned the Alt-key on the keyboard. 

13.) Display
============

MS-DOS Oberon by default assumes a VGA display interface with a resolution 
of 640 * 480 * 16. However, support is also provided for the ET4000 SVGA 
standard and for systems equipped with a ET4000/W32 or a S3 graphics 
accelerator chipset with a resolution of 1024 * 768 * 256. In order 
to activate the SVGA support, simply open Installation.Tool, 
execute the renaming command and restart Oberon.

14.) Printing
=============

DOS-Oberon currently supports Postscript and HP PCL printing. To that 
purpose, different drivers are available: The HP500 printer family, 
HPLaserJet4 and Postscript. These drivers assume that an appropriate 
printer device is connected to one of the parallel ports LPT1 or LPT2 
or the serial ports COM1 or COM2 with 9600 baud for Postscript printers 
and 19200 baud for HP printers. If no suitable printer is installed, 
a printfile (Document.Print) is generated on the local disk. Simply 
open Installation.Tool in Oberon, execute the renaming command and 
restart Oberon.

Print command: XXX.Print (LPT1|LPT2|COM1|COM2|other) (*|filename)~

15.) System Installation and Operation
======================================

1) assert FILES = 64 in CONFIG.SYS
2) create new directory
3) copy SYSTEM.EXE into new directory
4) execute SYSTEM.EXE (self-contained basic system)
5) if desired execute GADGETS.EXE and further .EXE files

to load and start Oberon

6) install mouse driver
7) set directory containing the Oberon system to current directory
8) execute command OBERON

Alternatively to 7), specify environment in AUTOEXEC.BAT:
PATH C:\WORK; ... others
SET OBERON = C:\WORK

16.) System Exit
================

Activate command System.Quit

17.) Getting started with Oberon
================================

The above mentioned book The Oberon System - User Guide and Programmer's 
Manual is a complete and comprehensive guide to the basic Oberon system. 
In addition, a well-structured hypertext of online documentation is included 
in the MS-DOS Oberon package, together with several sample source code files
and with a sophisticated module browser.

For further details, install and start Oberon, click middle at Desktops.Open
Oberon.Desk in the system tool and then click middle again at the Tutorial 
icon in Oberon.Desk. 

18.) Contact Address
====================

MS-DOS Oberon
Institute for Computer Systems
ETH Zentrum
CH-8092 Zuerich

E-mail: Oberon@inf.ethz.ch 
E-Fax: +41 1 632 1075

19.) Acknowledgement
====================

The MS-DOS Oberon project has partly been supported by IBM research
laboratory, Rueschlikon Switzerland. It has been carried out by A. Disteli
(Disteli@inf.ethz.ch). Most of the Gadgets toolkit has been developed
by J. Marais (Marais@inf.ethz.ch). A. Fischer (Fischer@inf.ethz.ch) 
is the author of the online documentation.

20.) Disclaimer
===============

Permission to use, copy, modify or distribute this software and its
documentation for any purpose is hereby granted without fee, provided that
the above copyright notice appear in all copies and that both that copyright
notice and this permission notice appear in supporting documentation, and 
that the name of ETH not be used in advertising or publicity pertaining 
to distribution of the software without specific, written prior permission.

ETH disclaims all warranties with regard to this software, including all
implied special, indirect or consequential damages or any damages whatsoever
resulting from loss of use, data or profits, whether in an action of 
contract, negligence or other tortious action, arising out of or 
in connection with the use or performance of this software.

21.) Changes from Previous to Current Release
=============================================

(1) New structure of EXE-files, see "Available Packages" above

(2) New grey-tone Gadgets-look for viewers in the basic system

(3) Minor improvements in the basic system:
  Edit.Open now opens an empty text if called without name selection
  Backup commands now accept name selection in log viewer

(4) Improved compiler, allows REAL-constant expressions now

(5) More elaborate debugging tool "Debugger", installable on desire

(6) Numerous cleanups and improvements in the Gadgets system

(7) New picture editing tool "Rembrandt", replacing the "Paint" program 
  and including a raster font editor and a backdrop generator

(8) New and versatile module browsing tool "Watson"

(9) Complete online documentation in the form of a tutorial hypertext

(10) New software to access Internet services, including e-mail, WWW
  and Telnet; currently requiring Ethernet connection to Internet
