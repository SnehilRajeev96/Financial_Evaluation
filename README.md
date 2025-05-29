# Agentverse AI-Powered Financial Analysis System

This repository contains a modular, agent-based system designed to automate strategic financial analysis and valuation estimation for public companies. It leverages a multi-agent architecture, powered by scraping, calculations, and rule-based scoring — all orchestrated by a centralized Coordinator Agent.

 Use Case: AI-powered revenue multiple estimation for companies like Apple, based on financial, market, innovation, competitive, and ESG signals.

---

 Folder Structure

```
.
├── coordinator_agent.py                  # Orchestrates all agents and runs final scoring
├── financial_agent.py                    # Extracts and computes key financial metrics
├── market_agent.py                       # Analyzes market share, TAM, growth vs competitors
├── innovation_ip_agent.py                # Tracks patents, R&D %, productization metrics
├── esg_compliance_agent.py               # Collects ESG ratings, DEI %, compliance badges
├── usps_competitive_agent.py             # Captures niche capability %, partnerships, NPS
├── scoring_agent.py                      # Normalizes all metrics and calculates final score
└── README.md                             # Documentation
```

---

 Core Agents & Roles (Explained)

CoordinatorAgent  
Serves as the central orchestrator that sequentially activates all specialized agents—Financial, Market Intelligence, Innovation/IP, ESG & Compliance, and USPs/Competitive Edge.  
Key functions:
- Manages execution flow for each agent  
- Aggregates structured outputs  
- Passes consolidated data to the CalculationScoringAgent  
This agent enables seamless integration and end-to-end automation of the analysis and valuation pipeline.

FinancialDataAgent  
Extracts key financial metrics from company websites or databases. It parses revenue, profit, cash flow, employee count, and client concentration data to calculate:
- Revenue Growth Rate
- EBITDA Margin
- Net Profit Margin
- Revenue per Employee
- Client Concentration Risk (how dependent the company is on top clients)  
This agent quantifies the company's operational efficiency and profitability.

MarketIntelligenceAgent  
Gathers market data including the company’s revenue, total addressable market (TAM), and competitive environment. It compares the company’s growth with that of competitors and evaluates:
- Global Market Share
- Growth Advantage vs Competitors
- Regional Revenue Growth
- Industry Diversification (presence in multiple sectors)  
This agent helps measure market positioning and growth sustainability.

InnovationIPAgent  
Assesses how innovative the company is by analyzing patents, R&D spending, and the proportion of revenue coming from intellectual property (IP)-based products. It evaluates:
- Number of Patents (and how they compare to industry average)
- R&D Spend as % of Revenue
- Productization Level (how well R&D translates into revenue)  
This agent captures the company’s ability to create defensible innovation.

ESGComplianceAgent  
Scrapes ESG ratings, diversity statistics, and regulatory badges like ISO, GDPR, or HIPAA. It evaluates the company’s ethical and governance posture using:
- ESG Rating (from third-party sources like MSCI or Sustainalytics)
- DEI (Diversity, Equity & Inclusion) Representation
- Number of Compliance Certifications Achieved  
This agent helps assess investor risk from a sustainability and governance perspective.

USPsCompetitiveEdgeAgent  
Measures the company’s unique strengths and brand defensibility. It collects data on specialized revenue streams, strategic partnerships, and customer satisfaction. Key outputs:
- Niche Capability % (share of revenue from specialized technologies)
- Number of Strategic Partnerships
- Net Promoter Score (NPS) to gauge customer loyalty  
This agent maps differentiation and customer trust into tangible metrics.

CalculationScoringAgent  
Takes all outputs from the above agents and assigns a weighted score (1 to 5 scale) to each category based on predefined benchmarks. It then computes:
- Weighted Performance Score
- Estimated Revenue Multiple (6x to 16x range based on total score)  
This agent converts diverse company signals into a single, comparable valuation metric.

---

How It Works

Step 1: CoordinatorAgent calls each of the 5 specialized agents  
Step 2: Each agent scrapes or ingests company data and computes metrics  
Step 3: Results are passed to CalculationScoringAgent  
Step 4: A final weighted score is computed and mapped to a revenue multiple  
Step 5: Output is served as a structured JSON — ready for dashboard visualization

---

Example Output

```json
{
  "scores": {
    "financial": 4.33,
    "market": 3.75,
    "innovation": 4.1,
    "competitive": 4.5,
    "esg": 3.8
  },
  "weighted_score": 4.16,
  "revenue_multiple_estimate": "11–13x"
}
```

---

Requirements

- Python 3.8+
- requests
- beautifulsoup4

Install dependencies:
```bash
pip install -r requirements.txt
```

