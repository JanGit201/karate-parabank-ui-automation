# Karate ParaBank UI Automation Framework

A robust automated UI testing framework built with the **Karate Framework** and **JUnit 5** to validate user workflows on the ParaBank demo application. This project demonstrates modern BDD (Behavior Driven Development) practices, dynamic test data generation, and stable browser interaction via the Chrome DevTools protocol.

---

## 🚀 Key Features
* **Zero Webdriver Dependency:** Utilizes Karate's native Chrome DevTools integration for faster, lighter execution without requiring separate WebDriver binaries.
* **Dynamic Data Generation:** Features runtime JavaScript evaluation to generate unique user registration credentials dynamically for isolated test runs.
* **Smart Wait Mechanisms:** Built-in auto-waiting (`waitFor`) to guarantee robust synchronization with asynchronous elements and eliminate test flakiness.
* **Recruiter-Ready Reporting:** Auto-generates detailed HTML reports with embedded failure screenshots.

---

## 🛠️ Tech Stack & Prerequisites
* **Java Development Kit (JDK):** Version 11 or higher
* **Build Tool:** Apache Maven 3.6+
* **Automation Framework:** Karate Core & JUnit 5 Integration (v1.4.1)
* **Target Browser:** Google Chrome

---

## 📂 Project Structure
```text
karate-parabank-ui-automation/
├── src/
│   └── test/
│       └── java/
│           ├── karate-config.js      # Global framework configuration & environments
│           ├── logback-test.xml      # Console and file logging levels configuration
│           └── ui/
│               ├── ParaBankUI.feature # Gherkin end-to-end test scenarios
│               └── UiTestRunner.java  # JUnit 5 test execution entry point
├── .gitignore                         # Excludes local targets and metadata from Git
└── pom.xml                            # Project dependencies and build management
```
---

## 📝 Sample UI Test Scenario

Below is an example demonstrating how a ParaBank login validation scenario is structured within this framework:

```gherkin
Feature: ParaBank User Authentication

  Background:
    * configure driver = { type: 'chrome' }

  Scenario: Verify successful user login with valid credentials
    Given driver 'https://parabank.parasoft.com/parabank/index.htm'
    And input("//input[@name='username']", 'john_doe')
    And input("//input[@name='password']", 'Password123')
    When click("//input[@value='Log In']")
    Then waitForText('#leftPanel', 'Welcome John Doe')
```
