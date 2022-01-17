---
title: CR2032 Battery Testing
keywords: 2032, cr2032, coin battery, testing coin battery
last_updated: Jan 13, 2022
tags:
summary: "This page is a work in progress - stay tuned for updates"
sidebar: mydoc_sidebar
permalink: cr2032_battery_testing.html
folder: mydoc
---
# Testing the CR2032 Coin Battery
Some CR2032 coin batteries cost a lot more than others, are they better? You would assume more expensive implies a better product.

So, the questions are:
- Is there a difference between different brands of CR2032 batteries?
- So how can we tell?

We can search the Internet for testing of CR2032 batteries. Most of what we find is that the more expensive manufacturers provide lots of test results. The cheap batteries do not provide that much information. What we see from the manufacturer’s steady state testing (like turning on the lights till the battery dies) is the normal lithium battery characteristics, when testing starts, the voltage will drop when you turn on the light, then lithium will go a long time with little voltage drop. Near the end of battery life, roughly the last 10 percent, the voltage will follow fast roll off. A good example is the [Energizer CR2032 Product Data Sheet ](https://data.energizer.com/pdfs/cr2032.pdf).

 Most real-world usage for coin batteries, such as with the [JemRF devices](https://www.jemrf.com), are not a steady state load, but a pulse load when the device transmits. Then there is a relatively long rest time before transmitting again. This cycle is a few milliseconds to transmit, then from 1-to-5-minute sleep period. Like using a TV or Garage door opener, a short press of the button then a wait period.
I have also observed that a lithium battery will recover some when the load is removed. I assume this mode would lengthen the lifetime of the battery, so one additional question:
- Will pulse loads change the power curve?

## Test Plan
To better match real-world usage, the test conditions would need to be a load pulse, then a long rest and pulse again. To do that, we built a test rig to hold and test 4 CR2032 batteries. The testing was for each battery to turn on an LED for .25 seconds, one at a time, then repeat.  This cycle allowed each battery the same on and off time.  The off time being 3 times longer to allow for some battery recovery.
The normal lithium CR2032 battery operates at 2.8 volts. So testing was run until the batteries were below 2.4 volts.  While batteries in many devices will still operate below 2.4 volts, I picked 2.4 volts based on manufacture data, which show at 2.4 volts the battery has started the fast roll off phase.
## Testing the Batteries
Using the test plan, a test cycle would emulate a brief transmission of a wireless device.  The LED load is about that of the [JemRF devices](https://www.jemrf.com) when they transmit.  Each battery is connected to an individual LED light to emulate the transmission load of about 11 milliamps of power. Each battery was pulsed ¼ of a second. There were 4 batteries tested per set.  Each battery will be on .25 seconds and off for .75 seconds.
Testing for each set of batteries ran from 6 to almost 10 days.  The process pulsed the batteries once a second, or some 86,400 times a day.  After 6 days, the number of pulses (518,400) would, if stretched out at a pulse rate of once a minute, would equate to about 14 months of usage.

## Test Results
The results of the batteries tested so far showed all did well, with one outlasting all the others. My method of ranking the batteries was to compare their cost against their performance.
First, I needed to create a performance rating. To do that, I assigned a ranking for the number of days the battery lasted. I then used this chart to assign a ranking to each battery. Then for comparison, using the batteries that lasted 6-7 days as average, I show a percentage improvement value for each extra day the battery lasted.

|Performance(P)|  Days  |Percent Better|
|:----:|:------:|:------:|
|    1   |  6-7   |Average|
|    2   |  7-8   |14%|
|    3   |  8-9   |25%|
|    4   |  9-10  |33%|
|    5   |  10-11  |40%|

 The chart below is the summary of the batteries tested so far.  It compares their cost (if bought 10 at a time) and how they performed.  The rating was based on how long they remained above the cut off, with the best being #1.  I weighted the cost of the battery with the performance to create the Cost(C)/ Performance(P) value, and ordered the chart by the C/P Order.

|Brand  |Code for Testing|General Cost (C) |Days Working|Cost Per Performance|C/P Order|
|-------|-------------------|:---------------:|:---------------:|:--------------:|:-----------:|
|NightKonic |NCR2032    |$ 0.25   |8-9|.083 |1|
|PGSonic	|PGCR2032	|$ 0.45 |8-9 |.150|2|
|Duracell   |DCR2032    |$ 1.21   |10-11|.234  |3|
|JOOBEF 	|GCR2032	|$ 0.25 |6-7|.250|4|
|Panasonic  |PCR2032    |$ 0.5    |6-7|.500  |5|
|Energizer  |ECR2032    |$ 0.76   |6-7|.710  |6|
|Amazon |ACR2032    |0.79   |6-7|.790  |7|

Because prices are under constant change, your price could change the Cost to Performance Order.  These prices were what I paid at the time I ordered them or their cost at this publication.

## Conclusion
For now, my sample base is too small to draw a big conclusion about which is better. It does imply that the price is not a guarantee of the quality of power produced. Price could validate a long shelf life and/or consistency of performance, but I do not want to spend the next 10 years testing batteries.

Testing to date does imply some may do a little better, it is still a price to performance issue for most of us. For example, the Panasonic, Energizer and Amazon performing almost identically, but vary greatly in price.

While the Duracell CR2032 appears a performance winner, the NightKonic performed almost as well. The real difference is toward the end of life, the NightKonic results between batteries varies, where the Duracell appears more consistent. From cost to performance, the extra long run time of the Duracell makes it a battery worth considering; but with NightKonic at one quarter the cost of the Duracell, the NightKonic appears to be a good choice.

For my sensor needs, there was not the difference between batteries that I was expecting. For our bathroom scales, key fobs, a burst used to lock and unlock the car and remotes to change the TV channels, there is not much difference at all (well OK, channel surfers maybe).

The last question of will the pulse testing change the power curve, the answer is No. The only difference is the drop off is slower than a steady state load.  That's not a real surprise.

In Summary, all the batteries tested to date, should last well over a year in my sensors, even updating once a minute.  With the normal update setting of once every 5 minutes, I would expect devices to be operating just fine for two years or more.

## Disclaimer
I have not received any funds, support, or direction of any kind from the different vendors. Testing was done for my own benefit at my cost to help my customers.

I have no plans to test any more vendor products, as this is getting expensive, but my testing will continue until I am satisfied with the consistancy of the results. I also want to be satisfied that cheaper is a good answer, or I identify a really good battery at a good price.

***
## <center>Full Test Report</center>
***
### Testing Process
As described above, the test conditions would create a pulse load, then a long rest and pulse again.
To do that I built a [test rig](https://jemrf.github.io/RF-Documentation/images/BatteryTestSet.gif) to hold and test 4 CR2032 batteries. I used a 16 bit A/D converter to read the voltage and connected it all up to a Raspberry Pi. The software would pulse a load on each battery one at a time for a few minutes then read the voltage.
Almost immediately we learned logging data every few minutes was a waste of effort because the change was very slow, so logging was changed to every 6 minutes, still too often, but for now it works.
The test cycle will emulate a brief transmission with an led load of 11 ma, for each battery, one at a time for .25 seconds. There will be 4 batteries tested so each battery will be on .25 seconds and off for .75 seconds.

There are two loops to the test cycle. First the internal loop runs the load cycle 20 times, then prints on screen the voltages to provide a visual display test is running. The outer loop cycles the internal loops 20 times before logging the voltage to the database. The result is the battery is load tested 400 times before data is logged. This 400 test cycle results in data logging every 6 minutes.
The test will run until two or more batteries have a voltage drop below 2.5 volts. Then, I export the data and I plot the results.
 - Note: In reviewing the results from Test 2 while Test 3 was running, I realized the cutoff should be 2.4 volts and used 2.4 volts as the cutoff point for Test 3 and all tests after it.

### Test Run 1
The first test was to validate the test set. Step one was to verify the test stand was working and correct any wiring and connection issues.
Next was adjusting the loops to lengthen the time between samples.
Last was creating the database tables and getting the database link to stay connected.  My Synology box was set for nightly full saves, which I discovered disables the database during that time causing the program to fail and exit when it lost the connection. I opted for fail vs software retry, because if there were lots of drops then the results would be at risk.

### Test Run 2
Test 2 was the first real test.  I used two new Energizer 2032 batteries and two new NightKonic CR2032 I purchased from Amazon. The test ran for 6 days and over 572,000 cycles. Which if extracted to once a minute, would be over a year of sustained usage. Below is the plot of the results.

{% include image.html file="cr2032_test_2.jpg" alt="Test Run 2 Energizer and NightKonic"%}
[Test run 2 Results using Energizer and Nightkonic CR 2032 batteries](https://jemrf.github.io/RF-Documentation/images/cr2032_test_2.jpg)

Like all good tests to show off, something strange seems to happen. One of the NightKonic batteries went to almost 0 volts.  While the test was running, I did see the #4 led was not coming on. My first thought was that my test set had broken, so I removed the battery and verified its voltage, it was .8 volts.  The test set checked OK, so I thought maybe the cat had walked across the set and shorted the battery. I checked the wire to be sure that would not happen again. I did observe the battery was recovering, so I put it back to finish the test.  It was not until I saw the graph that I found out it happened twice. [Link to Full Graph and it is weird.](https://jemrf.github.io/RF-Documentation/images/cr2032_test_2_fullplot.jpg)

The two Energizer batteries had very consistent graphs.  The surprise was the performance of the other NightKonic by outlasting the Energizers.
Links to Amazon where the base cost of Energizer is $.95 each and the base cost of the NightKonic is $.25.

[Energizer on Amazon](https://www.amazon.com/s?k=energizer+ecr2032&ref=nb_sb_noss_1)

[NightKonic on Amazon](https://www.amazon.com/s?k=nightkonic+cr2032+3v+lithium+battery&ref=nb_sb_noss_1)

### Test Run 3:
Test 3 shows the results using two Panasonic batteries, one Energizer and one NightKonic.  The configuration was #1 and #3 were Panasonic batteries, #2 was Nightkonic and to be sure the slot #4 battery holder was not the problem, I put the Energizer in slot 4 because both had the same result plot in Test 2.  Test results after 6 days and over 572,000 cycles.
{% include image.html file="cr2032_test_3.jpg" alt="Test Run 3 Panasonic, Energizer and NightKonic"%}

[Test run 3 Results using 2 Panasonic batteries, one Energizer and one NightKonic.](https://jemrf.github.io/RF-Documentation/images/cr2032_test_3.jpg)

From the results you can see that the Panasonic tracked with the Energizer following the same plot as Test 2.  The NightKonic again had the same plot result as the good battery in test 2.

The blip at the end of the curves was caused because I stopped the test for a minute then decided to continue for another day.

The Amazon average price for Panasonic is $.50.

[Panasonic on Amazon](https://www.amazon.com/s?k=panasonic+cr2032+3v+battery&ref=bnav_search_go)

### Test 3 Extended.
In some RF transmitters their performance drops when the voltage is 2.4 and less, that was my reasoning for stopping the test above. But I thought I would continue test 3 for another 24 hours to see if we had reached the end.  The result is you can see the normal lithium rapid drop off for both the Panasonic and Energizer batteries while the NightKonic is just dropping below the usable level.  Again the blip is the same marker from above when I stopped then resumed the test.

{% include image.html file="cr2032_test_3_extended.jpg" alt="Test Run 3 Extended"%}
[Test Run 3 Extended 24 hours with Panasonic, Energizer and NightKonic batteries.](https://jemrf.github.io/RF-Documentation/images/cr2032_test_3_extended.jpg)

### Test 4 Panasonic and NightKonic
This is a retest of both batteries. I let the test run until all batteries were below the 2.4 volt cutoff.
Because of the strange test result with the first set of NightKonic,
The real goal is to test three more NightKonic batteries.
I did a random selection of NightKonic from different purchases.
The results were without issue, the Panasonic performed just like the previous two tested.
The NightKonic performed perfectly, again performing above the cut off two days after the Panasonic dropped out.
You can see some deviations in the NightKonic cures one dropped below cut off a day before the other two.
That to me would imply some quality control issues with the NightKonic.

{% include image.html file="cr2032_test_4.jpg" alt="Test Run 4 Extended"%}
[Test Run 4 Panasonic and NightKonic batteries.](https://jemrf.github.io/RF-Documentation/images/cr2032_test_4.jpg)

### Test 5 Amazon and Duracell
This test was the longest test, lasting 11 days.
This test was interrupted by database lock out on the second day into causing the test to be suspended for almost 8 hours.
Again, as before when this happened, you can see the spike from the batteries recovering.
The result of the suspension extended the test results a day.
The real reason for the additional days was the performance of the Duracell batteries.
While the most expensive tested so far, they lasted the longest before dropping below the 2.4 volt cutoff. The Amazon CR2032 followed the curves of the Energizer and Panasonic batteries.

The Duracell best price I found was $1.21 each.  The Amazon cost $1.37 each.

[Amazon CR2032 Battery](https://www.amazon.com/AmazonBasics-CR2032-Lithium-Coin-Cell/dp/B0787K2XWZ/ref=psdc_15745581_t1_B00HVS2TCQ)

[Duracell on Amazon](https://www.amazon.com/gp/product/B019QPD9LG/ref=ox_sc_act_title_1?smid=A19DY5EK03NION&psc=1)

{% include image.html file="cr2032_test_5.jpg" alt="Test Run 5 "%}
[Test Run 5 Amazon and Duracell batteries.](https://jemrf.github.io/RF-Documentation/images/cr2032_test_5.jpg)

### Test 6 PGSonic and JOOBEF by GutAlkaLi
Test 6 was a smooth test with no interruptions or strange events.  This test lasted almost 9 days. Testing the PGSonic and JOOBEF batteries by GutAlkaLi, with the PGSonic lasting almost two days longer than the JOOBEF.   That adds a new battery to the high performers, the PGSonic curves are very close to the Nightknoic.  A future run off test between the PGSonic and the Nightkonic are needed.

[ JOOBEF by GutAlkaLi on Amazon](https://www.amazon.com/Lithium-Battery-Electronic-Calculators-Watches/dp/B07SBMM72C/ref=sr_1_2?keywords=GutAlkaLi+cr2032&qid=1642128749&sr=8-2)

[PGSonic on Amazon]( https://www.amazon.com/CR2032-3V-Lithium-Battery-10pcs/dp/B098ZW4GDY/ref=sr_1_8?crid=T2PSYLYDYD3D&keywords=pgsonic+cr2032&qid=1642128844&sprefix=pgsonic+cr2032%2Caps%2C1471&sr=8-8)

{% include image.html file="cr2032_test_6f.jpg" alt="Test Run 6"%}
[Test run 6, PGSonic and JOOBEF](https://jemrf.github.io/RF-Documentation/images/cr2032_test_6f.jpg)
### In Work
I have one other brands on Amazon to test; JunPower. I will match it with PGSonic & Nightkonic. It is Janurary 13, 2022, I will update this in a few weeks with those test results as each completes, as well as a joint retest of the Duracell vs the NightKonic.

