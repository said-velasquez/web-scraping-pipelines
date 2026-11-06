# Web Scraping Pipelines

Two scraping projects in Python: a Selenium bot that browses the Steam store and collects cheap games, and a Requests + BeautifulSoup scraper that collects Spanish newspaper headlines and scores their sentiment with a Hugging Face Transformers model.

![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)
![Selenium](https://img.shields.io/badge/Selenium-43B02A?logo=selenium&logoColor=white)
![BeautifulSoup](https://img.shields.io/badge/BeautifulSoup-4B8BBE)
![Hugging Face](https://img.shields.io/badge/Hugging%20Face-FFD21E?logo=huggingface&logoColor=black)

## 1. Steam store scraper

[`notebooks/01_steam_store_scraper.ipynb`](notebooks/01_steam_store_scraper.ipynb)

- Opens the Steam store with Selenium and runs a search.
- Moves the price slider to show only games under €5, using JavaScript events and `ActionChains`.
- Extracts the title, rating, price, original price, discount and link of each game with XPath into a pandas DataFrame.
- Groups the games into discount ranges and charts the distribution with Seaborn.

## 2. Spanish news headline sentiment

[`notebooks/02_spanish_news_headline_sentiment.ipynb`](notebooks/02_spanish_news_headline_sentiment.ipynb)

- Scrapes **181** front-page headlines from *El Mundo* and *El País* with Requests and BeautifulSoup (CSS selectors).
- Labels each headline as positive or negative with a Transformers `sentiment-analysis` pipeline.
- Compares both outlets: about two thirds of the headlines were negative in each newspaper (67% El Mundo, 65% El País).

> [!NOTE]
> The default pipeline model is trained on English text, so its labels on Spanish headlines are only indicative. A Spanish or multilingual model is the next step to get more reliable results.

> [!IMPORTANT]
> Websites change their HTML over time. If a scraper stops finding elements, the selectors need updating. Please scrape responsibly and respect each site's terms of use.

## Run it

```bash
git clone https://github.com/said-velasquez/web-scraping-pipelines.git
cd web-scraping-pipelines
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook
```

The Steam scraper needs Google Chrome installed. Selenium 4.6+ downloads a matching ChromeDriver automatically.

## Tech stack

Python, Selenium, Requests, BeautifulSoup, Hugging Face Transformers, pandas, Matplotlib, Seaborn, Jupyter.

## Author

**Said Velásquez**, Computer Engineering student at Universidad UNIE (Madrid).
[LinkedIn](https://www.linkedin.com/in/said-vel%C3%A1squez-650905333) · [GitHub](https://github.com/said-velasquez)
