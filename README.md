# AgentX Crypto Trading Framework

![AgentX Banner](https://fmqflmhh.manus.space/images/banner.png)

## Overview

AgentX is a hierarchical agent-based system for cryptocurrency trading that functions similarly to a professional hedge fund structure. It leverages multiple AI agents working together to research, analyze, make decisions, and execute trades in the cryptocurrency market.

**Live Demo:** [https://fmqflmhh.manus.space](https://fmqflmhh.manus.space)

## Features

### Executive Layer
- **Chief Coordinator Agent**: Reviews recommendations from lower-level agents and makes final allocation decisions
- **Risk Manager Agent**: Monitors overall portfolio risk exposure and sets appropriate risk parameters
- **Performance Analyst Agent**: Tracks system metrics and provides optimization feedback

### Strategy Layer
- **Market Research Agent**: Monitors news feeds, social media, and market data sources to analyze sentiment and identify trading opportunities
- **Technical Analysis Agent**: Performs pattern recognition and signal generation using various technical indicators
- **Fundamental Analysis Agent**: Evaluates crypto projects based on on-chain metrics and development activity
- **Macro Analysis Agent**: Monitors broader market conditions and economic factors
- **Correlation Agent**: Tracks relationships between crypto assets and other market variables

### Execution Layer
- **Trade Execution Agent**: Executes approved trades with optimal timing using various execution strategies
- **Liquidity Monitoring Agent**: Tracks exchange conditions across multiple venues
- **Order Book Agent**: Analyzes market depth and order flow to provide trading insights

### Additional Features
- Standardized communication protocols between agents
- Comprehensive logging system
- Interactive dashboard for system monitoring
- Modular and expandable architecture
- Resilient to failures and unexpected market conditions

## System Architecture

The AgentX system is organized into three hierarchical layers:

```
┌─────────────────────────────────────────────────────────────┐
│                     EXECUTIVE LAYER                          │
│                                                             │
│  ┌───────────────┐    ┌───────────────┐    ┌───────────────┐│
│  │     Chief     │    │     Risk      │    │  Performance  ││
│  │  Coordinator  │    │    Manager    │    │    Analyst    ││
│  └───────┬───────┘    └───────┬───────┘    └───────┬───────┘│
└─────────────────────────────────────────────────────────────┘
                 │                 │                 │
                 ▼                 ▼                 ▼
┌─────────────────────────────────────────────────────────────┐
│                      STRATEGY LAYER                          │
│                                                             │
│  ┌───────────┐ ┌───────────┐ ┌───────────┐ ┌───────────┐   │
│  │  Market   │ │ Technical │ │Fundamental│ │   Macro   │   │
│  │ Research  │ │ Analysis  │ │ Analysis  │ │ Analysis  │   │
│  └───────────┘ └───────────┘ └───────────┘ └───────────┘   │
│                                                             │
│                      ┌───────────┐                          │
│                      │Correlation│                          │
│                      │   Agent   │                          │
│                      └───────────┘                          │
└─────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│                     EXECUTION LAYER                          │
│                                                             │
│  ┌───────────────┐    ┌───────────────┐    ┌───────────────┐│
│  │     Trade     │    │   Liquidity   │    │  Order Book   ││
│  │   Execution   │    │   Monitoring  │    │     Agent     ││
│  └───────────────┘    └───────────────┘    └───────────────┘│
└─────────────────────────────────────────────────────────────┘
```

## Installation

### Prerequisites
- Python 3.10+
- Node.js 20.0+
- 8GB RAM minimum (16GB recommended)
- Modern multi-core CPU
- Internet connection for market data access

### Standard Installation

1. Clone the repository
```bash
git clone https://github.com/13otKmdr/AgentX.git
cd AgentX
```

2. Set up Python environment
```bash
python3 -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
```

3. Install Node.js dependencies
```bash
cd src/dashboard
npm install
cd ../..
```

4. Configure the system
```bash
cp config/default.json config/local.json
# Edit config/local.json with your preferred settings
```

5. Run the system
```bash
python src/main.py
```

6. Access the dashboard at `http://localhost:5000`

### Docker Installation

1. Install Docker from [docker.com](https://docs.docker.com/get-docker/)

2. Clone the repository
```bash
git clone https://github.com/13otKmdr/AgentX.git
cd AgentX
```

3. Configure the system
```bash
cp config/default.json config/local.json
# Edit config/local.json with your preferred settings
```

4. Build and run with Docker Compose
```bash
docker-compose up -d
```

5. Access the dashboard at `http://localhost:5000`

For detailed installation instructions, see the [Installation Guide](https://fmqflmhh.manus.space/docs/installation.html).

## Usage

### Basic Usage

1. Configure your system parameters in the configuration file
2. Start the system: `python src/main.py`
3. Access the dashboard and click "Start" to begin trading
4. Monitor performance, trades, and system status through the dashboard

### Configuration

The main configuration file is located at `config/local.json`. Key configuration sections include:

- System settings (update interval, log level)
- Agent-specific parameters
- Risk parameters (max drawdown, volatility limits)
- Allocation limits
- Exchange API credentials
- Monitored trading pairs

Example configuration:
```json
{
  "system": {
    "name": "AgentX Trading System",
    "update_interval": 1.0,
    "log_level": "INFO"
  },
  "agents": {
    "executive": {
      "chief_coordinator": {
        "update_frequency": 0.5,
        "allocation_limits": {
          "max_per_asset": 0.2,
          "max_per_strategy": 0.3
        }
      },
      "risk_manager": {
        "update_frequency": 0.5,
        "risk_limits": {
          "max_drawdown": 0.1,
          "max_volatility": 0.2,
          "max_correlation": 0.7
        }
      }
    }
  },
  "exchanges": {
    "binance": {
      "api_key": "YOUR_API_KEY",
      "api_secret": "YOUR_API_SECRET"
    }
  },
  "assets": {
    "monitored_pairs": [
      "BTC/USDT", "ETH/USDT", "BNB/USDT", "SOL/USDT", "ADA/USDT"
    ]
  }
}
```

## Documentation

- [User Guide](https://fmqflmhh.manus.space/docs/user_guide.html): Comprehensive guide to using the AgentX system
- [API Documentation](https://fmqflmhh.manus.space/docs/api_docs.html): Details on programmatic access to the system
- [Installation Guide](https://fmqflmhh.manus.space/docs/installation.html): Step-by-step setup instructions

## Development

### Adding Custom Agents

1. Create a new agent class that extends the appropriate base class
2. Implement required methods (update, handle_message, etc.)
3. Register the agent in the system configuration

Example:
```python
from src.strategy.base_strategy import BaseStrategyAgent
from src.protocols import MessageType, AgentType

class MyCustomStrategyAgent(BaseStrategyAgent):
    def __init__(self, agent_id, router, config_file=None, logger=None):
        super().__init__(
            agent_id=agent_id,
            agent_type=AgentType.CUSTOM_STRATEGY,
            router=router,
            config_file=config_file,
            logger=logger
        )
        
    def update(self):
        # Custom strategy logic here
        pass
        
    def handle_market_data(self, message):
        # Process market data
        pass
        
    def generate_signals(self):
        # Generate trading signals
        recommendation = {
            "asset": "BTC/USDT",
            "action": "buy",
            "confidence": 0.8,
            # Additional details...
        }
        
        # Send recommendation to chief coordinator
        self.broker.send(
            to="chief_coordinator",
            message_type=MessageType.TRADE_RECOMMENDATION,
            content={"recommendation": recommendation}
        )
```

### Testing

Run the test suite:
```bash
python -m pytest tests/
```

## Roadmap

- **Q2 2025**: Enhanced sentiment analysis for Market Research Agent
- **Q3 2025**: Additional technical indicators and pattern recognition
- **Q4 2025**: Machine learning integration for performance optimization
- **Q1 2026**: Multi-exchange support expansion
- **Q2 2026**: Mobile application for monitoring and alerts

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Built using OpenAI's Agent SDK
- Inspired by professional hedge fund structures
- Special thanks to all contributors and the crypto trading community

---

© 2025 AgentX. All rights reserved.
