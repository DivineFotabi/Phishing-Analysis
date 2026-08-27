# Phishing-Analysis
# Email Overview
<img width="1852" height="801" alt="image" src="https://github.com/user-attachments/assets/61ab9ed9-1704-45b4-8c10-baa1a36e7152" />
Email shows to have come from Ripple News team urging its investors to unlock thier token accounts by registering into a link. This could be a possible credential capture attempt on thier users.

# Header Analysis
<img width="1555" height="692" alt="image" src="https://github.com/user-attachments/assets/463afe3b-82df-45dd-9a97-5d561108056b" />
Analysing the standard headers we noticed that information from Ripple News will contain the Ripple domain name incorporated in the email not the em5893.janbaskdigitaldesign.com as seen in the Return-Path.The Return-Path indicates the email where delivery failure notifications should be sent. This a possible email spoofing attempt by the sender and a potential redflag.

# Authentication
Sender Policy Framework(spf)
This authorises which mail servers can send mails onbehave of thier domains. when we look at the Received headers we can see when the email moved from the sender's mail server (s.wrqvtnrb.outbound-mail.sendgrid.net) to our trusted google mail server (AM7EUR06FT058.mail.protection.outlook.com). 

<img width="672" height="186" alt="image" src="https://github.com/user-attachments/assets/59a8d74b-4c1d-4f15-84b0-d3c6668ef0ec" />

Email originated from s.wrqvtnrb.outbound-mail.sendgrid.net which is authorise to send emails for em5893.janbaskdigitaldesign.com and the spf recorded included sengrid.net indicating that emails can be sent through the sendgrid infrastructure and the receiving google server allow the email to pass through. Hence Spf=Pass

Domain Key Identified Mail (Dkim)

This authenticate the origin of the message. The purpose of this is to verify that the email message was sent from the domain it claims to be 

<img width="972" height="170" alt="image" src="https://github.com/user-attachments/assets/e53a9bde-f574-4d1a-ad09-6ae07efda491" />

V=1 which stands for the version one, a=rsa-sha256 refers to the algorithm used to genarate the signature, c=relaxed/relaxed ,this refers to the algorithm used for the header and the body of the message. We have the domain d=janbaskdigitaldesign.com and the selector s=S1 both are used to locate the public key that email systems can used to verify the signature. bh whish stands for the body hash and encoded in B64, b: the b filled which is the Dkim signature itself

<img width="1847" height="422" alt="image" src="https://github.com/user-attachments/assets/b1d7c751-4c00-4d9b-a0a2-7a99af2d979c" />

Checked the public key manually and verified that it corresponds to that of the tool

<img width="1532" height="871" alt="image" src="https://github.com/user-attachments/assets/91104ed2-66dc-4a69-ac64-3559c069715b" />

This indicates the public keys matched and hence Dkim=pass

<img width="627" height="57" alt="image" src="https://github.com/user-attachments/assets/d8007f51-45aa-482e-9343-8e9048a10189" />

Domain Base Message Authentication Reporting and conformance (DMARC)

This helps to add a layer of control for domain owners. Hence DMARC= Pass.

Summarising the authentication analysis in the authentication header above shows that spf= pass, Dkim= pass. Dmac= pass but had we failed it will be set to reject indicating that it will tell the mail server to reject the email. This does not automatic determine the faith of an email as attackers always have ways to pass this check by like registering a look-alike domain or compromising a legitimate mail box like google.

# Content Analysis

<img width="1702" height="785" alt="image" src="https://github.com/user-attachments/assets/7ef597eb-3ef5-42c4-b08b-5e780266fd7b" />
The email shows to have come from Ripple News. After searching on the sender I saw that mails from Ripple team are incorporated with the Ripple.com domain and not janbaskdigitaldesign.com.This is a possible spoofing attempt.The email subject and first line shows and attempt of inducing a sense of urgency claiming we need to submit certain details to unblock our token. Showing high rate of social engineering . 

<img width="1770" height="815" alt="image" src="https://github.com/user-attachments/assets/9ca01e30-b718-4fa6-aa03-a2c7dc4a39b2" /> 
When we hover over the little image at the top of the mail I discovered that the email contained imbeded links.This is an attempt to hide executable links unlike the submit button link which is somehow visible though not trusted and not to be clicked aswell. This is a call for concern.

# URL Analysis











