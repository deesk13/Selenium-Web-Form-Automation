# Selenium Web Form Automation

## 📌 Project Overview

This project demonstrates **web form automation using Python and Selenium WebDriver**.

The automation script opens a demo registration form, enters user information, selects radio buttons and checkboxes, fills address details, selects values from dropdowns, enters date and time, fills an email and mobile number, dynamically extracts a verification code, and finally submits the form.

## 🛠️ Technologies Used

* Python
* Selenium WebDriver
* Chrome WebDriver
* XPath
* CSS Selectors
* Explicit Wait
* Selenium `Select` class

## 🌐 Demo Website

The project automates the following demo form:

`https://vinothqaacademy.com/demo-site/`

## 📂 Project Structure

```text
selenium-web-form/
│
├── methods.py
└── README.md
```

## ⚙️ Installation

### 1. Clone the repository

```bash
git clone <your-repository-url>
```

### 2. Open the project

```bash
cd selenium-web-form
```

### 3. Create a virtual environment

```bash
python -m venv .venv
```

### 4. Activate the virtual environment

Windows:

```bash
.venv\Scripts\activate
```

### 5. Install Selenium

```bash
pip install selenium
```

## ▶️ Run the Program

```bash
python methods.py
```

The Chrome browser will open automatically and Selenium will perform the form-filling operations.

## 🧪 Automation Steps

The script performs the following operations:

### 1. Open the Demo Website

```python
driver.get("https://vinothqaacademy.com/demo-site/")
```

Opens the demo registration form.

### 2. Enter First Name and Last Name

```python
first_name.send_keys("Deva")
last_name.send_keys("dharshini")
```

The `send_keys()` method enters text into input fields.

### 3. Select Gender

```python
gender_female.click()
```

The Female radio button is selected using `click()`.

### 4. Select Courses

The script selects:

* Selenium WebDriver
* TestNG

It first checks whether the checkbox is already selected.

```python
if not course_selenium.is_selected():
    course_selenium.click()
```

`is_selected()` verifies the current state of a radio button or checkbox.

### 5. Enter Address Details

The following fields are populated:

* Street Address
* City
* State
* Postal Code

Example:

```python
city.send_keys("Chennai")
```

### 6. Select Country

The Selenium `Select` class is used for the country dropdown.

```python
country_dropdown = Select(
    driver.find_element(
        By.XPATH,
        "//select[contains(@id, 'vfb-13-country')]"
    )
)

country_dropdown.select_by_visible_text("India")
```

### 7. Enter Email

```python
email.send_keys("dharshini.test@example.com")
```

### 8. Enter Date

```python
date_input.send_keys("10/25/2026")
```

### 9. Select Time

The hour and minute dropdowns are handled using `Select`.

```python
time_hh.select_by_visible_text("10")
time_mm.select_by_visible_text("30")
```

### 10. Enter Mobile Number

```python
mobile.send_keys("9876543210")
```

### 11. Enter Query

The textarea is located and populated using:

```python
query_box.send_keys(
    "Automation testing request for registration workflow."
)
```

### 12. Dynamic Verification Code

The script reads the verification label from the webpage and extracts only the digits.

```python
verification_label = driver.find_element(
    By.XPATH,
    "//label[contains(text(), 'Example:')]"
).text

verification_code = "".join(
    filter(str.isdigit, verification_label)
)
```

The extracted code is then entered into the verification field.

### 13. Submit the Form

The submit button is located using an XPath and clicked.

```python
submit_btn = wait.until(
    EC.element_to_be_clickable(
        (
            By.XPATH,
            "//input[@type='submit' or @name='vfb-submit']"
        )
    )
)

submit_btn.click()

```
<img width="1820" height="866" alt="Screenshot 2026-10-06 115118" src="https://github.com/user-attachments/assets/7e743ba9-17f7-4181-9233-68a1afeed09b" />


## 🔍 Selenium Methods Demonstrated

| Selenium Method                 | Purpose                           |
| ------------------------------- | --------------------------------- |
| `get()`                         | Open a webpage                    |
| `find_element()`                | Locate an element                 |
| `send_keys()`                   | Enter text                        |
| `click()`                       | Click an element                  |
| `is_selected()`                 | Check checkbox/radio selection    |
| `Select()`                      | Work with dropdowns               |
| `select_by_visible_text()`      | Select dropdown option            |
| `WebDriverWait()`               | Wait for elements                 |
| `presence_of_element_located()` | Wait until element exists         |
| `element_to_be_clickable()`     | Wait until element can be clicked |
| `maximize_window()`             | Maximize browser window           |
| `quit()`                        | Close browser                     |

## ⏳ Explicit Wait

The project uses Selenium's explicit wait:

```python
wait = WebDriverWait(driver, 15)
```

For example:

```python
wait.until(
    EC.presence_of_element_located(
        (By.XPATH, "//input[contains(@id, 'vfb-5')]")
    )
)
```

This is better than depending only on fixed delays because Selenium waits for the required condition.

Automation Practice
