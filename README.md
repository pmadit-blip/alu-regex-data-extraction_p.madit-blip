# Regex Data Extraction and Secure Validation

## Project Overview

This program was used to extract, validate and process different data types from raw text using Python and regular expressions.

And the program also accepts the input file and checks the patterns for validity, performs validation checks, checks for security threats and then stores the results in the JSON format.

The project also illustrates how sensitive data such as credit card details can be kept safe through masking.

## Project Structure

alu-regex-data-extraction_p.madit-blip/
├── input/
│ └── raw-text.txt
├── src/
│ └── main.py
├── output/
│ └── sample-output.json
└── README.md

## Data Types Extracted

The program extracts the following data types:

- Email addresses
- ALU email addresses
- URLs
- Phone numbers
- Credit card numbers
- Time values

Email addresses and credit card numbers are the main required data types. URLs, phone numbers, and time values are also included.

## Email Validation

The program uses regular expressions to identify email addresses.

It also checks for the required ALU email domains:

- @alueducation.com
- @alumni.alueducation.com
- @si.alueducation.com

The program separates these ALU email addresses into different categories in the JSON output.

Invalid email formats and emails from unsupported domains are not included as valid ALU email addresses.

## URL Extraction

The software retrieves URLs with HTTPS protocols.

Several types of URLs with varying complexities are shown in input.

A defective URL like http//broken-url.com is rejected in this software.

## Phone Number Extraction

The program extracts phone numbers using regular expressions.

The input contains different phone number formats, including:

- International numbers beginning with +
- Numbers separated by spaces
- Numbers separated by hyphens
- Numbers using parentheses

Invalid values, such as numbers containing letters or numbers that are too short, are not accepted.

## Credit Card Validation and Security

The credit card numbers are considered private data.

The program can scan 16-digit numerical strings with possible inclusion of whitespace or punctuation.

It also filters out some invalid credit card numbers, such as incomplete credit card numbers, numbers composed entirely of zeros, or known invalid test card numbers.

The full credit card number will not be available in the outputs.

However, the number will be obscured and only the last four digits will be shown.

For example:

**** **** **** 0906

This helps ensure that sensitive financial data is not unnecessarily exposed.

## Time Extraction


The program is able to recognise both 12-hour and 24-hour format.

Some examples include:

   
- 08:20
- 8:30 PM
- 21:30

using regular expressions, it guarantees that the minutes will always be from 00 to 59.

In such a case, invalid time of 06:75 would not be accepted.

## Security Checks

The raw input is treated as untrusted data.

The program checks for patterns that may represent security threats, including:

- Script injection
- SQL injection
- Path traversal
- Unsafe JavaScript URL schemes

When these patterns are detected, the program records a security alert instead of placing the malicious content in the output.

## Realistic Input

The input file represents a customer-support style log.

It contains realistic examples of ALU email addresses, alumni addresses, SI addresses, URLs, phone numbers, credit card-like numbers, and different time formats.

It also contains invalid data and suspicious input so that the program can be tested against both valid and invalid cases.

## Edge Cases Tested

The program tests several invalid or unusual cases, including:

- Emails with an invalid format
- Emails from unsupported domains
- Incomplete credit card numbers
- All-zero credit card numbers
- Known test credit card numbers
- Invalid phone numbers
- Malformed URLs
- Invalid time values
- Script injection attempts
- SQL injection patterns
- Path traversal attempts
- Unsafe JavaScript URLs

These cases help test whether the program can distinguish valid data from malformed or potentially dangerous input.

## Output

The extracted results are saved in:

output/sample-output.json

The JSON output contains:

- Emails
- ALU official emails
- ALU alumni emails
- ALU SI emails
- URLs
- Phone numbers
- Masked credit cards
- Times
- Security alerts

Sensitive credit card numbers are masked before being saved.

## How to Run

From the project directory, run:

python3 src/main.py

The program reads the data from:

input/raw-text.txt

and generates the results in:

output/sample-output.json

The results are also displayed in the terminal.

## Testing

I tested the program by running:

python3 src/main.py

I then checked the generated output using:

cat output/sample-output.json

The generated JSON output was checked to make sure that the extracted data and security alerts were correctly saved.

## Security Awareness

This project demonstrates the importance of treating raw input as untrusted.

Regular expressions can help identify expected patterns, but validation is also important because input may be malformed or malicious.

Sensitive information is also protected. Therefore, in this project, credit card numbers are masked so that the complete numbers are not exposed in the output.

## AI Usage

AI was used to help understand concepts related to regular expressions, validation, security and to develop realistic sample input data.

The program was tested using the provided raw input and the results were checked against the expected requirements.
