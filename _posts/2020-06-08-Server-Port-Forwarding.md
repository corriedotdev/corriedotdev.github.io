---
layout: post
title: Game Server Port Forwarding, CGN & NAT Type 'Strict'
excerpt: "Sent down a hole of configuration to get my game server visible on the WAN. Discussing what Carrier Grade Nat (CGN) is and Restricted NAT types."
categories: [Networking]
comments: true
---

# Port forwarding is easy right?
In summary, I've been trying to open port 25565 on my Windows Server 2019 machine to run a game server accessible over WAN. Never had issues opening ports in the past.. and as per normal ive been sent down a rabbit hole of reading that I found quite interesting. 

Given my background I wasn't about to give up, I was already a few hours in. To start, connecting to the game server locally seemed to have worked, and was able to connect with localhost. 

Another device on the LAN also worked, which was reassuring but the public IP was a different story. I used a VPN to attempt access to the server with the public IP so it wasn't going to clash as it was the same IP as my machine, also using tools like open port check tool returns that port 25565 is not open.

So here are the steps I've followed

- I have disabled the firewall entirely and will add exclusions rules when I get to the bottom of the - issue. When ready this will be UDP and TCP exclusions in the Windows firewall.

- I have a static IPv4 assigned from my ISP as it was using a CGN (see below for more details on this)

- [This guide][1] was followed from the ISP to open ports

- I have also created a DHCP filter and statically assigned my LAN ip so the machine IP locally won't expire 

- Disabled firewall and "prevent hackers" in the router settings also

[The image located here is an example of my port forwarding configuration][2]

  [1]: https://hyperoptic.com/wp-content/uploads/2019/08/Port-forwarding-and-DMZ-for-ZTE-ZXHN-H298A-v1.3.pdf
  [2]: https://i.stack.imgur.com/wa5hf.png


So all seems well right? Wrong. The port was still showing as closed using the command

{% highlight console %} 
netstat -a -n
{% endhighlight %}

**Alternatively** 
You could use the servers MAC address over a static local IP.
{: .notice}

## Solution
Then I reached my limit and restarted the router. I'm sure you can understand my mindset when it got to this stage. I then decided to explicitly assign UDP and TCP port forwarding as separate rules in the port forwarding configuration and boom. Worked instantly.

**Watch out!** 
Make sure to go back and enable any firewall rules that you removed during the debugging stage.
{: .notice}

## So what is Carrier Grade NAT
IPv4 Addresses are nearing exhaustion so some measures have been introduced to help prevent so many being used. Interestingly I initially imagined the system was just a series of hops through various large scale switches and it appears from my new understanding thats what is is doing to an extent. Connections to the public web would pass through three different IPv4 addressing domains, the initial connection from your private network, the ISP private network abd the public internet.

My ISP has deployed a CGN - Hyperoptic is pretty new - and uses a [RFC 1918][3] which is used for 'best practices' when assigning addresses on a private network. Address collisions can occur however so routing traffic won't always go as planned. The passage above is a testament to that. I had to explicitly ask the ISP for a fixed IP address so I could open ports on my network. It wouldn't be possible to open ports on a CGN without theoretically opening the ports for everyone who is using that ISP. What is cool however is that the [Internet Assigned Authority][4] have allocated the following IPv4 block of addresses for ISP to use CGNs. So you can actually quickly identify if you are using a CGN or not. The block they assigned is 100.64.0.0/10. 

**Internet Assigned Authority** I thought this authority were similar to W3.com where they list the best practices and don't really enforce anything.; But it does appear that IP addresses need a level of policing and IANA are responsible for hte allocation of globally unique names and numbers used in Internet protocols. 
{: .notice} 

  [3]: https://tools.ietf.org/html/rfc1918
  [4]: https://www.wikiwand.com/en/Internet_Assigned_Numbers_Authority

## NAT Type Strict
Going back to Call of Duty days when you are trying to set up a quick scope lobby with your friends but you can't because your NAT type is strict. What does this mean? And why does a reboot of the router work? I came across NAT type in the router options and wanted to dive in.

**NAT stands for**
Network Address Translation 
{: .notice}

The technology was created to prevent ISP's from assigning multiple IP addresses to each host a customer has, that connects to the router or when the network would change. From this statement alone you can see how without NAT type being another layer of IPv4 address preservation, there would be even fewer.. if any addresses remaining. To this extent it is interesting to see that ISP's are now preserving their IP addresses even more by implementing it from a carrier level using CGN.

On the internal network, when a packet is past through the NAT / router to the external network, the IP address in the source field of the packet header  is replaced with the IP address of the external IP address. Once the IP has been changed, the connection that the packet is using will need to be assigned a port number from a pool of available ports. This port will be inserted into the source port packet field and then forwards the packet to the external address. The NAT device makes an entry in a translation table containing the internal IP address, original source port, the translated source port and internal IP address. Therefore, the device that is receiving the packet does not know it has undergone this translation of IP addresses, from internal to external. A similar process is undertaken when a load balanced client-server architecture is being used. This is actually very topical to what I am working on with my current client regarding F5 load balancers. 

**How many IPV4 Addresses are there**
2^32 = 4,294,967,296
{: .notice}

## Further Reading
* [Breakdown of CGN](https://www.a10networks.com/blog/carrier-grade-nat/)

<a href="#" id="emailclick" onclick="replace_email()">My Email</a>

<!-- SCRIPTS HERE -->
<script>
var email;

function add_mailto() {
  const elem = document.getElementById("emailclick");
  elem.href = `mailto:${email}`;
}

function replace_email() {
  // spam prevention
  const domain = "cjgstudio.com";
  const name = [16, 28, 1, 1, 26, 22];
  const xor_with = 115;
  let constructed = "";
  name.forEach(function(i) {
    constructed += String.fromCharCode(i ^ xor_with);
  })
  email = `${constructed}@${domain}`;
  const elem = document.getElementById("emailclick");
  elem.text = email;

  window.setTimeout(add_mailto, 100);
}
</script>