# AUTO-CERTIFICATE-GENERATOR and Email Automation Script

## Overview

This script automates the process of generating certificates and emailing them to recipients using data from a Google Spreadsheet. The certificates are created from a Google Slides template, customized for each recipient, and sent as PDF attachments via Gmail. Additionally, the script now supports automatic execution when new data is entered in a specified column in the Google Sheet.

## Features

- **Google Slides Integration**: Uses a Google Slides template to generate customized certificates for each recipient.
- **Spreadsheet Integration**: Retrieves recipient information (e.g., names, email addresses) from a Google Spreadsheet.
- **Automated Email Sending**: Sends personalized emails with the certificate as a PDF attachment.
- **Draft Email Template**: Utilizes a Gmail draft email as the template for the message body and subject.
- **Automatic Trigger**: Automatically triggers the certificate creation and email process when new data is entered in a specific column of the Google Spreadsheet.

## Prerequisites

Before running this script, make sure the following prerequisites are met:

1. **Google Spreadsheet**:
   - The first sheet in the active spreadsheet should contain recipient data.
   - The first column should contain recipient names.
   - The fourth column should contain recipient email addresses.

2. **Google Slides Template**:
   - You need a Google Slides file that serves as a certificate template.
   - The placeholder text `<<Name>>` should be present in the template wherever you want the recipient's name to appear.

3. **Gmail Draft Email**:
   - Create a draft email in Gmail that will be used as the template for the emails sent.
   - The email draft should be at the top of the draft emails list.

## Setup

1. **Copy the Script**: Copy the provided script into the Google Apps Script editor linked to your Google Spreadsheet.
2. **Update Slide Template ID**: Replace the `slideTemplateId` in the script with the actual ID of your Google Slides template.
3. **Prepare Draft Email**: Ensure your Gmail draft email is set up and contains the necessary placeholders.
4. **Permissions**: The script will require permissions to access Google Sheets, Google Slides, Gmail, and Google Drive.

## How It Works

1. **Start Function**: The `createCertificates()` function is executed either manually or automatically on new data entry.
2. **Fetch Data**: The script retrieves all rows of data from the first sheet in the active spreadsheet or processes only the newly entered row.
3. **Slide Copy Creation**: For each row, it makes a copy of the Google Slides certificate template.
4. **Customize Slide**: The script replaces the placeholder `<<Name>>` in the slide with the recipient's name from the spreadsheet.
5. **Save as PDF**: The customized slide is saved as a PDF file.
6. **Send Email**: An email is sent to the recipient, attaching the generated PDF certificate. The subject and body of the email are personalized using the draft email.
7. **Cleanup**: The temporary slide copy is moved to the trash after the email is sent.
8. **Logging**: Throughout the process, key actions are logged for debugging and tracking.

## New Features

- **Automatic Execution on Data Entry**: The script now includes an `onEdit` trigger, which automatically processes new data entries in a specified column. This automation eliminates the need to manually run the script every time new data is added to the spreadsheet.

### How the Automation Works

1. **onEdit Trigger**: The script triggers automatically whenever new data is entered in a specific column of the Google Spreadsheet.
2. **Column Check**: The script processes the newly entered row only if the edit occurred in the specified column (e.g., the column for recipient names or email addresses).
3. **Efficient Processing**: The script skips over unedited rows, ensuring that only new entries are processed, reducing redundant operations.

## Setup for Automation

1. **Specify Target Column**: In the script, update the `targetColumn` variable to reflect the column where new data (e.g., recipient names or email addresses) is expected.
2. **Set Up Trigger**: In the Google Apps Script editor, set up an `onEdit` trigger for the `createCertificates()` function to automatically execute the script upon new data entry.

### Steps to Set Up the Trigger

1. **Open Script Editor**: Go to "Extensions" > "Apps Script" in Google Sheets.
2. **Add Trigger**: In the Apps Script editor, click the clock icon (Triggers), then click "Add Trigger".
3. **Configure Trigger**: Choose the `createCertificates` function, select "From spreadsheet" as the event source, and "On edit" as the event type.
4. **Save Trigger**: Save the trigger and the script will now automatically execute when new data is entered in the specified column.

## Important Notes

- **Spreadsheet Format**: Ensure the spreadsheet follows the expected format (e.g., names in the first column and email addresses in the fourth column).
- **Error Handling**: The script assumes that all rows contain valid data. Make sure the spreadsheet is clean and free of empty rows or invalid data.
- **Draft Email**: Only the first draft in your Gmail is used. Ensure that the draft email is correctly set up with `<<Name>>` as a placeholder.
- **Google Apps Script Quotas**: Be mindful of Google Apps Script quotas, such as the daily email sending limits.

## Customization

- **Additional Placeholders**: You can modify the script to handle additional placeholders in the Google Slides template or email body by adding more `replace()` functions.
- **Row Structure**: If your spreadsheet has a different structure, adjust the column indices (`row[0]` for name, `row[1]` for email) to match your data layout.

## Execution Process

### Manual Execution

1. **Open Google Sheets**: Go to Google Sheets and open the spreadsheet you want to work with.
2. **Access the Script Editor**: Click on "Extensions" > "Apps Script".
3. **Run the Script**: Select the `createCertificates` function from the dropdown in the script editor, then click the "Run" button.

### Automatic Execution

- Once the `onEdit` trigger is set up, the script will automatically run whenever new data is entered in the specified column.

### Authorize Your Script

- The first time you run the script or trigger, you may need to authorize it. Follow the on-screen prompts to grant the necessary permissions.

## License

This script is provided as-is, without any warranty or guarantee of functionality. Feel free to modify and adapt it to suit your specific needs.
