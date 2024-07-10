# email_notification
 how to use smtplib to send an email notification.
```bash
import smtplib
from email.mime.multipart import MIMEMultipart
from email.mime.text import MIMEText

def send_email_alert(price, url, recipient_email):
    sender_email = "your_email@example.com"
    sender_password = "your_email_password"
    
    message = MIMEMultipart()
    message['From'] = sender_email
    message['To'] = recipient_email
    message['Subject'] = "Price Drop Alert!"
    
    body = f"The price of the product has dropped to Rs.{price}. Check it out here: {url}"
    message.attach(MIMEText(body, 'plain'))
    
    with smtplib.SMTP('smtp.gmail.com', 587) as server:
        server.starttls()
        server.login(sender_email, sender_password)
        server.send_message(message)


# Example usage
price = 1500
url = "https://www.myntra.com/product-url"
recipient_email = "recipient@example.com"
send_email_alert(price, url, recipient_email)
```
The error you may encounter, SMTPAuthenticationError: (534, ...), indicates that Google has blocked the sign-in attempt because it requires an application-specific password. This typically occurs when using less secure apps or scripts to sign in to your Gmail account. To resolve this, you need to use an App Password or enable "Less secure app access" (which is not recommended due to security concerns).

By using app password u can send email notification.

```bash
import smtplib
from email.mime.multipart import MIMEMultipart
from email.mime.text import MIMEText

def send_email_alert(price, url, recipient_email):
    sender_email = "your_email@example.com"
    sender_password = "your_app_password"  # Use the generated App Password here
    
    message = MIMEMultipart()
    message['From'] = sender_email
    message['To'] = recipient_email
    message['Subject'] = "Price Drop Alert!"
    
    body = f"The price of the product has dropped to Rs.26. Check it out here: {url}"
    message.attach(MIMEText(body, 'plain'))
    
    with smtplib.SMTP('smtp.gmail.com', 587) as server:
        server.starttls()
        server.login(sender_email, sender_password)
        server.send_message(message)

# Example usage
price = 1500
url = "https://www.myntra.com/product-url"
recipient_email = "recipient@example.com"
send_email_alert(price, url, recipient_email)
```
![Screenshot 2024-07-10 153302](https://github.com/Ritulkumari/email_notification/assets/98699438/a23e4fe8-604c-4349-a849-3fa9dfd1418a)

This is how it gonna show up and notify the recipient u want to!!! 

