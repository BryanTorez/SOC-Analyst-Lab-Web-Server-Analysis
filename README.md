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
Let's begin our analysis. Starting from the top, we can see that there is a communication initiated from our '10.0.0.115' address over to '10.0.0.105' on Port 445. What that tells me is that '105' is a file server of some sort because it does have SMB opened. Now if we go over to the SMB protocol which is on packet number four, we can expand the packets by clicking on smb2 and we can actually see the header of the SMB.: <br/>
<br />
<img src="https://snipboard.io/CIH5zU.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/p0GxDL.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/zdv12O.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Now if we take a look at the session setup response on packet number nine and expand SMB under the smb2 header we could actually see the username domain and the host computer that initiated the request. So from here we can see that the account was 'root', under the domain of 'WORKINGROUP', and the host-name is 'CYBERDEFENDERS VIRTUAL-MACHINE'. So what I'll do here is put it in my notepad, aswell as the '10.0.0.105' IP. : <br/>
<br />
<img src="https://snipboard.io/NMCHim.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/MqCpgV.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/OLR7Nf.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Scrolling down here I'm not going to go super deep into what these fields mean for SMB so instead I am going to leave a link down in the description for you if you wanted to learn more about it if I take a look here I do see a PDF document called workor report 2023 PDF so what I can do here is actually try downloading this PDF document by heading over to file export objects go to SMB and here we can see the workor report file and there are two of them here 2023 and 2022 we could actually just save both of them and you know what I'll save it under my downloads and we can head over to ourdownloads directory I'll hold shift right click and open up Powershell I'll type in get- file and hit Tab and then I do see the workor report 2022 selected so I'll go ahead and hit enter and this is my Shaw 256 file hash the next thing I can do is go over to virus total and we can search up that hash now we do see no security vendors flaged this file as malicious does that mean it's safe definitely not but it's a start let's do the same for the 2023 copy that out paste that in here and same thing no security vendors flagged this file as malicious now taking a look at the file type it is text Tex with the magic of asky text what that means is that I can actually just rightclick and edit with notepad++ now if you don't have notepad++ that is okay you can always open it with your notepad itself click on more apps and notepad and that is thetext work report for year 2022 dot dot dot I willing to bet that this says the same thing yeah 2023 cool now that we got that out of the way go ahead and close that out there is just constant communication towards 115 and 105 and because we did take a look at the files that existed in our SMB we did go overto file export objects SMB and we only saw two files I am going to skip over a lot of the S SMB stuff and now we actually see SSH connection starting from packet 137 our cyber Defenders virtual machine initiated a SSH session to the IP of 10 0.0112 and we can see that it is a sin and then our 112 was like Hey I'm alive so Sak and the last handshake 115 said hey how's it going says a here and an SSH connection was successfully established okay so that tells me that 112 is an SSH server now we continue to scroll down because SSH is encrypted it really isn't too much here on packet 685 our IP address of 115 then communicates over to 112 on port 8080 and this is our first HTTP protocol what I can do is right click this click on follow HTTP stream and here we can see the packet itself taking a look at the user agent it is Mozilla 5.0 and I do see you buntu Linux what that tells me is that the Cyber Defenders virtual machine so this operating system is Ubuntu and looking at the server response which is this right here we can see that the title is Apache Tomcat specifically with the version of 7.08 copy that out that means our SSH server is also our Apache Tomcat server type in and paste that in now it is getting a lot more interesting I'll go ahead and remove my TCP stream and if we go over to our notepad rather than scrolling down and just taking a look at all of these events because that's going to take forever we do want to start drilling down into our top IP address which is 14.01 120 now if I go ahead and copy this and type in ip addr equal equals and paste that in hit enter and if you take a look here on packet 1091 92 93 94 95 and continue rning on you can see a bunch of sin requests which is a clear indicator of a sin scan it's targeting Port 256 443 199 1113 25 3306 and many more here what we can do is take a look at what ports are opened on our Apache Tomcat server to do this l'll just look at the sinac so right here I'll find a packet that says syac and this is on packet number 1108 I'll expand the transmission control protocol AKA TCP and for my flag see how it says syac I'll go ahead and rightclick this select prepare as filter and I'll click on and selected but what I also want to do here is change my filter to look at the source IP address of 10.0.0 1112 where the destination IP is the 14.01 120 so to change that I'll type in ip src and this is going to equal to 10.0.0 1112 I'll put two and for signs ip dst equal equals 140.0 120 hit enter and we can see a bunch of sxs these are all of the ports that are open our Port 22 and port 8080 and look at that there's also a port 8009 that is open and that seems to be it so there are three open ports let's go ahead and make a note out of that open ports 22 8080 and 8009 let's go ahead and rerun our previous query to do that we can click on the drop down and select ip adder equals the external IP address and without making this video too too long the next thing I tend to do here is take a look at the HTTP protocol so type in two ENT and HTTP hit enter and these are all of the HTTP requests that contain our external IP address and when it comes to http protocols there are two request methods that are quite interesting the first one is the get request and the other is the post request the get request you're essentially retrieving information from the server whereas the post request is that you're modifying slash uploading something to the server now when I'm investigating potential suspicious activities I always tend to look for the Post request to modify that all I need to do is type in request method equal equals post you might ask but Stephen if I'm new to Wi shark how would I know that well one easy way here is to select a packet that contains the get or a pos requ request so our packet 19951 has a get request as we can see under the info column if we scroll down here at the very bottom and expand our hypertext transfer protocol we can expand the get request here and then we can see request method is get what I can do is Select it right click prepare as filter and select it now you can see that our filter automatically included the get request and then simply replace get with post so that is how you can do it but because I already added it I'll go ahead and just remove that and hit enter so we do only have one post request and this is on packet number 2,616 go ahead and select it right click follow HTTP stream and O take a look at that there's a file name starting with jxq and taking a look at the asky header here we can see that it is PK so that is quite interesting if I go ahead and open up Gary Kessler taking a look at the file signature I'll type in PK a file signature starting with PK can be a zip file as we can see right here going back over to our wi shark let's take note of this here so this began at 18224 18224 140.0 1220 uploaded I'll just say post PK file towards Tom server and just for easy reference I'm going to put in the packet number which is 2616 let's go back to our query where we're looking for the external IP and HTTP request because I want to see what happened before the post request and that is this one right here $25.99 we can see our Tomcat server responded back to the external IP with an HTTP XML as a protocol but if I scroll up just a bit I see a lot of these 401 unauthorized and there's a lot of get requests towards manager/ HTML let's go ahead and follow one of these here so these are going towards the example I don't really care about that what I care about is the manager so this right here the manager HTML because we're seeing a lot of the manager HTML get requests if I take a look at the server response it's does say 401 unauthorized you are not authorized to view this page if you have not changed any configuration files please examine the file Tomcat users xml interesting this appears to be some kind of login page because it has username and password of secret but this is probably just the default credentials here you know what let's go and search that up so I'll type in Tomcat manager HTML and I'll include the ver number as well just in case o we do see a link called hack tricks what is this default credentials the manager HTML directory is particularly sensitive as it allows the upload and deployment of War files which can lead to code execution I think that's what we saw right because if we go back over to our wire shark where there was a post request we do see a war file pretty cool this directory is protected by basic HTTP authentication with common credentials being admin admin Tomcat Tomcat admin no password admin secret Tomcat secret and admin Tomcat you got to love default credentials scrolling down to the next get request for the manager HTML we do see authorization basic and here is base 64 go ahead and copy that let's open up cyber chef and I'll go ahead and paste in that value here and drag in my from base 64 we can see that it's trying admin admin here and if we go back overso this one was a 401 and you know what I'll scroll all the way down and see if there are any 200s and O right here get manager HTML the server responded with 200 okay meaning that they successfullyauthenticated I'll go ahead and copy this Bas 64 and let's see what kind ocredentials they used who admin Tomcat okay let's note that down here so admin Tomcat login success and what packet number was that at so if I click on this the packet number that was successfully logged in was on 20553 20553 this occurred at 18224 and if I were to go back over to my filter for the external IP and HTTP so the attacker logged in from packet 2553 which is this one right here 2553 once they logged in they performed a post request for the war file and then afterwards they did a get request to that file I am going to remove the HTTP protocol and just search for the external IP address because if we only Zone in for HTTP we might be missing other stuff and the main thing I want to focus on are the events that occurred after the post request and we do continue to see traffic between between our Tomcat server to our attacker o port 8080 we do see a get request towards that file that the attacker uploaded and immediately afterwards we get a sin synac act on Port 80 hm let's go ahead and follow TCP stream and O look at that who am I we get a return value of root a change directories to/ temp they performed a print working directory and we do see for sltm and then they created what appears to be a Cron job now what this is is essentially a schedule task if you're familiar with Windows now you might ask what exactly does this command do and if you're not familiar with Linux it might look pretty confusing so you know what let's go ahead and copy this and let's use chat gbt go ahead and paste that in but before you hit enter you want to try andmake sure to anonymize any of the artifacts such as IP addresses domainscomputers usernames and many others so in this case this right here is our IP address of the attacker so instead of flat out giving out the IP address to chat gbt I'm just going to say IP I'll leave the port as is which is 443 because that's quite common and now I'll go ahead and include what does this command do and at the top it says the command you provided is used to create a reverse shell which is the type of connection used to gain remote access to a system pretty awesome scrolling down in essence this command creates a reverse shell the system running the command will connect to the specified IP address on Port 443 and establish a shell session this can be used by an attacker to gain remote control over the compromised Machine by using chat gbt we know exactly what this particular command does it establishes a reverse shell towards our attacker's IP address on Port 443 to establish persistence now that we have all of that information let's head back over to our cyber Defenders and begin answering our questions starting with number one given the suspicious activity detected on the web server can you identify the source IP address responsible for initiating these request on our server so we did see a sin scan in the beginning and that was coming from our external IP address which is this one right here 140.0 1220 paste that in question number two what's the City from where the attacker originated from what I'll use is abuse ipdb and taking a look at our city it is this right here nice question three from the peab analysis multiple open ports were detected as the result of the attacker's activity scan which of these ports provides access to the web server admin panel well we know that it is port 8080 following the discovery of open ports on our server it appears that the attack attempted to enumerate and uncover directories and files on our web server which tools can you identify from the analysis that assisted the attacker in this enumeration process ooh going back over to our wire shark here let's go back to our filter for HTTP and the attacker's address scrolling all the way up here looking under the info column I am going to select a path such as this one right here the get SL dos right-click follow HTTP stream and we can see that the user agent is gobster specifically version 3.6 copy that out I wonder if they want me to include 3.6 no they do not so I'll go ahead and just type in gobster and that's correct question five the attacker made numerous requests trying to identify administrative interfaces which specific directory associated with the admin panel was the attacker able to uncover this was the the for SL manager because if you recall the manager/ HTML was what the attacker used to log to the panel upon accessing the admin panel the attacker made attempts to Brute Force the log on credentials can you identify the correct username and password combo that we can and we added it here so I'll just go ahead and copy that admin and Tomcat that is correct question number seven once inside the admin panel the attacker attemp to upload a file can you identify the name of the malicious file I don't think we copied that yeah we did not okay so let me see if I have this here and I still do awesome so the file name is this right here starts with jxq ends in W does it want the file extension as well and looking at the format it appears that it does past that in upon successfully establishing a reverse shell the attacker aimed to ensure persistence on the compromised machine can you determine the specific command they are scheduled to run so if we go back over to our wire shark here I do not have it open so that was a rookie mistake by me let's go back over to our external IP address and this was on Port 80 near the bottom and that was this one right here Port 80 right click follow starting from the slash bin all the way to the end go ahead and copy that out and let's paste that in and awesome we just completed Tom Cat takeover if you followed along congratulations on completing the Tom Cat takeover lab by cyber Defenders and hopefully you are becoming more confident in analyzing peaps using wire shark I know for me when I first started wire shark was extremely intimidating but you can see how powerful this tool can be for us analysts lastly there is no shame in using AI to help with our investigation just do keep in mind to try your best to anonymize information such as IPS domains usernames and computers because at the end of the day you are sharing your information with AI so you don't want to give out potential confidential information and as a reminder I do have a course called the my defer sock analyst course and if you are looking for a practical Hands-On course this is perfect for you you can find more information in the description down below that is it for the video and I hope that you found that informative if you did let me know by hitting that like button and subscribe if you want to remember to stay curious and do things differently:
