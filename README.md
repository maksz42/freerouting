# freerouting

[ ![Download](https://api.bintray.com/packages/miho/Freerouting/freerouting/images/download.svg) ](https://bintray.com/miho/Freerouting/freerouting/_latestVersion)

Freerouting is an advanced autorouter for all PCB programs that support the standard Specctra or Electra DSN interface.

It basically does this:

![](https://raw.githubusercontent.com/miho/freerouting/master/res/img/freerouting.jpg)

## What has changed?

Freerouting is a fantastic piece of software. But the code hasn't been updated in a while and had some design flaws. Some of them are fixed now. This version of freerouting has been refactored to be fully compatible with JDK11.

[Binary installers for Linux, macOS and Windows can be downloaded here](https://freerouting.mihosoft.eu/).

### New Features

- Uses gradle as build system (which is compatible with command line, NetBeans, IntelliJ, Eclipse and more)
- New code base uses proper package names. That is, freerouting can finally be used as library.
- Removed local dependencies. Publication via maven central and/or bintray is now possibe.
- WebStart code has been removed (WebStart is officially deprecated)
- Several `ClassCastException` bugs in the graphics package have been fixed
- Swing UI uses native look&feel if possible
- Prepared Jigsaw module support (still WIP)
- other minor fixes

## How to Build It

### Requirements

- Java >= 11
- Internet connection (dependencies are downloaded automatically)
- IDE: [Gradle](http://www.gradle.org/) Plugin (not necessary for command line usage)

### IDE

Open the `freerouting` [Gradle](http://www.gradle.org/) project in your favourite IDE (NB, IntelliJ, Eclipse etc. with Gradle Plugin) and build it
by calling the `assemble` task.

### Command Line

Navigate to the [Gradle](http://www.gradle.org/) project (e.g., `path/to/freerouting`) and enter the following command

#### Bash (Linux/OS X/Cygwin/other Unix-like shell)

    bash gradlew assemble
    
#### Windows (CMD)

    gradlew assemble
    
#### Generated Executables

All four .jar files will be generated in the _build\libs_ subfolder. You would typically run the _freerouting-executable.jar_ file.

## From the original author:

Java Based Printed Circuit Board Routing Software from FreeRouting.net written by Alfons Wirtz.

http://www.freerouting.net/fen/viewtopic.php?f=4&t=255

by alfons © Sat Mar 08, 2014 12:07 pm

Because I am no more maintaining the Freerouting project since 4 years and future Java versions may block my Freerouting Java Web Start application completely, I finally decided to open the source of the Freerouting project under the GNU public license version 3.

I have attached the complete source code of the Freerouting project. Please feel free downloading and using the sources according to the GPLv3 license.


Introduction:
=============

This software can be used together with all host PCB design software systems containing a standard Specctra or Electra DSN interface. It imports .dsn-files generated by the Specctra interface of the host system and exports Specctra session files.(There exists also an interface to Cadsoft-Eagle.)

There are three modes for routing traces: 90 degree, 45 degree and free angle. The interactive router is production stable and unsurpassed in its free angle capabilities. An autorouter is currently under development and already stable in the conventional 45 degree mode.

After launching the router a window appears with buttons to display some router demonstrations, to open a sample design, or to open a design of your own.

After opening a design you can start the autorouter with the button in the toolbar on top of the board window.

The board editor has three different interactive states. You can switch between this states with the buttons Select, Route and Drag on the left of the toolbar.

In the beginning the board editor is in the select state. In this state you can select single board items by picking them with the left mouse button or select items in a rectangle by dragging the left mouse button. Only item types switched on in the select parameter sheet will be selected. After selecting some items the toolbar displays options for showing and manipulating these items. If you push the info button for example a window with text information about the selected items is displayed. After clicking a blue word in this text a new window with further information pops up. To return to the select state push the cancel button or click somewhere in the empty space of the board window.

By pushing the Route button you get into the state for interactive routing. In this state you can start a new trace by picking an item belonging to a net, for example a pin. Then you can follow the displayed airline with the mouse until you have reached the target item at the other end of the airline. The trace will be connected automatically to the target, if it is on the same layer. If you want to change to a different layer during interactive routing, select "change layer" and then the name of the new layer in the popup menu under the right mouse button. Then a via will be inserted, if that is possible, and a new trace starts on the new layer. You can also change the layer by pressing a number key.

After pushing the Drag button you get into the state for changing the location of vias, components or traces. In this state you can select vias or components and drag them with the left mouse button to a different location. The connected route is updated automatically. You can also move traces by pushing them from behind out of the empty space with the left mouse button pressed. That works on the current layer, which can be changed in the select parameter sheet. In this way you can make space for example to insert a new component.

For more information please use the online help in the board editor. From here you can download also a printable version of the online help.

If you have further questions or want some feedback, please sent an Email to support@ FreeRouting.net or visit our forum.

Additional steps for users of CadSoft-Eagle:
============================================

1) Download the latest Eagle2freerouter ulp file

2) Start Eagle and open in the control panel of Eagle for example the design my_design.brd.

3) Choose in the Files pulldown-menu of Eagle the item "execute ULP" and select the Eagle2freerouter ulp file. A file with name my_design.dsn is generated.

4) Start the router, push the "Open Your Own Design" button and select my_design.dsn in the file chooser.

5) After making some changes to the design with the router select "export Eagle session script" in the Files pulldown-menu. A file with name my_design.scr is generated.

6) Choose in the Files pulldown-menu of Eagle the item "execute Script" and select my_design.scr.


Additional steps for users of KiCad:
====================================

1) Download the latest freerouting-executable.jar file from the [Releases](https://github.com/freerouting/freerouting/releases)

2) Start KiCad and open your project in Pcbnew.

