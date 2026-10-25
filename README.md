# Revenue_Recovery_Agent


An AI-powered revenue recovery system designed to identify revenue at risk, manage recovery cases, analyze customer responses, and automate follow-up actions for failed payments and abandoned checkouts.

The system combines an Oracle database, Node.js/Express backend, React frontend, scheduled recovery workflows, and Groq-powered AI intent detection.

---

## 1. Project Overview

Businesses lose revenue when customers:

- Abandon checkout before completing payment
- Experience subscription payment failures
- Promise to pay later but do not complete the payment
- Ignore payment reminders
- Require multiple recovery attempts

The Revenue Recovery Agent provides an automated workflow for identifying and handling these cases.

Instead of simply recording failed transactions, the system creates recovery cases, assigns risk scores, determines appropriate recovery actions, tracks customer interactions, understands customer responses using AI, and schedules follow-up actions.

---

## 2. Objectives

The main objectives of the project are:

- Detect revenue that is at risk
- Create recovery cases for failed payments and abandoned checkouts
- Prioritize cases using risk scores
- Automatically determine the next recovery action
- Track recovery attempts
- Analyze customer responses
- Support Hinglish customer responses
- Detect promise-to-pay commitments
- Track whether promised payments are completed
- Automatically process due recovery cases
- Provide a dashboard for monitoring the recovery process

---

## 3. Major Use Cases

### 3.1 Checkout Drop-Off Recovery

When a customer starts a checkout but does not complete payment, the system identifies the abandoned checkout and creates a recovery case.

Possible recovery actions include:

- Send reminder
- Send payment link
- Voice call
- Follow-up

---

### 3.2 Failed Subscription Recovery

When a recurring subscription payment fails, the system creates a recovery case.

Examples of payment failure reasons include:

- Bank declined
- Insufficient funds
- Expired card

The recovery agent then determines the appropriate action such as retrying the payment or contacting the customer.

---

### 3.3 Promise-to-Pay Tracking

The system can detect when a customer promises to make a payment later.

Example:

> "Salary Monday ko aayegi, uske baad payment kar dunga."

The AI detects:

`PROMISE_TO_PAY`

and extracts the promised payment date.

The recovery case is updated to:

`PROMISED`

with:

`FOLLOW_UP`

as the next action.

After the promised date, the system checks whether the payment was completed.

If payment was received:

`RECOVERED`

If payment was not received:

`IN_PROGRESS`

and another recovery action can be scheduled.

---

### 3.4 Hinglish Customer Interaction

Customers may respond using English, Hindi, or Hinglish.

Examples:

> "Kal payment kar dunga."

> "Salary Monday ko aayegi."

> "Abhi payment nahi kar sakta."

The AI component analyzes these responses and determines the customer's intent.

---

## 4. Technology Stack

### Frontend

- React
- Vite
- JavaScript
- CSS

### Backend

- Node.js
- Express.js
- node-oracledb
- node-cron
- Groq SDK

### Database

- Oracle Database 21c XE
- Oracle running through Docker

### AI

Groq API is used for customer intent detection and promise-date extraction.

Current AI model:

`openai/gpt-oss-20b`

### Development Tools

- Visual Studio Code
- Oracle SQL Developer Extension for VS Code
- Postman
- Docker
- Git

---
