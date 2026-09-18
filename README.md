# Tax Notice Assistant

An AI-powered document processing assistant designed to interpret IRS and state tax notices, extract key financial and legal information, and automatically generate structured Excel summaries and professional response letters.

### Live Demo

[![Try in ChatGPT](https://img.shields.io/badge/Try%20in-ChatGPT-000000?logo=openai)](https://chatgpt.com/g/g-681d917a12c481919b01e79e4f293857-tax-notice-assistant)

## Project Overview

Tax notices often contain important information such as payment deadlines, penalties, tax periods, account identifiers, and balances across multiple pages of legal and financial language.

I developed a custom GPT workflow that first validates whether an uploaded document is actually a tax notice. If valid, the assistant extracts more than 20 standardized fields, summarizes the notice in a structured format, generates a formatted Excel workbook, and creates a professional Word response letter.

The goal of the project was to reduce the amount of manual review needed when processing tax notices while keeping outputs consistent across different jurisdictions and notice formats.

## Core Workflow

```text
Tax Notice Upload
        ↓
Document Validation
        ↓
Notice Identification
        ↓
Structured Data Extraction
        ↓
Missing-Value Standardization
        ↓
Excel Summary Generation
        ↓
Word Response Letter Generation
        ↓
User Review / Multi-Notice Merge Option
```

## Key Capabilities

- Validates whether an uploaded document is a tax notice before processing it
- Extracts important financial, legal, and account-level information
- Standardizes missing values using `TBD` or `Not Applicable`
- Generates a formatted Excel summary automatically
- Highlights the `Total Due` field for faster review
- Generates a professional response letter in Word format
- Supports IRS and state tax authority notices
- Handles multiple uploaded notices individually
- Offers to combine multiple Excel summaries into one workbook
- Avoids providing legal or financial advice beyond interpreting and responding to the notice

## Extracted Fields

The assistant was configured to extract the following fields:

- File Name
- Account Name (Legal Entity)
- Entity Type
- Entity ID
- Notice ID Number
- Jurisdiction
- State ID
- Notice Category
- Tax Period
- Issuance Date
- Tax Notice Context
- Response or Payment Due Date
- Tax Due
- Interest
- Penalty
- Other
- Payments Made
- Credit on Account (Pre-Notice)
- Credit on Account (Post-Notice)
- Total Due
- Fund Family
- Status
- Assigned Personnel
- GS Locator

## Document Validation

Before extracting financial information, the assistant determines whether the uploaded file is actually a tax notice.

This prevents unrelated tax documents from being incorrectly processed.

### Example Test Cases

| Document | Expected Behavior |
|---|---|
| Illinois Notice of Tax Due | Accept, extract fields, generate Excel and response letter |
| Georgia Statement of Taxpayer's Account(s) | Accept, extract fields, generate Excel and response letter |
| Arizona Accounts Receivable Demand Notice | Accept, extract fields, generate Excel and response letter |
| Form 1120 Schedule L | Reject as not being a tax notice |

The Schedule L example was intentionally used as a negative test case because it is part of a tax return rather than a notice requiring a response.

## Example Notice Types Tested

### Illinois Notice of Tax Due

The Illinois example included:

- Tax liability
- Late-payment penalty
- Interest
- Previous payments or credits
- Remaining balance
- Payment deadline

### Georgia Statement of Taxpayer's Account(s)

The Georgia example tested:

- Multiple tax periods
- Tax, penalty, and interest totals
- Account-level balance information
- State-specific notice formatting

### Arizona Accounts Receivable Demand Notice

The Arizona example tested:

- Delinquent account status
- Immediate action language
- Penalty-driven balances
- Collection notice formatting

## Output Formatting

### Excel Summary

The generated Excel workbook uses a standardized structure:

- Bold column headers
- Visible cell borders
- `Total Due` highlighted in light green
- Full jurisdiction name with state abbreviation
- Standardized missing-value handling

Example:

| Account Name | Jurisdiction | Notice Category | Tax Period | Tax Due | Penalty | Interest | Total Due |
|---|---|---|---|---:|---:|---:|---:|
| Sample Company LLC | Georgia (GA) | Account Balance Notice | 2023 | $950.00 | $170.00 | $208.86 | **$1,328.86** |

### Response Letter

For each valid notice, the assistant generates a professional response letter that:

- Uses formal business language
- Is under 400 words
- Is tailored to the notice context
- Uses clear and readable formatting
- Avoids unsupported legal or financial advice

## Tools and Technologies

- Custom GPT
- Generative AI / Large Language Models
- Prompt Engineering
- Document Processing
- Structured Data Extraction
- Microsoft Excel
- Microsoft Word
- Code Interpreter / Data Analysis

## Design Decisions

### 1. Validate Before Extracting

The workflow first determines whether the uploaded file is a tax notice. This reduces the chance of unrelated documents being incorrectly converted into structured notice records.

### 2. Standardized Schema

Every notice is mapped to the same set of fields even when different states use different layouts or terminology.

### 3. Consistent Missing Values

Fields that should exist but cannot be identified are marked as `TBD`, while fields that do not apply to the notice are marked as `Not Applicable`.

### 4. Automatic Deliverables

Rather than only displaying results in chat, the assistant automatically creates business-ready Excel and Word files.

## Limitations

- The assistant is intended for document interpretation and workflow support, not legal or financial advice.
- Extraction accuracy can depend on document quality and layout.
- Some tax notices may require additional context or supporting documents.
- Human review should be used before sending generated correspondence or taking financial action.
- Portfolio examples should use synthetic or sanitized information only.

## Privacy

The public portfolio version of this project does not include confidential taxpayer information, private account data, or proprietary company records.

Any examples included in this repository should use synthetic or sanitized documents.

## What I Learned

This project helped me practice:

- Designing AI workflows around unstructured documents
- Converting text-heavy documents into structured datasets
- Building validation rules before downstream processing
- Creating consistent outputs across multiple document formats
- Automating Excel and Word deliverables
- Designing AI workflows around sensitive financial information
- Writing prompts that enforce formatting and business rules

## Future Improvements

Potential improvements include:

- Adding automated confidence scores for extracted fields
- Adding field-level validation checks
- Expanding support for additional IRS and state notice formats
- Building a more formal evaluation set for extraction accuracy
- Adding a dashboard for tracking notices and deadlines
- Adding human approval steps before response letters are finalized

## Disclaimer

This project is for portfolio and demonstration purposes only. It is not intended to provide tax, legal, or financial advice.
