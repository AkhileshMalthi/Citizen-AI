# 🔧 API Reference - CitizenAI

Complete API documentation for the CitizenAI platform backend.

## 📋 Table of Contents

- [Authentication](#authentication)
- [Routes Overview](#routes-overview)
- [Endpoint Details](#endpoint-details)
- [Request/Response Examples](#request-response-examples)
- [Error Handling](#error-handling)
- [Rate Limiting](#rate-limiting)

---

## 🔐 Authentication

### **Session-Based Authentication**
CitizenAI uses Flask sessions for user authentication.

```python
# Login required decorator
from functools import wraps

def login_required(f):
    @wraps(f)
    def decorated_function(*args, **kwargs):
        if 'logged_in' not in session:
            return redirect(url_for('login'))
        return f(*args, **kwargs)
    return decorated_function
```

### **Demo Credentials**
- **Username**: `admin`
- **Password**: `password`

---

## 🛣️ Routes Overview

| Endpoint | Method | Auth Required | Description |
|----------|--------|---------------|-------------|
| `/` | GET | No | Landing page |
| `/login` | GET, POST | No | User authentication |
| `/logout` | GET | Yes | User logout |
| `/about` | GET | No | Project information |
| `/services` | GET | No | Services overview |
| `/chat` | GET | Yes | Chat interface |
| `/ask` | POST | Yes | AI question processing |
| `/feedback` | POST | Yes | Sentiment analysis |
| `/concern` | POST | Yes | Issue reporting |
| `/dashboard` | GET | Yes | Analytics dashboard |

---

## 📊 Endpoint Details

### **GET /** - Landing Page
**Description**: Main landing page with project overview.

**Parameters**: None

**Response**: HTML template with navigation and features preview.

```html
<!-- Rendered template -->
<div class="hero-section">
    <h1>Empowering Citizens Through AI</h1>
    <a href="/login" class="cta-button">Get Started</a>
</div>
```

---

### **GET/POST /login** - Authentication

#### **GET /login**
**Description**: Display login form.

**Response**: Login page template.

#### **POST /login**
**Description**: Process user credentials.

**Request Body**:
```json
{
    "username": "admin",
    "password": "password"
}
```

**Response (Success)**:
```python
# Redirect to chat page with session
session['logged_in'] = True
session['username'] = username
return redirect(url_for('chat'))
```

**Response (Error)**:
```html
<!-- Flash message displayed -->
<div class="flash-error">Invalid username or password.</div>
```

---

### **GET /logout** - User Logout
**Description**: Clear user session and redirect to home.

**Authentication**: Required

**Response**:
```python
session.clear()
return redirect(url_for('index'))
```

---

### **GET /chat** - Chat Interface
**Description**: Main chat interface with AI assistant, sentiment analysis, and concern reporting.

**Authentication**: Required

**Response**: Chat template with interactive forms.

```html
<!-- Key sections -->
<section class="chat-section">
    <form method="POST" action="/ask">
        <textarea name="question" required></textarea>
        <button type="submit">Submit Question</button>
    </form>
</section>
```

---

### **POST /ask** - AI Question Processing
**Description**: Process user questions and generate AI responses.

**Authentication**: Required

**Request Body**:
```json
{
    "question": "How do I apply for a business license?"
}
```

**Processing**:
```python
def ask_question():
    question = request.form.get('question', '').strip()
    response = granite_generate_response(question)  # AI processing
    
    # Store in chat history
    chat_entry = {
        'timestamp': datetime.now().strftime('%Y-%m-%d %H:%M:%S'),
        'question': question,
        'response': response
    }
    chat_history.append(chat_entry)
    
    return render_template('chat.html', 
                         question_response=response, 
                         user_question=question)
```

**Response**: Chat template with AI response displayed.

---

### **POST /feedback** - Sentiment Analysis
**Description**: Analyze sentiment of user feedback.

**Authentication**: Required

**Request Body**:
```json
{
    "feedback": "The service was excellent and very helpful!"
}
```

**Processing**:
```python
def submit_feedback():
    feedback_text = request.form.get('feedback', '').strip()
    sentiment = analyze_sentiment(feedback_text)  # 'Positive'/'Neutral'/'Negative'
    
    # Update sentiment counts
    sentiment_data[sentiment.lower()] += 1
    
    return render_template('chat.html', 
                         sentiment=sentiment, 
                         feedback_text=feedback_text)
```

**Sentiment Analysis Logic**:
```python
def analyze_sentiment(text):
    positive_words = ['good', 'great', 'excellent', 'amazing', ...]
    negative_words = ['bad', 'terrible', 'awful', 'horrible', ...]
    
    positive_score = sum(1 for word in positive_words if word in text.lower())
    negative_score = sum(1 for word in negative_words if word in text.lower())
    
    if positive_score > negative_score:
        return 'Positive'
    elif negative_score > positive_score:
        return 'Negative'
    else:
        return 'Neutral'
```

**Response**: Chat template with sentiment result.

---

### **POST /concern** - Issue Reporting
**Description**: Submit and track citizen concerns.

**Authentication**: Required

**Request Body**:
```json
{
    "concern": "The streetlight on Main Street has been broken for weeks."
}
```

**Processing**:
```python
def submit_concern():
    concern_text = request.form.get('concern', '').strip()
    
    concern_entry = {
        'timestamp': datetime.now().strftime('%Y-%m-%d %H:%M:%S'),
        'text': concern_text,
        'status': 'Open'
    }
    concerns.append(concern_entry)
    
    return render_template('chat.html', concern_submitted=True)
```

**Response**: Chat template with confirmation message.

---

### **GET /dashboard** - Analytics Dashboard
**Description**: Real-time analytics and citizen engagement metrics.

**Authentication**: Required

**Data Provided**:
```python
return render_template('dashboard.html', 
                     sentiment_data=sentiment_data,      # {'positive': 5, 'neutral': 2, 'negative': 1}
                     recent_concerns=concerns[-10:],     # Last 10 concerns
                     total_interactions=len(chat_history)) # Total chat interactions
```

**Dashboard Components**:
- Sentiment distribution chart (Chart.js)
- Engagement statistics
- Recent concerns list
- Key insights and recommendations

---

### **GET /about** - Project Information
**Description**: Detailed information about CitizenAI project.

**Authentication**: Not required

**Response**: About page template with project description and features.

---

### **GET /services** - Services Overview
**Description**: Overview of all CitizenAI services and capabilities.

**Authentication**: Not required

**Response**: Services page template with detailed service descriptions.

---

## 📝 Request/Response Examples

### **Complete Chat Interaction Flow**

1. **User Login**:
```bash
curl -X POST http://localhost:5000/login \
  -d "username=admin&password=password" \
  -c cookies.txt
```

2. **Ask Question**:
```bash
curl -X POST http://localhost:5000/ask \
  -d "question=How do I renew my driver's license?" \
  -b cookies.txt
```

3. **Submit Feedback**:
```bash
curl -X POST http://localhost:5000/feedback \
  -d "feedback=The AI assistant was very helpful!" \
  -b cookies.txt
```

4. **Report Concern**:
```bash
curl -X POST http://localhost:5000/concern \
  -d "concern=The online portal is down" \
  -b cookies.txt
```

5. **View Dashboard**:
```bash
curl http://localhost:5000/dashboard -b cookies.txt
```

---

## ⚠️ Error Handling

### **Common Error Responses**

#### **Authentication Required (401)**
```html
<!-- Redirects to login page -->
<script>window.location.href='/login';</script>
```

#### **Missing Form Data (400)**
```html
<div class="error-message">
    Please enter a question.
</div>
```

#### **Server Error (500)**
```html
<div class="error-message">
    I apologize, but I'm experiencing technical difficulties. 
    Please try again later.
</div>
```

### **Error Handling in Code**
```python
try:
    response = granite_generate_response(question)
except Exception as e:
    app.logger.error(f"AI generation error: {e}")
    response = "I'm currently experiencing technical difficulties. Please try again."
```

---

## 🚫 Rate Limiting

### **Current Implementation**
- No explicit rate limiting (demo version)
- Session-based access control
- In-memory storage limitations

### **Production Recommendations**
```python
from flask_limiter import Limiter
from flask_limiter.util import get_remote_address

limiter = Limiter(
    app,
    key_func=get_remote_address,
    default_limits=["200 per day", "50 per hour"]
)

@app.route('/ask', methods=['POST'])
@limiter.limit("10 per minute")
def ask_question():
    # Implementation
```

---

## 📊 Data Models

### **Chat History Entry**
```python
chat_entry = {
    'timestamp': '2025-06-29 14:30:00',
    'question': 'User question text',
    'response': 'AI generated response'
}
```

### **Sentiment Data**
```python
sentiment_data = {
    'positive': 15,    # Count of positive feedback
    'neutral': 8,      # Count of neutral feedback  
    'negative': 3      # Count of negative feedback
}
```

### **Concern Entry**
```python
concern_entry = {
    'timestamp': '2025-06-29 14:30:00',
    'text': 'User concern description',
    'status': 'Open'   # 'Open', 'In Progress', 'Resolved'
}
```

---

## 🔧 Development Notes

### **AI Model Integration**
```python
# Model initialization with error handling
def initialize_model():
    global tokenizer, model, device
    
    try:
        device = "cuda" if torch.cuda.is_available() else "cpu"
        tokenizer = AutoTokenizer.from_pretrained(model_path)
        
        if device == "cuda":
            # GPU with quantization
            model = AutoModelForCausalLM.from_pretrained(
                model_path,
                quantization_config=quantization_config,
                device_map="auto"
            )
        else:
            # CPU fallback
            model = AutoModelForCausalLM.from_pretrained(model_path)
        
        return True
    except Exception as e:
        print(f"Model initialization failed: {e}")
        return False
```

### **Template Rendering**
```python
# All routes use Flask template rendering
return render_template('template_name.html', 
                     variable1=value1,
                     variable2=value2)
```

---

## 🧪 Testing the API

### **Manual Testing Checklist**
- [ ] Load landing page (`/`)
- [ ] Login with demo credentials (`/login`)
- [ ] Ask AI questions (`/ask`)
- [ ] Submit feedback for sentiment analysis (`/feedback`) 
- [ ] Report concerns (`/concern`)
- [ ] View dashboard analytics (`/dashboard`)
- [ ] Navigate to about/services pages
- [ ] Logout and verify session cleared (`/logout`)

### **Automated Testing Example**
```python
import requests

def test_login():
    session = requests.Session()
    
    # Login
    response = session.post('http://localhost:5000/login', 
                          data={'username': 'admin', 'password': 'password'})
    assert response.status_code == 302  # Redirect after login
    
    # Access protected route
    response = session.get('http://localhost:5000/dashboard')
    assert response.status_code == 200
    assert 'Citizen Insights Dashboard' in response.text
```

---

*This API reference provides complete documentation for integrating with and extending the CitizenAI platform.*
