# MoMo SMS Data Processing System

## Team Information
**Team Name :** Blue  
**Course :** Enterprise Web Development  

## Team Members
1. [**Winebald Banituze**](https://github.com/banituze) - Backend Development & ETL Pipeline
2. [**Marie Anne Orphelie Perrine**](https://github.com/OrpheliePerrine) - Frontend Development & UI/UX
3. [**Nadia Akua Nsiah Odame**](https://github.com/Nadia-Odame) - Database Architecture & API Development
4. [**Chisom Louisa Obueze**](http://github.com/Chijoan) - Data Analytics & Visualization

## Project Description
An enterprise-level fullstack application designed to process MTN Mobile Money (MoMo) SMS transaction data in XML format. The system implements a comprehensive ETL (Extract, Transform, Load) pipeline that cleanses and categorizes financial transaction data, stores it in a relational database, and provides an interactive analytics dashboard for data visualization and business intelligence.

### Core Functionality
- **XML Data Processing** : Parse and validate MoMo SMS transaction data
- **Data Transformation** : Clean, normalize, and categorize transaction records
- **Relational Storage** : Persist structured data in SQLite with referential integrity
- **Analytics Dashboard** : Interactive frontend for transaction analysis and visualization
- **API Layer** : RESTful endpoints for programmatic data access

### Technology Stack
**Backend :**
- Python 3.x
- lxml/ElementTree for XML parsing
- SQLite3 for database management
- FastAPI for API development

**Frontend :**
- HTML5/CSS3
- Vanilla JavaScript
- Chart.js/D3.js for data visualization

**Development Tools :**
- Git & GitHub for version control
- PlantUML for system architecture
- GitHub Projects for Agile workflow

## System Architecture
[View High-Level Architecture Diagram](docs/architecture.png)

The system follows a modular ETL architecture with clear separation of concerns:
1. **Extraction Layer** : XML parsing and validation
2. **Transformation Layer** : Data cleaning, normalization, and categorization
3. **Loading Layer** : Database persistence and indexing
4. **Presentation Layer** : Analytics dashboard and API endpoints

## Project Structure
```
.
├── .env.example                      # DATABASE_URL or path to SQLite
├── requirements.txt                  # lxml/ElementTree, dateutil, etc.
├── index.html                        # Dashboard entry (static)
├── web/
│   ├── styles.css                    # Dashboard styling
│   ├── chart_handler.js              # Fetch + render charts/tables
│   └── assets/                       # Images/icons 
├── data/
│   ├── raw/                          # Provided XML input 
│   │   └── momo.xml
│   ├── processed/                    # Cleaned/derived outputs for frontend
│   │   └── dashboard.json            # Aggregates the dashboard reads
│   ├── db.sqlite3                    # SQLite DB file
│   └── logs/
│       ├── etl.log                   # Structured ETL logs
│       └── dead_letter/              # Unparsed/ignored XML snippets
├── etl/
│   ├── __init__.py
│   ├── config.py                     # File paths, thresholds, categories
│   ├── parse_xml.py                  # XML parsing (ElementTree/lxml)
│   ├── clean_normalize.py            # Amounts, dates, phone normalization
│   ├── categorize.py                 # Simple rules for transaction types
│   ├── load_db.py                    # Create tables + upsert to SQLite
│   └── run.py                        # CLI: parse -> clean -> categorize -> load -> export JSON
├── api/                              
│   ├── __init__.py
│   ├── app.py                        # Minimal FastAPI with /transactions, /analytics
│   ├── db.py                         # SQLite connection helpers
│   └── schemas.py                    # Pydantic response models
├── scripts/
│   ├── run_etl.sh                    # python etl/run.py --xml data/raw/momo.xml
│   ├── export_json.sh                # Rebuild data/processed/dashboard.json
│   └── serve_frontend.sh             # python -m http.server 8000 (or Flask static)
├── tests/
│   ├── test_parse_xml.py             # Small unit tests
│   ├── test_clean_normalize.py
│   └── test_categorize.py
└── docs/
    └── architecture.png              # System architecture diagram
```

## Getting Started

### Prerequisites
- Python 3.8+
- pip package manager
- Git

### Installation
```bash
# Clone the repository
git clone https://github.com/banituze/momo-sms.git
cd momo-sms

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Set up environment variables
cp .env.example .env
# Edit .env with your configuration
```

### Running the ETL Pipeline
```bash
# Process XML data
bash scripts/run_etl.sh

# Export dashboard data
bash scripts/export_json.sh
```

### Launching the Dashboard
```bash
# Start local server
bash scripts/serve_frontend.sh

# Access dashboard at http://localhost:8000
```

## Development Workflow

### Agile Methodology
We follow Scrum practices with 1-week sprints:
- **Daily Standups** : Team synchronization
- **Sprint Planning** : Task breakdown and assignment
- **Sprint Review** : Deliverable demonstration
- **Sprint Retrospective** : Process improvement

### Scrum Board
[View Team Scrum Board](https://github.com/users/banituze/projects/3)