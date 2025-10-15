# 🚀 Web App Generator API

FastAPI application that generates web applications using Gemini AI and deploys them to GitHub Pages.

## ✅ Current Status

**Files Ready:**
- ✅ main.py (443 lines) - FastAPI application
- ✅ models.py - Data models
- ✅ requirements.txt - Dependencies
- ✅ .env.example - Configuration template
- ✅ Python packages installed

**Next Steps: Configure & Run**

## 🔧 Quick Start

### 1. Configure Environment

Edit the `.env` file with your credentials:

```bash
nano .env
# or
code .env
```

**Required credentials:**

- **MY_SECRET** - Generate with: `openssl rand -hex 32`
- **GITHUB_TOKEN** - Get from: https://github.com/settings/tokens (needs `repo` scope)
- **GITHUB_USERNAME** - Your GitHub username
- **GEMINI_API_KEY** - Get from: https://makersuite.google.com/app/apikey

### 2. Verify Configuration

```bash
python test_setup.py
```

### 3. Run the Server

```bash
python main.py
```

Server will run on: **http://localhost:8000**

API Documentation: **http://localhost:8000/docs**

## 🧪 Test the API

### Health Check
```bash
curl http://localhost:8000/health
```

### Test Round 1 (Build)
```bash
curl -X POST http://localhost:8000/api-endpoint \
  -H "Content-Type: application/json" \
  -d '{
    "email": "test@example.com",
    "secret": "your_MY_SECRET_value",
    "task": "my-test-app",
    "round": 1,
    "nonce": "test-001",
    "brief": "Create a simple calculator with basic operations",
    "checks": ["functionality"],
    "evaluation_url": "https://httpbin.org/post",
    "attachments": ["Use modern CSS"]
  }'
```

## 📚 How It Works

### Round 1: Build & Deploy
1. Receives request with app description
2. Gemini AI generates HTML/CSS/JS
3. Creates GitHub repository
4. Commits files (index.html, LICENSE, README.md)
5. Enables GitHub Pages
6. Notifies evaluation server
7. **Result**: Live app at `https://yourusername.github.io/app-name/`

### Round 2: Revise & Update
1. Receives request with changes
2. Fetches existing code
3. Gemini AI updates the code
4. Updates repository
5. Notifies evaluation server
6. **Result**: Updated live app

## 📁 Project Structure

```
.
├── main.py              # FastAPI application
├── models.py            # Pydantic models
├── requirements.txt     # Dependencies
├── .env                 # Your credentials (DO NOT COMMIT)
├── .env.example         # Template
├── test_setup.py        # Setup verification
└── README.md           # This file
```

## 🔒 Security

- Never commit `.env` to git
- Use strong secrets
- GitHub token should have minimal permissions (only `repo`)

## �� API Endpoints

- `GET /` - Service info
- `GET /health` - Health check
- `POST /api-endpoint` - Main endpoint (requires authentication)
- `GET /docs` - Interactive API documentation

## 🎯 What You Need

### Before Running:
1. ✅ Python 3.8+ (you have 3.12.3 ✓)
2. ✅ Dependencies installed ✓
3. ⚠️  Configure .env file
4. ⚠️  Get credentials (see above)

### To Get Credentials:
Run: `cat .env.example` to see what you need

## 🚀 Ready to Go?

```bash
# 1. Configure
nano .env

# 2. Verify
python test_setup.py

# 3. Run
python main.py

# 4. Test
curl http://localhost:8000/health
```

Visit http://localhost:8000/docs for interactive API documentation!

## 📞 Need Help?

Check that:
- `.env` file has all required values
- GitHub token has `repo` scope
- Gemini API key is valid
- Port 8000 is not in use

---

**Status**: Ready to configure and run! 🎉
