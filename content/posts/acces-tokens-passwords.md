---
title: "Access tokens, passwords, sensible data, and how to avoid a data breach"
date: 2018-04-18T22:49:48+02:00
draft: false
categories: ["security", "privacy"]
tags: ["data security", "passwords", "company", "business critical"]
description: "A primer on data security for small businesses and others"
keywords: ["data security", "passwords", "company", "business critical", "small businesses", "data"]
---
# Some words about privacy (and data privacy) and how to assure it

Many people consider the terms data protection, data privacy, and privacy in general to be synonyms, and even though they are all closely related, they complement each other without ever being the same. 
___
privacy: the quality or state of being apart from company or observation<sup>[1](https://www.merriam-webster.com/dictionary/privacy)</sup>

data privacy: ...is about authorized access — who has it and who defines it<sup>[2](https://blog.ipswitch.com/data-privacy-vs-data-protection)</sup>

data protection: ...is about securing data against unauthorized access.<sup>[3](https://blog.ipswitch.com/data-privacy-vs-data-protection)</sup>
___

Whilst privacy is part of data privacy and data privacy is thus just extended in order to achieve a clearer understanding of which privacy one is referring to, it doesn't exclude the mere problem of still being under surveillance (like in privacy defined) and therefore being endangered of a possible data breach. Whereas data protection is about assuring that the possibility of a data breach, is as low as possible.

So that no penguins can be like:

<center>![Get your Information](/images/getinfo.gif)</center>

# 6 Basic rules to store passwords, access token, and other sensitive data securely and private

Most of these tips will be a no-brainer and come as no surprise, but especially because of this, it is of uttermost importance to pursue it, rather than just pray it. In organizational structures, people develop antipatterns very quickly (especially in software development, and other highly process structured environments). It starts out as a "shortcut" because Employee A needs to have quick access, that's why he wrote a password on a post-it next to his machine. Suddenly, all other employees do the same and a massive data breach is just a matter of time. Worst thing I've ever seen is writing down customer passwords on a random sheet of paper, leaving it in the wild for days. How to mitigate these issues is easily explained, but very hard to implement. Once an employee has developed a certain behaviour, it is very hard to retrain them. Thus, do not even start with poor management of sensitive information such as access tokens, and passwords.


## 1. Have a strong password creation policy

All services and SaaS Tools that require authentication have their own password policy. But having a company own password policy (defining proper requirements for a password used to authenticate accounts in company context) that lifts password complexity to a maximum, and thus making passwords more sturdy against brute force attacks, should be in place. This, of course, means that passwords are getting harder to remember, but if you can not remember that 32 characters long password with at least five special characters and alternated cases, do not fear and read rule number 3. 

## 2. Stop sharing accounts

Sharing accounts means sharing credentials - DO NOT EVER DO THIS! Especially not in a company/organizational environment. This most certainly always implies, that sooner or later, the account will be abused for malicious actions. Sharing credentials is basically not having authentification at all. It defeats the purpose. It is common practice to share accounts for internal tools like ZenDesk (for Ops), or Atlassian Cloud for engineering, which leads to uncontrollability of those tools. Even if the shared "stakeholder" account, as one might call it, has limited permissions, this account is more likely to create a data breach, as more users know the credentials than one. The likelihood of a data breach can be seen as a exponential curve, the more user share an account and thus have knowledge about the access, probably written down somewhere, the likelier it is that one of the users is having a data breach exposing the credentials to potential invaders. The common argument: "But we know who has the password, if someone does bad things, we will surely figure out who in our company deleted the file...." is simply wrong. Another common argument of limited permissions is easy to beat. Limited and controlled access does not stop other people from finding backdoors or possible bugs in systems that are out of your control. All the above-mentioned tools, that are used on a daily basis in thousands of companies have error-prone code. As most of this software is closed source, bugs and vulnerabilities are much more likely. Furthermore, the publication of possible vulnerabilities underlies the company itself, and they can remain in "To-Do" for ages. 
Thus, there can be zero days exploits that can potentially be used after having an entry point to the system like a shared account, that leaked because of one of the employees tends to search for weird things on the internet. 

If your CEO, COO, CFO or finance department tells you, that it is too expensive to buy slots for every employee in every tool, than you should reconsider your choice of tooling and switch to a much safer self hosted open source solution (which might have increased cost due to maintenance and self hosting), or simply reconsider your tooling choices in general. Most of the bigger platforms provide the tooling for all disciplins and you might be able to use the same platform/SaaS company product within different departments. Consolidate, or remove tools completely. Or just bite the bullet and spend a bit more money on unshared accounts, rather than having a ticking timebomb that will be much more expensive than accounts being shared, and compromised.

## 3. Use a password manager

This comes as no surprise, a password manager should be a basic tool every user within a company should have. Every employee that deals with passwords, access tokens, or other information, should be taught how to use a password manager. Otherwise, people will begin to create their own password management and the things I have encountered yet range from password protected excel sheets, to google sheets in google drive, post-it notes with full credentials on the desk, or textfiles. All of these options are equally wrong: completely wrong. It is not an option to store a password like this. It is highly understandable, that in a modern environment with several access tokens, not everyone is capable of memorizing all of them. Especially managers should always keep this in mind and enforce the usage of password managers. This way, the employees need to remember only one save password matching the password requirements mentioned in step 1. This should be part of the onboarding process of the new employee. Ideally, the password for the password manager is memorized immediately. Due to the unlikeliness, the password can be stored in a trustworthy place encrypted on an usb stick or other offline media, which is only readable with the GPG Key of the employee that he created on his machine. This allows only the user onwing the key and the file to read it. A fireproof safe for media (more in rule number four), is a perfect place to store such a file on a usb stick.

There are tons of "best password manager"-lists available, if you want a ressource on good software, here are some links:

[opensource.com](https://opensource.com/article/16/12/password-managers)

Mentioning KeyPass, KeyPassX, Padlock, and Passbolt as open source and partially self hosted solutions. 

Also worth mentioning is Encryptr from Spideroak:

[Spideroak - Encryptr](https://spideroak.com/encryptr/) 

Currently my choice of software for password management, due to the easy, clean interface, and the fact that it runs on all platforms plus it is also open source.

There are several commercial alternatives that work very well too, like LastPass or 1Password. However, the benefits of picking open source software is, that the code is open for review, and therefore, less likely to create vulnerable software. 
Hosting can always be a problem, if you don't trust a zero knowledge cloud, you should consider hosting an instance of Passbolt yourself.

## 3.1 Don't lock yourself out

It happenes that people trap themself out of systems because they saved their login to a pwd manager inside of their account. It might sound silly, but I've seen that happen.

## 4. Managing revocation certificates, one time tokens, and Master Passwords

Easiest of all, avoid situations where you create unnecessary new certificates, tokens, or master passwords. Keep things simple, and precise. However, a lot of these keys need to be stored offline and non-digital.

If it is only the owner, that needs the information, one can use the password safe. If a revocation certificate for a GPG Key is stored for e.g. additional security for authentication of API access of third parties or similar, it implies a handover process of the key, or multiple user must have access to it. This is not contradicting with rule #2, we are not talking about shared credentials. MasterPasswords (e.g. for Database access of production environments) are another example for this scenario. 

So how to save this kind of sensitive information?

Put it in a safe. It's that simple, for everything that you can possibly need, and that needs to be shared with other employees plus it needs to be offline available - put it in a safe. But buy a proper one that is fireproof, fixed and made for datadrives. This way you can easily risk a fire and let your location burn down, while bbqing some sausages not needing to worry about the Database Masterkey that is stored as an GPG encrypted textfile in an image (steganography - more on this topic later) on a AES256 encrypted USB Stick. Now you just need to worry in one case: that is all the people that know the different keys to enter the safe, unlock the usb stick, and everything else, are inside of the building that is burning down.

<center><iframe src="https://giphy.com/embed/zcchHpCm44aac" width="480" height="268" frameBorder="0" class="giphy-embed" allowFullScreen></iframe></center>

Another really neat way to save this kind of information is buying the above mentioned type of USB Stick, so that people that have the responsibility to maintain a product remotely and at any time, have a secure option to carry the keys with them. But as always, do not rely on one person, otherwise you will have a bus factor <sup>[4](https://en.wikipedia.org/wiki/Bus_factor)</sup> situation.

## 5. Use two tier authentication where you can

It's very easy - make use of two tier authentication whenever possible. Apple is a great example of providing proper two tier auth. For becoming a B2B Volume Purchasing Programm member, a user does not even have the chance, to skip this option. It enforces the user to activate two tier authentication. A lot of people secure their Steam, or Battle.net accounts with two tier auth., but leave their Apple ID (which allows possible intruders to track people, read information from iCloud etc.) unsecured. If a company provides the option, one should make use of it.

## 6. Learn about Steganography and use it
 
 Steganography is the hiding of a secret message within an ordinary message and the extraction of it at its destination<sup>[5](https://searchsecurity.techtarget.com/definition/steganography)</sup>. There is room for creative use with the knowledge about steganography. Steganography allows the user to save data (e.g. a text or a file) within an image, like this awesome fireproof data safe. It can also be saved in audio files. If you feel reminded about Mr. Robot, well, yes than you know that the writers did their research there. AES encryption of messages is also possible.

 Saving information in jpg files, can alter the filesize and thus point to hidden information. It is not recommended to hide big files within a cat image that is obviously not that big. However, saving some credentials, or a master password, within a scanned jpg of a document that is obsolete but seems to be important enough to save it on a secure USB Stick, might just be the perfect decoy. I also recommend saving the jpg inside of an pdf. Extracting the original is no problem and it can be decoded as usual.

 <center>![Get your Information](/images/safe_with_message.jpg)</center>

 Most tools available use the LSB method (Least significant bit) instead of adding bits and increasing the chance of being read out easily(such as in the file header). It replaces bits of the original file, that are not used. In a rgb bitmap the pixel is defined by three bytes for the color information. Most of the times not all of the 8 bits are used to define the color, therefore one could alter the LSB and gain three bits to store other information. This also has the benefit of not increasing the filesize. 

 Here is some more indepth ressource to the topic: [read me](https://null-byte.wonderhowto.com/how-to/steganography-hide-secret-data-inside-image-audio-file-seconds-0180936/)

<center><iframe src="https://giphy.com/embed/26ufdipQqU2lhNA4g" width="480" height="480" frameBorder="0" class="giphy-embed" allowFullScreen></iframe></center>

# 7. Learn about cryptography and use it

Cryptography tools like [GPG](https://www.gnupg.org/) help you to keep privacy and verify the source of documents. It's widely used in E-Mails and other communication, as well as to encrypt data or information. Basically, the main functionality is issuing private keys, and corresponding public keys, and encrypting the message that needs to be stored or sent. For more on the functionality of cryptography with [GPG see here](https://www.gnupg.org/gph/en/manual.html). The documentation also explains very well, how to manage your keys, key integrity, and the revocation process.

If managers, and employees alike follow by these simple rules and tips, a much safer environment is created. Implement a standard set of processes for information security in your onboarding process of new employees, and the likelihood to succeed in creating a safe environment in your company is much higher. 

<center><iframe src="https://giphy.com/embed/2xMO4pzC0TLLq" width="480" height="264" frameBorder="0" class="giphy-embed" allowFullScreen></iframe></center>