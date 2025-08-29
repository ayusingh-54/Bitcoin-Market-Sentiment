# Bitcoin Market Sentiment vs Trader Performance Analysis

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://python.org)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

## 📊 Project Overview

This project analyzes the relationship between Bitcoin market sentiment (Fear & Greed Index) and trader performance on Hyperliquid. Through comprehensive statistical analysis and data visualization, we uncover actionable insights for sentiment-aware trading strategies.

### 🎯 Key Research Questions

1. **Profitability Patterns**: How does trader profitability correlate with market sentiment?
2. **Risk Management**: Do traders adjust position sizes based on sentiment?
3. **Volume Dynamics**: How does trading volume change across different sentiment regimes?
4. **Behavioral Analysis**: Are traders more likely to go long/short during Fear vs Greed?
5. **Elite Performance**: Who are the top traders and in which conditions do they excel?

## 📈 Key Findings

### 🏆 Major Insights

- **Greed markets** show **+9.5% higher profitability** than Fear markets ($53.88 vs $49.21 avg PnL)
- **Statistical significance**: P-value < 0.001 (highly significant relationship)
- **Volume-Sentiment correlation**: r = 0.347 (moderate positive correlation)
- **Elite traders** achieve **65.4% win rate** vs 41.1% market average
- **Contrarian behavior**: 52.3% BUY orders during Fear vs 47.7% during Greed

### 📊 Performance Metrics by Sentiment

| Sentiment     | Avg PnL | Win Rate | Volatility | Volume Share |
| ------------- | ------- | -------- | ---------- | ------------ |
| Extreme Fear  | $45.12  | 39.8%    | σ = 1,045  | 18.2%        |
| Fear          | $49.21  | 40.3%    | σ = 990.88 | 22.4%        |
| Neutral       | $34.31  | 41.8%    | σ = 517.12 | 15.7%        |
| Greed         | $53.88  | 42.1%    | σ = 842.33 | 26.3%        |
| Extreme Greed | $51.34  | 41.9%    | σ = 923.45 | 17.4%        |

## 🚀 Quick Start

### Prerequisites

```bash
Python 3.8+
Jupyter Notebook
pip (Python package manager)
```

### Installation

1. **Clone the repository**

```bash
git clone <repository-url>
cd "Bitcoin Market Sentiment"
```

2. **Install dependencies**

```bash
pip install pandas numpy matplotlib seaborn scipy scikit-learn
```

3. **Download data files**

   - Place `fear_greed_index.csv` in the project directory
   - Place `historical_data.csv` in the project directory

4. **Launch Jupyter Notebook**

```bash
jupyter notebook index.ipynb
```

### 📋 Required Data Files

#### `fear_greed_index.csv`

```
date,value,classification
2024-01-01,45,Fear
2024-01-02,52,Neutral
...
```

#### `historical_data.csv`

```
account,timestamp_ist,execution_price,size_tokens,size_usd,closed_pnl,side
0x123...,01-01-2024 10:30,45000,1.5,67500,150.75,BUY
...
```

## 📁 Project Structure

```
Bitcoin Market Sentiment/
├── README.md                 # This file
├── index.ipynb              # Main analysis notebook
├── fear_greed_index.csv     # Bitcoin Fear & Greed Index data
├── historical_data.csv      # Hyperliquid trading data
├── requirements.txt         # Python dependencies
└── images/                  # Generated visualizations
    ├── profitability_analysis.png
    ├── volume_dynamics.png
    └── behavioral_patterns.png
```

## 🔬 Analysis Methodology

### 1. **Data Preprocessing**

- **Data Cleaning**: Handle missing values, standardize formats
- **Feature Engineering**: Create sentiment scores, trade outcomes, PnL percentages
- **Data Merging**: Combine trading data with sentiment data by date

### 2. **Statistical Analysis**

- **Correlation Analysis**: Pearson and Spearman correlations
- **Significance Testing**: T-tests, Chi-square tests
- **Effect Size Calculations**: Cohen's d for practical significance

### 3. **Advanced Metrics**

- **Risk-Adjusted Returns**: Sharpe-like ratios
- **Volume Momentum**: Moving averages and momentum indicators
- **Anomaly Detection**: Z-score analysis for volume spikes
- **Behavioral Bias Analysis**: Contrarian vs momentum patterns

### 4. **Visualization Framework**

- **Time Series Analysis**: Volume and sentiment evolution
- **Distribution Analysis**: PnL distributions by sentiment
- **Correlation Heatmaps**: Multi-dimensional relationship mapping
- **Performance Dashboards**: Elite trader analysis

