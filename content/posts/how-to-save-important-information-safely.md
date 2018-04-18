---
title: "Access tokens, passwords, sensible data, and how to avoid a data breach"
date: 2018-04-12T01:09:48+02:00
draft: true
categories: ["security", "privacy"]
tags: ["data security", "passwords", "company", "business critical"]
description: "A primer on data security for small businesses and others"
keywords: ["data security", "passwords", "company", "business critical", "small businesses", "data"]
---
# Some words about privacy (and data privacy)

Many people consider the terms data protection, data privacy, and privacy in generell to be synonyms, and even though they are all closely related, they complement each other without ever being the same. 
___
privacy: the quality or state of being apart from company or observation<sup>[1](https://www.merriam-webster.com/dictionary/privacy)</sup>

data privacy: ...is about authorized access — who has it and who defines it<sup>[2](https://blog.ipswitch.com/data-privacy-vs-data-protection)</sup>

data protection: ...is about securing data against unauthorized access.<sup>[3](https://blog.ipswitch.com/data-privacy-vs-data-protection)</sup>
___

Whilst privacy is part of data privacy and data privacy is thus just extended in order to achieve a clearer understanding of which privacy one is referring to, it doesn't exclude the mere problem of still being under surveillance (like in privacy defined) and therefore being endangered of a possible databreach. Whereas data protection is about assuring that the possibility of an data breach, is as low as possible.

**==This article is focusing on the basics of data protection for DevOps, IT, and IT Management==**

So that no penguins can be like:

<center>![Get your Information](/images/getinfo.gif)</center>

# 10 Basic steps to store passwords, access token, and other sensible data securely and private

Most of these tips will be a no brainer and come as no surprise, but especially because of this, it is of uttermost importance to pursue it, rather than just pray it. In organizational structures, people develop antipatterns very quickly (especially in software development, and other highly process structured environments). It starts out as a "shortcut" because Employee A needs to have quick access, that's why he wrote a password on a post-it next to his machine. Suddenly, all other employees do the same and a massive data breach is just a matter of time. Worst things I've seen are operations employees in support writing down customer passwords on a random sheet of paper, leaving it in the wild for days. How to mitigate these issues is easily explained, but very hard to implement. Once a employee has developed a certain behaviour, it is very hard to retrain them. Thus, do not even start with poor management of sensible information such as access tokens, and passwords.


## 1. Have a strong password policy

A lot of services and SaaS Tools that require authentication have their own password policy. But having an own password policy (defining proper requirements for a password used to authenticate accounts in company context) that lifts password complexity to a maximum, and thus making passwords more sturdy against brute force attacks should be in place. This of course means that passwords are getting harder to remember, but if you can not remember that 32 characters long password with at least  

## 2. Stop sharing accounts

Sharing accounts means sharing credentials - DO NOT EVER DO THIS! Especially not in a company/organizational environment. This most certainly always implies, that sooner or later, the account will be abused for malicious actions. Sharing credentials is basically not having authentification at all. It defeats the purpose. It is common practice to share accounts to internal tools like ZenDesk (for Ops), or Atlassian Cloud for engineering, which leads to uncontrollability of those tools. Even if the shared "stakeholder" account, as one might call it, has limited permissions, this account is more likely to create a data breach, as more users know the credentials than one. The likelihood of a databreach can be seen as a exponantial curve, the more user share an account and thus have knowledge about the access, probably written down somewhere, the likelier it is that one of the users is having a data breach exposing the credentials to potential invaders. The common argument: "But we know who has the password, if someone does bad things, we will surely figure out who in our company deleted the file...." is simply wrong. Another common argument of limited permissions is easy to beat. Limited and controlled access does not stop other people from finding backdoors or possible bugs in systems that are out of your control. All the above mentioned tools, that are used on a daily basis in thousands of companies have error prone code. As most of this software is closed source, bugs and vulnerabilities are much more likely. Furthermore, the publication of possible vulnerabilities underlies the company itself, and they can remain in "To-Do" for ages. 
Thus, there can be zero days exploits that can potentially be used after having an entry point to the system like a shared account, that leaked because of one of the employees tends to search for weird things on the internet. 

If your CEO, COO, 

## 3. Use a password manager

This comes as no surprise, a password manager should be a basic tool every user within a company should have. Every employee that deals with passwords, access tokens, or other information, should be taught how to use a password manager. Otherwise, people will begin to create their own password management

## 4. Managing revocation certificates, one time tokens, and Master Passwords

## 5. Use encryption where you can

## 6. Learn about Steganography
 
