---
title: CR2032 Battery Testing
keywords: 2032, cr2032, coin battery, testing coin battery
last_updated: Dec 15, 2021
tags:
summary: "This page is under construction - stay tuned for updates"
sidebar: mydoc_sidebar
permalink: cr2032_battery_testing.html
folder: mydoc
---
# Testing the CR2032 Coin Battery
Some CR2032 coin batteries cost a lot more than others, are they better? You would assume more expensive implies a better product.
So the question is: Is there a difference between different brands of CR2032 batteries?

### So how can we tell?
We can search the Internet for testing of CR2032 batteries.  Most of what we find is that the more expensive manufacturers provide lots of test results, the cheap batteries do not provide that much information.
What we see from the manufacturer's steady state testing is the normal lithium battery characteristics, a voltage drop when put under load, a long slow drop then a fast roll off.

In most real world usage such as with the JemRF devices, the usage of the CR2032 battery is not a steady load, but a pulse load when the device transmits. Then there is a relatively long rest time before transmitting again. This cycle is a few milliseconds to transmit then 1 to 5 minute sleep period. I have also observed that a lithium battery will recover some when the load is removed. I assume this mode would lengthen the life time of the battery, but would that change the curve?

### Testing Process
So the test conditions would need to be a pulse of load then a long rest and pulse again.
To do that I built a test rig to hold and test 4 CR2032 batteries. I used a 16 bit A/D converter to read the voltage and connected it all up to a Raspberry Pi. The software would pulse a load on each battery one at a time for a few minutes then read the voltage.
Almost immediately we learned logging data every few minutes was a waste of effort because the change was very slow, so logging was changed to every 6 minutes, still too often, but for now it works.
The test cycle will turn on an led load of 11 ma, for each battery, one at a time for .25 seconds. There will be 4 batteries tested so each battery will be on .25 seconds and off for .75 seconds.

There are two loops to the test cycle, first the internal loop runs the load cycle 20 times then prints on screen the voltages to provide a visual display test is running. The outer loop cycles the internal loops 20 times before logging the voltage to the database. The result is the battery is load tested 400 times before data is logged. This 400 test cycle results in data logging every 6 minutes.
The test will run until two or more batteries have a voltages drop below 2.5 volts. Then I export the data and l plot the results.

### Test Run 1
The first test was a test to validate the test set.
First the test stand was working and correct any wiring and connection issues.
Next was adjusting the loops to lengthen the time between samples
Last was creating the database tables and getting the database link to stay connected.  My Synology box was set for nightly full saves, which I discovered disables the database during that time causing the program to fail and exit when it lost the connection. I opted for fail vs software retry because if there were lots of drops then the results would be at risk.

### Test Run 2
Test 2 was the first real test.  I used two new Energizer 2032 batteries and two new NightKonic CR2032 I found from Amazon. The test ran for 6 days and over 572,000 cycles. Below is the plot of the results.

{% include image.html file="cr2032_test_2.jpg" alt="Test Run 2 Energizer and NightKonic"%}
Test run 2 Results using Energizer and Nightkonic CR 2032 batteries

Like all good tests to show off, something strange seems to happen. One of the NightKonic batteries went to almost 0 volts.  While the test was running i did see the #4 led was not coming on. My first thought was that my test set had broken, so I removed the battery and verified its voltage, it was .8 volts.  The test set checked OK. so I thought maybe the cat had walked across the set and shorted the battery. I checked the wire to be sure that would not happen again. I did observe the battery was recovering so I put it back to finish the test.  It was not until I saw the graph that I found out it happened twice.
The two Energizer batteries had very consistent graphs.  The surprise was the performance of the other NightKonic by outlasting the Energizers.
Links to Amazon where the base cost of Energizer is $1.00 each and the base cost of the NightKonic is $.25.
[Energizer on Amazon](https://www.amazon.com/s?k=energizer+ecr2032&ref=nb_sb_noss_1)
[NightKonic on Amazon](https://www.amazon.com/s?k=nightkonic+cr2032+3v+lithium+battery&ref=nb_sb_noss_1)

### Test Run 3:
Test 3 shows the results using two Panasonic batteries, one Energizer and one NightKonic.  The configuration was #1 and #3 were Panasonic batteries, #2 was Nightkonic and to be sure the slot #4 battery holder was not the problem, I put the Energizer in slot 4 because both had the same result plot in Test 2.  Test results after 6 days and over 572,000 cycles.
{% include image.html file="cr2032_test_3.jpg" alt="Test Run 3 Panasonic, Energizer and NightKonic"%}

Test run 3 Results using 2 Panasonic batteries, one Energizer and one NightKonic.

From the results you can see that the Panasonic tracked with the Energizer following the same plot as Test 2.  The NightKonic again had the same plot result as the good battery in test 2.

The blip at the end of the curves was caused because I stopped the test for a minute then decided to continue for another day.

The Amazon average price for Panasonic is $.50.
[Panasonic on Amazon](https://www.amazon.com/s?k=panasonic+cr2032+3v+battery&ref=bnav_search_go)


### Test 3 Extended.
In some RF transmitters there performance drops when the voltage is 2.4 and less, that was my reasoning for stopping the test above. But I thought I would continue test 3 for another 24 hours to see if we had reached the end.  The result is you can see the normal lithium rapid drop off for both the Panasonic and Energizer batteries while the NightKonic is just dropping below the usable level.  Again the blip is the same marker from above when I stopped then resumed the test.

{% include image.html file="cr2032_test_3_extended.jpg" alt="Test Run 3 Extended"%}
Test Run 3 Extended 24 hours with Panasonic, Energizer and NightKonic batteries.

