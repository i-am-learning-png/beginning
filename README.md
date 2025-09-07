# beginning
!pip install vaderSentiment textblob 
!pip install yfinance pandas

# Step 1: Import libraries
import yfinance as yf
import pandas as pd
import tweepy
from vaderSentiment.vaderSentiment import SentimentIntensityAnalyzer

#I want to track the changes in stock price ever since an event broke out
symbols = ["TGT", "UNH", "PARA"]
company_names = {"TGT": "Target", "UNH": "UnitedHealth", "PARA": "Paramount"}
events = {
    "TGT": {"2025-02-01": "CEO change"},
    "PARA": {"2025-08-11": "UFC rights deal"},
    "UNH": {"2025-07-24": "Department of Justice investigation"}
}

all_data = []

for symbol in symbols:
  #collecting financial statements
  stock = yf.Ticker(symbol)
  balance_sheet = stock.balance_sheet
  cash_flow = stock.cashflow
  income_statement = stock.financials
  # statement_of_shareholder_equity = stock.statement_of_shareholder_equity
  # yfinance does not have a direct method for this

for event_date in events[symbol]:
    #finding out the price
    event_dt = pd.to_datetime(event_date)
    window = 7  # days before and after
    start = (event_dt - pd.Timedelta(days=window)).strftime('%Y-%m-%d')
    end = (event_dt + pd.Timedelta(days=window)).strftime('%Y-%m-%d')
    hist = stock.history(start=start, end=end)
    

 git init 
  
