# officemonster-product-scraper

A Jupyter notebook that extracts product details from a product page on officemonster.co.uk, plus a list of product URLs collected for it.

## Status

Prototype. The notebook scrapes one product page, set in the `url` variable. It loads `urls.csv` but does not yet loop over it. The CSS selectors match the 2023 site layout and may no longer work. The notebook that built the URL list is not in this repository.

## Features

- Downloads a product page with `requests` and parses it with BeautifulSoup.
- Reads the configurator options (the JSON inside `input.product_options`).
- Extracts title, image list, price, short description, brand and manufacturer.
- Collects the results in a Python dictionary.

## Tech stack

Python 3, Jupyter, requests, BeautifulSoup4, pandas.

## Structure

```
Product Scraper.ipynb          scraper for one product page
urls.csv                       about 5,200 product URLs (column: url)
URL Processing/
  combined_urls.csv            merged URL lists
  desking.csv                  URLs for the desking category
LICENSE
```

## Setup

```bash
pip install requests beautifulsoup4 pandas notebook
jupyter notebook "Product Scraper.ipynb"
```

No environment variables are needed.

## Usage

1. Open the notebook and set `url` to a product page.
2. Run all cells. The last cell shows the extracted dictionary, for example `title`, `price`, `images`, `brand` and the option labels with their values.
3. To scrape everything, loop over `urls` and call `get_soup` for each one (not implemented).

## Limitations

- One page per run, no saving of results to disk.
- No retry, delay or proxy handling. Be polite to the site and check its terms before scraping at scale.
- Selectors are fragile and tied to the old page layout.

## License

MIT
