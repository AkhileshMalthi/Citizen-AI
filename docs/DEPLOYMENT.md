# 🚀 Deployment Guide - CitizenAI

This guide covers deploying CitizenAI from development to production environments.

## 📋 Pre-Deployment Checklist

### ✅ **Development Complete**
- [ ] All features tested locally
- [ ] Documentation updated
- [ ] Error handling implemented
- [ ] Security measures in place

### ✅ **Production Ready**
- [ ] Environment variables configured
- [ ] Database setup complete
- [ ] SSL certificates obtained
- [ ] Domain name configured

---

## 🌍 Deployment Options

### 1. **Local/On-Premise Deployment**

#### **System Requirements**
- **OS**: Ubuntu 20.04+ / Windows Server 2019+ / CentOS 8+
- **RAM**: 16GB minimum (32GB recommended for AI models)
- **CPU**: 8 cores minimum
- **GPU**: NVIDIA GPU with 8GB+ VRAM (optional but recommended)
- **Storage**: 50GB minimum SSD space

#### **Installation Steps**
```bash
# 1. Clone repository
git clone <repository-url>
cd CitizenAI

# 2. Create virtual environment
python -m venv venv
source venv/bin/activate  # Linux/Mac
# or
venv\Scripts\activate     # Windows

# 3. Install dependencies
pip install -r requirements.txt

# 4. Set environment variables
export FLASK_ENV=production
export SECRET_KEY="your-secure-secret-key"
export DATABASE_URL="postgresql://user:pass@localhost/citizenai"

# 5. Initialize database
python init_db.py

# 6. Run with production server
gunicorn --bind 0.0.0.0:5000 app:app
```

### 2. **Cloud Deployment (AWS)**

#### **AWS Setup**
```bash
# 1. Create EC2 instance
aws ec2 run-instances \
  --image-id ami-0abcdef1234567890 \
  --count 1 \
  --instance-type t3.large \
  --key-name your-key-pair

# 2. Setup RDS database
aws rds create-db-instance \
  --db-instance-identifier citizenai-db \
  --db-instance-class db.t3.micro \
  --engine postgres

# 3. Configure security groups
aws ec2 create-security-group \
  --group-name citizenai-sg \
  --description "CitizenAI security group"
```

#### **Docker Deployment**
```dockerfile
# Dockerfile
FROM python:3.11-slim

WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt

COPY . .
EXPOSE 5000

CMD ["gunicorn", "--bind", "0.0.0.0:5000", "app:app"]
```

```bash
# Build and run
docker build -t citizenai .
docker run -p 5000:5000 citizenai
```

### 3. **Kubernetes Deployment**

#### **K8s Configuration**
```yaml
# deployment.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: citizenai
spec:
  replicas: 3
  selector:
    matchLabels:
      app: citizenai
  template:
    metadata:
      labels:
        app: citizenai
    spec:
      containers:
      - name: citizenai
        image: citizenai:latest
        ports:
        - containerPort: 5000
        env:
        - name: DATABASE_URL
          valueFrom:
            secretKeyRef:
              name: citizenai-secrets
              key: database-url
---
apiVersion: v1
kind: Service
metadata:
  name: citizenai-service
spec:
  selector:
    app: citizenai
  ports:
  - port: 80
    targetPort: 5000
  type: LoadBalancer
```

---

## 🔒 Security Configuration

### **Environment Variables**
```bash
# Production environment variables
export FLASK_ENV=production
export SECRET_KEY="your-256-bit-secret-key"
export DATABASE_URL="postgresql://user:pass@host:5432/citizenai"
export JWT_SECRET_KEY="your-jwt-secret"
export MAIL_SERVER="smtp.gmail.com"
export MAIL_PORT=587
export MAIL_USERNAME="your-email@domain.com"
export MAIL_PASSWORD="your-app-password"
export REDIS_URL="redis://localhost:6379"
```

### **SSL/TLS Setup**
```bash
# Using Let's Encrypt with Certbot
sudo apt install certbot python3-certbot-nginx
sudo certbot --nginx -d yourdomain.com
```

### **Nginx Configuration**
```nginx
# /etc/nginx/sites-available/citizenai
server {
    listen 80;
    server_name yourdomain.com;
    return 301 https://$server_name$request_uri;
}

server {
    listen 443 ssl;
    server_name yourdomain.com;
    
    ssl_certificate /etc/letsencrypt/live/yourdomain.com/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/yourdomain.com/privkey.pem;
    
    location / {
        proxy_pass http://127.0.0.1:5000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```

---

## 🗄️ Database Migration

