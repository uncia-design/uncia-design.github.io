---
title: "Data Engineering & Dashboards"
layout: single
permalink: /data-engineering/
---

## Why Data Matters in Architecture & Construction

At **Uncia**, we believe that great design requires rigorous data analysis. Every project begins with numbers: What will construction cost? How long will permitting take? What's the financial return? Without accurate data and transparent visualization, design decisions are made in the dark. Our data engineering team develops interactive tools that answer these critical questions, enabling confident investment decisions.

## ROI Dashboard Examples

### Project ROI Visualization

Our interactive dashboards help project stakeholders understand investment returns across multiple scenarios:

```
Project: Round Rock City Center Mixed-Use Development

FINANCIAL OVERVIEW
├─ Total Investment: $120M
├─ Expected Annual Revenue: $9.8M (Year 5+)
├─ Payback Period: 12.3 years
├─ IRR (20-year horizon): 8.2%
└─ Property Value Appreciation: +$45M (37.5%)

ANNUAL CASH FLOW PROJECTION
Year    Revenue    Costs    Net CF    Cumulative
1       $1.2M     $3.1M   -$1.9M    -$1.9M
2       $3.4M     $1.5M    $1.9M    $0.0M
3       $5.6M     $1.2M    $4.4M    $4.4M
4       $7.8M     $1.1M    $6.7M    $11.1M
5       $9.8M     $1.0M    $8.8M    $19.9M
```

**Key Features:**
- Real-time sensitivity analysis (adjust rental rates, occupancy, construction costs)
- Scenario comparison (conservative, base case, optimistic projections)
- Break-even analysis and payback visualization
- Tax depreciation impact on investor returns
- Financing scenarios (different loan terms, down payments)

### ADU Investment Returns

For homeowners considering ADU development:

```
ADU INVESTMENT ANALYSIS

Property Details:
├─ Existing Home Value: $850K (Austin, TX)
├─ Lot Size: 0.45 acres
└─ Current Annual Property Tax: $8,400

ADU Project:
├─ Design & Permitting: $35K
├─ Construction: $180K (for 600 sf, 1BR/1BA unit)
├─ Total Investment: $215K
└─ Financing (80/20): Loan $172K + Cash $43K

Revenue Stream:
├─ Monthly Rent: $1,900
├─ Annual Gross Revenue: $22,800 (at 100% occupancy)
├─ Vacancy Rate (assumed): 5%
├─ Annual Net Revenue: $21,660
└─ Cap Rate (Year 1): 10.1%

Return Analysis:
├─ Simple Payback: 9.9 years
├─ Cash-on-Cash Return (Year 1): 50.4% (net cash flow / equity invested)
├─ 10-Year NPV (8% discount): $87K
└─ IRR (10-year horizon): 15.3%

Home Value Impact:
├─ Appraised Value Increase: +$120K (ADU adds ~55% of construction cost)
├─ New Home Value: $970K
├─ Equity Position: +$135K
└─ Wealth Creation: ADU + appreciation + loan paydown
```

**Dashboard Interactivity:**
- Adjust construction costs based on current market rates
- Model different rent levels (comparable research)
- Sensitivity to occupancy rates
- Property tax implications
- Refinancing scenarios
- Sell-vs-hold analysis

## Construction Cost Estimation Dashboard

### Why Accurate Cost Estimation Matters

Construction costs can vary by 20-30% without disciplined estimation. Our dashboard brings transparency and precision:

```
PROJECT COST ESTIMATION FRAMEWORK

1. LABOR COSTS (40-50% of total)
   ├─ Skilled Trades (electricians, plumbers, carpenters, HVAC)
   │  └─ Historical rates: $45-120/hour (varies by trade, experience)
   ├─ General Labor: $22-35/hour
   ├─ Productivity Factors: Complexity, site conditions, weather
   └─ Worker's Compensation & Benefits: 35-40% markup

2. MATERIALS (30-35% of total)
   ├─ Structural (concrete, steel, lumber)
   ├─ Envelope (windows, doors, insulation, roofing)
   ├─ MEP (mechanical, electrical, plumbing systems)
   ├─ Finishes (flooring, paint, trim, fixtures)
   └─ Market Volatility: Real-time pricing from suppliers

3. EQUIPMENT & TOOLS (5-10%)
   ├─ Heavy Equipment (cranes, excavators—rental)
   ├─ Power Tools (temporary power, air compressors)
   └─ Safety Equipment & Temporary Structures

4. OVERHEAD & PROFIT (15-20%)
   ├─ General Conditions (site management, security, cleanup)
   ├─ Insurance & Bonds: 2-5% of contract
   ├─ Contingency (typically 10-15% for unknowns)
   └─ Profit Margin: 5-10% for contractor
```

### Example: K-12 School Building Cost Model

