- 👋 Hi, I’m @dandan120l
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
dandan120l/dandan120l is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
import smtplib
import random
import string
from selenium import webdriver
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.chrome.service import Service
from selenium.webdriver.common.by import By

# Function to generate a random email address
def generate_random_email():
    random_string = ''.join(random.choices(string.ascii_lowercase + string.digits, k=8))
    return f"{random_string}@example.com"

# Generate a random email address
email_address = generate_random_email()

# Send an email with SMTP (Simple Mail Transfer Protocol)
smtp_server = "smtp.example.com"  # Replace with your SMTP server details
smtp_port = 587  # Replace with your SMTP port number
sender_email = "your-email@example.com"  # Replace with your email address
receiver_email = email_address
password = "your-password"  # Replace with your email password

message = f"Subject: New YouTube Subscription\n\nSubscribe to Lemkin Realty"
with smtplib.SMTP(smtp_server, smtp_port) as server:
    server.starttls()
    server.login(sender_email, password)
    server.sendmail(sender_email, receiver_email, message)

# Open Chrome browser using Selenium WebDriver
webdriver_service = Service('path/to/chromedriver')  # Replace with the path to your chromedriver executable
webdriver_service.start()
driver = webdriver.WebDriver(service=webdriver_service)

# Go to YouTube and subscribe to Lemkin Realty
driver.get("https://www.youtube.com/")
search_box = driver.find_element(By.NAME, "search_query")
search_box.send_keys("Lemkin Realty")
search_box.send_keys(Keys.ENTER)
driver.find_element(By.CSS_SELECTOR, "#channel-subscribe-button").click()

# Close the browser
driver.quit()
