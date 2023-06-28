# Klipper_fan_stall
Klipper fan stall macros and hardware repository

To work with Timmit fan stall pcb, i created some macros that can be usefull to pause the print if the hotend fan is not running.

The hw can be found here https://github.com/timmit99/Fan_Stall_Detector.

You would need to change some settings on the main macro file:
```
[gcode_button HEF_FAN]
pin: !PA2                            <-this is the pin that's connected to the fan failure
press_gcode: _HEF_ALARM_SET
release_gcode: _HEF_ALARM_CLEAR

[delayed_gcode _HEF_ALARM]
gcode:
  M118 HEF FAN Stopped                <- This is the code that is run when klipper detects the fan failure
  #PAUSE_PRINT
  TURN_OFF_HEATERS

[gcode_macro _HEF_ALARM_COUNTS]
variable_hefalarm_threshold:  4       <- How many failures to detect before triggering an error (a minimum of 4 is recommended)

## should not be the need to edit anything below this line
```
