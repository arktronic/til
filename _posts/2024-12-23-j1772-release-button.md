---
layout: post
date: 2024-12-23
title: Troubleshooting a stuck J1772 release button
tags:
- j1772
- evse
---

Certain electric car charger models (which shall remain nameless) have a penchant for breaking. One specific type of issue I've encountered multiple times is when the handle is plugged into a car, but charging does not initiate, and the car displays a message along the lines of, "verify everything is plugged in securely".

Today, I learned that the nature of the particular issue I keep seeing is that the charging handle's cable release button gets stuck in the pressed position — electrically, not mechanically. In all cases, this has meant we RMA the whole charger, but convincing the manufacturer that this is indeed the issue has been... challenging, to say the least. Thankfully, I finally had a conversation with a support person who was technical enough that they were able to tell me exactly what to check.

**WARNING: ⚡ If you are planning on doing anything involving electricity, make sure you (1) know what you're doing, and (2) always power equipment off before doing anything with it! Level 2 EVSEs are 240V and can kill you pretty easily if you do bad things with them!**

The pinout of the J1772 connector is as follows:

```
       |  |
     --------
   /          \
  (  L1    L2  )
  (            )
  ( PP      CP )
   \    PE    /
     --------
```

Apologies for the ASCII art. I don't practice that a whole lot.

Anyway, the two important pins for our purposes are PE (Protective Earth, i.e., ground) and PP (Proximity Pilot). According to [this website](https://docs.powerflex.com/reference/how-it-works-l2-ev-chargers/?v=1.1.0), the resistance between these two pins when cable release button is at rest should be around 150Ω, but when pressed, the resistance should increase to around 480Ω.

So, to figure out if the button is stuck in the pressed position, **TURN OFF POWER TO THE CHARGER**, and then simply measure the resistance between those two pins. When I did that with the latest faulty charger I'm dealing with, the resistance was around 482Ω regardless of whether I was pressing the cable release button. Mystery solved, and I now have another tool in my toolbox for quickly getting to the root cause of an EVSE malfunction.
