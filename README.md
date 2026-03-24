# PlaywriteWithMCP
🚀 Building a Fully Automated Testing Pipeline: From Test Plan to Jira Bugs

Welcome! In this repository, we've implemented a complete End-to-End Automated Testing workflow using Playwright and Jira MCP.

We wanted to make sure our login flows are completely bulletproof, from the planning stage all the way to handling bugs. Here is a step-by-step breakdown of how the pipeline works:

📝 1. Create a Test Plan
We start by defining a clear Test Plan. This document acts as our roadmap, outlining our testing strategy, the resources required, and our primary focus areas for the login functionality.

🧪 2. Define the Test Cases
We break down the plan into positive and negative test cases. This includes testing valid accounts as well as aggressive testing scenarios like SQL injection payloads and invalid character sets. (Check out the demo folder for screenshots of our test cases and login UI!)

🤖 3. Test Execution
Playwright automatically runs through our test cases. It navigates to the login screen, inputs the data, interacts with the DOM, and validates whether the application responded safely and correctly.

📊 4. Custom HTML Reporting
After execution, a custom HTML report is generated instantly. It provides a clean, interactive summary showing exact test results, traces, and screenshots of the execution run.
<img width="1819" height="791" alt="image" src="https://github.com/user-attachments/assets/6ada2dd0-b80a-41c2-9ec5-64c4446c3cbf" />

🐞 5. Automating Jira Bugs with MCP
The most powerful piece of this pipeline: If a test fails in Playwright, our Jira Model Context Protocol (MCP) integration takes over. It automatically analyzes the failed test case and logs a highly detailed Bug Ticket into Jira, detailing the exact console logs and steps to reproduce. Zero manual bug logging required!
<img width="1731" height="811" alt="image" src="https://github.com/user-attachments/assets/1af6457d-5992-44e0-960b-332e83e1c817" />

Check out 

demo folder and 
Loginflow.md
 in the repo for a deeper dive into the automation setup!

 🚀 AI-Powered Test Automation Framework (Playwright + MCP)
📌 Overview
This project demonstrates an end-to-end test automation pipeline that integrates Playwright with AI (Model Context Protocol) to automate not only test execution but also bug reporting in JIRA.
The goal is to eliminate manual effort in QA and build a scalable, intelligent testing system.

⚙️ Tech Stack
	• Playwright (UI Automation)
	• JavaScript
	• JIRA API Integration
	• Model Context Protocol (MCP - AI)
	• HTML Reporting

🔄 Workflow Architecture
	1. Test Planning
		○ Define scope and test scenarios
		○ Identify edge cases
	2. Test Case Design
		○ Happy paths & negative scenarios
		○ ECP (Equivalence Class Partitioning)
		○ BVA (Boundary Value Analysis)
	3. Automation Framework
		○ Page Object Model (POM)
		○ Reusable utilities
		○ Data-driven testing
	4. Test Execution
		○ Cross-browser execution
		○ Assertions and validations
	5. Reporting
		○ Interactive HTML reports
		○ Logs, traces, screenshots
	6. AI-Based Bug Creation
		○ Automatic JIRA ticket creation on failure
		○ Includes:
			§ Steps to reproduce
			§ Screenshots
			§ Logs

🔥 Key Features
	• End-to-end automation (Planning → Execution → Reporting → Bug Creation)
	• Zero manual bug reporting
	• Scalable framework design (POM + reusable components)
	• Handles real-world edge cases (invalid inputs, SQL injection, multilingual data)

📊 Impact
	• ⏱️ Reduced manual bug reporting effort by ~80%
	• ⚡ Faster regression cycles
	• 🎯 Improved defect quality with detailed logs

📸 Screenshots
(Add your Playwright report + test case screenshots here)

▶️ How to Run
npm install
npx playwright test
npx playwright show-report

📌 Future Enhancements
	• CI/CD integration (GitHub Actions / Jenkins)
	• API testing integration
	• Dashboard reporting (Allure / custom UI)

🤝 Connect With Me
	• LinkedIn: (your link)
	• GitHub: https://github.com/mahadasyamnirmala/PlaywriteWithMCP: 🚀 Building a Fully Automated Testing Pipeline: From Test Plan to Jira Bugs

⭐ If you found this useful, consider giving it a star!
<img width="892" height="2149" alt="image" src="https://github.com/user-attachments/assets/d06f4f81-8faf-46fb-8356-712b44412866" />

