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
<br />
<img src="https://snipboard.io/QuWn4h.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/3fkeXY.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Look at the scenario. Here it says, "Our SOC team has detected suspicious activity on one of the web servers within the company's internet. In order to gain a deeper understanding of the situation, the team has captured network traffic for analysis. This PCAP file potentially contains a series of malicious activities that have resulted in the compromise of the Apache Tomcat web server. We need to investigate this incident further." : <br/>
<br />
<br />
<img src="https://snipboard.io/WrklbE.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/9mBwVY.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
To get started with the lab, I'll go ahead and click on 'Join Lab'. Then I'll click on 'Download Lab Files'. I'll go ahead and save this under my downloads directory. : <br />
<br />
<img src="https://snipboard.io/qaAEWC.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/n6MmvQ.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/LBwPD0.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Now if you are following along I would highly recommend that you perform your analysis on a virtual machine and if you don't know how to get started with a virtual machine. I'll provide a video for you down below for you to take a look at. https://www.youtube.com/watch?v=nvdnQX9UkMY&t=256s&pp=ygUPdmlydHVhbCBtYWNoaW5l: <br/>
<br />
<br />
<br />
<br />
Over to my downloads directory. Right-click then extract to this directory. The password is going to be 'cyberdefenders.org'. If you're not sure you can always head back over to the website where it says the pass is 'cyberdefenders.org'. : <br/>
<br />
<br />
<img src="https://snipboard.io/TGOKLa.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/XUiw5p.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/1D9YvG.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Now to download '7zip', you must head to '7-zip.com' and then click on download. Click on 'Okay' to extract the file. Now we should have a new directory. You can just head over there and double-click the web server PCAP. : <br/>
<br />
<br />
<img src="https://snipboard.io/Rqyg5i.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/RPGd9E.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/cBSDPV.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Now if you're following along your Wireshark may look a bit different than mine. That is because I did use this previously in other labs. Here are some configurations that we'll just quickly go over just to make sure that you can follow along properly. First and foremost I am using Wireshark version 4.4 and the reason why I mentioned this is because some earlier versions of Wireshark can have some discrepancies. So if you are planning on following along I would highly recommend that you update your version to 4.4. : <br/>
<br />
<br />
<img src="https://snipboard.io/STg3Qo.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
The next thing I want to mention here is the time. By default, your time column shouldn't look like mine. To change this you want to head over to 'View'. Scroll down to 'Time Display Format' and make sure that you select 'UTC Date and Time of Day'. Once you select that, your time should look like mine. Then you want to make sure to sort it by time by simply clicking on this column here. Once you do that we should be good to start analyzing this PCAP: <br/>
<br />
<br />
<img src="https://snipboard.io/sdGecQ.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/N0Wcvh.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/F0GCPR.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
When it comes to network analysis, particularly with a PCAP, the first thing I like to do here is to take a look at the 'Statistics' Tab and in particular the 'Capture File Properties'. From here we can see that the first packet was on 2023-09-10 at 18:13:06 and the last packet was at 18:27:37 with a duration of 14 minutes and 30 seconds. : <br/>
<br />
<br />
<img src="https://snipboard.io/tDFKBQ.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/c7HfAe.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Now one thing to keep in mind is that your time might be different than mine and that is because the timing for the first and last packet is based on your computer's time zone. Meaning if I was using a PST time zone on my computer then the first and last packet time would change accordingly. In my instance, I am using UTC on my computer so that means the first and last packet for this particular PCAP is in UTC time. That is just something to keep in mind. : <br/>
<br />
<br />
<br />
<br />
...but if you take a look at the packets here. The timing shouldn't be reflected in your computer time zone because you did select the 'UTC Date and Time'. Once you select that you're essentially telling Wireshark to display everything in UTC time.: <br />
<br />
<img src="https://snipboard.io/nx1b4L.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/4i02pE.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
So now that we've gone over the first and last packet. Looking at the bottom, we can see that the total number of packets captured was 2,070 packets. Now you want to build a habit of checking those properties because if somebody were to hand you a PCAP, you want to make sure that you're analyzing the correct one. : <br/>
<br />
<br />
<img src="https://snipboard.io/n5ow8M.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
The next thing that you want to do here is to click on 'Statistics' and go over to 'Protocol Hierarchy'. This will tell you all of the protocols that exist within this particular PCAP. We can see that there are UDP, TCP, SMB, multicast DNS, SSH, and HTTP protocols. : <br/>
<br />
<br />
<img src="https://snipboard.io/nJ3N5P.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/jfVLmz.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Then let's go over to 'Conversations' and head over to 'ipv4'. From here, I like to sort it by bytes. That way we can see who are the top talkers. Now from the top here, we can see that the top talker is coming from this address of '14.0.0.120' talking to '10.0.0.112'. So that is something to keep a note on my notepad. Aswell as the second entry of '10.0.0.115'.: <br/>
<br />
<br />
<img src="https://snipboard.io/b8MsiB.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/DbfYye.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/YZbg35.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Go ahead and select 'TCP'. We have 9,465 entries. That's quite insane. And similar to what we did earlier, go ahead and sort it by bytes. Now the highest bytes are at the top and we can see it's going to ports '8080', '22', and '445' which is SMB, '80', and '443'. So let's make a note out of that.: <br/>
<br />
<br />
<img src="https://snipboard.io/mGQHJi.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/zG9jXF.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/c4uNzX.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Let's begin our analysis. Starting from the top, we can see that there is a communication initiated from our '10.0.0.115' address over to '10.0.0.105' on Port 445. What that tells me is that '105' is a file server of some sort because it does have SMB opened. Now if we go over to the SMB protocol which is on packet number four, we can expand the packets by clicking on SMB2 and we can actually see the header of the SMB.: <br/>
<br />
<br />
<img src="https://snipboard.io/zJ2ZTo.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/YvO08z.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Now if we take a look at the session setup response on packet number nine and expand SMB under the smb2 header we could actually see the username domain and the host computer that initiated the request. So from here we can see that the account was 'root', under the domain of 'WORKINGROUP', and the host-name is 'CYBERDEFENDERS VIRTUAL-MACHINE'. So what I'll do here is put it in my notepad, aswell as the '10.0.0.105' IP. : <br/>
<br />
<br />
<img src="https://snipboard.io/oaNOK7.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/znDiSc.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/w2CVoG.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Scrolling down here, I'm not going to go super deep into what these fields mean for SMB. So instead I am going to leave a link down in the description for you if you wanted to learn more about it. If I take a look here I do see a PDF document called work_report 2023 PDF.
<br />
<br />
<img src="https://snipboard.io/nMTjA9.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/EyAQWi.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
So what I can do here is actually try downloading this PDF document by heading over to "File". Click on "Export Objects". Select "SMB". Here we can see the "work_report" file. There one from '2023' and another from '2022'. We could actually just save both of them under "Downloads".
<br />
<br />
<img src="https://snipboard.io/Py5bwi.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/oBGObE.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/xuDLYB.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
We can head over to our downloads directory. I'll hold shift and right-click. I'll open up Powershell. I'll type in "Get-FileHash" and hit "Tab". I see the work_report 2022 selected. So I'll go ahead and hit "Enter". Then, we'll see the sha256 file hash.
<br />
<br />
<img src="https://snipboard.io/TuY9LJ.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/nCEDmh.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/Zcixb4.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
The next thing I can do is go over to VirusTotal and we can search up that hash. Now, we see no security vendors flagged this file as malicious. Does that mean it's safe? Definitely not, but it's a start. Let's do the same for the '2023'. Copy that out and paste. Once again, same thing. No security vendors flagged this file as malicious.
<br />
<br />
<img src="https://snipboard.io/uGVwgl.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/V2uOLI.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/gt2OCN.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Now taking a look at the "File Type", it is "Text" with the "Magic" being "ASCII text". What that means is that I can actually just right-click and edit with notepad. 
For the '2022' file it says, "Work Report for year 2022...". The '2023' file is almost identical to '2022' file.
<br />
<br />
<img src="https://snipboard.io/uQ9O72.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/C8RKzY.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/GpguhC.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/gPi7kc.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Now that we got that out of the way. Go ahead and close that out. There is just constant communication towards '115' and '105'. I'm going to skip over a lot of the SMB stuff. So now we can see SSH connection starting from packet '137'. Our Cyber Defenders virtual machine initiated a SSH session to the IP of '10.0.0.112' and we can see that it is a "SYN".
<br />
<br />
<img src="https://snipboard.io/QnR15j.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/RV2rPu.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/2vwsEV.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Our '112' was like, "Hey! I'm alive." So it's a "SYN, ACK". Then the last handshake '115', said, "Hey! How's it going! So it's an "ACK". Zn SSH connection was successfully established. Okay, so that tells me that '112' is an SSH server. Now, we continue to scroll down since SSH is encrypted. There isn't really too much here.
<br />
<br />
<img src="https://snipboard.io/2vwsEV.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/vVZ6bO.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/Jrfd75.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/3Xbkql.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
On packet '685'. Our IP address of '115' communicates over to '112' on port '8080' and this is our first HTTP protocol. What I can do is right-click this. Click on "Follow". Select "HTTP Stream..." Here we can see the packet itself. Taking a look at the user agent, it is "Mozilla/5.0" and I also see "Ubuntu:Linux". What that tells me is that the Cyber Defenders virtual machines operating system is Ubuntu.
<br />
<br />
<img src="https://snipboard.io/nGBmUO.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/sAKIol.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/WzefVQ.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/pO8zS9.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Looking at the server response, we can see that the title is "Apache Tomcat", specifically with the version of '7.0.88'. Now copy and paste that into the notepad. So that means our SSH server is also our Apache Tomcat server. Now, it's getting a lot more interesting.
<br />
<br />
<img src="https://snipboard.io/9xT0Yq.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/2B0JLS.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
I'll go ahead and remove my TCP stream. If we look over to our notepad... rather than scrolling down and taking a look at all of these events since that's going to take forever. We want to start drilling down into our top IP address, which is '14.0.0.120' on our notepad.
<br />
<br />
<img src="https://snipboard.io/oxGZ6a.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
So I'll go ahead and copy this. Then type in "ip.addr==" and paste that in. Hit "Enter". Now, if you take a look at packet '1091', '1092', '1093', '1094', '1095' and continue scrolling down. You can see a bunch of "SIN" requests, which is a clear indicator of a "SIN" scan.
<br />
<br />
<img src="https://snipboard.io/CIid1o.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/X5u0Gl.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
It's targeting port '256', '443', '199', '113, '25', '3306', and many more. What we can do is take a look at what ports are opened on our Apache Tomcat server. To do this, I'll look at the "SYN, ACK" on number '1108'. I'll expand the "Transmission Control Protocol". For "Flag", see how it says "SYN". I'll go ahead and right-click this. Select "Prepare as Filter" and click on "...and selected".
<br />
<br />
<img src="https://snipboard.io/5xqLZ2.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/z9rxmF.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/RnoVub.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/85HaxY.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
What I also want to do is change my filter to look at the source IP address of '10.0.0.112'. Where the "Destination IP" is '14.0.0.120'. So to change that, I'll type in "(ip.src == 10.0.0.112 && ip.dst == 14.0.0.120)&&(tcp.flags == 0x0012)". Hit "Enter".
<br />
<br />
<img src="https://snipboard.io/okWpBw.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/BGgXck.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Now we can see a bunch of "SYN,ACK's". These are all of the ports that are open. Including, port '22', port '8080' and port '8009' that is open. So there are three open ports. Let's go ahead and make a note out of that. Let's go ahead and rerun our previous query.
<br />
<br />
<img src="https://snipboard.io/pBrOi6.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/hCGKul.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/tsQdUb.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
To do that, we can click on the drop down and select "ip.addr == 14.0.0.120". Without making this part too long, the next thing I tend to do here is take a look at the HTTP protocol. So type in "&& HTTP". Hit "Enter". Now these are all of the HTTP requests that contain our external IP address.
<br />
<br />
<img src="https://snipboard.io/d4E6Hu.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/F63dQ2.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/qRcD1B.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/EXYAy9.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
When it comes to HTTP protocols, there are two request methods that are quite interesting. The first one is the "Get-request" and the other is the "Post-request". For the "Get-request", you're essentially retrieving information from the server, whereas the post request is that you're modifying/uploading something to the server. Now, when I'm investigating potential suspicious activities, I always tend to look for the "Post-request".
<br />
<br />
<br />
<br />
To modify that, all I need to do is type in "request.method == POST". You might ask, "Bryan... if I'm new to Wireshark, how would I know that?"
<br />
<br />
<img src="https://snipboard.io/qQyMX7.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Well, one easy way here is to select a packet that contains the "Get" or a "Post-request". So our packet '19951', has a "Get-request" as we can see under the info column. If we scroll down here to bottom and expand our hypertext transfer protocol, we can expand the "Get-request" and we can see the "Request Method" is "Get".
<br />
<br />
<img src="https://snipboard.io/vTwsQR.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/Kdofb1.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/H1PET0.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/03ERoT.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
What I can do is. Select it. Right-click. Select "Prepare as Filter". Then "...and Selected". Now you can see that our filter automatically included the "Get-request". However, we're just going to replace "GET" with "POST". So that is how you can do it. Again however, since I already added it, I'll go ahead and just remove that. Hit "Enter".
<br />
<br />
<img src="https://snipboard.io/ky1qTh.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/0KrvX8.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/5NLPgm.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/431R7G.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
So we do only have one "Post-request" and this is on packet '20616'. Go ahead and select it. Right-click. Click "Follow". Select "HTTP Stream". Take a look at that. There's a file name starting with "JXQ" and taking a look at the ASCII header, we can see that it says "PK". So that is quite interesting.
<br />
<br />
<img src="https://snipboard.io/RFsph4.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/gdIsoW.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/7MRiKh.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/knCprs.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
I'll go ahead and open up Gary Kessler to take a look at the file signature. I'll type in "PK". So a file signature starting with "PK" can be a "ZIP" file as we can see right here. Going back over to our Wireshark. Let's take note of this here. So this began at '18:22:14'. I'll just say "20616 - 18:22:14 - 14.0.0.120 - Uploaded (POST) PK File towards Tomcat Server". Just for easy reference, I put in the packet number '20616'.
<br />
<br />
<img src="https://snipboard.io/ia6PgM.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/K1OBag.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/dVgUlw.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Let's go back to our query where we're looking for the external IP and HTTP request since I want to see what happened before the "Post-request". So it's under the number '20599'. We can see our Tomcat server responded back to the external IP with an HTTP/XML as a protocol.
<br />
<br />
<img src="https://snipboard.io/oaFB0G.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/Bab0cy.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/eQifLy.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
However, if I scroll up just a bit, I see a lot of these '401' unauthorized and there are a lot of "Get-requests" towards "Manager/html". Let's go ahead and follow one of these here. So these are going towards "examples/". I don't really care about that. What I care about is the "manager".
<br />
<br />
<img src="https://snipboard.io/0h1oPK.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/byQKFj.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/xu1vPM.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/EbcHQ5.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Since we're seeing a lot of the "manager/html" "Get-requests", if I take a look at the server response. It does say "401 unauthorized" as well as "You are not authorized to view this page. If you have not changed any configuration files, please examine the file tomcat-users.xml." 
<br />
<br />
<img src="https://snipboard.io/3UGibL.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Interesting. So this appears to be some kind of login page since it has "username" and "password" of secret. However, this is probably just the default credentials here. You know what, let's go and search that up. So I'll type in "tomcat manager HTML" and I'll include the version number as well just in case.
<br />
<br />
<img src="https://snipboard.io/fnvhtF.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/dlrIag.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
We see a link called "HackTricks". So under "Default Credentials", the "/manager/html directory is particularly sensitive as it allows the upload and deployment of WAR files, which can lead to code execution." I think that's what we saw on Wireshark. 
<br />
<br />
<img src="https://snipboard.io/06OZnF.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/BuvJqa.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<br />
<br />
<br />
<br />
If we go back over to our Wireshark, where there was a "Post-request". We do see a "WAR" file. Pretty cool. So this directory is protected by basic HTTP authentication with common credentials being: "admin:admin", "tomcat:tomcat", "admin:", "admin:s3cr3t", "tomcat:s3cr3t", and "admin:tomcat". You gotta love default credentials...
<br />
<br />
<img src="https://snipboard.io/qRV8EM.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/VnYp0U.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Scrolling down to the next "Get-request" for the "/manager/html", we do see "Authorization: Basic" and here is base '64'. Go ahead and copy that. Let's open up CyberChef, and I'll go ahead and paste in that value. Then, drag in my "From Base64". We can see that it's trying "admin:admin" here.
<br />
<br />
<img src="https://snipboard.io/zR7b1u.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/iq9XMG.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/dtoqZr.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
I'll scroll all the way down and see if there are any 200's. So there's one right here, "GET /manager/html" aswell as the server responding with "200 OK". Meaning that they successfully authenticated. I'll go ahead and copy this base64 and let's see what kind ocredentials they used. 
<br />
<br />
<img src="https://snipboard.io/bJSoqB.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/9Ba7PA.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
So it says "admin:tomcat". Okay, let's note that down here. So I'll type "admin:tomcat login success", and what packet number was that at? So if I click on "Accept", the packet number is '20553'. This occurred at '18:20:24'.
<br />
<br />
<img src="https://snipboard.io/QIfyKv.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/aGXlHz.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/N197Mf.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/CvRVsP.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
If I were to go back over to my filter for the external IP and HTTP.So the attacker logged in from packet '20553'. Once they logged in, they performed a "Post-request" for the WAR file and then afterwards they did a "Get-request" to that file.
<br />
<br />
<img src="https://snipboard.io/cwu5HC.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/kVWF0I.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/rYtlBZ.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/hZXulH.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
I'm gonna remove the HTTP protocol and just search for the external IP address since if we only zone in for HTTP, we might be missing other stuff. The main thing I want to focus on are the events that occurred after the "Post-request".
<br />
<br />
<img src="https://snipboard.io/g1a3CP.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/gBfjDU.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/yC6aeR.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/mo3CEz.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
We do continue to see traffic between our Tomcat server to our attacker on port '8080'. We do see a "Get-request" towards that file that the attacker uploaded and immediately afterwards we get a "SYN", "SYN, ACK" and "ACK" on port '80'.
<br />
<br />
<img src="https://snipboard.io/I8VXjc.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/msc7IF.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/Y1MnO9.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/6ECWy0.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Let's go ahead and "Follow". Select "TCP stream" and look at that. We get "whoami". We get a return value of "root". We get a change directory to "/tmp". They performed a "print working directory" and we do see "/tmp". Then they created what appears to be a "cron" job. Now what this is, is a essentially a schedule task, if you're familiar with Windows.
<br />
<br />
<img src="https://snipboard.io/2KvwoL.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/hYwEfQ.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Now, you might ask. What exactly does this command do? If you're not familiar with Linux, it might look pretty confusing. So you know what, let's go ahead and copy this. Let's use ChatGBT. Go ahead and paste that in, but before you hit "Enter", you want to make sure to anonymize any of the artifacts. Such as IP addresses, domains, computers, usernames, and many others.
<br />
<br />
<img src="https://snipboard.io/nchCSA.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/XstG5p.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
So in this case, this right here is our IP address of the attacker. So instead of flat out giving out the IP address to ChatGBT, I'm just gonna say "IP". I'll leave the port as it is, which is '443' since that's quite common. Now, I'll go ahead and include, "what does this command do?"
<br />
<br />
<img src="https://snipboard.io/Er9Lzy.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/bVlN8f.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
At the top it says, "The command you've provided is used to create a reverse shell, which is the type of connection used to gain remote access to a system." Thats pretty interesting. Scrolling down. "In essence, this command creates a reverse shell. The system running the command will connect to the specified IP address on port 443 and establish a shell session. This can be used by an attacker to gain remote control over the compromised machine."
<br />
<br />
<img src="https://snipboard.io/Lis1VI.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/GsQy9r.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
By using ChatGBT, we know exactly what this particular command does. It establishes a reverse shell towards our attacker's IP address on Port '443' to establish persistence. Now that we have all of that information, let's head back over to our Cyber Defenders and begin answering our questions. 
<br />
<br />
<img src="https://snipboard.io/763ONG.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Starting with number one, "Given the suspicious activity detected on the web server,... can you identify the source IP address responsible for initiating these requests on our server?" So we did see a "SYN" scan in the beginning and that was coming from our external IP address, which is this one right here, '14.0.0.120'. Paste that in. 
<br />
<br />
<img src="https://snipboard.io/YdrQBW.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/BcwMiR.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/86FDhV.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Question number two, what's the city from where the attacker originated from? What I'll use is abuseipdb.com. Taking a look at the city, it's this right here. Nice.
<br />
<br />
<img src="https://snipboard.io/SZUp0q.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/YiTUkx.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/ZDq7ch.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Question three, "From the pcap analysis, multiple open ports were detected as a result of the attacker's activitie scan. Which of these ports provides access to the web server admin panel?" Well, we know that it is port '8080'.
<br />
<br />
<img src="https://snipboard.io/icesd3.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/6cindl.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Question four, "Following the discovery of open ports on our server, it appears that the attack attempted to enumerate and uncover directories and files on our web server. Which tools can you identify from the analysis that assisted the attacker in this enumeration process?" Going back over to our Wireshark. Let's go back to our filter for HTTP and the attacker's address. Scrolling all the way up, looking under the info column, I'm going to select a path such as this one right here, "GET /docs/". Right-click. Click "Follow". Select "HTTP stream" and we can see that the user agent is gobuster, specifically, version 3.6. So just type, "gobuster".
<br />
<br />
<img src="https://snipboard.io/Vo5OJK.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/iuqCRo.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/TBIy9w.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/XsR3N1.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/anysLU.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Question five, "...the attacker made numerous requests trying to identify administrative interfaces. Which specific directory associated with the admin panel was the attacker able to uncover?" This was the the "/manager". If you recall, the "manager/html" was what the attacker used to log into the panel.
<br />
<br />
<img src="https://snipboard.io/CuSLZ7.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/5aExSd.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Question six, "Upon accessing the admin panel, the attacker made attempts to brute-force the login credentials. ...can you identify the correct username and password combination? That we can, and we added it here. So I'll just go ahead and copy that. "admin:tomcat" is is correct.
<br />
<br />
<img src="https://snipboard.io/ZsD0VH.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/RskYTJ.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/vIYmNf.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Question seven, "Once inside the admin panel, the attacker attempted to upload a file... Can you identify the name of the malicious file? I don't think we copied that. So let me see if I have this here and I still do awesome. So the file name is "JXQOZY.war".
<br />
<br />
<img src="https://snipboard.io/5Bgiht.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/1E5jOk.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/tOCNyn.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Question eight, "Upon successfully establishing a reverse shell... the attacker aimed to ensure persistence on the compromised machine... can you determine the specific command they are scheduled to run?" So if we go back over to our Wireshark. Let's go back over to our external IP address and this was on Port '80' near the bottom. So that was this one right here. Right-click. Click "Follow". Copy starting from "/bin" all the way to the end. Then paste it in.

<br />
<br />
<img src="https://snipboard.io/feEo9J.jpgz" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/nYlTEh.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/z7JpkD.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/vFA70f.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/05Q6KA.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/MgyBlQ.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Awesome, we just completed Tomcat Takeover. If you followed along, congratulations on completing the Tomcat takeover lab by Cyber Defenders and hopefully you are becoming more confident in analyzing pcaps using Wireshark. I know for me when I first started, Wireshark was extremely intimidating, but you can see how powerful this tool can be for us analysts. Lastly, there is no shame in using AI to help with our investigation. Just keep in mind that you should try your best to anonymize information such as IPS, domains, usernames, and computers. Since at the end of the day, you are sharing your information with AI, you don't want to give out potentially confidential information. Remember to stay curious and do things differently:
