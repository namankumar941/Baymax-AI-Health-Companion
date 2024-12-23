# Baymax - AI Health Companion

This project is a **Medical Report Management System** designed to simplify and streamline the analysis of medical reports. Users can upload their report PDFs, which are then processed using the **pdf-parse** library in Node.js to extract relevant data. The extracted information is further structured and organized using the OpenAI API to fit a predefined format.

The system tracks and displays over 100+ vitals, grouped under specific categories such as Kidney Panel, Liver Function Tests, Urinalysis, Vitamin Panel, and 20+ other sections, allowing users to view a comparative analysis of all uploaded reports. This eliminates the need to manually review each report to track changes in a specific vital. For instance, under the Kidney Panel section, all relevant vitals from every uploaded report are presented in one place, providing an intuitive and efficient way to monitor changes over time.

This tool ensures users have quick and clear access to their medical trends, enabling better health management without the hassle of navigating through individual reports.
# Purpose of This Project
**Centralized Medical Data Management:** Consolidates data from multiple medical reports into one platform for easy access.

**Vital Tracking Over Time:** Tracks changes in over 100+ vitals, allowing users to monitor their health trends across different timeframes.

**Categorization of Health Metrics:** Organizes vitals into predefined categories such as Kidney Panel, Liver Function Tests, Vitamin Panel, and more for better clarity.

**Comparative Analysis:** Provides a side-by-side comparison of vitals from all uploaded reports, simplifying the process of identifying changes or patterns.

**Group Functionality:** Allows users to create groups where all members can share and view each other’s medical reports and trends, fostering collaborative health tracking.

**Automated Data Processing:** Automatically extracts and restructures data from PDFs, saving time and reducing manual effort.

**Health Monitoring Made Easy:** Offers an intuitive way to review health trends without manually reading through multiple reports.

**Improved Health Decision-Making:** Empowers users with actionable insights for better health management and proactive decision-making.
# Architecture
# 1) Google Login via OAuth 2.0 Authentication
This application implements user authentication through Google Login using OAuth 2.0. The authentication flow is handled by Passport.js with the passport-google-oauth20 strategy. To set up Google login, you'll need to create OAuth credentials in the Google Cloud Console, which will provide the clientID and clientSecret required for the integration.

The authentication flow consists of two main routes:

**/auth/google:**
This route triggers the Google login process by redirecting users to Google’s authentication page, where they can log in and grant necessary permissions.

**/auth/google/redirect:**
Once the user logs in, Google redirects them to this route, where Passport.js handles the OAuth callback. The user’s profile information is then retrieved, and if the user is not already registered, a new user is created in the database. If they are an existing user, their profile is retrieved, and the session is initialized.

# 2) API Assistant with OpenAI Integration
This project integrates the OpenAI API to extract, process, and restructure data from medical test report files, specifically PDFs. The workflow automates parsing, formatting, and enhancing data for downstream usage while maintaining a defined structure.

**OpenAI Interaction:**
The project leverages OpenAI's GPT model to perform the following tasks:

1 Extract and rearrange medical test data.

2 Transform the extracted content into a structured JSON format.

3 Restructure the JSON into a specific predefined format.

4 Incorporate an **originalName** key into the JSON object, mapping values based on a predefined biological terminology array.

