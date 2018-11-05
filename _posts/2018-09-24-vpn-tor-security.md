---
title: How to use Encryption, VPNs, and TOR to secure your online browsing
layout: post
date: 2018-09-24 9:03
tags: howto
---

{% include image.html src="https://www.dropbox.com/s/3y9xnwc4rgqygtk/hackinghustlingwhite.jpg?dl=1" caption="Graphic by Paul Glover"%}

This weekend, [eyebeam](https://www.eyebeam.org/) invited us at [t4tech](t4tech-nyc.github.io) in to teach a series of workshops on tactical skills for sex workers in a post-SESTA world. It was such a fantastic event and I was so happy to have been invited. Here's a companion post meant for anyone who wasn't able to attend or would like to review the material we covered in the VPNs and Tor workshop. All materials we put together are available [here](soph.info/hh).


# Background

[SESTA (Stop Enabling Sex Traffickers Act)](https://en.wikipedia.org/wiki/Stop_Enabling_Sex_Traffickers_Act) is a bill passed this year, that was meant to be an anti-sex trafficking measure. Previously, websites were largely [shielded from liability](https://en.wikipedia.org/wiki/Section_230_of_the_Communications_Decency_Act) for the activity of users on the website. SESTA creates an exception to this that essentially holds websites at risk for activity of any user that concerns sex trafficking. *However*, the authors of the bill failed to make any distinction between sex trafficking and sex work.

This has had devastating effects on the lives of many sex workers. SESTA places the onus on websites to police all user activity for sex work, and these sites have responded with a heavy hand. Websites had provided marketplaces that were key to safe and independent work practices for sex workers and nearly all of these have been destroyed by SESTA. [Research by Scott Cunningham of Baylor University and colleagues](https://cear.gsu.edu/files/gravity_forms/45-9a8e751f713c799256f347c4aad2a49d/2017/04/Online-Erotic-Services-Advertising-and-Murder.pdf) has shown that these online marketplaces for sex work reduced the homicide rate for women, especially the strangulation homicide rate, and led to safer sex practices.

In college, I remember several conversations among my group of friends at the intersection of STEM and social justice about whether or not the advancement of technology was a good thing in and of itself. Today those discussions seem hopelessly naive—our technology and the way we regulate it are being used to target sex workers, an especially marginalized population, and to make their lives less safe and secure. Without serious and deliberate effort, tech is just another tool that can be used by those with power to harm and take from those without.

# Recommendations and caveats for VPNs and Tor.

## Glossary

I'll go into more detail about how VPNs and Tor work, but for now I want to stick with a brief summary.

**IP Address** (often called "location") is an identifier for the network you are using to access the internet. When I send a tweet from my home network, twitter logs the IP Address. If someone with subpoena power wanted to know who sent that tweet, they could subpoena twitter for the IP Address, and my cable company for my billing address.

**Encryption** is a process of transforming text or data so that it is unreadable, except by someone with a private key.

**HTTPS** is the encrypted version of the transfer protocol used for network traffic. HTTPS provides a reasonable level of privacy for some of your online data. HTTPS does not hide your IP address or which website you are visiting.

A **VPN** uses a service to make your network traffic *private*. It typically makes private your data, the site you're visiting, and your IP Address. The service that provides your VPN still sees all of your traffic and could still potentially trace it back to you, so it's not considered anonymous. Pros: relatively fast speeds, easy to set up on a variety of devices. Cons: relies on trust in a single service.

**Tor** is a routing protocol that anonymizes network traffic by randomly routing it through several layers of relays with a new layer of encryption/decryption at each step. Unlike VPNs, Tor does not rely on trust in the network. A Tor browser can be downloaded that routes all traffic from that browser through the Tor network. Pros: anonymous, easy to use as a browser. Cons: Slow, difficult to set up for mobile apps and other uses.

## The Data we leak

I'll use a table like the following to visualize what kinds of data is shared with different potential threats.

The naive case. No security measures taken.

|                | IP Address | Site | Data | Tor? |
|:---------------|:-----------|:-----|:-----|:-----|
| Local threats  | ✅          | ✅    | ✅    | -    |
| Our ISP        | ✅          | ✅    | ✅    | -    |
| Eavesdroppers  | ✅          | ✅    | ✅    | -    |
| External ISP   | ✅          | ✅    | ✅    | -    |
| External Sites | ✅          | ✅    | ✅    | -    |

## Recommendation 1: Use HTTPS everywhere

HTTPS is going to be your main line of defense and it's an essential component of every other tool I'm going to discuss. Without HTTPS, Tor is extremely vulnerable.

You have a few options for this. The EFF has developed a browser extension [HTTPS Everywhere](https://www.eff.org/https-everywhere) that forces all sites that can to use HTTPS. For times when you can't install a browser extension (like on iOS), the [Brave browser](https://brave.com/) is available on all major mobile and desktop operating systems and has HTTPS everywhere built in.

## Recommendation 2: Pick a VPN service, buy a subscription, and set it up on all your devices.

Using a VPN requires trust in a specific service. Which service you pick is an individual choice. I'll put a few comparisons below for you to look at so that you can review and make an informed decision. Whatever you do, don't use a free VPN—it takes resources to run a VPN and if you aren't paying for it directly, then your traffic is the only revenue source. You should also consider the plans and software offered by each. How many devices will you want to use simultaneously and what kind of devices? Make sure that the service you select supports the devices you plan to use.

- [TorrentFreak Guide](https://torrentfreak.com/vpn-services-keep-anonymous-2018/)
- [The Wirecutter Review](https://thewirecutter.com/reviews/best-vpn-service/)
- [That One Privacy Site](https://thatoneprivacysite.net/)

The easiest way to set up a VPN is to do so individually on each device. Another option to consider is configuring your router to run all of your home network's traffic over a VPN. To do this, you'll likely need to either purchase a wifi router with tomato installed by default or flash your existing router.

## Recommendation 3: Use Tor when it makes sense
