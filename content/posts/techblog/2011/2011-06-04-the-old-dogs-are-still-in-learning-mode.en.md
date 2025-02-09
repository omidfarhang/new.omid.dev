---
title: The old dogs are still in learning mode
date: 2011-06-04T09:13:00+00:00
layout: single
author_profile: true
url: 2011/06/04/the-old-dogs-are-still-in-learning-mode/
tags:
  - review
  - rogue software
lang: en
categories: 
  - TechBlog
---
Norman Security Blog wrote a good article about Fake AVs and their new variants and how to protect ourselves, Credit to my friend, Pondus, for sharing this:

**Background**

[Fake antimalware](http://www.norman.com/security_center/virus_description_archive/80133/) has become a profitable industry for the cybercriminals. New variants appear on a daily basis, and new techniques for tricking the users are fine-tuned.

[![](http://4.bp.blogspot.com/-b_fSQydqQ2A/Tenu0hP-AuI/AAAAAAAAD44/M3kt6nwagAY/s1600/dog_laptop-1_None.medium.png)](http://4.bp.blogspot.com/-b_fSQydqQ2A/Tenu0hP-AuI/AAAAAAAAD44/M3kt6nwagAY/s1600/dog_laptop-1_None.medium.png)

A few weeks ago we wrote in our security article – [Cybercriminals focus on new targets](http://www.norman.com/security_center/security_center_archive/2011/cybercriminals_focus_on_new_targets/en-us) – about fake antimalware for Apple's Mac OS X operating system. In its [security update 2011-003 for Mac OS X](http://support.apple.com/kb/HT4657), available 31 May, Apple enhanced considerably its protection against malware. This includes the ability to automatically download new malware signatures, similar to the functionality found in standard antimalware tools. This signifies that Apple now regards its Mac OS X platform as a serious target for cybercriminals.

In [one of our security articles last autumn](http://www.norman.com/security_center/security_center_archive/2010/91940/en-us), we showed that the cybercriminals had started to use a new technique. This included infecting web sites and presenting the visitors with a fake warning customized to the users' browser. See the article [Old dogs learn new tricks](http://www.norman.com/security_center/security_center_archive/2010/91940/en-us) for more details.

**Another variant**

A while ago, another variant emerged. This one combines the traditional fake antimalware infection technique (displaying a fake malware scan showing infections) with the technique used in our abovementioned security article (customized web page).

So it is fair to say that this article's title about the old dogs' learning ability is relevant.

Here is one example of a fake scanning window displayed through Firefox:

[![](http://3.bp.blogspot.com/-jpgtwuzV3rA/TenvqvxQekI/AAAAAAAAD48/Jc2TIcH5qzs/s400/firefox_fake_malware_alert_None.large.png)](http://3.bp.blogspot.com/-jpgtwuzV3rA/TenvqvxQekI/AAAAAAAAD48/Jc2TIcH5qzs/s1600/firefox_fake_malware_alert_None.large.png)

Clicking the recommended Start Protection button will start installing the malicious software.

The real warning page from Mozilla's Firefox looks like this:

[![](http://2.bp.blogspot.com/-5_jpP5Tjtow/TenvsnZSaNI/AAAAAAAAD5A/brEFAtagmxY/s400/firefox_standard_alert_None.large.png)](http://2.bp.blogspot.com/-5_jpP5Tjtow/TenvsnZSaNI/AAAAAAAAD5A/brEFAtagmxY/s1600/firefox_standard_alert_None.large.png)

As you can see, the warning from Mozilla does not have any option to install any type of protection software. This is the standard behavior for all browsers.

One might expect that another variant of fake warning window to appear at a later point in time. This could be identical to the real Firefox warning, except that both the available buttons start installation of malware. The reason why the cybercriminals have not introduced this variant yet is only speculative. Perhaps their achieved success with displaying fake scanning results has proven sufficiently successful?

One of the clever tricks that this social engineering technique uses, it that the web site (usually an infected site) that displays the message checks the browser visiting the site, and displays a warning message similar to the browser's real warning.

  
**Protection mechanisms**

In order to protect yourself against this type of threats, you should not rely on specific rules. You should rather try to get into the correct mind-set. This will enable you to detect the attempts to use various social engineering techniques to trick you to perform actions that may harm you and your computer.

We repeat our recommendations from [our article 10 September last year](http://www.norman.com/security_center/security_center_archive/2011/cybercriminals_focus_on_new_targets/en-us):

> Ask yourself some control questions:  
> Is this the way the vendors of web browsers inform their users that security updates are available?  
> Generalization: Beware of unusual behavior!
> 
> Would big software vendors link to a third party web site for product downloads/purchases?  
> Generalization: If possible, check the URL in your browser! Does it comply with the web site the link suggested? 

> Does anything seem strange? (Are there e.g. spelling mistakes or strange wordings, which may imply that professional software vendors are not involved?)  
> Generalization: Watch out for unprofessionalism!