---
layout: default
title: CitizenAI Documentation
---

<style>
/* Custom CSS for CitizenAI Documentation */
:root {
  --primary-color: #0366d6;
  --secondary-color: #28a745;
  --accent-color: #f39c12;
  --background-color: #ffffff;
  --text-color: #24292e;
  --border-color: #e1e4e8;
  --code-background: #f6f8fa;
}

body {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', 'Oxygen', 'Ubuntu', 'Cantarell', sans-serif;
  line-height: 1.6;
  color: var(--text-color);
}

h1, h2, h3, h4, h5, h6 {
  font-weight: 600;
  line-height: 1.25;
  margin-top: 24px;
  margin-bottom: 16px;
}

h1 {
  font-size: 2em;
  border-bottom: 1px solid var(--border-color);
  padding-bottom: 0.3em;
}

h2 {
  font-size: 1.5em;
  border-bottom: 1px solid var(--border-color);
  padding-bottom: 0.3em;
}

table {
  border-collapse: collapse;
  width: 100%;
  margin: 16px 0;
  overflow: auto;
}

table th, table td {
  padding: 12px 16px;
  border: 1px solid var(--border-color);
  text-align: left;
}

table th {
  background-color: var(--code-background);
  font-weight: 600;
}

table tr:nth-child(even) {
  background-color: rgba(0, 0, 0, 0.02);
}

pre {
  background-color: var(--code-background);
  border-radius: 6px;
  padding: 16px;
  overflow: auto;
  border: 1px solid var(--border-color);
}

code {
  background-color: var(--code-background);
  padding: 2px 4px;
  border-radius: 3px;
  font-size: 85%;
}

details {
  margin: 16px 0;
  border: 1px solid var(--border-color);
  border-radius: 6px;
}

summary {
  padding: 12px 16px;
  cursor: pointer;
  background-color: var(--code-background);
  border-radius: 6px 6px 0 0;
  font-weight: 600;
}

details[open] summary {
  border-bottom: 1px solid var(--border-color);
}

details > *:not(summary) {
  padding: 0 16px 16px;
}

blockquote {
  padding: 16px;
  margin: 16px 0;
  color: #6a737d;
  border-left: 4px solid var(--primary-color);
  background-color: var(--code-background);
  border-radius: 0 6px 6px 0;
}

.main-content {
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem;
}

@media (max-width: 768px) {
  table {
    font-size: 14px;
    overflow-x: auto;
  }
  
  .main-content {
    padding: 1rem;
  }
  
  h1 { font-size: 1.75em; }
  h2 { font-size: 1.375em; }
}
</style>

<div align="center">

# 🤖 CitizenAI Documentation

**Intelligent Citizen Engagement Platform**

