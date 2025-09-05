# Glitter Ads: Google Ads Trend Reporting

## Overview

The `glitter-ads` project provides a powerful and automated solution for analyzing Google Ads keyword search volume trends across various geographical locations. Utilizing Google Colab notebooks, it connects to the Google Ads API to fetch historical data, processes and aggregates this information, and then seamlessly integrates it into a Google Sheet for easy visualization and analysis. Additionally, it logs all operations to a Google Doc for comprehensive record-keeping.

This tool is invaluable for SEO specialists, marketing agencies like KC Local SEO, and businesses looking to understand search demand fluctuations, identify emerging trends, and make data-driven decisions for their Google Ads campaigns.

## Features

*   **Automated Google Ads API Integration:** Fetches historical monthly search volume data for specified keywords.
*   **Extensive Geo-Targeting:** Supports analysis for:
    *   United States (overall)
    *   All individual US States
    *   Major US Cities
    *   Canada (overall)
    *   All individual Canadian Provinces
    *   Major Canadian Locations
*   **Configurable Keyword Grouping:** Define custom keyword categories (e.g., "General Storage", "Near Me", "Features", "Vehicle Storage") to analyze aggregated trends.
*   **Dynamic Google Sheet Reporting:**
    *   Automatically creates or updates a Google Sheet with a dedicated worksheet for each processed location.
    *   Clears and repopulates data efficiently.
    *   Dynamically adjusts column widths for readability.
    *   Includes a "StateSummary" sheet with 1-month, 3-month, 6-month, 12-month, and 24-month change and percentage change analysis for US states.
    *   Generates a "Table of Contents" sheet with clickable hyperlinks to all individual location and summary sheets for effortless navigation.
*   **Google Docs Activity Logging:** Maintains a detailed log of each script execution, including timestamps, processing status for each location (success/failure), and any encountered errors, stored in a designated Google Doc.
*   **Easy Deployment:** Designed to run within Google Colab for a smooth, cloud-based execution environment.

## Getting Started

To use the Glitter Ads notebooks, you'll need a Google account, access to Google Cloud Platform, and a Google Ads account with API access.

### Prerequisites

*   A Google Account.
*   Access to Google Colab.
*   A Google Cloud Project with the Google Sheets, Google Drive, and Google Docs APIs enabled.
*   A Google Ads Account with a Developer Token and API access.

### Setup Instructions

#### 1. Open the Notebook in Google Colab

Navigate to the `glitter-ads` repository on GitHub and open `Google_Ads_Trend_Reporting.ipynb` (or `Google_Ads_Trend_Reporting_Multifamily.ipynb`) directly in Google Colab.

#### 2. Install Required Libraries

The first cell in the notebook handles the installation of all necessary Python libraries. Run this cell:

```python
!pip install google-ads google-auth-oauthlib gspread python-dateutil google-api-python-client gspread-formatting
```

#### 3. Google API Authentication

The notebook uses `google.colab.auth` for authentication. Run the authentication cell. You will be prompted to sign in with your Google account and grant the necessary permissions (`spreadsheets`, `drive`, `documents`).

#### 4. Configure Google Ads API Credentials in Colab Secrets

The Google Ads API requires specific credentials. It is highly recommended to store these as **Colab Secrets** for security.

1.  In Google Colab, click on the "Secrets" (key) icon on the left sidebar.
2.  Add the following secrets with their corresponding values from your Google Ads API setup:
    *   `ADS_DEVELOPER_TOKEN`
    *   `ADS_CLIENT_ID`
    *   `ADS_CLIENT_SECRET`
    *   `ADS_REFRESH_TOKEN`
    *   `ADS_LOGIN_CUSTOMER_ID` (your Google Ads account ID, without hyphens)

    Ensure "Notebook access" is toggled ON for these secrets.

#### 5. Configure Google Docs Logging ID

The script logs its execution to a Google Doc. You need to provide the ID of the Google Doc you want to use for logging.

1.  Create a new Google Doc (or use an existing one).
2.  Copy its ID from the URL. For example, if the URL is `https://docs.google.com/document/d/1ZMv52EXlCDNX0sWBDcQRNdvuOxRcdOogMy0jHGvVgTE/edit`, the ID is `1ZMv52EXlCDNX0jHGvVgTE`.
3.  Update the `DOCS_LOG_ID` variable in the notebook's "SECTION 2: IMPORTS & AUTHENTICATION" to this ID:

    ```python
    DOCS_LOG_ID = 'YOUR_GOOGLE_DOC_ID_HERE'
    ```

#### 6. Configure Google Sheet URL

The script will create/update worksheets in a designated Google Sheet.

1.  Create a new Google Sheet (or use an existing one). Ensure the first sheet is named `Sheet1` as it will be used as a template.
2.  Copy its URL.
3.  Update the `SPREADSHEET_URL` variable in the notebook's "SECTION 3: CONFIGURATION" to this URL:

    ```python
    SPREADSHEET_URL = 'YOUR_GOOGLE_SHEET_URL_HERE'
    ```

#### 7. Define Keyword Groups