```
COST BREAKDOWN FOR 120,000 SF SCHOOL FACILITY

Category                          Rate/Unit    Quantity    Subtotal
─────────────────────────────────────────────────────────────────
SITE WORK & FOUNDATION
Excavation & Grading             $3/sf        120K        $360K
Foundation & Flatwork            $8/sf        120K        $960K
Parking & Roads                  $4/sf        25K         $100K

STRUCTURAL FRAME
Steel Structure                  $12/sf       120K        $1.44M
Concrete Floors                  $6/sf        95K         $570K

EXTERIOR WALLS & ROOF
Walls & Glazing                  $18/sf       120K        $2.16M
Roof Systems                     $8/sf        120K        $960K
Doors & Hardware                 $2/sf        120K        $240K

INTERIOR FINISHES
Flooring                         $6/sf        120K        $720K
Wall Finishes & Paint            $4/sf        120K        $480K
Doors & Interior Hardware        $3/sf        120K        $360K
Toilet Rooms & Accessories       $8/sf        6K          $48K
Ceilings & Acoustic              $3/sf        120K        $360K

MEP SYSTEMS
HVAC                            $12/sf       120K        $1.44M
Electrical & Power              $8/sf        120K        $960K
Plumbing & Gas                  $5/sf        120K        $600K
Fire Protection                 $2/sf        120K        $240K

SPECIAL SYSTEMS
Lab Equipment & Safety          $4/sf        12K         $48K
Technology & Controls           $3/sf        120K        $360K
Food Service Equipment          $1/sf        8K          $8K

SUBTOTAL CONSTRUCTION                                     $12.4M
─────────────────────────────────────────────────────────────────
Contingency (12%)                                         $1.49M
General Conditions (8%)                                   $0.99M
Fee (7%)                                                  $0.87M
─────────────────────────────────────────────────────────────────
TOTAL PROJECT COST (ESTIMATE)                             $16.2M

Per-Square-Foot Cost: $135/sf (reasonable for K-12 school)
```

**Cost Sensitivity Analysis:**
- 10% wage inflation → +$0.8M
- 15% material cost increase → +$1.2M
- Extended timeline (weather delays) → +$0.4M (overhead escalation)
- Scope addition (10% items) → +$1.6M

## Dashboard Features & Capabilities

### Real-Time Data Integration

Our dashboards connect to live data sources:

- **Labor Rates**: Bureau of Labor Statistics (BLS), regional union rates
- **Material Pricing**: Building material supplier APIs, commodity futures
- **Market Data**: Real estate comps, comparable projects, historical trends
- **Economic Indicators**: Inflation rates, interest rates, construction index

### Scenario Planning & Sensitivity

Answer "what if" questions instantly:

```
SCENARIO COMPARISON: ADU PROJECT

                    CONSERVATIVE    BASE CASE    OPTIMISTIC
Construction Cost   $215K           $210K        $205K
Rental Rate         $1,700/mo       $1,900/mo    $2,100/mo
Occupancy Rate      90%             95%          98%
Appreciation/Year   2%              3.5%         5%
Payback Period      11.2 years      9.9 years    8.1 years
10-Year IRR         11.8%           15.3%        19.7%
```

Users can adjust any variable and see real-time impact on returns.

### Comparative Analysis

Compare multiple project scenarios or investment options:

- **Option A**: ADU on existing home
- **Option B**: Townhouse community development
- **Option C**: Small multifamily building
- **Option D**: Hold & renovate for appreciation

Side-by-side ROI, payback, and wealth creation projections.

### Reporting & Export

Generate professional reports:

- Executive summary with key metrics
- Detailed assumption documentation
- Charts and graphs for stakeholder presentations
- Sensitivity tables and scenario comparisons
- Excel export for further analysis
- PDF reports for lending/financing applications

## Why This Matters

**For Project Owners:**
- Understand true project costs before commitment
- Compare investment scenarios objectively
- Make confident financing decisions
- Communicate clearly with lenders and stakeholders
- Monitor actual costs against estimates during construction

**For Architects & Designers:**
- Develop cost-conscious designs within budgets
- Justify design choices with financial analysis
- Value-engineer efficiently (eliminate waste, not quality)
- Communicate with developers and clients using same data framework
- Predict and manage cost overruns proactively

**For Investors & Developers:**
- Evaluate project feasibility quickly
- Screen opportunities for financial viability
- Model different development scenarios
- Understand sensitivity to key variables
- Present confident pro formas to investors and lenders

## Our Approach

At Uncia, data engineering means:

1. **Rigorous Research**: Comprehensive cost databases, comparable project analysis
2. **Transparent Assumptions**: Every estimate clearly documented with sources
3. **Sensitivity Analysis**: Understanding what impacts returns most significantly
4. **Scenario Planning**: Multiple paths forward, not just one "expected" outcome
5. **Ongoing Refinement**: Actuals vs. estimates, learning from completed projects
6. **Professional Communication**: Making complex financial analysis accessible

## Get Started

Whether you're:
- **Considering an ADU**: Use our ROI calculator to model your investment
- **Planning a construction project**: Get accurate cost estimates before commitment
- **Evaluating development opportunities**: Analyze projects competitively
- **Seeking financing**: Generate professional pro formas for lenders

**Contact us** at [zhun.jiao.architect@gmail.com](mailto:zhun.jiao.architect@gmail.com) to discuss how data-driven design can improve your project outcomes.

---

## Tools & Technologies

Uncia develops dashboards and analytical tools using:

- **Data Analysis**: Python (Pandas, NumPy), R for statistical modeling
- **Visualization**: Interactive tools (Plotly, D3.js, Tableau)
- **Web Integration**: Custom web dashboards accessible from any browser
- **Real-time Updates**: API connections to live cost and market data
- **Reporting**: Automated PDF generation, Excel integration

## Sample Dashboard Screenshots

[Interactive examples would display here in production, showing ROI calculators, cost estimators, and scenario analysis tools]

---

## Questions?

How can data-informed design improve your project? Let's talk.

**Email**: [zhun.jiao.architect@gmail.com](mailto:zhun.jiao.architect@gmail.com)  
**Explore**: [View Our Projects](/projects/) | [Learn More About Uncia](/about/)
