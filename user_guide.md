# Glitter Ads: User Guide for Google Ads Trend Reporting

Welcome to the Glitter Ads User Guide! This document will walk you through how to use the Google Ads Trend Reporting tool to gain valuable insights into keyword search volumes over time. Our goal is to make this process as straightforward as possible so you can focus on the data, not the technical details.

## What is Glitter Ads?

Glitter Ads helps you understand what people are searching for on Google, specifically related to your business or industry. It pulls historical data from Google Ads, organizes it into easy-to-read reports in a Google Sheet, and keeps a log of every time you run it in a Google Doc. This means you can quickly see trends, identify new opportunities, and make smarter decisions for your online advertising efforts.

## What You'll Need

To use this tool, you simply need:

1.  **A Google Account:** To access Google Colab, Google Sheets, and Google Docs.
2.  **Access to the Google Colab Notebook:** You will be provided with a link to the main notebook (e.g., `Google_Ads_Trend_Reporting.ipynb`).
3.  **Access to the Google Sheet:** This is where your reports will be generated. You will be provided with a link to this spreadsheet.
4.  **Access to the Google Doc (Activity Log):** This document keeps a record of when the tool was run and any important messages. You will be provided with a link to this document.

**Note:** All the complex setup, including connecting to the Google Ads API and defining keyword groups, has already been handled for you by your administrator. You just need to run the tool and view the results!

## Getting Started: How to Run Your Reports

Follow these simple steps to generate your Google Ads trend reports:

### Step 1: Open the Google Colab Notebook

Click on the link provided to you, which will open the `Google_Ads_Trend_Reporting.ipynb` (or `Google_Ads_Trend_Reporting_Multifamily.ipynb` for multifamily-specific reports) in Google Colab. It will look like a document with code and text sections.

### Step 2: Authenticate with Google

When you open the notebook, or when you first run it, Google Colab will ask you to authenticate. This is a crucial step that allows the notebook to access your Google Sheet and Google Doc.

1.  Click the **"Connect to Google Drive"** button or follow any prompts to **"Authenticate"** or **"Sign in with Google."**
2.  Choose your Google account.
3.  You will be asked to grant permissions for Google Sheets, Google Drive, and Google Docs. **Click "Allow"** for all requested permissions. This is necessary for the script to create sheets, write data, and log activity.

    *If you skip this or deny permissions, the script will not be able to run correctly.*

### Step 3: Run the Entire Notebook

Once authenticated, you are ready to run the report generation process.

1.  In the Google Colab menu at the top, go to **`Runtime`**.
2.  Select **`Run all`** from the dropdown menu.

    *Alternatively, you might see a play-like button (▶️) next to the first code cell. Clicking this and then confirming to run subsequent cells will also work, but `Runtime > Run all` is the safest option.* 

3.  **Wait for the execution to complete.** You will see messages and progress updates directly in the notebook as it fetches data for different locations. This process can take some time, especially if many locations are being processed. 

    *Do not close the browser tab until you see the "All operations complete" message.*

### Step 4: View Your Reports and Activity Log

Once the notebook finishes running, your reports will be ready!

1.  **Access the Google Sheet:** Click on the link provided to your Google Sheet. You will find new or updated sheets with your keyword trend data.
2.  **Access the Google Doc (Activity Log):** Click on the link provided to your Google Doc to review the detailed log of the run.

## Understanding Your Reports

Your Google Sheet will contain several important worksheets:

*   **Table of Contents:** This is usually the first sheet. It provides clickable links to all other reports in the spreadsheet, making navigation easy.
*   **Individual Location Sheets:** You will see sheets named after countries, states, and cities (e.g., "United States", "California", "New York, NY", "Canada", "Ontario"). Each of these sheets displays the monthly search volume for your predefined keyword groups within that specific geographical area.
*   **StateSummary (for Google_Ads_Trend_Reporting.ipynb):** This sheet provides a powerful overview of search volume trends across all US states. It includes calculations for 1-month, 3-month, 6-month, 12-month, and 24-month changes (both absolute and percentage) to help you quickly spot growth or decline in demand.

Your **Google Doc** will serve as an activity log, recording the date and time of each run, along with messages indicating which locations were processed successfully and which encountered issues.

## Troubleshooting Common Issues

*   **"Script didn't run" / "Errors appeared in the notebook":**
    *   Ensure you successfully authenticated with your Google account and granted all necessary permissions.
    *   Check the Google Doc activity log for specific error messages.
    *   **If the issue persists, please contact your administrator or the project maintainers for assistance.**
*   **"My Google Sheet looks empty or incomplete":**
    *   Ensure the notebook finished running completely (look for "All operations complete" in the Colab output).
    *   Sometimes, network issues can cause incomplete updates. Try running the notebook again.
    *   **If problems continue, reach out to your administrator.**
*   **"Some locations show an error in the activity log":**
    *   The Google Ads API occasionally has trouble recognizing certain location names. This is usually flagged in the activity log. The script will skip these problematic locations but continue with others. Your administrator can review and correct these if needed.

## Support

If you encounter any issues not covered here, or have questions about customizing your reports, please contact your project administrator or the Glitter Ads support team.
