---

layout: post
title: 'New release: 1.3.10'
author: foosel
date: 2018-12-10 14:50:00 +0100
card: /assets/img/blog/2018-12/2018-12-10-octoprint-1.3.10-card.png
featuredimage: /assets/img/blog/2018-12/2018-12-10-octoprint-1.3.10-card.png
poster: /assets/img/blog/2018-12/2018-12-10-octoprint-1.3.10-poster.png
excerpt: After four weeks of testing by the community and just in time for the holidays, I'm happy to present you OctoPrint 1.3.10. While this is a maintenance release, it not only packs a bunch of bug fixes but also a whole lot of improvements, including the new Backup & Restore plugin and Application Keys plugin.   
images:
- url: /assets/img/blog/2018-11/2018-11-06-octoprint-1.3.10rc1-pisupport.png
  title: The new warning symbols of the Pi Support plugin when undervoltage and overheating are detected.
- url: /assets/img/blog/2018-11/2018-11-06-octoprint-1.3.10rc1-backup.png
  title: The new Backup & Restore Plugin.
- url: /assets/img/blog/2018-11/2018-11-06-octoprint-1.3.10rc1-appkeys_notification.png
  title: An access request notification generated by the new Application Keys Plugin...
- url: /assets/img/blog/2018-11/2018-11-06-octoprint-1.3.10rc1-appkeys_usersettings.png
  title: ... and the new user settings dialog for management of all your Application Keys.
- url: /assets/img/blog/2018-11/2018-11-06-octoprint-1.3.10rc1-forcedlogin.png
  title: The new ForcedLogin makes sure anonymous users will no longer be able to watch your prints.

---

As an early christmas present 🎄 I'm happy to present you OctoPrint 1.3.10. This a maintenance release again, 
consisting of various improvements and fixes. It was made possible only through your continued 
**[support of my work](/support-octoprint/)** 💕.