In "SECTION 3: CONFIGURATION", customize the `KEYWORD_GROUPS` dictionary. This defines the categories and the keywords for which you want to fetch search volume data.

```python
KEYWORD_GROUPS = {
    'General Storage': ["self storage", "self storage unit", "storage units"],
    'Near Me': ["storage units near me", "self storage near me"],
    # Add more groups and keywords as needed
}
```

#### 8. Define Locations to Check

The `LOCATIONS_TO_CHECK` tuple in "SECTION 3: CONFIGURATION" specifies all the geographical areas for which data will be fetched. This can include individual US states, US cities, Canadian provinces, and Canadian locations. You can comment out or modify parts of this tuple if you only want to process a subset of locations.

## Usage

### `Google_Ads_Trend_Reporting.ipynb`

This is the main notebook for general Google Ads keyword trend reporting. After completing the setup:

1.  **Run all cells sequentially.** The notebook is structured into sections for installation, authentication, configuration, core logic, and main execution.
2.  The script will iterate through all defined `LOCATIONS_TO_CHECK`, fetch historical search volume data for each keyword group, and update the specified Google Sheet.
3.  A "StateSummary" sheet will be created/updated to provide an aggregated view of US state trends, including month-over-month and year-over-year changes.
4.  A "Table of Contents" sheet will be generated at the beginning of your Google Sheet, offering easy navigation to all generated location-specific reports.
5.  All execution logs, including progress and any errors, will be appended to your configured Google Doc.

### `Google_Ads_Trend_Reporting_Multifamily.ipynb`

This notebook is a specialized version of the main reporting script, specifically tailored for the multifamily housing industry. It contains pre-configured keyword groups and potentially different location lists relevant to multifamily marketing. The setup and usage steps are generally the same as the main notebook, but it focuses on providing insights for multifamily-specific search trends.

## Configuration Details

The following variables in "SECTION 3: CONFIGURATION" are crucial for customizing the script:

*   **`KEYWORD_GROUPS`**: A dictionary where keys are your desired keyword group names (e.g., "General Storage") and values are lists of keywords (strings) belonging to that group.
*   **`SPREADSHEET_URL`**: The full URL of the Google Sheet where all reports will be generated. Ensure this sheet has at least one blank sheet named `Sheet1` to serve as a template.
*   **`US_STATES`**: A list of all 50 US state names.
*   **`US_CITIES`**: A list of major US cities (format: "City, State Abbreviation").
*   **`CA_PROVINCES`**: A list of Canadian province names.
*   **`CA_LOCATIONS`**: A list of major Canadian cities/locations (format: "City, Province").
*   **`LOCATIONS_TO_CHECK`**: A tuple combining `["United States"]`, `US_STATES`, `US_CITIES`, `["Canada"]`, `CA_PROVINCES`, and `CA_LOCATIONS`. This tuple defines the complete list of locations for which the script will fetch data. You can comment out or modify parts of this tuple if you only want to process a subset of locations.

## Output

Upon successful execution, the script will:

*   **Update a Google Sheet:** The specified Google Sheet will contain:
    *   Individual worksheets for each `LOCATION_TO_CHECK` (e.g., "United States", "California", "Kansas City, MO", "Ontario"). Each sheet will display monthly search volumes for your defined keyword groups.
    *   A "StateSummary" worksheet (for `Google_Ads_Trend_Reporting.ipynb`) providing an aggregated view of US state trends with various change metrics.
    *   A "Table of Contents" worksheet, acting as an interactive index to all generated reports.
*   **Update a Google Doc:** The specified Google Doc will contain a running log of each execution, detailing which locations were processed and whether the data fetch and sheet update for that location were successful or failed.

## Troubleshooting

*   **Authentication Errors:** Double-check your Google Cloud Project settings to ensure the Google Sheets, Google Drive, and Google Docs APIs are enabled. Verify your Colab secrets for Google Ads API credentials.
*   **`gspread.exceptions.WorksheetNotFound`:** Ensure your target Google Sheet has a sheet named `Sheet1` to be used as a template, or adjust the code to use a different template sheet name if necessary.
*   **Google Ads API Rate Limits (Error 429):** The script includes a retry mechanism with exponential backoff. If you encounter persistent rate limit errors, you may need to increase the `time.sleep()` duration within the `get_historical_metrics` function or reduce the number of locations/keywords processed in a single run.
*   **`Could not find a location criterion`:** This indicates that the Google Ads API could not recognize the specified location name. Verify the spelling and format of location names in your `US_CITIES` or `CA_LOCATIONS` lists. For cities, ensure they are in "City, State Abbreviation" or "City, Province" format.
*   **`DeprecationWarning: The order of arguments in worksheet.update()`:** This is a warning from the `gspread` library and typically does not prevent the script from running. It advises using named arguments for `worksheet.update()` calls (e.g., `worksheet.update(values=data, range_name='A1')`) for future compatibility.

## Contributing

We welcome contributions to improve the Glitter Ads project! Please feel free to fork the repository, make your changes, and submit a pull request.

## License

This project is licensed under the MIT License.
