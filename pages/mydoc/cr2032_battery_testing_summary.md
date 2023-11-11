---
title: CR2032 Battery Testing Summary
keywords: 2032, cr2032, coin battery, testing coin battery
last_updated: Dec 15, 2021
tags:
summary: "This page is under construction - stay tuned for updates"
sidebar: mydoc_sidebar
permalink: cr2032_battery_testing_summary.html
folder: mydoc
---
# Testing the CR2032 Coin Battery Summary
Questions which CR2032 is better and what are the differences in CR2032 coin batteries.  Because some cost a lot more than others, are they better? You would normally assume more expensive implies a better product.
So, the questions are:
- Is there a difference between different brands of CR2032 batteries?
- So how can we tell?

We can search the Internet for testing of CR2032 batteries. Most of what was find is that the more expensive manufacturers provide lots of test results, the cheap batteries do not provide that much information. What we see from the manufacturer’s steady state testing (like turning on the lights till the battery dies). is the normal lithium battery characteristics, when testing start the voltage will drop when put under load, then a long slow drop ending with a sudden fast roll off. A good example is the [Energizer CR2032 Product Data Sheet ](https://data.energizer.com/pdfs/cr2032.pdf).

In most real-world usage for coin batteries, such as with the [JemRF devices](https://www.jemrf.com), are not a steady state load, but a pulse load when the device transmits. Then there is a relatively long rest time before transmitting again. This cycle is a few milliseconds to transmit then from 1-to-5-minute sleep period. Like using a TV or Garage door opener, a short press of the button then a wait period.
I have also observed that a lithium battery will recover some when the load is removed. I assume this mode would lengthen the lifetime of the battery, so one additional question:
- Will pluse loads change the power curve?

## Test Plan
To better match real-world usage, the test conditions would need to be a pulse of load then a long rest and pulse again. To do that we built a test rig to hold and test 4 CR2032 batteries. The testing was for each battery to turn on an LED for .25 seconds, one at a time. Then repeat.  This cycle allowed each battery the same on and off time.  The off time being 3 times longer to allow for some battery recovery.
The normal lithium CR2032 battery operates at 2.8 volts. So testing was run until the batteries were below 2.4 volts.  While batteries in many devices will still operate below 2.4 volts, some test end voltage was needed and manufacture data show at 2.4 volts the battery has started the fast roll off phase.
## Batteries Tested
Here are the batteries tested so far:

|Brand	|Code for Testing	|General Cost	|Performance	|Cost Per Performance|
|-------|-------------------|---------------|---------------|-----------|
|NightKonic	|NCR2032	|0.25	|2	|1|
|Panasonic	|PCR2032	|0.5	|3	|2|
|Energizer	|ECR2032	|0.71	|3	|3|
|Duracell	|DCR2032	|1.17	|1	|4|
|Amazon	|ACR2032	|0.79	|3  |5|

## Conclusion
For now, my sample base is too small to draw a big conclusion about which is better. It does imply that the price is not a guarantee of the quality of power produced. Price can’t validate shelf life and repeatability, but I do not want to spend the next 10 years validating.
Testing to date does imply some may do a little better, it is still a price to performance issue for most of us.  For example, the Panasonic, Energizer and Amazon performing almost identically, but vary greatly in price.

While the Duracell CR2032 appears a performance winner, the NightKonic performed almost as well.  The real difference is toward the end of life the NightKonic results between batteries varies where the Duracell appears more consistent. From cost to performance the NightKonic is one quarter the cost of the Duracell.

For my sensor needs, this was not the difference I was expecting. For our bathroom scales, car fobs, a burst used to lock and unlock the car and remotes to change the TV channels, there is not much difference at all (well OK, channel surfers maybe).

The last question will the pulse testing chanage the power curve, the answer appears to be No. The only difference is the drop off is slower that a steady state load. Not a real supprise there.

I had been exclusively using Energizers for my critical needs, but going forward I am buying the cheaper NightKonic batteries. With the exception for hard-to-reach locations. For those, I will consider using the Duracell CR2032.

## Disclaimer
I have not received any funds, support, or direction of any kind from the different vendors. Testing was done for my own benefit at my cost to help my customers.

My testing will continue until I am satisfied that cheaper is a good answer, or I identify a really good battery at a good price.
