# EMAIL ANALYSIS : Email Header Analysis | Home Lab

<img width="661" height="292" alt="emailAnalysis2" src="https://github.com/user-attachments/assets/a4bbc238-7730-40cc-93b7-6df8de3af846" />


## Introduction

Analyzing emails depends on the type of mail in your inbox, whether a phishing email or just the normal. In this lab, I analyzed a random email to check if it indicates a legitimate or suspicious mail. **This is a manual check with no online or cli tools.**

## Practical Demo

This is the procedure for getting email analysis.

**Open Email.**

![image.png](EMAIL%20ANALYSIS%20Email%20Header%20Analysis%20Home%20Lab/image.png)

This is the test email I am going to analyze

![front.png](EMAIL%20ANALYSIS%20Email%20Header%20Analysis%20Home%20Lab/front.png)

In the email body window, I decided to check the “**show details”** menu of the email by clicking on the drop down arrow below the sender’s name. This provides us with a **simplified email authentication summary** box. We can see from the image, where the ownership domain is constant, making this part of the email **✅ Valid.**

**Next step is to check for the raw headers.**

In the email body, click on the 3 dots

![showOriginal.png](EMAIL%20ANALYSIS%20Email%20Header%20Analysis%20Home%20Lab/showOriginal.png)

Then click on “**show original”** in the drop down menu.

A new **window/tab** will appear.

![originalMsg.png](EMAIL%20ANALYSIS%20Email%20Header%20Analysis%20Home%20Lab/originalMsg.png)

Seeing all 3 security checks “**PASS**” which are the SPF, DKIM and DMARC, proves this part of the email is also **✅ Valid.**

**Moving to the raw headers of the email.**

Below the image above, we have the email header.

![First part of the email header.](EMAIL%20ANALYSIS%20Email%20Header%20Analysis%20Home%20Lab/1stpartHeader.png)

First part of the email header.

**We can see from the header, where:**

- Delivered-To : shows the recipient email address
- Received : indicating the SMTP server that received or accepted the email

> NOTE : In the ARC - Seal field, the “**cv=none**” failing does not necessarily mean the email is bad, although it counts in email authentication. Not a red flag, since it happens to most emails that are original.
> 

- ARC-Message-Signature : verifies the integrity of the email content - it shows how the domain, **google.com**, verified the SPF, DKIM and DMARC.

**SPF (Sender Policy Framework)** — pass : indicates the domain [scottmax.com](http://scottmax.com) permits the host (IP address) to send emails.

**DKIM (Domain Keys Identified Mail)** — pass : both [scottmax.com](http://scottmax.com) and [sendgrid.info](http://sendgrid.info) are verified successfully.

**DMARC (Domain-based Message Authentication, Reporting and Conformance)** — pass as well, depending on SPF and DKIM.

- Return-Path : it shows the message was mailed by a subdomain of **ScottMax,** displaying **ckespa.scottmax.com**

✅ **Valid**

![Second part of the email header.](EMAIL%20ANALYSIS%20Email%20Header%20Analysis%20Home%20Lab/image%201.png)

Second part of the email header.

- Received-SPF : SPF indicates the sending IP matches the DNS SPF records for scottmax.com

✅ **Valid**

- DKIM Signatures
    - Both have valid hashes (**header.b= “value”**) representing each provider
    - [**scottmax.com](http://scottmax.com)** pass as the main domain
    - [**sendgrid.info](http://sendgrid.info)** pass as the email delivery infrastructure

✅ **Valid and Accurate**

- Message-ID : indicates the email was transmitted from [**convertkit.com](http://convertkit.com)** known for marketing and newsletters.
- Content-Type : ✅ **Valid and Accurate;** indicating email in plain-text form.

> NOTE: Although there are some errors like, ARC:cv=none and ARC-Message-Signature:c=relaxed/relaxed (duplicating both headers and body) does not necessarily mean the email is compromised.
> 

## Overall verification

**The email header remains accurate, valid and authenticated.**

- It originates from verified sources (**scottmax, convertkit** and **sendgrid**)
- Most authenticated fields pass clean (**SPF, DKIM** and **DMARC**)

**Trusted level : 9 / 10 (SAFE)**

## Thank you.
