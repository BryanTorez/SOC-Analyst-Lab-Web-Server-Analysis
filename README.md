<h1>SOC Analyst Lab - Web Server Analysis (Tomcat)</h1>


<h2>Description</h2>
Ready for another network analysis walkthrough? In this walkthrough, we'll be going over a lab called Tomcat takeover by Cyber Defenders and my objective here is to help you obtain more confidence using wire shark and analyzing PCAPS. Let's go ahead and get started.


<h2>Applications Used </h2>
REMnux Malware Toolkit Website (https://docs.remnux.org/install-distro/get-virtual-appliance)
<br />
<br />
Cyber Defenders Website (https://cyberdefenders.org/)
<br />
<br />
Virustotal Website (https://www.virustotal.com/gui/home/upload)
<br />
<br />
Wireshark Website (https://www.wireshark.org/)

<h2>Walk-through Project:</h2>

<p align="center">
To get started with this lab you want to head to 'cyber.org' and create an account, if you haven't done so already. Once you've created an account and signed in, you want to head over to the search tab and search for 'Tomcat Takeover'. : <br/>
<br />
<img src="https://snipboard.io/I2l4SY.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
<br />
Look at the scenario. Here it says, "Our SOC team has detected suspicious activity on one of the web servers within the company's internet. In order to gain a deeper understanding of the situation, the team has captured network traffic for analysis. This PCAP file potentially contains a series of malicious activities that have resulted in the compromise of the Apache Tomcat web server. We need to investigate this incident further." : <br/>
<br />
<img src="https://snipboard.io/GMH5c3.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
To get started with the lab, I'll go ahead and click on 'Join Lab'. Then I'll click on 'Download Lab Files'. I'll go ahead and save this under my downloads directory. : <br/>
<br />
<img src="https://snipboard.io/ZukT8A.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/is8xlf.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/SDtpEq.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Now if you are following along I would highly recommend that you perform your analysis on a virtual machine and if you don't know how to get started with a virtual machine. I'll provide a video for you down below for you to take a look at. https://www.youtube.com/watch?v=nvdnQX9UkMY&t=256s&pp=ygUPdmlydHVhbCBtYWNoaW5l: <br/>
<br />
<img src="https://snipboard.io/Nl3L62.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Over to my downloads directory. Right-click then extract to this directory. The password is going to be 'cyberdefenders.org'. If you're not sure you can always head back over to the website where it says the pass is 'cyberdefenders.org'. : <br/>
<br />
<img src="https://snipboard.io/ywTGWV.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/o9jt7X.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/9HTYfd.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Now to download '7zip', you must head to '7-zip.com' and then click on download. Click on 'Okay' to extract the file. Now we should have a new directory. You can just head over there and double-click the web server PCAP. : <br/>
<br />
<img src="https://snipboard.io/gKY48R.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/R6gJ75.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Now if you're following along your Wireshark may look a bit different than mine. That is because I did use this previously in other labs. Here are some configurations that we'll just quickly go over just to make sure that you can follow along properly. First and foremost I am using Wireshark version 4.4 and the reason why I mentioned this is because some earlier versions of Wireshark can have some discrepancies. So if you are planning on following along I would highly recommend that you update your version to 4.4. : <br/>
<br />
<img src="https://snipboard.io/sXOaUg.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/aG9s2A.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
The next thing I want to mention here is the time. By default, your time column shouldn't look like mine. To change this you want to head over to 'View'. Scroll down to 'Time Display Format' and make sure that you select 'UTC Date and Time of Day'. Once you select that, your time should look like mine. Then you want to make sure to sort it by time by simply clicking on this column here. Once you do that we should be good to start analyzing this PCAP: <br/>
<br />
<img src="https://snipboard.io/uICqcE.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/AeMdox.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
When it comes to network analysis, particularly with a PCAP, the first thing I like to do here is to take a look at the 'Statistics' Tab and in particular the 'Capture File Properties'. From here we can see that the first packet was on 2023-09-10 at 18:13:06 and the last packet was at 18:27:37 with a duration of 14 minutes and 30 seconds. : <br/>
<br />
<img src="https://snipboard.io/FUktWl.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/fROXFL.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Now one thing to keep in mind is that your time might be different than mine and that is because the timing for the first and last packet is based on your computer's time zone. Meaning if I was using a PST time zone on my computer then the first and last packet time would change accordingly. In my instance, I am using UTC on my computer so that means the first and last packet for this particular PCAP is in UTC time. That is just something to keep in mind. : <br/>
<br />
<br />
<br />
<br />
...but if you take a look at the packets here. The timing shouldn't be reflected in your computer time zone because you did select the 'UTC Date and Time'. Once you select that you're essentially telling Wireshark to display everything in UTC time.: <br/>
<br />
<img src="https://snipboard.io/5F8HSK.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/JyezoA.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
So now that we've gone over the first and last packet. Looking at the bottom, we can see that the total number of packets captured was 2,070 packets. Now you might be thinking well that was kind of useless in a lab environment too. But you do want to build a habit of checking those properties because if somebody were to hand you a PCAP, you want to make sure that you're analyzing the correct one. : <br/>
<br />
<img src="https://snipboard.io/Z81AFW.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
The next thing that you want to do here is to click on 'Statistics' and go over to 'Protocol Hierarchy'. This will tell you all of the protocols that exist within this particular PCAP. We can see that there are UDP, TCP, SMB, multicast DNS, SSH, and HTTP protocols. : <br/>
<br />
<img src="https://snipboard.io/Mocpg9.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Then let's go over to 'Conversations' and head over to 'ipv4'. From here, I like to sort it by bytes. That way we can see who are the top talkers. Now from the top here, we can see that the top talker is coming from this address of '14.0.0.120' talking to '10.0.0.112'. So that is something to keep a note on my notepad. Aswell as the second entry of '10.0.0.115'.: <br/>
<br />
<img src="https://snipboard.io/vZNHBz.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/nq89Zg.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Go ahead and select 'TCP'. We have 9,465 entries. That's quite insane. And similar to what we did earlier, go ahead and sort it by bytes. Now the highest bytes are at the top and we can see it's going to ports '8080', '22', and '445' which is SMB, '80', and '443'. So let's make a note out of that.: <br/>
<br />
<img src="https://snipboard.io/USYP5V.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/jDNHeJ.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/gw8H2K.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Let's begin our analysis. Starting from the top, we can see that there is a communication initiated from our '10.0.0.115' address over to '10.0.0.105' on Port 445 what that tells me is that 105 is a file server of some sort because it does have SMB opened now if we go over to the SMB protocol which is on packet number four we can expand the packets by clicking on smb2 and we can actually see the header of the SMB now if we take a look at the session setup response on packet number n and expand SMB under the smb2 header we could actually see the: <br/>
<br />
<img src="https://snipboard.io/SKWgji.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/t6dWjO.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/296s5t.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
: <br/>
<br />
<img src="https://snipboard.io/SKWgji.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/t6dWjO.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/296s5t.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
: <br/>
<br />
<img src="https://snipboard.io/SKWgji.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/t6dWjO.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/296s5t.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
: <br/>
<br />
<img src="https://snipboard.io/SKWgji.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/t6dWjO.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/296s5t.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
: <br/>
<br />
<img src="https://snipboard.io/SKWgji.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/t6dWjO.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/296s5t.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
: <br/>
<br />
<img src="https://snipboard.io/SKWgji.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/t6dWjO.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/296s5t.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
: <br/>
<br />
<img src="https://snipboard.io/SKWgji.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/t6dWjO.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/296s5t.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
: <br/>
<br />
<img src="https://snipboard.io/SKWgji.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/t6dWjO.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/296s5t.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
