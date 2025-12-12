---
# Rebuild trigger
layout: default
title: Endorphin.es Plus 3 + DOREMIDI MPC-10
---




[← Back to Home](https://kylebeckgit.github.io/)


**Some background on why I bought the DOREMIDI for anyone who is considering going down the same path**:

I already had a PLUS 3 to use with my hardware that has expression inputs (Analog Heat+FX and Osmose in my case). I loved the form factor and the hardware feels great. I didn’t have a portable hardware solution to control my software synthesizers (or other hardware that acecpts midi but not expression) in the same way, so I wanted to see if there was a solution out there to bridge this gap and let me use the PLUS 3 with more stuff. The DOREMIDI got a shout out on one of Looppop’s youtube videos & I couldn’t find much else on the market that did what it did at a low pricepoint. One challenge is I didn’t see any real world experiences of people setting up the PLUS 3 with DOREMIDI and what that process looked like, so I knew there would likely be some kinks getting things set up (sure enough, it took a good little chunk of time to get it working). 

**Does the DOREMIDI work for my intended goal?**: it is working well! I’m enjoying the greatly expanded uses of my PLUS 3 as a hardware controller for soft synths, though I’ve yet to try it with my other hardware so I cant vouch for the MIDI output capabilities yet (to date I’ve only used it exclusively for MIDI over USB)

So how did I get it set up? See below. 

### Configuration Guide 

This guide explains the exact configuration I use to make the **Endorphin.es Plus 3** pedal work with the **DOREMIDI MPC-10**. 

My end goal was being able to use the PLUS 3’s expression and sustain outputs with software synthesizers. Following these steps I was able to get it to work perfectly. 
My wiring setup: 

Expression jack -> EXP 1 on DOREMIDI 
Sustain jack -> EXP 2 on DOREMIDI

The DOREMIDI application required some tinkering to get everything working. Essentially I wanted the PLUS 3 to operate in software similarly to how it works with hardware. 

**The first thing I struggled with**: the cable you use is ~important~! Using the wrong cable could render the device unrecognized and unable to connect to the DOREMIDI software. I used a different USB c cable from the one that came in the box, and could not get the DOREMIDI software to recognize the hardware. Switching to the USB cable that came in the box fixed this problem.

Once you have the DOREMIDI software connecting to the device, you can dial everything in. Here’s how I got it working for my preferences. 
⠀
# PEDAL 1 (Expression) — Continuous Fader
Use this for controlling DAW parameters (e.g., CC1 → last touched in Bitwig).

| **Setting**        | **Value**                   |
|:------------------:|:---------------------------:|
| **Pedal Number**   | 1                           |
| **Pedal Type**     | Expression                  |
| **Event**          | Continuous Controllers (CC) |
| **Controller No.** | **1**                       |
| **MIDI Channel**   | 1                           |
| **Min**            | 0                           |
| **Max**            | 127                         |
| **Gain**           | 0                           |
| **Curve**          | 0                           |
| **Trigger Level**  | OFF                         |

### Expected Output
- CC 1 0
- CC 1 4
- CC 1 17
- …
- CC 1 127

Smooth, continuous values with no stepping or interference.

# PEDAL 2 (Switch) — Momentary Button
Use this for toggling on and off. The on position will hold the maximum midi value set for PEDAL 2. 

| **Setting**        | **Value**                                         |
|:------------------:|:-------------------------------------------------:|
| **Pedal Number**   | 2                                                 |
| **Pedal Type**     | Switch                                            |
| **Event**          | Continuous Controllers (CC)                       |
| **Controller No.** | **66**                                            |
| **MIDI Channel**   | 1                                                 |
| **Min**            | 0                                                 |
| **Max**            | 127                                               |
| **Trigger Mode**   | **Reset** (ensures both press + release are sent) |

### The output you should now see from the MIDI readout:
- Press   → CC 66 127
- Release → CC 66 0


This will get you to the point where the fader is a smooth increase / decrease, and the momentary button is a maximum value on / off toggle. You can customize things like the CC number, midi channel, min / max values etc. until your heart is content, maybe you even want to change the behavior so it works less like the PLUS 3 does in the hardware world with expression inputs. 

Thanks for reading! I hope this was helpful for anyone who was struggling getting the PLUS 3 working in their software. If you have any questions or run into issues I *might* be able to help given I struggled through some challenges myself getting everything operational.

<div style="text-align: center;">
<a href="https://buymeacoffee.com/kylebeck" target="_blank" style="display: inline-block;"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" style="height: 60px !important;width: 217px !important;" ></a>
</div>