## 📊 Key Visualizations

### 1. **Profitability vs Market Sentiment**

- Bar charts with statistical significance indicators
- Distribution plots with density curves
- Risk-adjusted return analysis

### 2. **Volume Dynamics Analysis**

- Time series with technical indicators
- Volume momentum by sentiment
- Anomaly detection visualizations

### 3. **Behavioral Trading Patterns**

- Direction distribution (Buy/Sell) by sentiment
- Win rate analysis across market conditions
- Risk appetite indicators

### 4. **Elite Trader Performance**

- Top performer identification
- Sentiment specialization analysis
- Risk vs return scatter plots

## 🎯 Strategic Implementation

### 📈 **Level 1: Immediate Tactics (0-30 days)**

```python
# Dynamic Position Sizing
if fear_greed_index > 80:  # Extreme Greed
    position_size *= 0.75  # Reduce by 25%
elif fear_greed_index < 20:  # Extreme Fear
    position_size *= 0.85  # Reduce by 15%
```

### 🏗️ **Level 2: Systematic Development (1-6 months)**

- **Sentiment Overlay Strategies**: Fear/Greed specific algorithms
- **Volume-Sentiment Momentum**: Combined indicator systems
- **Elite Pattern Replication**: Top trader strategy analysis

### 🚀 **Level 3: Advanced Integration (6+ months)**

- **Machine Learning Models**: Sentiment prediction algorithms
- **Portfolio Optimization**: Sentiment-aware risk management
- **Cross-Asset Analysis**: Multi-market sentiment strategies

## 📋 Usage Examples

### Basic Analysis

```python
# Load and analyze data
sentiment_df = pd.read_csv("fear_greed_index.csv")
trader_df = pd.read_csv("historical_data.csv")

# Merge datasets
merged_df = trader_df.merge(sentiment_df, on='date')

# Calculate performance by sentiment
performance = merged_df.groupby('sentiment_classification')['closed_pnl'].mean()
```

### Advanced Analytics

```python
# Risk-adjusted performance analysis
def calculate_sharpe_ratio(returns, risk_free_rate=0):
    return (returns.mean() - risk_free_rate) / returns.std()

# Elite trader identification
top_traders = merged_df.groupby('account').agg({
    'closed_pnl': ['sum', 'count', 'mean'],
    'trade_outcome': lambda x: (x == 'Win').sum() / len(x)
})
```

## 🔧 Customization Options

### **Data Sources**

- Modify data loading section for different exchanges
- Adapt sentiment indicators (RSI, social sentiment, etc.)
- Integrate real-time data feeds

### **Analysis Parameters**

- Adjust time windows for moving averages
- Customize sentiment score mappings
- Modify statistical significance thresholds

### **Visualization Themes**

- Color schemes for different market conditions
- Custom plot styles and annotations
- Interactive dashboard components

## 🚨 Important Notes

### **Data Quality Requirements**

- Ensure timestamp consistency between datasets
- Validate sentiment data completeness
- Handle missing values appropriately

### **Statistical Considerations**

- **Sample Size**: Minimum 1000 trades recommended for reliable results
- **Time Period**: At least 6 months of data for seasonal effects
- **Market Regimes**: Consider bull/bear market contexts

### **Risk Disclaimers**

- Past performance doesn't guarantee future results
- Sentiment relationships may change during market regime shifts
- Always implement proper risk management protocols

## 🤝 Contributing

1. **Fork the repository**
2. **Create feature branch** (`git checkout -b feature/AmazingFeature`)
3. **Commit changes** (`git commit -m 'Add AmazingFeature'`)
4. **Push to branch** (`git push origin feature/AmazingFeature`)
5. **Open Pull Request**

### **Contribution Areas**

- Additional sentiment indicators
- Enhanced statistical models
- Real-time data integration
- Cross-asset analysis extensions

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 📞 Contact

- **Author**: Ayush Singh 
- **Project Link**: https://github.com/ayusingh-54/Bitcoin-Market-Sentiment/edit/main/README.md
- **Email**: ayusingh693@gmail.com

## 🙏 Acknowledgments

- **Hyperliquid**: For providing comprehensive trading data
- **Alternative.me**: Fear & Greed Index data source
- **Community**: Contributors and feedback providers

## 📚 References

1. Behavioral Finance Literature
2. Cryptocurrency Market Analysis Papers
3. Sentiment Analysis Methodologies
4. Statistical Trading Strategy Research

---

### ⭐ If this project helped you, please star the repository!

**Happy Trading! 📈**
