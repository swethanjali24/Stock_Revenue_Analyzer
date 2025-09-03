# 📊 Stock-Revenue Analyzer

This project shows how a company’s **stock price** and its **revenue** change over time.  

We use two tools:  
- **yfinance** → to get stock prices  
- **BeautifulSoup** → to scrape revenue data from the web  

---

## 🔧 Installation

Make sure you have Python 3 installed. Then install the required libraries:

pip install yfinance beautifulsoup4 requests plotly

---

## ▶️ Usage

### 1. Get Stock Data
import yfinance as yf

amd = yf.Ticker("AMD")
stock_data = amd.history(period="max")

### 2. Get Revenue Data
import requests
from bs4 import BeautifulSoup

url = "https://example.com/revenue"
html = requests.get(url).text
soup = BeautifulSoup(html, "html.parser")

# Example scraping
table = soup.find("table")

### 3. Plot Stock vs Revenue
import plotly.graph_objects as go
from plotly.subplots import make_subplots

def graph(stock_data, revenue_data, stock_name):
    fig = make_subplots(rows=2, cols=1, shared_xaxes=True,
                        subplot_titles=(f"{stock_name} Stock Price", f"{stock_name} Revenue"))
    
    fig.add_trace(go.Scatter(x=stock_data.index, y=stock_data['Close'], name="Stock Price"), row=1, col=1)
    fig.add_trace(go.Bar(x=revenue_data['Date'], y=revenue_data['Revenue'], name="Revenue"), row=2, col=1)
    
    fig.update_layout(title=f"{stock_name} Stock vs Revenue", xaxis_title="Date", yaxis_title="Value")
    fig.show()

# Example usage:
# graph(stock_data, revenue_data, "AMD")

---

## 📌 Output

- 📈 Stock price history graph  
- 💰 Revenue trend graph  
- 🔗 Combined view of stock vs revenue  

---

## 📂 Project Structure
stock-revenue-analyzer/  
│-- analyzer.py        # Main script with graph()  
│-- README.md          # Project info  
│-- requirements.txt   # List of dependencies  

---

## 🎯 Why This Project?

- Learn **web scraping** with BeautifulSoup  
- Practice **stock data analysis** with yfinance  
- Create **visualizations** with Plotly  

---


