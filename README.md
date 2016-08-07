# Crestron-Template
Template Code for Crestron Residential Programming Projects
This code is the template that I would use to start all my Crestron residential projects.  It is not meant to be code that you would install directly but must be customized for each client.  The code includes drivers for the majority of different client devices that I encountered over the years.  Rather than having to write the drivers for each device when you start a new project the concept of this template is that you would delete the drivers that aren't applicable for the client whose project you are developing.  So, if your client uses cable TV; delete the DirecTV driver code and the graphics for that device from the VisionTools Pro-e files.  The same can be said for features that may not be relevant to all customers.  For example there is code that sets back the thermostat whenever the alarm system is armed in away mode.  This is great for a small house where the customers want to save money.  It should not be used in a large house, or a home with radiant heat, where there is too much thermal lag and the temperature should simply be maintained at a constant level.  I strongly encourage people who make use of this code to go through the process of fully deleting code that isn't relevant to the system they are working on.  This will greatly simplify the code and make it much more maintainable over the life of the project.  A little extra work up front to do this will lower the cost of maintenance significantly.  

The code template consists of 2 programs that run in different slots on a 3-Series Crestron Processor

1) AV program - This is the primary program and includes all the programming for audio/video control, HVAC, Security, and interfacing with touch panels.

2) Lighting - This program communicates with the AV program over an EISC symbol and contains the code for communication with the lighting system.  This code is currently written to communicate with a Lutron lighting system as most projects that I worked on over the years used Lutron lighting.  This code could easily be changed to communicate with Crestron lighting equipment or the entire program could be changed to work with a D3 program.

The programming makes use of several data files that are loaded into either NVRAM or RM using Toolbox.  These are

1) Devices.txt - Defines the names of the source devices, the crosspoint ID for the device, and routing information

2) Rooms.txt - Defines the names of the rooms in the system and the crosspoint ID for each room

3) HVAC.txt - Defines the names of each HVAC zone and the crosspoint ID for each zone

4) Lighting.txt - Defines the name of each lighting zone/room and the xpoint ID for each one.

A word document is included that describes these in more detail.

As mentioned above the programs make extensive use of crosspoint routing.  Much of the complexity of the routing is hidden from the developer in modules and through use of specifying crosspoint ID's in the data files.  

Things you may want to change

1) If there are devices, or features, that you never use then delete that code from the template to save yourself from having to go through the effort of deleting them on every project.

2) In the same way that the lighting code is in a separate program the code for HVAC, the security system, door locks, etc. could be moved to a separate program.  This would make the AV program cleaner.  I've done this on the code for my house but changing the template is left as an exercise for the user.

3) There is a bug in the HVAC setback module that I have not found.  I have seen a few times that code for setting back the thermostat when the alarm system is armed and restoring the thermostat to the previous setting when the alarm system is disarmed may not work right and the thermostat may be left at the setback temperature.  I haven't been able to pin down the exact circumstances when this occurs to figure out what is causing the bug.  I suspect it is a timing issue when someone arms the alarm system then disarms it because they forgot something in the house and then arms it again.  However, I'm not sure.  Just wanted to provide full disclosure.  

I hope this template helps people as it has helped me over the years.
