+++
title = "Field values"
weight = 10
+++

## Output fields
The resulting output fields can be classified into several categories:

- The **Device**:
The hardware that was used.
- The **Operating System**:
The base software that runs on the hardware
- The **Layout Engine**:
The underlying core that converts the 'HTML' into a visual/interactive
- The **Agent**:
The actual "Browser" that was used.
- **Extra fields**:
In some cases we have additional fields to describe the agent. These fields are among others specific fields for the Facebook and Kobo apps,
and fields to describe deliberate useragent manipulation situations (Anonymization, Hackers, etc.)

Note that **not all fields are always available**. So if you look at a specific field you will in general find null values and "Unknown" in there as well.

There are as little as possible lookup tables included the system really tries to analyze the useragent and extract values from it.
The aim of this approach is to have a system that can classify as much traffic as possible yet require as little as possible maintenance
because all versions and in many places also the names of the used components are extracted without knowing them beforehand.


## Values explained

**Note about the `Hacker` classification:**

Security scanning tools (like nmap, nessus and openvas) are also classified as Hacker.
My reasoning is that it is a system that someone uses to find security problems.
With tools like this it is clear it is not a normal visitor that is interested in the content of the website.
What is uncertain is the reason behind this: is it to fix problems or to abuse them?
So I classify all of them as hacking oriented tools.                            |

### DeviceClass

| Value                 | Meaning                                                                                                                                       |
|-----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| Desktop               | The device is assessed as a Desktop/Laptop class device                                                                                       |
| Anonymized            | In some cases the useragent has been altered by anonymization software                                                                        |
| Unknown               | We really don't know, these are usually useragents that look normal yet contain almost no information about the device                        |
| Mobile                | A device that is mobile yet we do not know if it is a eReader/Tablet/Phone or Watch                                                           |
| Tablet                | A mobile device with a rather large screen (common > 7")                                                                                      |
| Phone                 | A mobile device with a small screen (common < 7")                                                                                             |
| Watch                 | A mobile device with a tiny screen (common < 2"). Normally these are an additional screen for a phone/tablet type device.                     |
| Augmented Reality     | A mobile device with a AR capabilities (like Google Glass)                                                                                    |
| Virtual Reality       | A mobile device with a VR capabilities                                                                                                        |
| eReader               | Similar to a Tablet yet in most cases with an eInk screen                                                                                     |
| Set-top box           | A connected device that allows interacting via a TV sized screen                                                                              |
| TV                    | Similar to Set-top box yet here this is built into the TV                                                                                     |
| Home Appliance        | A (usally large) home appliance (like a Fridge)                                                                                               |
| Game Console          | 'Fixed' game systems like the PlayStation and XBox                                                                                            |
| Handheld Game Console | 'Mobile' game systems like the 3DS                                                                                                            |
| Voice                 | A voice driven device (i.e. ask a question and the page is read aloud). Like Alexa and Google Home.                                           |
| Car                   | A Car based browser as found in for example the Tesla vehicles                                                                                |
| Robot                 | Robots that visit the site                                                                                                                    |
| Robot Mobile          | Robots that visit the site indicating they want to be seen as a Mobile visitor                                                                |
| Robot Imitator        | Robots that visit the site pretending they are robots like google, but they are not. Note that in most cases they ARE Robots.                 |
| Cloud                 | A cloud based application. Not a Robot or Hacker but a normal application that needs to connect. This includes for example Mastodon servers.  |
| Hacker                | In case scripting is detected in the useragent string, also fallback in really broken situations                                              |

### OperatingSystemClass

| Value        | Meaning                                                  |
|--------------|----------------------------------------------------------|
| Desktop      | The type of OS you would run on a Desktop or Laptop      |
| Mobile       | The type of OS you would run on a Phone, Tablet or Watch |
| Cloud        | Looks like a thing that runs in a cloud environment      |
| Embedded     | Apparently embedded into something like a TV             |
| Game Console | A game console like PS4, Xbox                            |
| Hacker       | A hacker, so it can really be anything.                  |
| Anonymized   | It was explicitly hidden                                 |
| Unknown      | We don't know                                            |

### LayoutEngineClass

| Value       | Meaning                                                                                 |
|-------------|-----------------------------------------------------------------------------------------|
| Browser     | A regular browser                                                                       |
| Desktop App | A desktop app (often a PWA)                                                             |
| Mobile App  | A mobile app which probably includes a regular webbrowser                               |
| Hacker      | A hacker, so it can really be anything.                                                 |
| Robot       | A robot spidering the site                                                              |
| Cloud       | A cloud based application where it is unclear what kind of layout engine is really used |
| Special     | Something special we cannot fully classify                                              |
| Unknown     | We don't know                                                                           |

### AgentClass

| Value             | Meaning                                                                                                |
|-------------------|--------------------------------------------------------------------------------------------------------|
| Browser           | A regular browser                                                                                      |
| Browser Webview   | A regular browser being used as part of a mobile app                                                   |
| Desktop App       | A desktop app (often a PWA)                                                                            |
| Mobile App        | A mobile app                                                                                           |
| Robot             | A robot that wants to be treated as a desktop device                                                   |
| Robot Mobile      | A robot that wants to be treated as a mobile device                                                    |
| Cloud Application | Something running in a cloud that is intended to be Human facing (so not a regular robot)              |
| Server            | Something running in a cloud that is intended to be Server-to-Server (so not a regular robot)          |
| Email Client      | This is an email application that did the request                                                      |
| Voice             | A voice driven 'browser' (i.e. ask a question and the page is read aloud). Like Alexa and Google Home. |
| Special           | Something special we cannot fully classify                                                             |
| Testclient        | A website testing tool                                                                                 |
| Hacker            | A hacker, so it can really be anything.                                                                |
| Unknown           | We don't know                                                                                          |

### AgentSecurity

| Value           | Meaning                                                                                               |
|-----------------|-------------------------------------------------------------------------------------------------------|
| Weak security   | Indicated to use deliberately weakened encryption (usually due to export restrictions or local laws). |
| Strong security | Indicated to use strong (normal) encryption.                                                          |
| Unknown         | It was not specified (very common)                                                                    |
| Hacker          | A hacker, so it can really be anything.                                                               |

