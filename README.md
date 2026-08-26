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
