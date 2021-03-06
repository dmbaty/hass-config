## Home Assistant Configuration
Currently I'm running this in LXC container on a proxmox machine.  This config is still a work in progress but hopefully it will help others who are learning Home Assistant.

I've added quite a few automations but have more planned.
### Components
- Weather
  - wunderground
- Device tracking
  - Unifi based
- Climate
  - Econet (hot water heater)
- Z-Wave
  - Aeon Labs Z-Stick gen 5 as the controller
  - A random mix of light modules/switches/bulbs, most are GE/Jasco
    - Some require a periodic power cycle (via the pull tab) which is a bit frustrating
    - Some appear to work OK but won't send a node info frame (to trigger the add/remove from the network) until a power cycle
  - Schlage FE599 and a few Schlage Connect (BE469/BE468) locks
    - Working to get notifications when certain user codes are used and user code configuration working with these
    - Notifying when a user code is used on the FE599 is difficult - I have an ugly workaround (check every second) right now
  - A few sensors
    - Monoprice garage door sensors (x2)
    - Monoprice shock/vibration sensor (for dryer detection, still in progress)
    - Monoprice multi-sensor - not sure exactly where this will go
    - Leak detection sensor (need to add a few more of these and a water valve eventually)
- Emulated Hue
  - Mostly for Alexa integration
- Google Assistant
- Envisalink
  - Connected to an old Honeywell panel
- Notifications
  - HTML5
  - Pushbullet
  - Email to text (via carrier service)
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

notify_important is meant for notifications that can't be muted.

notify_critical is meant for time senstive notifications (water leaks, furnace not running correctly, etc).

### Future improvements
Just about everything...
