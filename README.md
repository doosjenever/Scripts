# LickHunterPro Variable Pairs

On the LickHunterPro Discord a user named Sanduckchan created an overview on the Binance Futures liquidations. You can visit the site @ http://www.lickhunter.com/data/
My script fetches the pairs from the site and places them in the settings.py. The problem was with open orders. When the pairs got replaced you lost track of the open orders. That's why the script also checks your open orders on Binance Futures and combines those pairs with the pairs from the site.

# Features:
- Auto copies **settings.py** to **binanceWebsocket** and **binanceProfit**
- Pairs based on **Top 10 burned by Volume - 24h**, **Top 10 by Liq-Events - 24h**, **Average Liq-Volume in USD - 24h** and **Average Liq-Amount - 24h**
- Set a maximum of traidingpairs
- Set a maximum of open orders, so you don't get too much open orders
- Open order isolation - When X percent of your wallet balance gets hit by open orders, only the open order pairs will be traded until the percentage drops below X

# Prerequisites:
- PowerShell 5.1 - https://www.microsoft.com/en-us/download/details.aspx?id=54616
- You have to have a working LickHunterPro configuration, all settings in settings.py should be in place and change your pairs line to: **pairs = []**

# Installation:
- Place **Start-LickHunterPro-VarPairV1.5.ps1**, **LickHunterPro.ps1** and **Stop-LickHunterPro.ps1** in the root of the LickHunterPro folder, in my case C:\LickHunterPro\
- Edit **Start-LickHunter-Pro-VarPair.ps1** with **NotePad++** or **Windows PowerShell ISE**
  - $APIKey = "key" **Set your Binance Futures API key, this can be a read only one**
  - $APISecret = "secret" **Set your Binance Futures API secret**
  - $maxPairs = "8" **The maximum pairs you want to trade, always the top of the chart is used**
  - $maxPositions = "3" **The maximum orders you want to have open at the same time**
  - $openOrderIsolationPercentage = "10" **Only trade open order pairs when X percentage of wallet balance is reached**
  - $tadingMode = **Choose a mode to base match your pairs. Modes: 1. $staticPairs 2. $whitelist 3. $tradingAge**
  - $staticPairs = **Trade only the pairs you want to trade**
  - $whitelist = **Set your personal whitelist of pairs you want to be able to trade**
  - $tradingAge = **All coins below trading age will not be traded**
  - $blacklist = **You can blacklist coins that are above your trading age, so they won't be traded**
  - $tradePairs = "1" **Choose 1, 2, 3 or 4, depending what chart your wan't to base your pairs on (1. Top 10 burned by Volume - 24h, 2. Top 10 by Liq-Events - 24h, 3. Average Liq-Volume in USD - 24h, 4. Average Liq-Amount - 24h)**
  - $fundingRateThreshold = **$true or $false, default is $false, set to $true if you don't want to trade pairs with a high Funding Rate**
  - $maxFundingRate = **For explanation about funding rate you can read this https://www.binance.com/en/support/faq/360033525031**  

- Save your changed settings
- Open Powershell and navigate to you LickHunterPro folder. From there run **Get-ChildItem | Unblock-File**
- Run **Start-LickHunterPro-VarPair.ps1** from PowerShell

# Donate
- ETH: **0xA63Bca4aa47e42498889AB5185336FEa54835C7E**
- USDT/ERC20: **0xA63Bca4aa47e42498889AB5185336FEa54835C7E**
