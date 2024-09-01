# AUTO-CERTIFICATE-GENERATOR and Email Automation Script

## Overview

This script automates the process of generating certificates and emailing them to recipients using data from a Google Spreadsheet. The certificates are created from a Google Slides template, customized for each recipient, and sent as PDF attachments via Gmail.

## Features

- **Google Slides Integration**: Uses a Google Slides template to generate customized certificates for each recipient.
- **Spreadsheet Integration**: Retrieves recipient information (e.g., names, email addresses) from a Google Spreadsheet.
- **Automated Email Sending**: Sends personalized emails with the certificate as a PDF attachment.
- **Draft Email Template**: Utilizes a Gmail draft email as the template for the message body and subject.

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
   - The draft email body should include `<<Name>>` as a placeholder for personalization.

## Setup

1. **Copy the Script**: Copy the provided script into the Google Apps Script editor linked to your Google Spreadsheet.
2. **Update Slide Template ID**: Replace the `slideTemplateId` in the script with the actual ID of your Google Slides template.
3. **Prepare Draft Email**: Ensure your Gmail draft email is set up and contains the necessary placeholders.
4. **Permissions**: The script will require permissions to access Google Sheets, Google Slides, Gmail, and Google Drive.

## How It Works

1. **Start Function**: The `createCertificates()` function is executed.
2. **Fetch Data**: The script retrieves all rows of data from the first sheet in the active spreadsheet.
3. **Slide Copy Creation**: For each row, it makes a copy of the Google Slides certificate template.
4. **Customize Slide**: The script replaces the placeholder `<<Name>>` in the slide with the recipient's name from the spreadsheet.
5. **Save as PDF**: The customized slide is saved as a PDF file.
6. **Send Email**: An email is sent to the recipient, attaching the generated PDF certificate. The subject and body of the email are personalized using the draft email.
7. **Cleanup**: The temporary slide copy is moved to the trash after the email is sent.
8. **Logging**: Throughout the process, key actions are logged for debugging and tracking.

## Important Notes

- **Spreadsheet Format**: Ensure the spreadsheet follows the expected format (e.g., names in the first column and email addresses in the fourth column).
- **Error Handling**: The script assumes that all rows contain valid data. Make sure the spreadsheet is clean and free of empty rows or invalid data.
- **Draft Email**: Only the first draft in your Gmail is used. Ensure that the draft email is correctly set up with `<<Name>>` as a placeholder.

## Customization

- **Additional Placeholders**: You can modify the script to handle additional placeholders in the Google Slides template or email body by adding more `replace()` functions.
- **Row Structure**: If your spreadsheet has a different structure, adjust the column indices (`row[0]` for name, `row[3]` for email) to match your data layout.

## Running the Script

1. Open the Google Apps Script editor from your Google Spreadsheet.
2. Click on the function dropdown menu and select `createCertificates`.
3. Click the run button (▶) to execute the script.

## License

This script is provided as-is, without any warranty or guarantee of functionality. Feel free to modify and adapt it to suit your specific needs.

