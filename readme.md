# Invoice Processor

This repository contains a script to process invoice files, identify whether they are invoices, and extract relevant details such as the invoice date, seller's company name, and the first item listed. The processed files are then moved to appropriate folders based on whether they are invoices or not.

## Purpose

The purpose of this repository is to automate the processing of invoice files. The script reads files from a specified folder, uses the Google Generative AI to analyze the content, and extracts relevant details if the file is identified as an invoice. The results are saved in a JSON file, and the files are moved to respective folders (`invoices` or `non-invoices`).

## Setup

### Prerequisites

- Node.js (version 18 or higher)
- npm (Node Package Manager)

### Installation

1. Clone the repository

1. Install the dependencies:
```sh
npm install
```
1. Create a .env file in the root directory and add your Google Generative AI API key:
```txt
GEMINI_API_KEY=your_api_key_here
```
### Folder Structure
Ensure your workspace has the following structure:
```markdown
.DS_Store
.env
.gitignore
invoice-processor.ts
package.json
test_files/
    .DS_Store
    backup/
        .DS_Store
    error/
    invoices/
    non-invoices/
    results.json
tsconfig.json
```

### Configuration
The tsconfig.json file is already configured with the necessary compiler options:
```json
{
    "compilerOptions": {
      "types": ["node"],
      "esModuleInterop": true
    }
}
```
### Usage
1. Place the files you want to process in the test_files folder.
2. Run the script:
```sh
npm start
```
This will execute the invoice-processor.ts script and process the files in the test_files folder.

3. The results will be saved in results.json, and the processed files will be moved to either the invoices or non-invoices folder based on whether they are identified as invoices.

### Example
Here is an example of the results.json file generated after processing:
```JSON
[
  {
    "fileName": "Scan2024-12-20_114554.pdf",
    "isInvoice": false,
    "invoiceDate": "2024-08-30",
    "sellerName": "IRS",
    "firstItem": null
  },
  {
    "fileName": "Scan2024-12-20_114829.pdf",
    "isInvoice": true,
    "invoiceDate": "2024-04-09",
    "sellerName": "CVS",
    "firstItem": "VITAMIN B12"
  }
]
```

### License
This project is licensed under the MIT License.