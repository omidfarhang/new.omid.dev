---
title: Stuxnet Missing Link Found, Resolves Some Mysteries Around the Cyberweapon
date: 2013-02-27T16:12:00+00:00
layout: single
author_profile: true
url: 2013/02/27/stuxnet-missing-link-found-resolves-some-mysteries-around-the-cyberweapon/
tags:
  - Cyber War
  - Iran
  - malware
  - news
  - review
  - Stuxnet
lang: en
category: techblog
---
_Cross-posted from_ [_WIRED_](http://www.wired.com/threatlevel/2013/02/new-stuxnet-variant-found/all/)_._ 

[![Ahmadinejad-at-Natanz-in-2008](http://lh4.ggpht.com/-MjRcWkbyBz4/US4pE-oaobI/AAAAAAAAH3g/hyVPMApvy1Q/Ahmadinejad-at-Natanz-in-2008_thumb%25255B2%25255D.jpg?imgmax=800 "Ahmadinejad-at-Natanz-in-2008")](http://lh6.ggpht.com/-Ddf4V0bOokQ/US4pBrXxyuI/AAAAAAAAH3Y/0ibgWKrHlgY/s1600-h/Ahmadinejad-at-Natanz-in-2008%25255B5%25255D.jpg)

As Iran met in Kazakhstan this week with members of the UN Security Council to discuss its nuclear program, researchers announced that a new variant of the sophisticated cyberweapon known as Stuxnet had been found, which predates other known versions of the malicious code that were reportedly unleashed by the U.S. and Israel several years ago in an attempt to sabotage Iran’s nuclear program. 

The new variant was designed for a different kind of attack against centrifuges used in Iran’s uranium enrichment program than later versions that were released, according to Symantec, the U.S-based computer security firm that [reverse-engineered Stuxnet in 2010](http://www.wired.com/threatlevel/2011/07/how-digital-detectives-deciphered-stuxnet/) and also found the latest variant. 

The new variant appears to have been released in 2007, two years earlier than other variants of the code were released, indicating that Stuxnet was active much earlier than previously known. A command-and-control server used with the malware was registered even earlier than this, on Nov. 3, 2005. 

Like three later versions of Stuxnet that were released in the wild in 2009 and 2010, this one was designed to attack Siemens PLCs used in Iran’s uranium enrichment program in Natanz. 

But instead of changing the speed of spinning centrifuges controlled by the PLCs, as those later versions did, this one focused on sabotaging the operation of valves controlling the flow of uranium hexafluoride gas into the centrifuges and cascades — the structure that connects multiple centrifuges together so that the gas can pass between them during the enrichment process. The malware’s goal was to manipulate the movement of gas in such a way that pressure inside the centrifuges and cascade increased five times the normal operating pressure. 

“That would have very dire consequences in a facility,” says Liam O’Murchu, manager of security response operations for Symantec. “Because if pressure goes up, there’s a good chance the gas will turn into a solid state, and that will cause all sorts of damage and imbalances to the centrifuges.” 

The new finding, described in a [paper released by Symantec on Tuesday](http://www.wired.com/images_blogs/threatlevel/2013/02/Whitepaper-Stuxnet-0.5-The-Missing-Link-1-copy.pdf) (.pdf), resolves a number of longstanding mysteries around a part of the attack code that appeared in the 2009 and 2010 variants of Stuxnet but was incomplete in those variants and had been disabled by the attackers. 

The 2009 and 2010 versions of Stuxnet contained two attack sequences that each targeted different models of PLCs made by Siemens being used in Iran’s uranium enrichment plant — the Siemens S7-315 and S7-417 models of PLC. 

In these later variants of Stuxnet, however, only the 315 attack code worked. The 417 attack code had been deliberately disabled by the attackers and was also missing important blocks of code that prevented researchers from determining definitively what it was designed to do. As a result, researchers have long guessed that it was used to sabotage valves, but couldn’t say for certain how it affected them. There were also mysteries around why the attack code was disabled — was it disabled because the attackers had failed to finish the code or had they disabled it for some other reason? 

The 2007 variant resolves that mystery by making it clear that the 417 attack code had at one time been fully complete and enabled before the attackers disabled it in later versions of the weapon. And because the 2007 variant only contained the 417 attack code — with no code attacking the Siemens 315 PLC — it appears that the attackers disabled the 417 code in later versions because they wanted to change their tactics, dropping their focus on sabotaging the valves in order to focus instead on sabotaging the spinning centrifuges. 

[![Natanz_Satellite2](http://lh3.ggpht.com/-VVF34viZQ2Y/US4pLpsi3gI/AAAAAAAAH3w/bshvCDUqErw/Natanz_Satellite2_thumb%25255B3%25255D.jpg?imgmax=800 "Natanz_Satellite2")](http://lh5.ggpht.com/-MJgXjCTuJR0/US4pIsr0BwI/AAAAAAAAH3o/o1L1o4M4NrM/s1600-h/Natanz_Satellite2%25255B5%25255D.jpg)Symantec discovered the 2007 variant a few months ago during a routine search of its malware database while looking for files that matched patterns of known malware. 

Though the variant was only recently found, it had been in the wild at least as early as Nov. 15, 2007, when someone uploaded it to [VirusTotal](https://www.virustotal.com/en/) for analysis. VirusTotal is a free online virus scanner that aggregates more than three-dozen brands of antivirus scanners and is used by researchers and others to determine if a file discovered on a system contains signatures of known malware. It’s not known who submitted the sample to VirusTotal or in what country they were based, but Symantec believes the 2007 version was very limited in its reach and likely only affected machines in Iran. 

Until now, the first known variant of Stuxnet uncovered was released in June 2009, followed by a second variant in March 2010 and a third in April 2010. Researchers always suspected that other variants of Stuxnet existed, based on the version numbers the attackers gave their code, as well as other clues. 

The June 2009 variant, for example, was labeled version 1.001. The March 2010 variant was 1.100, and the April 2010 variant was 1.101. The gaps in version numbers suggested that other versions of Stuxnet were developed, even if they were not released into the wild. That theory bore out when the researchers discovered the 2007 variant, which turned out to be version 0.5. 

Though Stuxnet 0.5 was in the wild as early as 2007, it was still active when the June 2009 version was released. Stuxnet 0.5 had a stop date of July 4, 2009 coded into it, which meant that after this date it would no longer infect new computers, though it would still continue to sabotage machines it had already infected, unless it got replaced with a new version of Stuxnet. The 2007 version was also programmed to stop communicating with command-and-control servers on Jan. 11, 2009, five months before the next version of Stuxnet was released. It’s possible that when the June 2009 version was released, which had the ability to update older versions of Stuxnet via peer-to-peer communication, it replaced the older 2007 version on infected machines. 

Stuxnet 0.5 was much less aggressive than later versions in that it used fewer spreading mechanisms. The researchers found no zero-day exploits in the malware to help it spread, which is probably one reason it never got caught. 

By contrast, the 2010 variants of Stuxnet used four zero-day exploits as well as other methods that caused it to spread wildly out of control to more than 100,000 machines in and outside of Iran. 

Stuxnet 0.5 was very surgical and spread only by infecting Siemens Step 7 project files — the files that are used to program Siemens’ S7 line of PLCs. The files are often shared among programmers, so this would have allowed Stuxnet to infect core machines used to program the 417 PLCs at Natanz. 

If it found itself on a system that was connected to the internet, the malware communicated with four command-and-control servers hosted in the U.S., Canada, France and Thailand. 

The domains for the servers were: smartclick.org, best-advertising.net, internetadvertising4u.com, and ad-marketing.net. All of the domains are now down or registered to new parties, but during the time the attackers used them, they had the same home page design, which made them appear to belong to an internet advertising firm called Media Suffix. A tag line on the homepage read, “Deliver What the Mind Can Dream.” 

Like later versions of Stuxnet, this one had the ability to deliver updates of itself to machines that were not connected to the internet, using peer-to-peer communication. Though later versions used RPC for the peer-to-peer communication, this one used [Windows mailslots](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365130%28v=vs.85%29.aspx). All the attackers had to do was use the command-and-control server to update the code on one infected machine that was connected to the internet, and others on the local internal network would receive the update from that machine. 

[![Stuxnet-CC-Home-Page](http://lh3.ggpht.com/-W6FKiak-HaU/US4pR0HV1DI/AAAAAAAAH4A/wG-c4a50x_E/Stuxnet-CC-Home-Page_thumb%25255B2%25255D.png?imgmax=800 "Stuxnet-CC-Home-Page")](http://lh5.ggpht.com/-l-KA5hE6Idw/US4pOnY8XsI/AAAAAAAAH34/EB0q5zQ23Xo/s1600-h/Stuxnet-CC-Home-Page%25255B4%25255D.png) 

Once Stuxnet 0.5 found itself on a 417 PLC, and determined that it had found the right system, the attack proceeded in eight stages, sabotaging 6 out of 18 centrifuge cascades. 

In the first part, Stuxnet simply sat on the PLC watching normal operations in the cascades for about 30 days and waiting for the systems to reach a certain state of operation before the attack progressed. 

In the next part, Stuxnet recorded various data points while the cascades and centrifuges operated normally, in order to replay this data to operators once the sabotage began and prevent them from detecting changes in the valves or gas pressure. 

Each cascade in Natanz is organized in 15 stages or rows, with a different number of centrifuges installed in each stage. Uranium hexafluoride is pumped into cascades at stage 10, where it spins at high speed for months. The centrifugal force causes slightly lighter U-235 isotopes in the gas (the desired isotope for enrichment) to separate from heavier U-238 isotopes. 

[![Centrifuge-Stages_Symantec](http://lh4.ggpht.com/-CL1F3c9JZvY/US4pXBkdfdI/AAAAAAAAH4Q/0MeJB_XQbdE/Centrifuge-Stages_Symantec_thumb%25255B4%25255D.jpg?imgmax=800 "Centrifuge-Stages_Symantec")](http://lh6.ggpht.com/-6SWKSQIIYmU/US4pU8dAqlI/AAAAAAAAH4I/TrMRexIvMmc/s1600-h/Centrifuge-Stages_Symantec%25255B6%25255D.jpg)The gas containing the concentration of U-235 is then siphoned out of the centrifuges and passed to stage 9 of the cascade to be further enriched, while the depleted gas containing the concentration of U-238 isotopes is diverted to cascades in stage 11. The process repeats for a number of stages, with the enriched uranium becoming more concentrated with U-235 isotopes at each stage until the desired level of enrichment is achieved. 

There are three valves on a cascade that work in unison to control the flow of gas into and out of centrifuges, as well as auxiliary valves that control the flow of gas into and out of each stage in a cascade and into and out of the cascade itself. 

When the sabotage kicked in, Stuxnet closed and opened various centrifuge and auxiliary valves to increase the gas pressure, thereby sabotaging the enrichment process. Stuxnet closed valves on six out of 18 cascades and modified other valves on randomly chosen individual centrifuges to prevent operators from detecting a pattern of problems. In the final step of the attack, the sequence was reset to begin the attack over again at the first stage. 

It’s long been suspected by some experts that Stuxnet was already sabotaging cascades at Natanz sometime between late 2008 and mid-2009. The new finding from Symantec supports that theory. 

Stuxnet 0.5 was looking for a system in which cascade modules were labeled A21 through A28. Natanz has two cascade halls — Hall A and Hall B. Only Hall A was operating in 2008 and 2009 when Stuxnet would have been active on infected machines. 

Hall A is divided into cascade rooms that are labeled Unit A21, Unit A22, etc up to Unit A28. Iran began its installation of centrifuges in two rooms in Hall A in 2006 and 2007 — Unit A24 and Unit A26 — and later expanded to other rooms. In February 2007, Iran announced that it had begun to enrich uranium at Natanz. 

According to reports released by the UN’s International Atomic Energy Agency, which monitors Iran’s nuclear program, by May 2007, Iran had installed 10 cascades, consisting of a total of 1,064 centrifuges, in Hall A. By May of 2008, Iran had 2,952 centrifuges installed, and Iranian President Mahmoud Ahmadinejad announced plans to increase the number of centrifuges to 6,000. The numbers did increase throughout 2008 and early 2009, with gas being fed into them shortly after they were installed. But the number of cascades that were being fed gas and the amount of gas being fed began to drop sometime between January and August 2009 when Iran appeared to be having problems with some of its cascades. In late 2009, IAEA inspectors noticed that technicians at Natanz were actually removing centrifuges from cascades and replacing them with new ones. All of this would seem to coincide with the timing of Stuxnet. 

[![ISIS-chart](http://lh5.ggpht.com/-TkcBjduZzJg/US4pdQ-1S7I/AAAAAAAAH4g/M7WEI8F5g-g/ISIS-chart_thumb%25255B3%25255D.jpg?imgmax=800 "ISIS-chart")](http://lh6.ggpht.com/-A866abqJ12I/US4pabcmmaI/AAAAAAAAH4Y/ntTjH8RzowQ/s1600-h/ISIS-chart%25255B5%25255D.jpg)One final interesting detail of note about the new variant — during the installation process of Stuxnet 0.5, the malware created a driver file that caused a forced reboot of a machine 20 days after the malware infected it. It did this by generating a BSoD (Blue Screen of Death) — the infamous blue screen that appears on Windows machines when they crash. 

Stuxnet was first discovered in June 2010 because some machines in Iran on which it was installed kept crashing and rebooting. Researchers were never able to determine why those machines crashed and rebooted, because other machines infected by Stuxnet did not respond in this way. 

Though the version of Stuxnet found on those machines was not Stuxnet 0.5, it raises the possibility that multiple versions of Stuxnet might have infected those machines even though only one was recovered when they were examined. O’Murchu thinks it’s unlikely, however, that VirusBlokAda — the antivirus firm that first discovered Stuxnet — would have missed another variant on the machines.