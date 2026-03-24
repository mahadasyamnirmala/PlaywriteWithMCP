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

🐞 5. Automating Jira Bugs with MCP
The most powerful piece of this pipeline: If a test fails in Playwright, our Jira Model Context Protocol (MCP) integration takes over. It automatically analyzes the failed test case and logs a highly detailed Bug Ticket into Jira, detailing the exact console logs and steps to reproduce. Zero manual bug logging required!

Check out 

demo folder and 
Loginflow.md
 in the repo for a deeper dive into the automation setup!
