## Selenium Projects - README Guide

### Overview
This README provides a detailed guide for several Selenium-based web automation projects. Each project demonstrates different functionalities using Selenium WebDriver, such as scraping information, automating form submissions, and interacting with various web elements.

### Prerequisites
Ensure you have the following installed on your system:
- Python
- Selenium (`pip install selenium`)
- WebDriver for your browser (e.g., `chromedriver` for Chrome)

### Projects

#### 1. Amazon Price Tracker
This script automates the process of checking the price of an item on Amazon.

**Usage:**
1. Initialize the Chrome WebDriver with options to keep the browser open after the script finishes.
2. Navigate to the desired Amazon product page.
3. Locate the price elements on the page using XPath.
4. Print the price of the product.

**Script:**
```python
from selenium import webdriver
from selenium.webdriver.common.by import By

chrome_options = webdriver.ChromeOptions()
chrome_options.add_experimental_option("detach", True)
driver = webdriver.Chrome(options=chrome_options)

driver.get("https://www.amazon.com/dp/B075CYMYK6?psc=1&ref_=cm_sw_r_cp_ud_ct_FM9M699VKHTT47YD50Q6")

price_dollar = driver.find_element(By.XPATH, value='//*[@id="corePriceDisplay_desktop_feature_div"]/div[1]/span[2]/span[2]/span[2]')
price_cents = driver.find_element(By.XPATH, value='//*[@id="corePriceDisplay_desktop_feature_div"]/div[1]/span[2]/span[2]/span[3]')

print(f"The price is {price_dollar.text}.{price_cents.text}")

driver.quit()
```

#### 2. Python.org Interaction
This script demonstrates how to interact with elements on the Python.org website.

**Usage:**
1. Initialize the Chrome WebDriver with options to keep the browser open after the script finishes.
2. Navigate to the Python.org homepage.
3. Interact with various elements such as search boxes, buttons, and links.

**Script:**
```python
from selenium import webdriver
from selenium.webdriver.common.by import By

chrome_options = webdriver.ChromeOptions()
chrome_options.add_experimental_option("detach", True)
driver = webdriver.Chrome(options=chrome_options)
driver.get("https://www.python.org/")

bug_link = driver.find_element(By.XPATH, value='//*[@id="site-map"]/div[2]/div/ul/li[3]/a')
print(bug_link.text)

driver.quit()
```

#### 3. Signup Form Automation
This script automates the process of filling and submitting a signup form.

**Usage:**
1. Initialize the Chrome WebDriver with options to keep the browser open after the script finishes.
2. Navigate to the signup form URL.
3. Locate the form fields and fill them with the appropriate information.
4. Submit the form.

**Script:**
```python
from selenium import webdriver
from selenium.webdriver.common.by import By

chrome_options = webdriver.ChromeOptions()
chrome_options.add_experimental_option("detach", True)
driver = webdriver.Chrome(options=chrome_options)
driver.get("http://secure-retreat-92358.herokuapp.com/")

first_name = driver.find_element(By.NAME, value="fName")
second_name = driver.find_element(By.NAME, value="lName")
email_address = driver.find_element(By.NAME, value="email")
submit = driver.find_element(By.CSS_SELECTOR, value="form button")

first_name.send_keys("first name")
second_name.send_keys("second name")
email_address.send_keys("your email account")
submit.click()
```

#### 4. Upcoming Events on Python.org
This script scrapes the upcoming events listed on the Python.org website.

**Usage:**
1. Initialize the Chrome WebDriver with options to keep the browser open after the script finishes.
2. Navigate to the Python.org homepage.
3. Scrape the event times and names.
4. Print the events in a dictionary format.

**Script:**
```python
from selenium import webdriver
from selenium.webdriver.common.by import By

chrome_options = webdriver.ChromeOptions()
chrome_options.add_experimental_option("detach", True)
driver = webdriver.Chrome(options=chrome_options)
driver.get("https://www.python.org/")

times = driver.find_elements(By.CSS_SELECTOR, value=".event-widget time")
names = driver.find_elements(By.CSS_SELECTOR, value=".event-widget li a")
events = {}

for n in range(len(times)):
    events[n] = {
        "time": times[n].text,
        "name": names[n].text,
    }
print(events)

driver.quit()
```

#### 5. Wikipedia Interaction
This script demonstrates interaction with the Wikipedia main page, including searching for articles.

**Usage:**
1. Initialize the Chrome WebDriver with options to keep the browser open after the script finishes.
2. Navigate to the Wikipedia main page.
3. Interact with elements such as the search bar to perform a search.

**Script:**
```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys

chrome_options = webdriver.ChromeOptions()
chrome_options.add_experimental_option("detach", True)
driver = webdriver.Chrome(options=chrome_options)
driver.get("https://en.wikipedia.org/wiki/Main_Page")

search = driver.find_element(By.NAME, value="search")
search.send_keys("Python", Keys.ENTER)
```

### Conclusion
These scripts demonstrate the use of Selenium WebDriver for various web automation tasks. Customize the scripts to fit your specific use cases and ensure that you have the necessary permissions to scrape or automate interactions on the websites you target.
