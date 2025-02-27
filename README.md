```markdown
# u-guessed-it

## Project Description

"u-guessed-it" is a simple web application designed to collect user input through a form and then seamlessly submit that data to an Airtable base. This allows for easy data collection and management without requiring complex backend infrastructure.

## Problem Solved

This project addresses the need to efficiently capture user-submitted data and store it in a structured format within Airtable.  Instead of manually entering data or relying on complex integrations, "u-guessed-it" provides a straightforward solution for sending form data directly to your Airtable base.

## Setup Instructions

Follow these steps to set up and run the "u-guessed-it" project:

1.  **Clone the Repository:**

    ```bash
    git clone <your-repository-url>
    cd u-guessed-it
    ```

2.  **Install Dependencies:**

    This project uses npm (Node Package Manager) to manage dependencies.  Run the following command to install the necessary packages:

    ```bash
    npm install
    ```

    *Note: While the provided files don't explicitly show dependencies, it's good practice to include this step in case future development requires them.*

3.  **Configure Airtable Integration:**

    To send data to Airtable, you'll need to obtain your Airtable API key and Base ID.

    *   **Get your Airtable API Key:**  Log in to your Airtable account and find your API key in your account settings.
    *   **Get your Base ID:**  Navigate to the Airtable base you want to use and find the Base ID in the API documentation for that base (usually found by clicking "API documentation" in the Help menu).
    *   **Update `script.js`:**  Open the `script.js` file and locate the section responsible for sending data to Airtable.  You'll need to replace the placeholder values with your actual API key and Base ID.  The code will likely look something like this (adjust based on your actual implementation):

        ```javascript
        const apiKey = 'YOUR_AIRTABLE_API_KEY'; // Replace with your actual API key
        const baseId = 'YOUR_AIRTABLE_BASE_ID'; // Replace with your actual Base ID
        const tableName = 'YourTableName'; // Replace with your table name

        // Example using fetch API (adjust as needed)
        fetch(`https://api.airtable.com/v0/${baseId}/${tableName}`, {
            method: 'POST',
            headers: {
                'Authorization': `Bearer ${apiKey}`,
                'Content-Type': 'application/json',
            },
            body: JSON.stringify({
                fields: {
                    // Map your form fields to Airtable columns here
                    'FieldName1': document.getElementById('formField1').value,
                    'FieldName2': document.getElementById('formField2').value,
                    // ... more fields
                }
            })
        })
        .then(response => response.json())
        .then(data => {
            console.log('Success:', data);
            // Handle success (e.g., display a confirmation message)
        })
        .catch(error => {
            console.error('Error:', error);
            // Handle error (e.g., display an error message)
        });
        ```

4.  **Open `index.html` in your browser:**

    Simply double-click the `index.html` file to open it in your web browser.

## Usage Examples

1.  **Filling out the form:**  Enter the required information into the form fields on the `index.html` page.

2.  **Submitting the form:**  Click the submit button.  The `script.js` file will then handle sending the form data to your configured Airtable base.

3.  **Verifying data in Airtable:**  Check your Airtable base to confirm that the data has been successfully submitted.

## Notable Features and Components

*   **`index.html`:**  The main HTML file that defines the structure and content of the web page, including the form.
*   **`style.css`:**  The CSS file that styles the appearance of the web page, making it visually appealing.
*   **`script.js`:**  The JavaScript file that handles the form submission logic and sends the data to Airtable.  This is where the Airtable API integration is implemented.
*   **Form Data Submission to Airtable:** The core functionality of the application, allowing users to easily send form data to an Airtable base.

## Troubleshooting

If you encounter issues with sending data to Airtable, consider the following:

*   **Incorrect API Key or Base ID:** Double-check that you have entered the correct API key and Base ID in the `script.js` file.  Even a small typo can prevent the data from being sent.
*   **CORS Issues:**  If you are encountering Cross-Origin Resource Sharing (CORS) errors, ensure that your Airtable base is configured to allow requests from your domain.  While Airtable generally handles CORS well, it's worth checking.
*   **Network Connectivity:**  Verify that you have a stable internet connection.
*   **Airtable Rate Limits:**  Airtable has rate limits on its API.  If you are submitting data too frequently, you may encounter errors.  Consider implementing a delay between submissions if necessary.
*   **Incorrect Field Mapping:** Ensure that the field names in your `script.js` file (within the `fields` object) exactly match the column names in your Airtable base.  Case sensitivity matters.
*   **Browser Console:**  Open your browser's developer console (usually by pressing F12) to check for any error messages or warnings.  These messages can provide valuable clues about what is going wrong.
*   **Check the Airtable API documentation:** Review the Airtable API documentation for any updates or changes that may affect your integration.

If you're still having trouble, provide the following information when seeking help:

*   The exact error message you are seeing (if any).
*   The relevant code snippet from your `script.js` file.
*   A description of the steps you have taken to troubleshoot the issue.
