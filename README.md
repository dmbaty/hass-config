## Home Assistant Configuration
Currently I'm running this in LXC container on a proxmox machine.  This config is still a work in progress but hopefully it will help others who are learning Home Assistant.

Note: many of the automations here are for testing purposes only right now.  I'll have to get my Z-Wave network moved over to HASS to make them actually do something.

### Components
- Weather
  - wunderground
- Device tracking
  - Unifi based
- Climate
  - Econet (hot water heater)
- Z-Wave
  - Currently using a Aeon Labs Z-Stick (old, 300 series based), plan to move to 500 series USB stick soon
  - Working to get notification and user code config with Schlage Connect (BE469/BE468) and FE599 locks
  - Plan to move rest of Z-Wave devices to HASS soon (~10 lights, 2 thermostats, a few sensors, etc)
- Emulated Hue
  - Mostly for Alexa integration
- Google Assistant
- Envisalink
  - Conencted to an old Honeywell panel
- Notifications
  - HTML5
  - Pushbullet
- Misc
  - Speedtest.net

### Automations
Again, more to come here...
- Home mode
  - This is used to enable/disable automations and is driven by the device tracker.
  - Options
    - Occupied: When one or more people are home
    - Override: Used to force the system into occupied mode and not exit this mode automatically (guests over, debugging, issues with automations, etc)
    - Away: When everyone is currrently not at home (ie, at work, out for a short period of time, etc)
    - Vacation: Used for times we will be away (ie, overnight).  Will automatically enter this mode after being away for 18 hours.

### Debug
I have a notify_status script to send lots of notifications to track what is happening in real time.  This is meant for debugging and can be easily enabled/disabled with a input_binary control.

notify_important is meant for notifications that can't be muted.  I may create a notify_critical in the future.

### Future improvements
Just about everything...