As you can see [in the changelog](https://github.com/foosel/OctoPrint/releases/tag/1.3.10) it packs a ton of 
improvements and bug fixes which would be too many to list here, so let me just present you with some of the
highlights:

  * The OctoPi Support Plugin is now the Pi Support Plugin, will be enabled when a Raspberry Pi is detected as the underlying hardware platform and report on undervoltage or overheating situations.
  * Added the Backup & Restore Plugin: The new bundled plugin will allow you to make a backup of your OctoPrint settings, files and list of installed plugins, and to restore from such a backup on the same or another instance. This should make migration paths from outdated installations to newer ones easier.
  * Added the Anonymous Usage Tracking Plugin. Tracking will only take place if the plugin is enabled and you've decided to opt-in during initial setup (or enabled it manually afterwards, through the corresponding switch in the settings). The tracking data will give insight into how OctoPrint is used, which versions are running and on what kind of hardware OctoPrint gets installed. You can learn about what will get tracked (if you opt-in) on [tracking.octoprint.org](https://tracking.octoprint.org). Please consider helping development by participating in the anonymous usage tracking 💕 
  * Added the Application Keys Plugin: The new bundled plugin offers an authorization for third party apps that doesn't involve manually copying API keys or using QR codes. Third party client developers are strongly advised to implement this workflow in their apps. Read more [in the documentation](http://docs.octoprint.org/en/maintenance/bundledplugins/appkeys.html). Thanks to Aldo Hoeben for the idea and initial implementation!
  * Automatic updates in outdated environments are no longer supported. After repeated issues out in the field with ancient installations and ancient underlying Python environments, OctoPrint's Softwareupdate Plugin will no longer allow automatic updates of itself or any installed plugins via the Software Update Plugin if a certain set of minimum versions of Python, `pip` and `setuptools` isn't detected. The current minimum versions reflect the environment found on OctoPi 0.14.0: Python 2.7.9, pip 9.0.1, setuptools 5.5.1. See also the [related FAQ entry](https://faq.octoprint.org/unsupported-python-environment).
  * OctoPrint will now try to protect/educate more prominently against the dangers of opening up OctoPrint on the public internet via various new explicit warnings in the UI as well as a new notification that pops up if you log in from an external IP address. Thanks to the new bundled ForcedLogin Plugin OctoPrint will also no longer be accessible in a read-only way by anonymous guests - to get back the old behaviour, disable the plugin.
  * Added detection of `EMERGENCY_PARSER` firmware capability and if it's present add `M108` to the cancel procedure, to cancel blocking heatups.
  * Improved GCODE analysis speed
  * ... and various further improvements and of course bug fixes.

There's also a small heads-up for plugin authors:

> OctoPrint has updated its `sarge` dependency. The new version 0.1.5 has a small breaking change - the `async` keyword was renamed to `async_` for compatibility reasons with Python 3.7. This might also affect your plugin if you happen to use `sarge` somewhere therein. OctoPrint has a workaround for this in place so your plugin will continue to function for now. However, you should look into updating it to use `async_` instead of `async` if running against OctoPrint 1.3.10+.
> 
> See also [here](https://sarge.readthedocs.io/en/latest/overview.html#id1) for the `sarge` changelog.

The full list of changes can of course be found in the
[Changelog](https://github.com/foosel/OctoPrint/releases/tag/1.3.10) - as always.

Also see the **Further Information** and **Links** below for more information,
where to find help and how to roll back.

I also want to thank everyone who contributed to this release, especially [@BillyBlaze](https://github.com/BillyBlaze), [@bradcfisher](https://github.com/bradcfisher), [@eyal0](https://github.com/eyal0), [@fieldOfView](https://github.com/fieldOfView), [@gdombiak](https://github.com/gdombiak), [@gerfderp](https://github.com/gerfderp), [@hashashin](https://github.com/hashashin) and [@tedder](https://github.com/tedder) for their PRs.

And last but not least another special **Thank you!** to everyone who reported back on the release candidates this time: [@andrivet](https://github.com/andrivet), [@arminth](https://github.com/arminth), [@autonumous](https://github.com/autonumous), [@benlye](https://github.com/benlye), [@BillyBlaze](https://github.com/BillyBlaze), [@bradcfisher](https://github.com/bradcfisher), [@Charly333](https://github.com/Charly333), [@ChrisHeerschap](https://github.com/ChrisHeerschap), [@Crowlord](https://github.com/Crowlord), [@ctgreybeard](https://github.com/ctgreybeard), [@devildant](https://github.com/devildant), [@dimkin-eu](https://github.com/dimkin-eu), [@DominikPalo](https://github.com/DominikPalo), [@duncanlovett](https://github.com/duncanlovett), [@EddyMI3d](https://github.com/EddyMI3d), [@FanDjango](https://github.com/FanDjango), [@FormerLurker](https://github.com/FormerLurker), [@gdombiak](https://github.com/gdombiak), [@GhostlyCrowd](https://github.com/GhostlyCrowd), [@goeland86](https://github.com/goeland86), [@Goodeid](https://github.com/Goodeid), [@hamster65](https://github.com/hamster65), [@hashashin](https://github.com/hashashin), [@jenilliii](https://github.com/jenilliii), [@JohnOCFII](https://github.com/JohnOCFII), [@kmanley57](https://github.com/kmanley57), [@louispires](https://github.com/louispires), [@markuskruse](https://github.com/markuskruse), [@Nervemanna](https://github.com/Nervemanna), [@nionio6915](https://github.com/nionio6915), [@ntoff](https://github.com/ntoff), [@paukstelis](https://github.com/paukstelis), [@racenviper](https://github.com/racenviper), [@ramsesiden](https://github.com/ramsesiden), [@rtbon](https://github.com/rtbon), [@skohls](https://github.com/skohls), [@stough](https://github.com/stough), [@tech-rat](https://github.com/tech-rat), [@tedder](https://github.com/tedder), [@ThaliaFromPrussia](https://github.com/ThaliaFromPrussia), [@thisiskeithb](https://github.com/thisiskeithb), [@trendelkamp](https://github.com/trendelkamp), [@truglodite](https://github.com/truglodite), [@tteckenburg](https://github.com/tteckenburg), [@varazir](https://github.com/varazir), [@Webstas](https://github.com/Webstas) and [@zeroflow](https://github.com/zeroflow)

### Further Information

It may take up to 24h for your update notification to pop up, so don't 
be alarmed if it doesn't show up immediately after reading this. You
can force the update however via Settings > Software Update > 
Advanced options > Force check for update.

If you get an error about "no suitable distribution" during update, please read 
[this](https://discourse.octoprint.org/t/i-got-some-error-about-no-suitable-distribution-during-update-and-now-my-server-wont-start/235).

**If you have any problems with your OctoPrint installation, please seek 
support on the [community forum](https://discourse.octoprint.org).**

### Links

  * [Changelog and Release Notes](https://github.com/foosel/OctoPrint/releases/tag/1.3.10)
  * [Community forum](https://discourse.octoprint.org)
  * [FAQ](https://faq.octoprint.org)
  * [Documentation](http://docs.octoprint.org/)
  * [Contribution Guidelines (also relevant for creating bug reports!)](https://github.com/foosel/OctoPrint/blob/master/CONTRIBUTING.md)
  * [How to file a bug report](https://github.com/foosel/OctoPrint/blob/master/CONTRIBUTING.md#how-to-file-a-bug-report)
  * [How to roll back to an earlier release (OctoPi)](https://discourse.octoprint.org/t/how-can-i-revert-to-an-older-version-of-the-octoprint-installation-on-my-octopi-image/205)
  * [How to roll back to an earlier release (manual install)](https://discourse.octoprint.org/t/how-can-i-roll-back-to-an-earlier-version-after-an-update/234)