[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-Live-brightgreen)](https://your-username.github.io/CitizenAI)
[![Python](https://img.shields.io/badge/Python-3.11+-blue)](https://python.org)
[![Flask](https://img.shields.io/badge/Flask-3.0+-green)](https://flask.palletsprojects.com)
[![AI Model](https://img.shields.io/badge/AI-IBM%20Granite-orange)](https://huggingface.co/ibm-granite)

*Empowering citizens through AI-driven engagement and real-time analytics*

</div>

---

## 📋 Table of Contents

- [🎯 Overview](#-overview)
- [✨ Key Features](#-key-features)
- [🏗️ Project Structure](#️-project-structure)
- [🚀 Quick Start](#-quick-start)
- [🔧 Installation](#-installation)
- [📊 API Documentation](#-api-documentation)
- [🤖 AI Integration](#-ai-integration)
- [🧠 Sentiment Analysis](#-sentiment-analysis)
- [📈 Analytics Dashboard](#-analytics-dashboard)
- [⚠️ Concern Reporting](#️-concern-reporting)
- [🛠️ Development](#️-development)
- [🚢 Deployment](#-deployment)
- [📚 Additional Resources](#-additional-resources)
- [🤝 Contributing](#-contributing)
- [📄 License](#-license)

---

## 🎯 Overview

**CitizenAI** is an intelligent citizen engagement platform that leverages advanced AI technologies to facilitate seamless communication between citizens and government services. Built with Flask and powered by IBM's Granite language model, it provides real-time sentiment analysis, concern reporting, and comprehensive analytics.

### 🌟 Why CitizenAI?

> **Bridging the gap between citizens and government through intelligent automation**

- **🔍 Real-time Analysis**: Instant sentiment processing and feedback categorization
- **🤖 AI-Powered Chat**: Natural language interaction with government services
- **📊 Comprehensive Analytics**: Data-driven insights for better governance
- **⚡ Modern Architecture**: Scalable, responsive, and user-friendly design

---

## ✨ Key Features

<table>
<tr>
<td width="50%">

### 🎪 **User Experience**
- ✅ Intuitive chat interface
- ✅ Real-time feedback processing
- ✅ Mobile-responsive design
- ✅ Secure authentication system

</td>
<td width="50%">

### 🧠 **AI & Analytics**
- ✅ IBM Granite LLM integration
- ✅ Sentiment analysis engine
- ✅ Interactive data visualization
- ✅ Automated report generation

</td>
</tr>
<tr>
<td width="50%">

### 🔧 **Technical Stack**
- ✅ Flask web framework
- ✅ PyTorch & Transformers
- ✅ Chart.js visualizations
- ✅ Modern CSS3 styling

</td>
<td width="50%">

### 🚀 **Deployment Ready**
- ✅ Docker containerization
- ✅ Environment configuration
- ✅ Production optimizations
- ✅ Scalable architecture

</td>
</tr>
</table>

---

## 🏗️ Project Structure

```
CitizenAI/
├── 📁 docs/                    # 📚 Documentation files
│   ├── README.md              # 📖 Main documentation
│   ├── SETUP.md               # ⚙️ Installation guide
│   ├── BUILD_PROGRESS.md      # 🏗️ Development timeline
│   └── DASHBOARD_FIXES.md     # 🔧 Technical fixes
├── 📁 templates/              # 🖼️ HTML templates
│   ├── index.html             # 🏠 Landing page
│   ├── login.html             # 🔐 Authentication
│   ├── chat.html              # 💬 AI interaction
│   ├── dashboard.html         # 📊 Analytics
│   ├── about.html             # ℹ️ Project info
│   └── services.html          # 🛠️ Services overview
├── 📁 static/                 # 🎨 Static assets
│   ├── css/styles.css         # 🎭 Main stylesheet
│   ├── Images/                # 🖼️ Image assets
│   └── Favicon/               # 🔖 Favicon files
├── 📄 app.py                  # 🚀 Main Flask application
├── 📄 app_demo.py             # 🎮 Demo version
├── 📄 requirements.txt        # 📦 Python dependencies
└── 📄 README.md               # 📋 Project overview
```

---

## 🚀 Quick Start

### Prerequisites

Before you begin, ensure you have the following installed:

- **Python 3.11+** 🐍
- **Git** 📥
- **pip** 📦

### 🎯 One-Minute Setup

```bash
# 1️⃣ Clone the repository
git clone https://github.com/your-username/CitizenAI.git
cd CitizenAI

# 2️⃣ Install dependencies
pip install -r requirements.txt

# 3️⃣ Run the application
python app_demo.py  # For demo version
# OR
python app.py       # For full AI version

# 4️⃣ Open your browser
# Navigate to: http://localhost:5000
```

### 🔑 Demo Credentials

| Username | Password | Access Level |
|----------|----------|--------------|
| `admin` | `password` | Full Access |

---

## 🔧 Installation

### Option 1: Standard Installation

<details>
<summary>🔽 Click to expand detailed installation steps</summary>

#### Step 1: Environment Setup
```bash
# Create virtual environment
python -m venv venv

# Activate virtual environment
# Windows:
venv\Scripts\activate
# Linux/Mac:
source venv/bin/activate
```

#### Step 2: Install Dependencies
```bash
pip install --upgrade pip
pip install -r requirements.txt
```

#### Step 3: Verify Installation
```bash
python -c "import flask, torch, transformers; print('✅ All dependencies installed successfully!')"
```

</details>

### Option 2: Docker Installation

<details>
<summary>🔽 Click to expand Docker setup</summary>

```bash
# Build Docker image
docker build -t citizenai .

# Run container
docker run -p 5000:5000 citizenai

# Access application at http://localhost:5000
```

</details>

---

## 📊 API Documentation

### 🛠️ Main Endpoints

<div align="center">

| Endpoint | Method | Description | Auth Required | Response |
|----------|--------|-------------|---------------|----------|
| `/` | `GET` | 🏠 Landing page | ❌ | HTML |
| `/login` | `GET/POST` | 🔐 User authentication | ❌ | HTML/JSON |
| `/logout` | `GET` | 🚪 User logout | ✅ | Redirect |
| `/chat` | `GET` | 💬 Chat interface | ✅ | HTML |
| `/ask` | `POST` | 🤖 AI question processing | ✅ | JSON |
| `/feedback` | `POST` | 📝 Sentiment analysis | ✅ | JSON |
| `/concern` | `POST` | ⚠️ Issue reporting | ✅ | JSON |
| `/dashboard` | `GET` | 📊 Analytics dashboard | ✅ | HTML |
| `/about` | `GET` | ℹ️ Project information | ❌ | HTML |
| `/services` | `GET` | 🛠️ Services overview | ❌ | HTML |

</div>

### 📋 Request/Response Examples

<details>
<summary>🔽 View API Examples</summary>

#### Chat Request
```json
POST /ask
{
  "message": "How do I apply for a business license?"
}
```

#### Chat Response
```json
{
  "response": "To apply for a business license, you need to...",
  "timestamp": "2025-06-29T14:30:00Z"
}
```

#### Feedback Request
```json
POST /feedback
{
  "feedback": "The service was excellent and very helpful!"
}
```

#### Feedback Response
```json
{
  "sentiment": "Positive",
  "confidence": 0.95,
  "message": "Thank you for your feedback!"
}
```

</details>

---

## 🤖 AI Integration

### 🧠 IBM Granite Model

<div align="center">

| Feature | Specification | Status |
|---------|---------------|--------|
| **Model** | `ibm-granite/granite-3.0-3b-a800m-instruct` | ✅ Active |
| **Quantization** | 4-bit for memory efficiency | ✅ Optimized |
| **Device Support** | Auto GPU/CPU detection | ✅ Adaptive |
| **Fallback** | Demo responses when unavailable | ✅ Resilient |

</div>

### 🔧 Configuration

```python
# Model Configuration
MODEL_CONFIG = {
    "model_name": "ibm-granite/granite-3.0-3b-a800m-instruct",
    "quantization": "4bit",
    "max_tokens": 512,
    "temperature": 0.7,
    "device": "auto"  # GPU if available, else CPU
}
```

### 🎯 Key Capabilities

- 🌍 **Multi-language Support**: English, Spanish, French
- 🏛️ **Government Context**: Trained on civic and administrative data
- ⚡ **Real-time Processing**: Sub-second response times
- 🛡️ **Safety Filters**: Content moderation and bias detection

---

## 🧠 Sentiment Analysis

### 📈 Analysis Engine

Our sentiment analysis engine provides real-time emotional intelligence for citizen feedback.

<div align="center">

| Sentiment | Threshold | Color | Example Keywords |
|-----------|-----------|-------|------------------|
| 😊 **Positive** | > 0.1 | 🟢 Green | excellent, great, helpful, satisfied |
| 😐 **Neutral** | -0.1 to 0.1 | 🟡 Yellow | okay, average, standard, normal |
| 😞 **Negative** | < -0.1 | 🔴 Red | terrible, awful, frustrated, disappointed |

</div>

### 💡 Implementation

<details>
<summary>🔽 View Sentiment Analysis Code</summary>

```python
def analyze_sentiment(text):
    """
    Analyze sentiment using keyword-based approach
    
    Args:
        text (str): Input text to analyze
        
    Returns:
        dict: Sentiment classification and confidence
    """
    positive_words = [
        'good', 'great', 'excellent', 'amazing', 'helpful',
        'satisfied', 'love', 'awesome', 'perfect', 'outstanding'
    ]
    
    negative_words = [
        'bad', 'terrible', 'awful', 'horrible', 'hate',
        'frustrated', 'angry', 'disappointed', 'worst', 'useless'
    ]
    
    text_lower = text.lower()
    positive_count = sum(1 for word in positive_words if word in text_lower)
    negative_count = sum(1 for word in negative_words if word in text_lower)
    
    score = positive_count - negative_count
    
    if score > 0:
        return {'sentiment': 'Positive', 'confidence': min(score * 0.3, 1.0)}
    elif score < 0:
        return {'sentiment': 'Negative', 'confidence': min(abs(score) * 0.3, 1.0)}
    else:
        return {'sentiment': 'Neutral', 'confidence': 0.5}
```

</details>

---

## 📈 Analytics Dashboard

### 🎨 Visualization Components

<table>
<tr>
<td width="50%">

#### 📊 **Sentiment Distribution**
- Interactive doughnut chart
- Real-time data updates
- Percentage breakdowns
- Color-coded categories

</td>
<td width="50%">

#### 📈 **Engagement Metrics**
- Total interactions counter
- Trend analysis
- Peak usage hours
- User activity patterns

</td>
</tr>
<tr>
<td width="50%">

#### ⚠️ **Issue Tracking**
- Recent concerns display
- Status indicators
- Priority levels
- Resolution timeline

</td>
<td width="50%">

#### 💡 **Key Insights**
- Automated analysis
- Actionable recommendations
- Performance indicators
- Predictive trends

</td>
</tr>
</table>

### 🎯 Dashboard Features

- ✅ **Real-time Updates**: Live data synchronization
- ✅ **Responsive Design**: Mobile and desktop optimized
- ✅ **Interactive Charts**: Hover effects and tooltips
- ✅ **Export Capabilities**: PDF and CSV download options

---

## ⚠️ Concern Reporting

### 📝 Issue Management System

Our comprehensive issue tracking system ensures no citizen concern goes unaddressed.

<div align="center">

| Status | Description | Color | Action Required |
|--------|-------------|-------|-----------------|
| 🔴 **Open** | Newly submitted concern | Red | Review & Assign |
| 🟡 **In Progress** | Currently being addressed | Yellow | Monitor Progress |
| 🟢 **Resolved** | Issue has been resolved | Green | Follow-up |
| 🔵 **Closed** | Completed and verified | Blue | Archive |

</div>

### 📊 Data Structure

<details>
<summary>🔽 View Concern Data Model</summary>

```python
concern_schema = {
    "id": "unique_identifier",
    "timestamp": "2025-06-29T14:30:00Z",
    "user_id": "citizen_identifier",
    "category": "infrastructure|services|policy|other",
    "priority": "low|medium|high|urgent",
    "status": "open|in_progress|resolved|closed",
    "title": "Brief description",
    "description": "Detailed concern text",
    "location": "optional_location_data",
    "attachments": ["file_paths"],
    "assigned_to": "staff_member_id",
    "resolution_notes": "action_taken",
    "citizen_satisfaction": "rating_1_to_5"
}
```

</details>

---

## 🛠️ Development

### 🏗️ Development Environment

<div align="center">

| Component | Version | Purpose |
|-----------|---------|---------|
| **Python** | 3.11+ | Core runtime |
| **Flask** | 3.0+ | Web framework |
| **PyTorch** | 2.0+ | AI/ML operations |
| **Transformers** | 4.30+ | Model handling |
| **Chart.js** | 4.0+ | Data visualization |

</div>

### 🧪 Running Tests

```bash
# Run all tests
python -m pytest tests/

# Run specific test categories
python -m pytest tests/test_api.py       # API tests
python -m pytest tests/test_ai.py        # AI integration tests
python -m pytest tests/test_frontend.py  # Frontend tests

# Run with coverage
python -m pytest --cov=app tests/
```

### 🔍 Code Quality

```bash
# Linting
flake8 app.py
pylint app.py

# Formatting
black app.py
isort app.py

# Type checking
mypy app.py
```

---

## 🚢 Deployment

### 🌐 Production Deployment

<details>
<summary>🔽 View Deployment Options</summary>

#### Option 1: Traditional Server

```bash
# Install production server
pip install gunicorn

# Run with Gunicorn
gunicorn --bind 0.0.0.0:8000 app:app

# With multiple workers
gunicorn --workers 4 --bind 0.0.0.0:8000 app:app
```

#### Option 2: Docker Deployment

```dockerfile
FROM python:3.11-slim

WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .
EXPOSE 5000

CMD ["gunicorn", "--bind", "0.0.0.0:5000", "app:app"]
```

#### Option 3: Cloud Platforms

- **Heroku**: `git push heroku main`
- **AWS**: Use EC2 or ECS
- **Google Cloud**: App Engine or Cloud Run
- **Azure**: App Service

</details>

### 🔒 Security Considerations

- 🔐 **Environment Variables**: Store sensitive data securely
- 🛡️ **CSRF Protection**: Implement Flask-WTF
- 🔍 **Input Validation**: Sanitize all user inputs
- 📝 **Logging**: Comprehensive audit trails
- 🚫 **Rate Limiting**: Prevent abuse and DoS attacks

---

## 📚 Additional Resources

### 📖 Documentation Links

- **[📋 Setup Guide](SETUP.md)** - Detailed installation instructions
- **[🏗️ Build Progress](BUILD_PROGRESS.md)** - Development timeline and milestones
- **[🚀 Deployment Guide](DEPLOYMENT.md)** - Production deployment instructions
- **[🔧 API Reference](API_REFERENCE.md)** - Complete API documentation
- **[🐛 Dashboard Fixes](DASHBOARD_FIXES.md)** - Troubleshooting guide

### 🔗 External Resources

- [Flask Documentation](https://flask.palletsprojects.com/)
- [IBM Granite Model](https://huggingface.co/ibm-granite)
- [Chart.js Documentation](https://www.chartjs.org/docs/)
- [PyTorch Documentation](https://pytorch.org/docs/)

---

## 🤝 Contributing

We welcome contributions from the community! Here's how you can help:

### 🎯 How to Contribute

1. **🍴 Fork** the repository
2. **🌿 Create** a feature branch (`git checkout -b feature/amazing-feature`)
3. **💻 Commit** your changes (`git commit -m 'Add amazing feature'`)
4. **📤 Push** to the branch (`git push origin feature/amazing-feature`)
5. **🔄 Open** a Pull Request

### 📝 Contribution Guidelines

- Follow the existing code style
- Write clear commit messages
- Add tests for new features
- Update documentation as needed
- Ensure all tests pass

### 🐛 Reporting Issues

Found a bug? Please create an issue with:

- Clear description of the problem
- Steps to reproduce
- Expected vs actual behavior
- System information (OS, Python version, etc.)

---

## 📄 License

This project is licensed under the **MIT License** - see the [LICENSE](../LICENSE) file for details.

### 🙏 Acknowledgments

- **IBM** for the Granite language model
- **Flask** community for the excellent web framework
- **Chart.js** for beautiful data visualizations
- **Open Source Community** for inspiration and support

---

<div align="center">

### 🚀 Ready to Get Started?

[![Deploy to Heroku](https://img.shields.io/badge/Deploy%20to-Heroku-purple)](https://heroku.com/deploy)
[![Run on Google Cloud](https://img.shields.io/badge/Run%20on-Google%20Cloud-blue)](https://cloud.google.com)
[![Deploy on Railway](https://img.shields.io/badge/Deploy%20on-Railway-green)](https://railway.app)

---

**Built with ❤️ for better citizen engagement**

*Last Updated: June 29, 2025*  
*CitizenAI - Empowering Citizens Through AI* 🤖

</div>