3) Export the PCB into Specctra DSN (File / Export... / Specctra DSN).

4) Start the router by running the freerouting-executable.jar file, push the "Open Your Own Design" button and select the exported .dsn file in the file chooser.

5) Do the routing.

5) When you're finished, export the results into a Specctra session file (File / Export Specctra Session File). The router will generate a .ses file for you.

6) Go back to KiCad's Pcbnew and import the results (File / Import Specctra Session...).


Using the command line arguments:
=================================

Freerouter was designed as a GUI program, but it also can function as a command line tool. Typically you would have an input file (e.g. Specctra DSN) that you exported from you EDA (e.g. KiCad). If this file has unconnected routes, you would want to wire those with autorouter, and save the result in a format that you can then import back into your EDA.

The following command line arguments are supported by freerouter:

* -de [design input file]: loads up a Specctra .dsn file at startup 
* -di [design input directory]: if the GUI is used, this sets the default folder for the open design dialogs
* -dr [design rules file]: reads the rules from a previously saved .rules file
* -do [design output file]: saves a Specctra board (.dsn), a Specctra session file (.ses) or Eagle session script file (.scr) when the routing is finished
* -mp [number of passes]: sets the upper limit of the number of passes that will be performed
* -l [language]: "de" for German, otherwise it's English
* -mt [number of threads]: sets thread pool size for route optimization
* -us [greedy | global | hybrid]: sets board updating strategy for route optimization: greedy, global optimal or hybrid. When hybrid is selected, another option "hr" specifies hybrid ratio.
* -hr [m:n] : sets hybrid ratio in the format of #_global_optiomal_passes:#_prioritized_passes, e.g., 1:1. It's only effective when hybrid strategy is selected. 
* -is [sequential | random | prioritized]: sets item selection strategy for route optimization: sequential, random, prioritized. Prioritied stragegy selects items based on scores calculated in previous round.

A complete command line looks something like this if your are using PowerShell on Windows:

`
& "c:\Program Files\Java\jdk-11.0.6\bin\java.exe" -jar freerouting-executable.jar -de MyBoard.dsn -do MyBoard.ses -mp 100 -dr MyBoard.rules
`

This would read the _MyBoard.dsn_ file, do the auto-routing with the parameters defined in _MyBoard.rules_ for the maximum of 100 passes, and then save the result into the _MyBoard.ses_ file. 


Multi-threaded Implementation of Routing Optimization:
======================================================

When board complexity reached certain level, route optimization in previous version was slow to the the extent that was almost un-usable. This issues was addressed with multi-threading and various updating strategies.

Here is an example that shows the amount of speedup achieved by the initial author of this routing optimization. On a machine with 8 cores, the following options are used: -mt 16 -us greedy -is prioritized. After about 75 passes, the phase of routing optimation was finished after about 30 hours. # of vias was reduced from 566 to 418, and route length was reduced from 12.94 million to 12.07 million. The average CPU usage is around 1,500%, so comparing to previous single thread route optimization, the speedup is roughly 15 times. If previous version was used, this 30-hour (1 1/4 day) task would take about 20 days to finish.

A note about power supply to laptops: it was a surprise to see the laptop battery kept loosing charge when a power supply was connected. With the multi-threaded optimization, the computer will be pushed to its limit, so use an official power supply that comes with the laptop, or use a more powerful power supply. Also be aware of room temperature as the computer will become hotter and might be overheated, especially when the computer is moved to another room because you cannot withstand its unusual fan noise.

One critical task in multi-threaded optimation is to clone objects. In the initial multi-threaded implementation, a quick way to clone objects was used: clone via serialization. When someone gets time, take a look of implementing cloning in offical way.

Besides multi-threading, multiple optimzation strategies were also implemented. Global optimal strategy selects the global optimal update after processing all items in an optimation pass, while greedy strategy adopts an update as soon as it is found to be better than current one, so there will be multiple updates in a greedy optimization pass. Hybrid strategy mixes the above two, and there is an option to select the mixing ratio.

Sequential, random and prioritized item selection strategies are implemented to determine which item to process next during an optimization pass. Each item is ranked during the optimization pass so that it's possible to prioritize items with better scores when selecting items to process in next optimization pass.

Hopefully this multi-threaded routing optimization will make this router practical to route boards of high complexity.

