# Zillow Web Scraper and Google Form Automation

This project is a Python web scraper that extracts real estate data from Zillow for properties listed in San Francisco, CA, and automatically submits the data to a Google Form. The data extracted includes property addresses, prices, and links to the Zillow listings. The web scraping part uses the `BeautifulSoup` library, while the form submission uses Selenium.

## Features
- Scrapes Zillow for property listings in San Francisco, CA.
- Extracts:
  - Property addresses.
  - Prices.
  - Links to the listing.
- Automates Google Form submissions with the scraped data.

## Requirements

1. **Python 3.x**
2. **Google Chrome** (or any Chrome-based browser)
3. **WebDriver for Chrome** (Ensure `chromedriver` is installed and added to your PATH)
4. **Python Libraries**:
   - `beautifulsoup4`
   - `requests`
   - `selenium`

To install the necessary Python libraries, run the following command:

```bash
pip install beautifulsoup4 requests selenium
```

## Setup Instructions

1. Clone this repository to your local machine:
   ```bash
   git clone <repository-url>
   ```

2. Ensure you have Google Chrome and the `chromedriver` that matches your Chrome version installed. The correct version of `chromedriver` can be downloaded from [here](https://sites.google.com/a/chromium.org/chromedriver/downloads).

3. Add the path to `chromedriver` to your system PATH or place it in the project directory.

4. Update the `URL_TO_YOUR_GOOGLE_FORM` variable in the code with the URL of your actual Google Form.

5. Update the XPaths in the Selenium automation part if your form structure differs.

## How to Run

1. Run the script using Python:
   ```bash
   python zillow_scraper.py
   ```

2. The script will:
   - Fetch listings from Zillow.
   - Parse the address, price, and link for each listing.
   - Open your Google Form and auto-fill the details for each property.

3. Once the script is done, you should see the scraped data in your Google Form responses.

## Code Explanation

- **BeautifulSoup** is used for scraping the HTML content of the Zillow search page and extracting:
  - The property address from elements with class `.list-card-info address`.
  - The property price from elements with class `.list-card-heading`.
  - The Zillow link from elements with class `.list-card-top a`.

- **Selenium** is used to automate the task of filling out a Google Form with the data scraped from Zillow. For each listing, the script:
  - Opens the Google Form.
  - Inputs the address, price, and link into the corresponding fields.
  - Submits the form.

## Example Output

```bash
['$1,200,000', '$850,000', ...] 
['1234 Main St, San Francisco, CA', '5678 Oak St, San Francisco, CA', ...] 
['https://www.zillow.com/homedetails/1234-Main-St', 'https://www.zillow.com/homedetails/5678-Oak-St', ...]
```

## Troubleshooting

- **Form not submitting**: Ensure that the XPaths used in the Selenium section match your Google Form’s structure.
- **WebDriver not found**: Ensure that `chromedriver` is installed correctly and added to your PATH.
- **Blocked by Zillow**: Zillow may block repeated requests; consider adding delays between requests or rotating user agents.

## Disclaimer

This project is intended for educational purposes only. Ensure compliance with Zillow's terms of service and avoid excessive scraping that could lead to your IP being blocked.
