---
layout: post
title: "Plain Text Email"
subtitle: "sending text email to multiple people easily using python."
background: '/img/posts/01.jpg'
---

--------------------------------------------------------------------------------

## Plain Text Email in python

--------------------------------------------------------------------------------

--------------------------------------------------------------------------------

### <u>Steps involved:</u>

```

    1) Instantiate MIMEMultipart or MIMEText from email.mime module.
    2) Add required fields for that object.
    3) Open SMTP connection with respective host name through any port.
    4) Add login credentials and start encryption service.
    5) Send the mail.

```

--------------------------------------------------------------------------------

```python
# MIME - Multi Purpose Internet Mail Extensions Protocol --> Helps to send non ascii charecters (audio, video etc.) in mail.
# MIMEMultipart helps in sending image and other files, MIMEText supports text.

from email.mime.multipart import MIMEMultipart
from email.mime.text import MIMEText

message = MIMEMultipart()
# Name at the header in the message.
message["from"] = "ABC Info."
# Email ID to which we have to send the email.
message["to"] = "testuser@gmail.com"
# Subject of email.
message["subject"] = "Sent from Python Program."
```

```python
# Fill the body of the message here.
# We can even pass html template in place of this body text.
message.attach(MIMEText("This is the body of message."))
```

```python
# smtp connection is a context manager (has __enter__ and __exit__ dunder methods) so it's better to use with
# with handles deletion of resources or closing of connections on it's own.
# SMTP host name depends on provider such as gmail, yahoo

import smtplib

with smtplib.SMTP(host="smtp.gmail.com",port=587) as smtp:
    # Similar to say hello to smtp connection.
    smtp.ehlo()

    # We should encrypt our message for sending as a mail.
    # TLS - Transport Layer Security
    smtp.starttls()

    # Give login credentials here.
    smtp.login("abc@gmail.com","gmifmwzbaikzzhrl")

    smtp.send_message(message)
    print("Email sent..")
```

```
Email sent..
```

--------------------------------------------------------------------------------

## Note:

````
If you get SMTPAuthenticationError -->

```
1) Try to enable 2 step authentication and use App password for mail and respective device.

        ------------------------------- or ------------------------------

2) Give permission to apps with less security to access your mail account.
```

I have given a dummy mail ID and dummy password in the program.

gupthaaravapalli97@gmail.com

--------------------------------------------------------------------------------````
