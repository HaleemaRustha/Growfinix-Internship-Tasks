Task 2: Phishing Simulation & Social Engineering Awareness
Overview

This project demonstrates a controlled phishing simulation using GoPhish as part of a cybersecurity internship program. The objective is to understand how social engineering attacks are structured, how phishing campaigns are executed, and how user interaction can be analyzed in a controlled lab environment.

A mock scenario titled “TourEnquiries Data Update” was used to simulate a realistic internal communication designed to evaluate user awareness and response behavior.

Objectives
Design and execute a simulated phishing campaign in a controlled environment
Understand the structure and workflow of phishing attacks
Analyze how social engineering techniques influence user behavior
Gain practical experience with phishing simulation tools such as GoPhish
Tech Stack
GoPhish (Phishing simulation framework)
Web-based landing page (GoPhish hosted page)
Email template system (GoPhish editor)
Local testing environment (127.0.0.1)
Methodology
1. Campaign Setup

A phishing campaign was created using GoPhish with the following configuration:

Campaign Name: OSINT Training Simulation
Target Group: Training Users (mock user)
Email Template: “TourEnquiries Data Update”
Landing Page: Simulated credential capture page
URL: Localhost environment (127.0.0.1)
2. Email Template Design

A phishing email was created to simulate urgency and authority.

Key characteristics:

Professional corporate tone
Urgent subject line referencing a data update
Embedded call-to-action link
Designed to encourage user interaction
3. Landing Page

A simulated login page was configured to demonstrate credential capture flow.

Mimics a corporate authentication portal
Used for simulation purposes only
No real data collection involved
4. Target Group
Group Name: Training Users
Contains: 1 test user
Purpose: Controlled simulation environment
Results

Due to the absence of a configured SMTP server in the local lab environment, email delivery was not executed successfully.

Campaign metrics:

Emails Sent: 0
Emails Opened: 0
Link Clicked: 0
Credentials Submitted: 0

This reflects a mail delivery limitation rather than an issue in campaign design or configuration.

Key Learnings
Understood the end-to-end workflow of phishing simulation using GoPhish
Identified required components of a phishing campaign:
SMTP configuration
Email templates
Landing pages
Target groups
Gained awareness of how social engineering exploits urgency and trust
Understood the importance of secure email delivery infrastructure in simulation environments