# 📊 Dividend Analysis Toolkit for Google Sheets

> A comprehensive set of custom functions for analyzing dividend-paying stocks directly in Google Sheets. Get real-time dividend data, calculate yields, predict future payments, and analyze dividend growth trends.

[![Google Sheets](https://img.shields.io/badge/Google%20Sheets-Compatible-34A853?logo=googlesheets&logoColor=white)](https://sheets.google.com)
[![Version](https://img.shields.io/badge/Version-1.0-blue)](https://github.com/Ayman-AAA/Dividend-Analysis-Toolkit)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)
[![Data Source](https://img.shields.io/badge/Data%20Source-Yahoo%20Finance-purple)](https://finance.yahoo.com)

---

## 🚀 Quick Start

1. **Install** the add-on from Google Workspace Marketplace
2. **Open** any Google Sheet
3. **Use** functions like `=latestDividend("AAPL")` in any cell
4. **Analyze** - All functions automatically detect dividend frequency and patterns

---

## 📊 Available Functions

### 📈 Basic Dividend Information

#### `latestDividend(symbol)`
Returns the most recent dividend payment amount.

```javascript
=latestDividend("AAPL")     // → 0.25
=latestDividend("JNJ")      // → 1.19
=latestDividend("O")        // → 0.26 (monthly REIT)
```

#### `lastDividendDate(symbol)`
Returns the date of the most recent dividend payment.

```javascript
=lastDividendDate("AAPL")   // → 2024-11-07
=lastDividendDate("KO")     // → 2024-10-01
```

#### `lastExDividendDate(symbol)`
Estimates the ex-dividend date (approximately 2 days before payment date).

```javascript
=lastExDividendDate("MSFT") // → 2024-11-19
```

#### `getDividendFrequency(symbol)`
Determines how often dividends are paid.

```javascript
=getDividendFrequency("AAPL")  // → "Quarterly"
=getDividendFrequency("O")     // → "Monthly"
=getDividendFrequency("BAC")   // → "Quarterly"
```

---

### 💰 Dividend Analysis Functions

#### `ytdDividend(symbol)`
Total dividends paid in the current year.

```javascript
=ytdDividend("JNJ")         // → 4.76
=ytdDividend("MSFT")        // → 3.00
```

#### `trailingAnnualDividend(symbol)`
Total dividends paid in the last 12 months (most accurate for yield calculations).

```javascript
=trailingAnnualDividend("KO")   // → 1.84
=trailingAnnualDividend("PEP")  // → 4.60
```

#### `forwardAnnualDividend(symbol)`
Projected annual dividend based on latest payment and frequency.

```javascript
=forwardAnnualDividend("AAPL")  // → 1.00 (0.25 × 4 quarters)
=forwardAnnualDividend("O")     // → 3.12 (0.26 × 12 months)
```

---

### 📊 Yield Calculations

#### `latestDividendYield(symbol)`
Dividend yield based on most recent payment and current stock price.

```javascript
=latestDividendYield("T")       // → 0.0654 (6.54%)
=latestDividendYield("VZ")      // → 0.0612 (6.12%)
```

#### `trailingDividendYield(symbol)`
More accurate yield based on actual trailing 12-month dividends.

```javascript
=trailingDividendYield("JNJ")   // → 0.0289 (2.89%)
=trailingDividendYield("PG")    // → 0.0241 (2.41%)
```

---

### 🔮 Predictive Functions

#### `nextEstimatedDividendDate(symbol)`
Predicts when the next dividend payment will occur.

```javascript
=nextEstimatedDividendDate("AAPL")  // → 2025-02-13
=nextEstimatedDividendDate("O")     // → 2025-01-15
```

#### `estimatedNextDividend(symbol)`
Predicts the amount of the next dividend payment based on growth trends.

```javascript
=estimatedNextDividend("MSFT")  // → 0.83
=estimatedNextDividend("JNJ")   // → 1.22
```

#### `dividendGrowthTrend(symbol)`
Average dividend growth rate (as decimal: 0.05 = 5% growth).

```javascript
=dividendGrowthTrend("AAPL")    // → 0.0450 (4.5% average growth)
=dividendGrowthTrend("KO")      // → 0.0320 (3.2% average growth)
```

---

## 📈 Example Analysis Spreadsheet

Create a comprehensive dividend analysis with these column headers:

| Symbol | Latest Div | Frequency | YTD Total | Trailing Yield | Next Date | Est. Next | Growth Rate |
|--------|------------|-----------|-----------|----------------|-----------|-----------|-------------|
| AAPL | `=latestDividend(A2)` | `=getDividendFrequency(A2)` | `=ytdDividend(A2)` | `=trailingDividendYield(A2)` | `=nextEstimatedDividendDate(A2)` | `=estimatedNextDividend(A2)` | `=dividendGrowthTrend(A2)` |

---

## 🏢 Supported Stock Symbols

### ✅ Fully Supported
- **US Stocks**: NYSE, NASDAQ (AAPL, MSFT, JNJ, KO, PG, etc.)
- **REITs**: Most US REITs including monthly payers (O, STAG, WPC)
- **ETFs**: Dividend-focused ETFs (VYM, SCHD, VIG, etc.)
- **Utilities**: Regular dividend payers (T, VZ, SO, D)
- **Banks**: Major banks with regular dividends (JPM, BAC, WFC)

### ⚠️ Limited Support
- **International stocks**: May work with major ADRs (UL, NVS, TM)
- **Irregular payers**: Functions work but predictions less reliable
- **New IPOs**: Need dividend history for full functionality

### ❌ Not Supported
- Non-dividend paying stocks (will return 0 or null)
- Private companies or unlisted securities
- Cryptocurrency

---

## ⚠️ Important Limitations

### 📡 Data Source
- **Source**: Yahoo Finance API (free but not guaranteed)
- **Delay**: Data may be 15-20 minutes delayed
- **Accuracy**: Generally accurate but not suitable for high-frequency trading
- **Coverage**: Primarily US markets with some international coverage

### 🔧 Function Limitations
- **Historical data**: Limited to ~2 years of dividend history
- **Ex-dividend dates**: Estimated (±1-2 days accuracy)
- **Predictions**: Based on historical patterns, not forward guidance
- **Special dividends**: May be included in calculations
- **Stock splits**: May affect historical calculations

### ⚡ Rate Limits & Performance
- **Caching**: Functions cache data for 5 minutes to 24 hours
- **API limits**: Shared rate limits across all users
- **Performance**: First call may be slower, subsequent calls cached
- **Refresh**: Data refreshes automatically based on cache expiration

### ⚖️ Legal Disclaimers
- **Not financial advice**: For informational purposes only
- **No guarantees**: Past performance doesn't predict future results
- **Verify data**: Always cross-check important information
- **Trading decisions**: Consult financial professionals

---

## 🔧 Troubleshooting

### Common Issues

#### `"Error: Yahoo API returned no 'chart' field"`
- Stock symbol may be incorrect or delisted
- Try alternative ticker symbols (e.g., `BRK.A` vs `BRK-A`)

#### Functions return 0 or empty
- Stock may not pay dividends
- Verify correct symbol format
- Some stocks have limited historical data

#### Slow performance
- First call fetches fresh data (may take 3-5 seconds)
- Subsequent calls use cached data (instant)
- Avoid calling functions too frequently

#### Date functions return `#VALUE!`
- Format cells as Date to display properly
- Some stocks may not have sufficient dividend history

### Best Practices
- **Use consistent symbols**: Stick to primary exchange symbols
- **Cache awareness**: Functions cache data - don't expect real-time updates
- **Error handling**: Check if functions return valid data before complex calculations
- **Rate limiting**: Avoid mass updates of 100+ symbols simultaneously

---

## 🆘 Support & Contact

### Getting Help
- **Issues**: [Report bugs or request features](https://github.com/Ayman-AAA/Dividend-Analysis-Toolkit/issues)
- **Documentation**: This README covers all available functions
- **Examples**: See function examples above

### Contact Information
- **Email**: [aabukhater@gmail.com](mailto:aabukhater@gmail.com)
- **GitHub**: [https://github.com/Ayman-AAA/Dividend-Analysis-Toolkit](https://github.com/Ayman-AAA/Dividend-Analysis-Toolkit)
- **Updates**: Check marketplace listing for version updates

---

## 📋 Version History

- **v1.0**: Initial release

---

## 📄 License & Legal

This add-on is provided "as-is" without warranties. Users are responsible for verifying data accuracy. Not affiliated with Yahoo Finance or any financial institutions.

**Privacy**: This add-on only accesses your current spreadsheet and makes external API calls to fetch financial data. No personal data is stored or transmitted beyond what's necessary for functionality.

---

## 🏷️ Tags

`google-sheets` `dividends` `finance` `stocks` `analysis` `yahoo-finance` `add-on` `investment` `yield` `reit`

---

<div align="center">

**Last updated**: 7/25/2025 | **Compatible with**: Google Sheets | **Data source**: Yahoo Finance API

Made with ❤️ for dividend investors

</div>

