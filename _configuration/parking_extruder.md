# [Magnetic] Parking Extruder
<table>
  <tr><td>Parking Extruder</td><td>:</td><td>PE</td></tr>
  <tr><td>Magnetic Parking Extruder</td><td>:</td><td>MPE</td></tr>
</table>

This text describes the dual parking extruder configuration for <a href="https://reprap.org/wiki/Prusa_Mendel"> "Mendel or I3 Prusa"</a> systems. These systems moves the printing hotend on X axis and Z axis. The print bed moves on the Y axis. Therefor it is possible to install two printing hotends. One at the left and the second at the right side of the X axis.  
***
```cpp
//#define MAGNETIC_PARKING_EXTRUDER
#if ENABLED(PARKING_EXTRUDER) || ENABLED(MAGNETIC_PARKING_EXTRUDER)
  #define PARKING_EXTRUDER_PARKING_X { 32, 140 }     // X positions for parking the extruders. M951 L{X_Pos_Left} R{X_Pos_Right}
  #define PARKING_EXTRUDER_GRAB_DISTANCE 32           // mm to move beyond the parking point to grab the extruder. M951 I{Grab_Distance}
  #define TOOLCHANGE_ZRAISE 5                               // Z-raise before parking
  #if ENABLED(PARKING_EXTRUDER)
    #define PARKING_EXTRUDER_SOLENOIDS_INVERT           // If enabled, the solenoid is NOT magnetized with applied voltage
    #define PARKING_EXTRUDER_SOLENOIDS_PINS_ACTIVE LOW  // LOW or HIGH pin signal energizes the coil
    #define PARKING_EXTRUDER_SOLENOIDS_DELAY 250        // (ms) Delay for magnetic field. No delay if 0 or not defined.
    //#define MANUAL_SOLENOID_CONTROL                   // Manual control of docking solenoids with M380 S / M381
  #elif ENABLED(MAGNETIC_PARKING_EXTRUDER)
    #define MPE_FAST_SPEED      9000      // (mm/m) Speed for travel before last distance point. M951 H{Fast_Feedspeed}
    #define MPE_SLOW_SPEED      4500      // (mm/m) Speed for last distance travel to park and couple. M951 J{Slow_Feedspeed}
    #define MPE_TRAVEL_DISTANCE   10      // (mm) Last distance point. M951 D{Travel_Distance}
    #define MPE_COMPENSATION       0      // Offset Compensation -1 , 0 , 1 (multiplier) only for coupling. M951 C{Offset_Compensation}
  #endif
#endif
```
[MPE Kinamatics](https://youtu.be/0xCEiG9VS3k)
