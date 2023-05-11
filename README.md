# Python send message to gmail
 In this project you can send message to your gmail. i uploaded this file to "python everywhere" wichs can run the file in visual machine so i can send mail every day. 
 
 <h3> Code </h3> 
```python 
import smtplib
import random
from email.mime.text import MIMEText
from email.header import Header

my_email = "youremail"  # The email which is send the messege
pasword = "yourpassword"  # your email password

with open("basari.txt", "r", encoding="utf-8") as f: #  take random sentence from basari.txt file

    data = f.readlines()
    list = []
    for x in data:
         list.append(x)

    text = random.choice(list)
    text1 = f"""


           <h2>{text}</h2>  

    """  # email contect

contect = MIMEText(text1, "html", "utf-8")
contect['From'] = Header("Python Daily", "utf-8")  # email header
subject = "Daily Motivation"  # subject
contect['Subject'] = Header(subject, "utf-8")
with smtplib.SMTP("smtp.gmail.com") as connection:
    connection.starttls()
    connection.login(my_email, pasword)
    connection.sendmail(from_addr=my_email, to_addrs=[
                        "targetemail@gmail.com"], msg=contect.as_string())  # target email you can u more emails
    list.remove(text)  # remove this sended sentence in list

    # write the texts remove the sentence which is sended
    with open("basari.txt", "w", encoding="utf-8") as x:
        for item in list:
            x.write(item)

```