### **PostgreSQL Setup**
```sql
-- Create database
CREATE DATABASE citizenai;
CREATE USER citizenai_user WITH PASSWORD 'secure_password';
GRANT ALL PRIVILEGES ON DATABASE citizenai TO citizenai_user;

-- Create tables
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    username VARCHAR(80) UNIQUE NOT NULL,
    email VARCHAR(120) UNIQUE NOT NULL,
    password_hash VARCHAR(255) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE chat_history (
    id SERIAL PRIMARY KEY,
    user_id INTEGER REFERENCES users(id),
    question TEXT NOT NULL,
    response TEXT NOT NULL,
    timestamp TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE sentiment_feedback (
    id SERIAL PRIMARY KEY,
    user_id INTEGER REFERENCES users(id),
    feedback_text TEXT NOT NULL,
    sentiment VARCHAR(20) NOT NULL,
    timestamp TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE concerns (
    id SERIAL PRIMARY KEY,
    user_id INTEGER REFERENCES users(id),
    concern_text TEXT NOT NULL,
    status VARCHAR(20) DEFAULT 'Open',
    timestamp TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### **Migration Script**
```python
# migrate_data.py
import psycopg2
from app import app, chat_history, sentiment_data, concerns

def migrate_to_database():
    conn = psycopg2.connect(DATABASE_URL)
    cur = conn.cursor()
    
    # Migrate chat history
    for entry in chat_history:
        cur.execute(
            "INSERT INTO chat_history (question, response, timestamp) VALUES (%s, %s, %s)",
            (entry['question'], entry['response'], entry['timestamp'])
        )
    
    # Migrate concerns
    for concern in concerns:
        cur.execute(
            "INSERT INTO concerns (concern_text, status, timestamp) VALUES (%s, %s, %s)",
            (concern['text'], concern['status'], concern['timestamp'])
        )
    
    conn.commit()
    cur.close()
    conn.close()
```

---

## 📊 Performance Optimization

### **Caching Strategy**
```python
# Redis caching setup
import redis
from flask_caching import Cache

cache = Cache(app, config={'CACHE_TYPE': 'redis'})

@cache.memoize(timeout=300)
def get_sentiment_data():
    # Cache sentiment data for 5 minutes
    return sentiment_data
```

### **Load Balancing**
```yaml
# docker-compose.yml for load balancing
version: '3.8'
services:
  nginx:
    image: nginx:alpine
    ports:
      - "80:80"
    volumes:
      - ./nginx.conf:/etc/nginx/nginx.conf
    depends_on:
      - app1
      - app2

  app1:
    build: .
    environment:
      - DATABASE_URL=postgresql://user:pass@db:5432/citizenai

  app2:
    build: .
    environment:
      - DATABASE_URL=postgresql://user:pass@db:5432/citizenai

  db:
    image: postgres:13
    environment:
      - POSTGRES_DB=citizenai
      - POSTGRES_USER=user
      - POSTGRES_PASSWORD=pass
```

---

## 📈 Monitoring & Maintenance

### **Health Checks**
```python
# Add to app.py
@app.route('/health')
def health_check():
    return {
        'status': 'healthy',
        'timestamp': datetime.utcnow().isoformat(),
        'version': '1.0.0'
    }
```

### **Logging Configuration**
```python
import logging
from logging.handlers import RotatingFileHandler

if not app.debug:
    file_handler = RotatingFileHandler('logs/citizenai.log', maxBytes=10240, backupCount=10)
    file_handler.setFormatter(logging.Formatter(
        '%(asctime)s %(levelname)s: %(message)s [in %(pathname)s:%(lineno)d]'
    ))
    file_handler.setLevel(logging.INFO)
    app.logger.addHandler(file_handler)
```

### **Backup Strategy**
```bash
#!/bin/bash
# backup.sh - Daily database backup
DATE=$(date +%Y%m%d_%H%M%S)
pg_dump $DATABASE_URL > backups/citizenai_$DATE.sql
aws s3 cp backups/citizenai_$DATE.sql s3://your-backup-bucket/
```

---

## 🚨 Troubleshooting

### **Common Issues**

1. **Model Loading Fails**
   ```bash
   # Check GPU availability
   python -c "import torch; print(torch.cuda.is_available())"
   
   # Fallback to CPU
   export CUDA_VISIBLE_DEVICES=""
   ```

2. **Database Connection Issues**
   ```bash
   # Test connection
   psql $DATABASE_URL -c "SELECT 1;"
   
   # Check firewall
   sudo ufw status
   ```

3. **High Memory Usage**
   ```bash
   # Monitor memory
   htop
   
   # Restart service
   sudo systemctl restart citizenai
   ```

### **Performance Monitoring**
```bash
# System resources
htop
iotop
nethogs

# Application logs
tail -f logs/citizenai.log

# Database performance
psql -c "SELECT * FROM pg_stat_activity;"
```

---

## 📞 Support & Maintenance

### **Regular Maintenance Tasks**
- [ ] Weekly database backups
- [ ] Monthly security updates
- [ ] Quarterly performance reviews
- [ ] Annual SSL certificate renewal

### **Emergency Contacts**
- **System Admin**: admin@yourdomain.com
- **Database Admin**: dba@yourdomain.com
- **Security Team**: security@yourdomain.com

### **Rollback Procedure**
```bash
# Quick rollback steps
1. Stop current service
2. Restore previous version
3. Restore database backup
4. Restart services
5. Verify functionality
```

---

*This deployment guide ensures CitizenAI runs reliably in production environments with proper security, monitoring, and maintenance procedures.*
