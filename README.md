# Saudi Arabia Refinery & Energy

This [project](https://xuanx1.github.io/fuelLoad/saudi.html) provides interactive dashboards and visualizations for analyzing Saudi Arabia's refinery infrastructure, refined product production, demand patterns, natural gas data, and energy reserves. The visualizations are built using web technologies and present comprehensive energy sector data through interactive charts and maps with cycling page functionality.

## 🗺️ Interactive Dashboards [Preview](https://xuanx1.github.io/fuelLoad/saudi.html)
![Screenshot 2025-08-23 191945](https://github.com/user-attachments/assets/8015f2df-a73f-46b9-836f-1dcf309fc4fb)
![Screenshot 2025-08-23 195339](https://github.com/user-attachments/assets/428fc1ab-6fbb-4b9d-8d5f-b63391419db3)

### Main Visualization Files

- **`refinery-map.html`** — Interactive geographic map displaying Saudi Arabia's refinery locations with capacity and operational details
- **`production-demand-chart.html`** — Testing chart showing refined product production versus demand trends
- **`saudi.html`** — **Primary dashboard** combining multiple energy sector metrics with cycling pages for refined products and natural gas analysis

## 🔄 Cycling Dashboard Features

### Page 1: Refined Products Analysis
- **Production vs Demand**: Interactive line charts showing historical trends
- **Export Data**: Integration of refined product export statistics
- **Surplus/Deficit Analysis**: Real-time calculations and color-coded indicators
- **Statistics**: Average production, demand, surplus, and latest figures

### Page 2: Natural Gas Overview  
- **Production & Consumption**: Daily flow rates in MMSCFD
- **Reserve Capacity**: Converted reserve data (50-year theoretical depletion rate)
- **Unified Scale**: All metrics displayed on same axis for easy comparison
- **Reserve Analytics**: Growth percentages and capacity analysis

### Navigation Controls
- **Arrow Buttons**: Left/right navigation flanking the title
- **Page Indicators**: Small dots showing current page status
- **Smooth Transitions**: Seamless switching between data views

## 📊 Data Sources

**Primary Data Source**: [Saudi Open Data Portal](https://open.data.gov.sa/en/datasets)

All data files are located in the `data/` directory and sourced from the official Saudi Arabia government open data platform:

| File | Description | Purpose |
|------|-------------|---------|
| `Refinery capacities csv.csv` | Refinery infrastructure and capacity data | Mapping refinery locations and processing capabilities |
| `Production of Refined Products csv.csv` | Historical production data for refined petroleum products | Production trend analysis |
| `refined products demand csv.csv` | Domestic and regional demand for refined products | Demand forecasting and supply planning |
| `Exports of Refined Products 2024 csv.csv` | 2024 export statistics for refined petroleum products | Trade analysis and market insights |
| `Exports of Refined products csv.csv` | Historical export data for refined products | Long-term export trend analysis |
| `Reserves, Natural Gas csv.csv` | Natural gas reserves data (converted to MMSCFD equivalent) | Energy resource assessment and capacity planning |
| `Annual natural gas production csv.csv` | Natural gas production data in MMSCFD | Production tracking and trend analysis |
| `Annual Natural Gas Consumption csv.csv` | Natural gas consumption data in MMSCFD | Demand analysis and usage patterns |

## 📈 Enhanced Features

### Interactive Visualizations
- **Interactive Maps**: Explore refinery locations with detailed facility information and hover tooltips
- **Comparative Analytics**: Visualize production vs. demand relationships with intersection highlighting
- **Export Analysis**: Track refined product export patterns and trends
- **Resource Monitoring**: Natural gas reserves, production, and consumption analytics

### Chart Capabilities
- **Dual-Dataset Support**: Switch between refined products and natural gas data
- **Real-time Calculations**: Automatic surplus/deficit computations
- **Consistent Styling**: Unified design language across all visualizations
- **Responsive Design**: Optimized for various screen sizes and devices

### Data Processing
- **Unit Conversions**: Automatic conversion of reserves from BCM to MMSCFD equivalent
- **Temporal Aggregation**: Monthly data aggregated to yearly trends
- **Statistical Analysis**: Average calculations, growth rates, and trend indicators
