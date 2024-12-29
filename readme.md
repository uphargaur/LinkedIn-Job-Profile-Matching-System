# LinkedIn Job/Profile Matching System

A scalable system that crawls LinkedIn jobs and profiles, stores them in a database, and provides APIs to match jobs with profiles using advanced matching algorithms. Built with FastAPI, MongoDB, and modern matching algorithms.

## Author

**Uphar Gaur**
- 🎓 B.Tech in Computer Science Engineering, IIIT Una
- 💻 Backend Developer (Golang) at JhalaXCorp
- 📱 Android Developer with experience at Humors Tech and SaralX
- 🔗 [LinkedIn](https://www.linkedin.com/in/your-profile) | [GitHub](https://github.com/yourusername)
- 📧 Contact: uphargaur@gmail.com

## Features

- 🔍 Intelligent job and profile crawling system using Selenium
- 💾 MongoDB-based data storage with optimized indexing
- 🔄 Real-time matching algorithm using TF-IDF and semantic analysis
- 🚀 RESTful API built with FastAPI
- 📊 Advanced scoring system for profile matching
- ⚡ Rate limiting and anti-bot handling
- 📈 Scalable architecture supporting 1000 QPS

## Tech Stack

- **Backend**: FastAPI, Python
- **Database**: MongoDB
- **Web Crawling**: Selenium, BeautifulSoup
- **Cloud**: AWS EC2
- **DevOps**: Docker, GitHub Actions
- **Additional Tools**: Git, Linux

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
git clone https://github.com/uphargaur/linkedin-matcher.git
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

## API Documentation

### Get Matching Profiles
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

### Get Matching Jobs
```http
GET /api/jobs/search
```
Parameters:
- `experience`: Years of experience
- `job_function`: Job function/category
- `designation`: Job title
- `location`: Geographic location
- `preferences`: Additional preferences (optional)

## Scalability Features

Leveraging my experience at JhalaXCorp where I improved backend efficiency:

- AWS EC2 deployment with optimized instance configuration
- Efficient MongoDB indexing for fast queries
- Caching layer for frequent requests
- Rate limiting and request throttling
- Horizontal scaling support

## Testing

Run tests using pytest:
```bash
# Run all tests
pytest

# Run with coverage report
pytest --cov=app tests/
```

## Development Practices

Based on my experience in developing scalable applications:

- Clean, modular code architecture
- Comprehensive error handling
- Detailed API documentation
- Regular security updates
- Performance optimization
- Continuous Integration using GitHub Actions

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

## Contact

Uphar Gaur - uphargaur@gmail.com

Project Link: [https://github.com/uphargaur/linkedin-matcher](https://github.com/uphargaur/linkedin-matcher)

---
Built with ❤️ by Uphar Gaur