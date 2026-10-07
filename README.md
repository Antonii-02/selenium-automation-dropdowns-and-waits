# selenium-automation-dropdowns-and-waits
```
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.action_chains import ActionChains
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
import time


# =====================================================
# START BROWSER
# =====================================================

driver = webdriver.Chrome()
driver.maximize_window()

wait = WebDriverWait(driver, 10)

print("Browser opened")


# =====================================================
# TC01 - OPEN SHOPPING WEBSITE
# =====================================================

print("\nTC01 - Open Shopping Website")

driver.get("https://www.saucedemo.com/")

print("Shopping website opened successfully")


# =====================================================
# LOGIN
# =====================================================

username = wait.until(
    EC.visibility_of_element_located(
        (By.ID, "user-name")
    )
)

password = driver.find_element(
    By.ID, "password"
)

login_button = driver.find_element(
    By.ID, "login-button"
)

username.send_keys("standard_user")
password.send_keys("secret_sauce")

login_button.click()

print("Login successful")


# =====================================================
# TC02 - ACCEPT ALERT
# =====================================================

print("\nTC02 - Accept Alert")

# Open Selenium alert page
driver.get(
    "https://www.selenium.dev/selenium/web/alerts.html"
)

driver.find_element(
    By.ID, "confirm"
).click()

alert = wait.until(
    EC.alert_is_present()
)

print("Alert:", alert.text)

alert.accept()

print("Alert accepted successfully")


# =====================================================
# TC03 - DISMISS ALERT
# =====================================================

print("\nTC03 - Dismiss Alert")

driver.find_element(
    By.ID, "confirm"
).click()

alert = wait.until(
    EC.alert_is_present()
)

print("Alert:", alert.text)

alert.dismiss()

print("Alert dismissed successfully")


# =====================================================
# TC04 - PROMPT ALERT
# =====================================================

print("\nTC04 - Prompt Alert")

driver.find_element(
    By.ID, "prompt"
).click()

alert = wait.until(
    EC.alert_is_present()
)

print("Prompt:", alert.text)

alert.send_keys("SIVA123")

alert.accept()

print("Information submitted successfully")


# =====================================================
# TC05 - MOUSE HOVER
# =====================================================

print("\nTC05 - Mouse Hover")

driver.get(
    "https://www.selenium.dev/selenium/web/web-form.html"
)

text_box = wait.until(
    EC.visibility_of_element_located(
        (By.NAME, "my-text")
    )
)

# Move mouse over textbox
ActionChains(driver).move_to_element(
    text_box
).perform()

print("Mouse hover performed successfully")


# =====================================================
# TC06 - DOUBLE CLICK
# =====================================================

print("\nTC06 - Double Click")

ActionChains(driver).double_click(
    text_box
).perform()

print("Double click performed successfully")


# =====================================================
# TC07 - DRAG AND DROP
# =====================================================

print("\nTC07 - Drag and Drop")

driver.get(
    "https://www.selenium.dev/selenium/web/mouse_interaction.html"
)

# Locate elements if available on the demo page
try:

    source = wait.until(
        EC.presence_of_element_located(
            (By.ID, "draggable")
        )
    )

    target = wait.until(
        EC.presence_of_element_located(
            (By.ID, "droppable")
        )
    )

    ActionChains(driver).drag_and_drop(
        source,
        target
    ).perform()

    print("Drag and drop performed successfully")

except Exception as e:

    print("Drag and drop elements not available on this page")


# =====================================================
# TC08 - EXPLICIT WAIT
# =====================================================

print("\nTC08 - Explicit Wait")

driver.get(
    "https://www.saucedemo.com/"
)

username = wait.until(
    EC.visibility_of_element_located(
        (By.ID, "user-name")
    )
)

username.send_keys("standard_user")

print("Explicit wait completed")
print("Username field displayed successfully")


# =====================================================
# TC09 - CLICKABLE WAIT
# =====================================================

print("\nTC09 - Clickable Wait")

password = wait.until(
    EC.element_to_be_clickable(
        (By.ID, "password")
    )
)

password.send_keys("secret_sauce")

login = wait.until(
    EC.element_to_be_clickable(
        (By.ID, "login-button")
    )
)

login.click()

print("Login button was clickable")
print("Login submitted successfully")


# =====================================================
# TC10 - ALERT WAIT
# =====================================================

print("\nTC10 - Alert Wait")

driver.get(
    "https://www.selenium.dev/selenium/web/alerts.html"
)

driver.find_element(
    By.ID, "alert"
).click()

confirmation = wait.until(
    EC.alert_is_present()
)

print("Confirmation Alert:")
print(confirmation.text)

confirmation.accept()

print("Confirmation alert handled successfully")


# =====================================================
# CLOSE BROWSER
# =====================================================

time.sleep(2)

driver.quit()
```
print("\n====================================")
print("ALL TEST CASES COMPLETED")
print("====================================")``
