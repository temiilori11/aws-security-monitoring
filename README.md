# AWS Security Monitoring: Failed Console Login Detection

This project demonstrates how to build a real-time security monitoring system on AWS that detects failed console login attempts and sends instant alert notifications.

## 🔐 Goal
Create a CloudWatch alarm that triggers when multiple failed login attempts are detected in AWS CloudTrail, then notify via AWS SNS (email alert).

## 🚀 What I Built
- Enabled **AWS CloudTrail** to capture management events.
- Located **ConsoleLogin** failures in Event History.
- Created a **CloudWatch Logs Metric Filter** to track failed logins.
- Built a **custom metric** (`FailedLoginCount`).
- Added a **CloudWatch Alarm** that triggers when 3+ failures occur in 5 minutes.
- Connected the alarm to an **SNS Topic** to send email alerts.
- Created a **monitoring dashboard** showing failed login events in real time.

## 🛠 AWS Services Used
- **CloudTrail**
- **CloudWatch Logs**
- **CloudWatch Metric Filters**
- **CloudWatch Alarms**
- **SNS (Email Notifications)**
- **IAM (Users & Permissions)**

---

# 📸 Screenshots

### 1. CloudWatch Alarm Trigger  
![Alarm](

### 2. Email Notification  
![Alarm Email]

### 3. Metric Filter (Failed Console Login Attempts)  
![Metric Filter]

### 4. CloudTrail Event Logs  
![CloudTrail Events]

### 5. IAM User Setup  
![Users]

### 6. JSON Event View  
![JSON View]

### 7. Log Streams  
![Log Streams]

### 8. SNS Topics  
![SNS Topics]

---

# 📈 How It Works

### **1. CloudTrail captures all login events**
Every time someone logs into the AWS console, CloudTrail logs an event:
- `ConsoleLogin = Success`
- `ConsoleLogin = Failure`

### **2. CloudWatch Metric Filter watches the logs**  
The filter pattern used:

{ $.eventName = "ConsoleLogin" && $.responseElements.ConsoleLogin = "Failure" }

yaml
Copy code

Every failed login = metric increment.

### **3. Alarm fires when threshold exceeded**
Example threshold:
- **FailedLoginCount > 3 within 5 minutes**

### **4. SNS sends immediate alert**
Email includes:
- username  
- IP address  
- region  
- timestamp  
- failure reason  

---

# 📚 What I Learned
- How CloudTrail logs security events
- Building CloudWatch Metric Filters
- Creating real-time monitoring alerts
- SNS alerting architecture
- IAM best security practices

---

# 💼 Why This Project Matters
This project shows:
- Cloud security understanding  
- AWS monitoring skills  
- Logging & alerting knowledge  
- Real-world security operations workflows  
