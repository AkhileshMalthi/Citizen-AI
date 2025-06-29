# CitizenAI Setup and Installation Guide

## Quick Start

### 1. Install Dependencies
```powershell
# Create virtual environment (recommended)
python -m venv venv
.\venv\Scripts\Activate.ps1

# Install required packages
pip install -r requirements.txt
```

### 2. Run the Application
```powershell
python app.py
```

### 3. Access the Application
Open your browser and navigate to: `http://localhost:5000`

### 4. Login Credentials
- Username: `admin`
- Password: `password`

## Project Structure
```
CitizenAI/
├── app.py                 # Main Flask application
├── requirements.txt       # Python dependencies
├── templates/            # HTML templates
│   ├── index.html        # Landing page
│   ├── login.html        # Login page
│   ├── about.html        # About page
│   ├── services.html     # Services page
│   ├── chat.html         # Chat interface
│   └── dashboard.html    # Analytics dashboard
├── static/              # Static assets
│   ├── css/
│   │   └── styles.css   # Main stylesheet
│   ├── Images/          # Image assets
│   └── Favicon/         # Favicon files
└── README.md            # Project documentation
```

## Features Implemented

### ✅ Phase 1: Project Setup and Architecture
- [x] Project structure created
- [x] Dependencies defined in requirements.txt
- [x] Flask application framework set up
- [x] IBM Granite model integration prepared

### ✅ Phase 2: Core Backend Functionalities
- [x] Flask routes implemented
- [x] User authentication system
- [x] AI model integration with IBM Granite
- [x] Sentiment analysis functionality
- [x] Concern reporting system
- [x] In-memory data storage

### ✅ Phase 3: Frontend Development
- [x] HTML templates for all pages
- [x] Modern CSS styling with gradients and animations
- [x] Responsive design for mobile/desktop
- [x] Interactive forms and user interfaces
- [x] Dashboard with Chart.js integration

### ✅ Phase 4: Integration and Testing
- [x] Backend-frontend integration complete
- [x] Form handling and data flow
- [x] Error handling and flash messages
- [x] Session management

## Key Features

1. **🤖 AI Chat Assistant**
   - Real-time conversational AI using IBM Granite
   - Government service inquiries
   - Natural language processing

2. **🧠 Sentiment Analysis**
   - Automatic sentiment classification
   - Positive/Neutral/Negative categorization
   - Real-time feedback processing

3. **📊 Analytics Dashboard**
   - Interactive charts with Chart.js
   - Sentiment visualization
   - Concern tracking
   - Engagement metrics

4. **⚠️ Concern Reporting**
   - Issue submission system
   - Timestamp tracking
   - Status management

5. **🔐 User Authentication**
   - Login/logout functionality
   - Session management
   - Protected routes

## Hardware Requirements

### Minimum (CPU-only):
- 16GB RAM
- Intel i5 or AMD Ryzen 5
- 5GB free disk space

### Recommended (GPU):
- 16GB+ RAM
- NVIDIA GPU with 8GB+ VRAM
- CUDA-compatible graphics card

## Troubleshooting

### Model Loading Issues
If the IBM Granite model fails to load:
1. Check internet connection (first-time download)
2. Ensure sufficient RAM/VRAM
3. The app will use fallback responses if model initialization fails

### Dependencies
If you encounter package installation issues:
```powershell
pip install --upgrade pip
pip install torch --index-url https://download.pytorch.org/whl/cu118
pip install -r requirements.txt
```

## Next Steps for Production

1. **Database Integration**
   - Replace in-memory storage with PostgreSQL/MySQL
   - Add data persistence
   - Implement proper user management

2. **Security Enhancements**
   - Environment variables for secrets
   - Proper password hashing
   - CSRF protection
   - Rate limiting

3. **Scalability**
   - Redis for session storage
   - Load balancing
   - Docker containerization
   - Cloud deployment (AWS/Azure/GCP)

4. **Additional Features**
   - Email notifications
   - Multi-language support
   - Advanced analytics
   - API endpoints
   - Mobile app integration

## Technologies Used

- **Backend**: Python 3.10, Flask
- **AI/ML**: PyTorch, Transformers, IBM Granite
- **Frontend**: HTML5, CSS3, JavaScript
- **Charts**: Chart.js
- **Styling**: Modern CSS with animations and gradients
