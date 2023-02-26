---
toc: true
comments: true
title: Big Idea 5.6 Safe Computing
layout: post
description: This tech talk discusses safe computing
categories: [Week 22]
---

# Safe Computing

### Personal Identifiable Information (PII)
As we create a Web Site and post information we are adding to the Searchable PII.  However, there is a dichotomy as a site ***like LinkedIn is a place where we want to be known for our accomplishments***.  But be aware, the person that looks at your LinkedIn will, **most likely**, look at things like TikTok, Instagram or Facebook.  

### PII considerations
* Things that will be known by everyone:  Name, Email (suggest a junk email), Picture, High School attended, College Attended, Properties you own, State-City of residence, all State-City of previous residence, Credit Reports, ... 
* Gray area items, more cautious: Birth date, Place of Birth, Street Address, Phone Number, Maiden names of Mother and Grandmother, Drivers License Number, ...
* Things that you should strive to keep absolutely secret: Credentials for Access, Two-Factor Authentication on Financial accounts, Social Security Number, Tax records, ...

### Beware, Establish practices for your own Safety
* ***Multi-factor authentication*** often requires you to enter a code that has been texted or emailed to you.   Other types of authentication are biometrics (finger print or facial recognition).
* ***Malware*** is often sent in attachments to things in email.  Often they request you to click on an attachment and it starts the process of adding a virus to your computer.
* ***Phishing*** is where unknown sources try to entice you into a response, like click here and receive $500.  Often such systems impersonate someone like Amazon asking for login information.  Be careful to look closely at source of email (ie amzn.com vs amazon.com).

### Factors to Increase Security of System (**recommend** Watch 5.6 Video 2)
* Most of my financials or critical systems use **Multi Factor authentication**
* Biometrics is something that is used secure systems, fingerprints or facial recognition
* ***Symmetric*** encryption is a type of encryption where only ***one key (a secret key)*** is used to both encrypt and decrypt electronic information.
* ***Asymmetric cryptography***, also known as public-key cryptography, is a process that uses a pair of related keys -- ***one public key and one private key*** -- to encrypt and decrypt a message and protect it from unauthorized access or use.
* SSL Uses both Asymmetric and Symmetric Encryption

### Nefarious Uses of Internet
* A Virus or Malware compromise security, they are opposite of increasing security.  
* Phishing is a way to get a Virus on your machine, or a way to get you to input PII.
* After a Virus or being compromised by Phishing it is advised to review all of you PII vulnerabilities.

## Blog Post Reflection:
1. Describe PII you have seen on project in CompSci Principles.
    - Projects that include PII on a project in CSP is seen on the login page. When people login to a site on our website, their information includes their name and their email.
2. What are your feelings about PII and your personal exposure?
    - I think PIIs have the potential to be dangerous because people are able to stalk you online and I don’t want to be stalked. However, PII’s are necessary for login and user experience so it is important to be sure that the information you are giving is to a secure website where your information will not be stolen.
3. Describe good and bad passwords?  What is another step that is used to assist in authentication.
    - A good password is one that can not be guessed by other people and does not include any personal information.
    - A bad password is 1234567890 or something that can be easily guessed.
4. Try to describe Symmetric and Asymmetric encryption.
    - Symmetric Encryption: Method of encryption where the same key is used for both encryption and decryption; is fast and efficient (SECRET KEY)
    - Asymmetric Encryption: encryption that uses two different keys for encryption and decryption. The public key, is used for encrypting the data and shared widely, and the private key, is used for decrypting the data and must be kept confidential.
5. Provide an example of encryption we used in AWS deployment.
    - AES-256 encryption
6. Describe a phishing scheme you have learned about ***the hard way***.  Describe some other phishing techniques.
    - A phishing scheme I seen recently is where an unknown number texts you about a guaranteed way to make a lot of money using cryptocurrencies and asks you to click the link they have included. They say this link adds you to a giveaway where the winner gets to know the secret method to make the money. In reality the link just steals your information and the giveaway is fake.
    - Other phishing include malicious websites, voice mail messages, or email.