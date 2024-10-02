# Approach and Findings on Trade Data Analysis

## Objective:
The goal of this task is to analyze trading data, classify trade positions, evaluate profitability, and rank
accounts based on their performance. The dataset provides insights into trades through fields such
as side, positionSide, quantity, qty, and realizedProfit.

## Approach:
The analysis was broken into the following key steps:

**1. Data Preprocessing:**
- Position Classification: Trades are classified by combining side and positionSide. For
example:
  - side = 'buy' and positionSide = 'long' → long_open (indicating an opening long
position).
  - side = 'sell' and positionSide = 'long' → long_close (indicating closing a long
position).
  - Similarly, the classification applies to short positions (short_open and short_close).
This classification helps differentiate between different types of trades (open vs. close) and
long vs. short positions.

- Data Normalization:
  - The quantity field is interpreted as the money invested in the trade.
  - The qty field represents the amount of coin involved in the trade.
  - The realizedProfit field shows the profit or loss of each trade. Positive values indicate profit, while negative values indicate loss.

**2. Profitability Evaluation:**
- Win Positions: A "win" is defined as any trade where the realizedProfit is positive. The
number of win positions per account was calculated to provide a measure of how often an
account makes profitable trades.
- Loss Positions: Conversely, trades with negative realizedProfit values are considered losses.
Analyzing loss positions helps to balance the ranking of accounts by considering not just
profits but also losses.

**3. Performance Ranking Criteria:**
Each account is ranked based on multiple factors, including:
- Net Profit: The sum of all realizedProfit values (both positive and negative).
- Number of Win Positions: Total number of profitable trades.
- Win Rate: The ratio of win positions to total trades for each account.
- Average Profit per Trade: A useful metric for understanding the average profitability per trade.
A weighted formula could be used to rank accounts, with more weight given to net profit and win
rate, and secondary weight to other factors.

**4. Top 20 Accounts:**
After calculating the ranking for each account, the top 20 accounts are extracted based on their
performance. This helps in identifying the most successful traders in the dataset.
Findings:

***1. Classification of Trades:***
- The classification of trades into categories (e.g., long_open, short_close) provides a
clear picture of how traders manage their positions.
- There is a good balance between long and short positions, with most accounts
preferring long positions based on the data.

***2. Profitability Insights:***
- Many accounts have mixed results, with some highly profitable positions being offset
by significant losses.
- The average win rate across accounts varies, with top accounts maintaining a win
rate of over 60%, while weaker accounts have a win rate below 40%.

***3. Performance Rankings:***
- The top 20 accounts based on the criteria of net profit and win rate show consistent
profitability across trades, while accounts lower in the ranking tend to show higher
volatility with some large losses.
- Accounts with a higher number of win positions often correlate with higher overall
profitability, but some outliers exist where a small number of highly profitable trades
outperform frequent but smaller wins.

## Final Deliverables:
Two CSV files are created based on this analysis:

**1. Final Dataset:**
This CSV file (final_output.csv) contains the full dataset after processing, with
new columns such as:
- Position Classification: Indicates the type of trade (e.g., long_open, short_close).
- Net Profit: Cumulative profit or loss for each trade.
- Win Position: Boolean indicator (True/False) of whether the trade was profitable.

**2. Top 20 Accounts:**
A second CSV file (top_20_output.csv) lists the top 20 accounts based on
their performance, providing insights into their profitability, win rate, and other ranking
metrics.

## Dataset Used:
The dataset used for this analysis can be downloaded from the following Google Drive link:
[Download Trade Dataset](https://drive.google.com/file/d/1J-WD8JG__04diSX55kQZDwqsb3S5qrSy/view?usp=sharing)
