# Automate-Form-Submission.py-task-2

from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.chrome.service import Service
from webdriver_manager.chrome import ChromeDriverManager
import time

# Start browser
driver = webdriver.Chrome(service=Service(ChromeDriverManager().install()))
driver.maximize_window()

# Open form page
driver.get("https://www.selenium.dev/selenium/web/web-form.html")

# Wait for page load
time.sleep(2)

# Fill form fields
driver.find_element(By.NAME, "my-text").send_keys("Sharda Rathod")
driver.find_element(By.NAME, "my-password").send_keys("sharda@example.com")
driver.find_element(By.NAME, "my-textarea").send_keys("This is a test message")

# Click submit button
driver.find_element(By.CSS_SELECTOR, "button").click()

# Wait for result
time.sleep(2)

# Verify success message
message = driver.find_element(By.TAG_NAME, "h1").text

if "Form submitted" in message:
    print("✅ Form Submitted Successfully")
else:
    print("❌ Form Submission Failed")

# Close browser
driver.quit()
