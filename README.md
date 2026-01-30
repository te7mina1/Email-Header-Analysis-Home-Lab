# Email Header Analysis | Home Lab

## 🔍 Project Overview
This lab provides a hands-on walkthrough for analyzing email headers—a fundamental skill for Security Operations Center (SOC) analysts, incident responders, and email security professionals. The exercise focuses on extracting, interpreting, and correlating header fields to identify malicious indicators, trace email routes, and detect forgery attempts.

## 🎯 Why This Matters
Email remains a primary attack vector (phishing, Business Email Compromise, malware delivery). Understanding headers allows analysts to:

- Trace an email's origin and path
- Authenticate sender legitimacy (SPF, DKIM, DMARC)
- Identify spoofing and forwarding patterns
- Extract forensic artifacts for threat intelligence

## 🛠️ Tools Used
- Email Client/Service (Gmail, Outlook, Thunderbird, etc.)
- Header analysis tools (e.g., MXToolbox, MessageHeader Analyzer)
- Virtual Lab Environment (as per my secured setup)

## 🚀 Walkthrough Steps
Important steps I went about analysing the email headers.

### 1. Header Extraction
- Access raw headers from your email client
- Save as .eml file for offline analysis

### 2. Key Fields to Analyze

- **From / Reply-To**: Sender address	(Mismatch, deceptive domain)
- **Return-Path**:	Bounce destination	(Different from From)
- **Received**:	Mail server path	(Suspicious hops, foreign relays)
- **Message-ID**:	Unique identifier	(Missing or malformed)
- **Authentication-Results**:	SPF/DKIM/DMARC	(fail or softfail)
- **X-Headers**:	Custom tracking	(Anomalous client info)

### 3. Authentication Checks
- SPF: Verify sending IP is authorized
- DKIM: Validate digital signature
- DMARC: Check domain alignment


**|NOTE: Authentication checks are very important in email analysis. They form the fundamental trust and verification layer that determines whether an email is genuinely from who it claims to be.**

### 4. Trace Analysis
Map the Received chain from bottom (recipient) to top (origin), noting:
- IP addresses and geolocation
- Time stamps and delays
- Unusual server names

## ⚠️ Disclaimer
This lab is conducted in a controlled, virtual environment for educational purposes only. The techniques described are intended to build defensive skills for cybersecurity training.

## 🤝 Contributions
Feedback, issues, and suggestions are welcome to improve this lab.
