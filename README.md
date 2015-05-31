## Smart Alarm

Smart Alarm is a versatile home security application for the
[SmartThings](http://fbuy.me/bb9pe) home automation system.

*You can contribute to the development of this app by making donation via PayPal.*

[![PayPal](https://www.paypalobjects.com/en_US/i/btn/btn_donate_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=ATTTMV7JV2W9W)

### Features

* Two arming modes - Away and Stay.
* Unlimited number of security zones (sensors) - contact, motion, movement
(acceleration), moisture or smoke.
* Each security zone can be configured as Exterior (armed in both Away and
Stay modes), Interior (armed in Away mode only), Alert (always armed) or
Bypass (never armed).
* Entry and exit delays in both Stay and Away zones. Delays can be optionally
disabled for each zone.
* When an armed security zone is tripped, Smart Alarm can turn on sirens and
switches as well as execute chosen 'Hello, Home' action.
* Smart Alarm can send you push notifications and text messages when it's
armed, disarmed or when an alarm is triggered.
* Voice notifications using compatible audio devices, e.g. Sonos.


### Arming and Disarming

Smart Alarm can be armed and disarmed in three different ways:

1. Using home *Modes*. For example, you can configure Smart Alarm to arm in
Away mode when the home Mode is set to 'Away', to arm in Stay mode when the
home Mode is set to 'Night' and to disarm when the home Mode is set to 'Home'.
Using home Modes to arm and disarm Smart Alarm is a very flexible and powerful
technique because the modes can be changed by other Smart Apps and 'Hello,
Home' actions (also known as *phrases*). For example, 'Good Night!' action
activates the 'Night' mode, thus automatically arming Smart Alarm in Stay
mode.
2. Using a remote control, such as
[Aeon Labs Minimote](http://www.amazon.com/Aeon-Labs-DSA03202-v1-Minimote/dp/B00KU7ERAW)
3. Using REST API endpoints. Smart Alarm provides REST APIs to arm, disarm
and trigger panic alarm using HTTP GET request. This feature can be used to
integrate Smart Alarm into variety of web apps and dashboards.


### Screenshots

Coming soon....


### Using REST API

Smart Alarm provides the following REST API endpointss to arm, disarm and
trigger panic alarm using HTTP GET request.

    BASE_URL/armaway  - Arms Smart Alarm in Away node
    BASE_URL/armstay  - Arms Smart Alarm in Stay mode
    BASE_URL/disarm   - Disarms SmartAlarm
    BASE_URL/panic    - Triggers panic alarm
    BASE_URL/status   - Returns current status

The *BASE_URL* is https://graph.api.smartthings.com/api/smartapps/installations/APP_ID,
where APP_ID is the installed Smart App ID.

Please note that the REST API is disable by default. You can enable it using
Smart Alarm *REST API Options* menu. Before enabling the REST API, please make
sure that OAuth is enabled in the smart app settings in the IDE.

The REST API requires Access Token. You can obtain the access token using
SmartThings OAuth2 work flow, however as a convenience, Smart Alarm creates
the token for you. You can find your app's base URL and access token in the
SmartThings IDE.

Go to [My Locations](https://graph.api.smartthings.com/location/list) and
click on the "smartapps" link for your Location. Then find "Smart Alarm" in
the list of Installed SmartApps. Right-click on the "Smart Alarm" and select
"Open Link in New Window". Scroll down to the "Application State" section.
There you'll see "accessToken" and "url". Save those values and plug them in
into your web app.


### Installation

1. Open [SmartThings IDE](https://graph.api.smartthings.com) in your web
browser and log into your account.
2. Click on "My SmartApps" in the navigation bar at the top of the screen.
3. Click the green "+ New SmartApp" button on the right.
4. On the "New SmartApp" page, click the "From Code" tab.
5. In another browser window, open the Smart Alarm
[source code](https://raw.githubusercontent.com/statusbits/smartalarm/master/SmartAlarm.groovy).
6. Copy the Smart Alarm source and paste it into the new app editor window
(see Step 4).
7. Click the blue "Create" button at the button of the page. This will take
you back to the SmartThings IDE.
8. Click the "Publish" button above the IDE editor window and select "For Me"
in the drop-down list.
9. If you intend to use SmartAlarm REST API, click the "App Settings" button
above the IDE editor window. Otherwise skip to the Step 12.
10. In the app settings window, scroll down and click on the "OAuth" section,
then click the "Enable OAuth in SmartApp" button.
11. Click the blue "Update" button at the bottom of the page.
12. Open SmartThings mobile app on iPhone or Android and go to the Dashboard.
13. Tap on the round "+" button and navigate to "My Apps" section by swiping
the menu ribbon all the way to the left.
14. Locate "Smart Alarm" in the list of SmartApps that appears below the menu
ribbon and tap to install it.


### Revision History

**Version 2.4.0. Released 2015-05-30**
* Added movement (acceleration) sensors.
* Improved remote control button handling (Issues #25 and #27). Button numbers
are no longer limited to 1..4. You can also use both "Push" and "Hold" button
actions.
* Support "strobe" alarm mode (Issue #28). Alarms can now be turned on in
"siren", "strobe" or "both" modes.
* Added Sonos support (Issue #30). Smart Alarm now uses "Audio Player" device
type instead of "Speech Synthesis" for voice notifications.
* "Entrance" zones are no longer used. Instead, entry and exit delays can now
be disabled for each individual zone.

**Version 2.2.5. Released 2015-01-03**
* Take camera snapshots when alarm is triggered.
* Added support for Pushbullet notifications using
[Pushbullet](https://github.com/625alex/SmartThings/blob/master/devices/Pushbullet.groovy)
device handler.
* Added optional PIN code for arming/disarming via REST API.
* REST API is now disabled by default. You can enable it in the "REST API
Options" menu.
* Miscellaneous bug fixes.

**Version 2.2.1. Released 2014-12-06**
* Added option to disable entry delay in Stay mode.
* Fixed an issue related to scheduling delayed actions.

**Version 2.2.0. Released 2014-11-05**
* Exit delay is back. Note that the exit delay applies only to the Entrance
zones and only when arming in Away mode.
* Added voice notifications for the state changes (armed/disarmed).
* If the notification phrase is not entered then a default phrase will be
used.
* Moved voice configuration to "Notification Options" page

**Version 2.1.0. Released 2014-11-04**
* Added voice notifications using devices with 'Speech Synthesis' capability.
Currently, implemented only in the
[VLC Thing](https://github.com/statusbits/smartthings/tree/master/vlc_thing),
as far as I know.
* New notification options. You can now select notification options for alarm
notifications and status change separately.
* Increased the number for telephone numbers used for SMS notifications from
two to four.
* Fixed broken push notifications.

**Version 2.0.0. Released 2014-11-02**
* Simplified zone management. Each sensor is now treated as a separate
zone. The number of zones (sensors) is unlimited.
* New 'Entrance' zone type. Entry delay now only affects Entrance zones.
* Exit delay is eliminated.
* Removed buttons (Arm, Disarm, Panic) from the control panel pending
UI button implementation on Android platform.
* Refactored arming/disarming logic to work around event unsubscribtion
errors that started after SmartThings backend upgrade.

**Version 1.2.1. Released 2014-09-22**
* Fixed Issue #11 - Entry/Exit delays configuration changes are not applied.

**Version 1.2.0. Released 2014-09-18**
* Implemented REST endpoints to arm, disarm and trigger panic alarm with HTTP
GET requests.
* Added configuration setting to select home 'Mode' for disarming alarm.
* Exit and entry delays can now be configured for 15, 30, 45 or 60 seconds.
* Fixed an issue with broken SmartThings runIn() API.

**Version 1.1.3. Released 2014-09-14**
* You can now use remote control, such as Aeon Labs Minimote, to arm and
disarm Smart Alarm, as well as trigger panic alarm. 
* When alarm is set off, Smart Alarm can now execute 'Hello, Home' action in
addition to turning on sirens and light switches
* Added 'Arm Away', 'Arm Stay and 'Disarm' control panel buttons (iOS only).
* Modified Setup Menu work flow and some help text.

**Version 1.1.0. Released 2014-09-12**
* Released under GPLv3 License.
* Added 'About' page in the setup menu.
* Merged changes from Barry Burke (SANdood) branch
(https://github.com/SANdood/smartthings/tree/master/SmartAlarm). Thanks!

**Version 1.0.1. Released 2014-08-28**
* Fixed spelling mistakes, formatting, etc.

**Version 1.0.0. Released 2014-07-04**
* First public release.


License
-------

Copyright (C) 2014 Statusbits.com

This program is free software: you can redistribute it and/or modify it
under the terms of the GNU General Public License as published by the Free
Software Foundation, either version 3 of the License, or (at your option)
any later version.

This program is distributed in the hope that it will be useful, but
WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY
or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License
for more details.

You should have received a copy of the GNU General Public License along
with this program.  If not, see <http://www.gnu.org/licenses/>.
