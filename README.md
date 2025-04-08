Xeggex Single-Pair Trading Bot


This is a Python-based cryptocurrency trading bot for the Xeggex exchange. It uses WebSocket for real-time trade data and REST API for placing orders on a single trading pair. The bot buys when the price decreases by a threshold and sells when a profit margin is achieved, accounting for a 0.2% trading fee per trade.

Features
Trades a single pair (e.g., BTC/USDT).
Buys on a 0.5% price decrease and sells for a 1% profit after fees.
Logs trades to the console with fee and profit details.
Handles WebSocket disconnections (basic version without reconnection).


Prerequisites
Python 3.6+: Ensure Python is installed on your system.
Dependencies: Install required Python packages (see Installation).
Xeggex API Credentials: Obtain an API key and secret from your Xeggex account.


Installation

Windows
Install Python:
Download and install Python from python.org.
Ensure "Add Python to PATH" is checked during installation.

Install Dependencies:
Open Command Prompt (cmd):
pip install requests websocket-client
Download the Script:
Save the script as groktrade_single.py in a folder (e.g., C:\TradingBot).


Linux

Install Python:
Verify Python is installed:
bash
python3 --version
If not installed (e.g., on Ubuntu):
sudo apt update
sudo apt install python3 python3-pip
Install Dependencies:
Open a terminal:
pip3 install requests websocket-client
Download the Script:
Save the script as groktrade_single.py in a directory (e.g., ~/TradingBot).


Configuration
Edit the following parameters in groktrade_single.py before running:

Required Parameters
API_KEY (line ~20):
Your Xeggex API key.
Example: "your_api_key".
API_SECRET (line ~21):
Your Xeggex API secret.
Example: "your_api_secret".
Customizable Parameters
SYMBOL (line ~24):
The trading pair to monitor (e.g., "BTC/USDT").
Ensure the pair is supported by Xeggex.
AMOUNT (line ~25):
Fixed quantity to trade (e.g., "0.001" for 0.001 BTC).
Must meet Xeggex’s minimum trade size for the pair.
BUY_THRESHOLD (line ~26):
Price decrease percentage to trigger a buy (default: 0.005 = 0.5%).
PROFIT_MARGIN (line ~27):
Target profit margin after fees (default: 0.01 = 1%).
TRADING_FEE (line ~28):
Xeggex trading fee per trade (default: 0.002 = 0.2%). Verify with Xeggex.
MAX_POSITION (line ~30):
Maximum position size (default: 0.001). Limits total holdings.


Example Configuration
python


API_KEY = "abc123xyz789"
API_SECRET = "def456uvw012"
SYMBOL = "DOGE/USDT"
AMOUNT = "10.0"  # 10 DOGE
BUY_THRESHOLD = 0.005
PROFIT_MARGIN = 0.015  # 1.5% profit target
TRADING_FEE = 0.002
MAX_POSITION = 100.0  # Max 100 DOGE
Running the Bot
Windows
Navigate to Script Directory:
Open Command Prompt and change to the script’s folder:
cd C:\TradingBot


Run the Script:

Execute:
python groktrade_single.py
The bot will start and display trade activity in the console.


Linux
Navigate to Script Directory:
Open a terminal and change to the script’s directory:
cd ~/TradingBot

Run the Script:
Execute:
python3 groktrade_single.py
The bot will run and log trades to the console.


Stopping the Bot
Press Ctrl+C in the terminal to stop the script.
Output
Console: Displays real-time price updates, buy/sell orders, fees, and net profit after fees.
Example:

Price: 50000.00, Change: -0.0051, Position: 0.0
Buy order 123 placed successfully. Price: 50000.0, Fee: 0.1
Price: 50707.00, Change: 0.0141, Position: 0.001
Sell order 124 placed successfully. Price: 50707.0, Fee: 0.101414
Net profit after fees: 0.497172


Troubleshooting
ModuleNotFoundError: Ensure requests and websocket-client are installed (see Installation).
WebSocket Connection Lost: This version doesn’t auto-reconnect. Restart the script manually if the connection drops.
API Errors: Verify API_KEY, API_SECRET, and SYMBOL match your Xeggex account.
Insufficient Funds: Ensure your account has enough USDT to cover AMOUNT at the current price.


Notes
Risk: Test with small amounts first. Trading involves financial risk.
Fees: The bot assumes a 0.2% fee per trade (0.4% total per cycle). Confirm with Xeggex.
No Balance Check: This version doesn’t monitor balances or adjust quantities dynamically.
Reconnection: Lacks automatic reconnection. Upgrade to a later version for this feature.
