# LinkedIn Job/Profile Matching System

A scalable system that crawls LinkedIn jobs and profiles, stores them in a database, and provides APIs to match jobs with profiles using advanced matching algorithms.

## Table of Contents
- [Features](#features)
- [System Architecture](#system-architecture)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [API Documentation](#api-documentation)
- [Database Schema](#database-schema)
- [Testing](#testing)
- [Scalability](#scalability)
- [Contributing](#contributing)
- [License](#license)

## Features

- 🔍 Crawls LinkedIn jobs and profiles using Selenium
- 💾 Stores data in MongoDB with optimized indexing
- 🔄 Real-time matching algorithm using TF-IDF and semantic analysis
- 🚀 RESTful API built with FastAPI
- 📊 Scoring system based on skills, location, and experience
- ⚡ Handles rate limiting and anti-bot mechanisms
- 📈 Scales to handle 1000 QPS with 100 concurrent users

## System Architecture

```
├── crawler/
│   ├── job_crawler.py      # LinkedIn job crawler
│   ├── profile_crawler.py  # LinkedIn profile crawler
│   └── utils.py           # Shared crawler utilities
├── api/
│   ├── main.py            # FastAPI application
│   ├── models.py          # Pydantic models
│   └── routes/
│       ├── jobs.py        # Job-related endpoints
│       └── profiles.py    # Profile-related endpoints
├── matching/
│   ├── engine.py          # Matching algorithm implementation
│   └── scorers.py         # Individual scoring components
└── database/
    ├── models.py          # MongoDB models
    └── connection.py      # Database connection handling
```

## Prerequisites

- Python 3.8+
- MongoDB 4.4+
- Chrome/Chromium browser
- ChromeDriver
- Virtual environment (recommended)

## Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/linkedin-matcher.git
cd linkedin-matcher
```

2. Create and activate virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

4. Set up environment variables:
```bash
cp .env.example .env
# Edit .env with your configurations
```

## Configuration

### Environment Variables

Create a `.env` file with the following variables:
```
MONGODB_URL=mongodb://localhost:27017
API_KEY=your_secret_api_key
LINKEDIN_EMAIL=your_linkedin_email
LINKEDIN_PASSWORD=your_linkedin_password
RATE_LIMIT_PER_MINUTE=100
MAX_CONCURRENT_REQUESTS=100
```

### MongoDB Setup

1. Start MongoDB:
```bash
mongod --dbpath /path/to/data/db
```

2. Create indexes:
```bash
python scripts/create_indexes.py
```

## Usage

### Starting the API Server

```bash
uvicorn api.main:app --reload --workers 4 --host 0.0.0.0 --port 8000
```

### Running the Crawler

```bash
# Crawl jobs
python -m crawler.job_crawler

# Crawl profiles
python -m crawler.profile_crawler
```

### API Endpoints

#### Get Matching Profiles
```http
GET /api/profiles/search
```
Parameters:
- `designation`: Job title or role
- `location`: Geographic location
- `company`: Company name

Example:
```bash
curl -X GET "http://localhost:8000/api/profiles/search?designation=Software%20Engineer&location=San%20Francisco&company=Google"
```

#### Get Matching Jobs
```http
GET /api/jobs/search
```
Parameters:
- `experience`: Years of experience
- `job_function`: Job function/category
- `designation`: Job title
- `location`: Geographic location
- `preferences`: Additional preferences (optional)

Example:
```bash
curl -X GET "http://localhost:8000/api/jobs/search?experience=5&job_function=Engineering&designation=Senior%20Software%20Engineer&location=New%20York"
```

## Database Schema

### Jobs Collection
```javascript
{
  "_id": ObjectId,
  "title": String,
  "company": String,
  "location": String,
  "description": String,
  "skills": Array<String>,
  "requirements": {
    "experience": Number,
    "education": String,
    "skills": Array<String>
  },
  "posted_date": Date,
  "url": String,
  "metadata": {
    "crawled_at": Date,
    "last_updated": Date
  }
}
```

### Profiles Collection
```javascript
{
  "_id": ObjectId,
  "name": String,
  "title": String,
  "location": String,
  "current_company": String,
  "skills": Array<String>,
  "experience": [{
    "title": String,
    "company": String,
    "duration": {
      "start": Date,
      "end": Date
    },
    "description": String
  }],
  "url": String,
  "metadata": {
    "crawled_at": Date,
    "last_updated": Date
  }
}
```

## Testing

Run tests using pytest:
```bash
# Run all tests
pytest

# Run specific test file
pytest tests/test_matching_engine.py

# Run with coverage report
pytest --cov=app tests/
```

## Scalability

### System Capabilities
- Handles 1000 QPS with 100 concurrent users
- Efficient database indexing for fast queries
- Caching layer for frequent requests
- Horizontal scaling support

### Limitations
- LinkedIn's anti-scraping measures
- Rate limiting on crawling
- Data freshness challenges

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.

## Project Status

🚧 Under active development

## Authors

- Your Name - Initial work - [YourGithub](https://github.com/yourusername)

## Acknowledgments

- LinkedIn for providing the platform
- FastAPI for the excellent web framework
- MongoDB for the robust database system

## Support

For support, email fake@example.com or join our Slack channel.

---
Made with ❤️ by [Your Name/Company]
