# Startup Investor Matching Platform

A full-stack web application that matches startup founders with potential investors based on industry, funding stage, risk tolerance, and investment amount.

## 🏗️ Architecture

### Frontend
- **HTML5** - Semantic structure
- **CSS3** - Modern styling with CSS Grid/Flexbox
- **Vanilla JavaScript** - Interactive functionality
- **Responsive Design** - Mobile-first approach

### Backend
- **Python Flask** - RESTful API
- **Flask-CORS** - Cross-origin resource sharing
- **In-memory data** - No database required for MVP

## 🚀 Quick Start

### Prerequisites
- Python 3.7+
- pip (Python package manager)
- Modern web browser

### Installation

1. **Clone/Download the files**
   ```bash
   mkdir startup-investor-platform
   cd startup-investor-platform
   ```

2. **Save the files**
   - Save `app.py` (Flask backend)
   - Save `requirements.txt`
   - Save `index.html` (Frontend)

3. **Install Python dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Run the Flask backend**
   ```bash
   python app.py
   ```
   The API will be available at `http://localhost:5000`

5. **Open the frontend**
   - Open `index.html` in your web browser
   - Or serve it via a simple HTTP server:
   ```bash
   # Python 3
   python -m http.server 8080
   
   # Then visit http://localhost:8080
   ```

## 🔧 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/` | Health check |
| GET | `/api/investors` | List all investors |
| POST | `/api/match` | Find investor matches |
| GET | `/api/investors/<id>` | Get investor details |
| GET | `/api/industries` | List available industries |
| GET | `/api/funding-stages` | List funding stages |
| GET | `/api/stats` | Platform statistics |

### Example API Usage

**Find Matches:**
```bash
curl -X POST http://localhost:5000/api/match \
  -H "Content-Type: application/json" \
  -d '{
    "industry": "fintech",
    "funding_stage": "seed",
    "risk_tolerance": "high",
    "investment_amount": 500000,
    "company_name": "MyStartup"
  }'
```

## 🧮 Matching Algorithm

The scoring system awards points based on alignment:

- **+3 points** - Industry match
- **+2 points** - Funding stage overlap
- **+1 point** - Risk tolerance alignment
- **+1 point** - Investment amount within range

**Maximum Score: 7 points**

## 📊 Sample Data

The platform includes 6 hardcoded investor profiles:

1. **TechVentures Capital** - FinTech/SaaS/AI, Seed/Series A
2. **HealthFirst Partners** - HealthTech/AI, Pre-seed/Seed
3. **Growth Equity Solutions** - SaaS/E-commerce/FinTech, Series A/B
4. **Innovation Labs Fund** - AI/Blockchain/IoT, Pre-seed/Seed
5. **Education Forward VC** - EdTech/SaaS, Seed/Series A
6. **Commerce Accelerator** - E-commerce/SaaS/FinTech, Pre-seed to Series A

## 🎨 Frontend Features

- **Multi-step wizard interface**
- **Real-time form validation**
- **Loading states and animations**
- **Responsive design**
- **Professional UI matching the reference**
- **Interactive match results**

## 🔐 Security Considerations

For production deployment:

1. **Input validation** - Add server-side validation
2. **Rate limiting** - Prevent API abuse
3. **HTTPS** - Secure data transmission
4. **Authentication** - User management system
5. **Database** - Replace in-memory data with persistent storage

## 📈 Scaling Considerations

### Database Integration
```python
# Example SQLAlchemy model
class Investor(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    name = db.Column(db.String(100), nullable=False)
    industries = db.Column(db.JSON)
    stages = db.Column(db.JSON)
    # ... other fields
```

### Advanced Features
- **Real-time matching** with WebSocket connections
- **Machine learning** for improved matching accuracy
- **User authentication** and profile management
- **Messaging system** between founders and investors
- **Analytics dashboard** for platform insights

## 🐛 Troubleshooting

**CORS Issues:**
- Ensure Flask-CORS is installed and configured
- Check browser console for CORS errors

**Port Conflicts:**
- Change Flask port: `app.run(port=5001)`
- Update API URLs in frontend accordingly

**Module Not Found:**
- Ensure all dependencies are installed: `pip install -r requirements.txt`
- Check Python version compatibility

## 🚢 Deployment Options

### Local Development
- Use the setup instructions above

### Cloud Deployment
- **Heroku**: Add `Procfile` with `web: python app.py`
- **AWS EC2**: Use systemd service for process management
- **Google Cloud Run**: Containerize with Docker
- **DigitalOcean App Platform**: Direct GitHub deployment

### Docker Setup
```dockerfile
FROM python:3.9-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
EXPOSE 5000
CMD ["python", "app.py"]
```

## 📝 Next Steps

1. **Add database integration** (PostgreSQL/MongoDB)
2. **Implement user authentication** (JWT tokens)
3. **Add email notifications** for matches
4. **Create admin dashboard** for investor management
5. **Implement advanced search filters**
6. **Add investor application workflow**
7. **Build mobile app** with React Native/Flutter

## 🤝 Contributing

This is a MVP implementation. For production use:
- Add comprehensive error handling
- Implement logging and monitoring
- Add automated testing
- Set up CI/CD pipeline
- Add data validation and sanitization