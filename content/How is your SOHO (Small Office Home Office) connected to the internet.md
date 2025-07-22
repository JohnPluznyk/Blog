For the longest time it took me a while to figure out exactly how your ISP works. Today I am diving in and explaining how your ISP works and what exactly the service is they are providing.  

Yes, your ISP does provide you internet, but how exactly do they do that. A short and simple explanation for my SOHO could be the following: "I pay Verizon for internet service. They come and set up their fiber optic cables that hooks into an ONT (Optical Network Terminal) located on my houses premise. The ONT connects my router back to Verizon's Network (default gateway??? or Switch???). From there there Verizon's default gateway should be attached to the World Wide Web."  
  
In short term anytime when I use the internet my request goes from my computer, to my router, to the ONT, to Verizon's Network (**default gateway???**), and then onto the World Wide Web.  
  
One IMPORTANT question was how does my ISP know how to send the data back to my house. Verizon has thousands of customers but, how does it know to take the data from HTTP/HTTPS request and send it back to my private network (router, which sends it to my PC).  
  
The answer to the following question above, is your router's **public IP address** that your ISP temporarily assigns to your router.  
  
You can find your public IP address by going to (www.whatismyipaddress.com).  
  
But, when you run the "tracert" command you would think that the second hop of the process would be the same as your public IP address (Your router's public IP), Right? For example say ("whatismyipaddress gives the following address: 10.10.10.10" but when you run the tracert command you get the following for the second output 10.10.8.1). Why aren't these addresses the same. 

They aren't the same because the second hop of the command goes to the ISP's network (router???, Layer 3 switch??? )first and then onto the World Wide Web. This is because your router is connected to your ISP which then is connected to even bigger network.  **Think a really big Mesh network.**
```
S C:\Users\pluzn> tracert www.google.com

Tracing route to www.google.com [142.250.65.196]
over a maximum of 30 hops:

  1     1 ms     1 ms     1 ms  RT-AX58U-5448 [192.168.50.1]
  2     7 ms    18 ms    16 ms  lo0-100.PHLAPA-VFTTP-358.verizon-gni.net [72.94.61.1]
  3     *        *        *     Request timed out.
  4     *        *        *     Request timed out.
  5    15 ms     7 ms     9 ms  customer.alter.net [152.193.106.150]
  6     6 ms    20 ms    16 ms  192.178.107.21
  7    16 ms    18 ms     7 ms  142.251.60.239
  8    17 ms    21 ms    15 ms  lga25s72-in-f4.1e100.net [142.250.65.196]

Trace complete.
PS C:\Users\pluzn>
```
### Public IP Address

This is the WAN (Wide Area Network) IP assigned to your router or modem by your ISP (Verizon in this case). It is the IP address exposed to the internet, meaning websites and services see this IP when you connect to them.  \***Note**\*  Your public IP address is refreshed at a random rate around 24-48 hours.  This prevents any malicious users from targeting your network.  However, you can request a static IP from your ISP if needed for a server.
  
When you visit sites like "whatismyipaddress.com," they show the IP address that is used for external communications (your public IP). This is your router's public IP address which is the address shown to servers/websites when you make a request like an HTTP request.  Needed so that the website can send the data to your router which forwards it to your device.

### Second Hop in tracert

This IP is part of your ISP's internal network infrastructure. It represents the next router/network that your data passes through within the ISP's network after leaving your home network (your router).  
  
The second hop in tracert is typically the ISP’s gateway or first router in their infrastructure, not your public IP address. Your ISP uses multiple routers to route traffic efficiently within their network before it exits to the broader internet.  
  
In this case, 72.94.xx.1 is a router within Verizon's internal network that your data goes through on its way to their final destination (Google, in your trace).  

So, since your ISP gives your a public IP; could that leave you vulnerable to malicious users? Can others discover your public IP address 1.1.1.1? Can others that communicate through the same ISP router discover other users? How do we protect ourselves?

## How to Protect yourself

**Use a Firewall:** Ensure your router's firewall is enabled to block unsolicited incoming connections.  

**Disable Unnecessary Port Forwarding:** If you’ve opened ports for specific services, make sure they’re secured or disable them when not needed.  

**Use a VPN:** A Virtual Private Network (VPN) can mask your public IP address by routing your traffic through a server with a different IP address. This way, websites and external services will see the VPN’s IP rather than your real public IP.  
Regularly Update Router Firmware: Keeping your router’s firmware up to date ensures you have the latest security patches, reducing the risk of vulnerabilities.  

**Change Your IP Address (Dynamic IP):** If you want to change your public IP address, rebooting your router can sometimes assign a new dynamic IP from your ISP. This works unless you have a static IP.  

**Monitor Your Network:** You can use network monitoring tools to see if there’s any unusual activity (e.g., someone scanning your ports).  
  
I will discuss the above questions in the following:  
To put it simply, YES, your public IP address can be discovered by other people on the internet, but only if you give them a chance to. For example, when you perform an http request. You ask that website to send it to your PC which is on your private LAN. To get it to your LAN they will need to send the HTTP data to your Public IP address. Or for gaming you will need to connect to a mutal server and ask the server to send the data to your Public IP address (your router) and then to your local PC. There is no way of knowing who actually owns that IP address except that it is an IP address given from a service provider.  
  
*The only real way of making sure that the desired person on the internet is communicating with you is making sure they access it from their own Personal device.*  
  
How can we find these public IP addresses on the Internet? / How Can others discover your public IP address? The above process is described as port forwarding. The data will be sent to their public IP address and then is port forwarded to the device asking for that data.  
  
How can we scan for vulnerabilities?  
  
Can others that communicate through the same ISP router discover other users?  
For example if you figure out your public IP address is 1.1.1.1 what is stopping you from looking at addresses 1.1.1.#?  
  
The answer is technically yes. But due to the way ISP allocates addresses it can extremely difficult to target a single user. This is because your public IP addresses is typically dynamically assigned.  
Even though you can infer that *72.94.164.80* might be another user's public IP address, you cannot access their network or router directly just by knowing their public IP address. This is because of security measures like NAT (Network Address Translation) and firewalls that protect devices on private networks from external access.  
NAT is does not necessiarly protet ones public IP address from users. It simply just allows your personal devices to use your public IP address.

