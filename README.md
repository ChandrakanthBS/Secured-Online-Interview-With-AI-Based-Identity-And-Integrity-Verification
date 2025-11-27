# Online Meeting Platform

A comprehensive Django-based online meeting platform that enables real-time video conferencing, chat, and collaborative meetings with advanced features like face recognition and WebRTC integration.

## Features

- **User Authentication & Management**: Secure user registration, login, and profile management
- **Meeting Management**: Create, join, and manage online meetings with scheduling capabilities
- **Real-time Video Conferencing**: WebRTC-based video calls with screen sharing support
- **Real-time Chat**: Instant messaging during meetings with WebSocket connections
- **Face Recognition**: Advanced user verification using DeepFace and OpenCV
- **Responsive Design**: Mobile-friendly interface using Bootstrap 5
- **REST API**: Full REST API for integration with other services
- **Admin Panel**: Django admin interface for content management

## Prerequisites

Before running this application, make sure you have the following installed:

- **Python 3.8 or higher**
- **Redis Server** (required for WebSocket functionality)
- **Git** (for cloning the repository)

### Installing Prerequisites

#### Windows

```bash
# Install Python from https://python.org
# Install Redis from https://redis.io/download
```

#### Linux (Ubuntu/Debian)

```bash
sudo apt update
sudo apt install python3 python3-pip redis-server git
```

#### macOS

```bash
brew install python redis git
```

## Installation

1. **Clone the repository**

   ```bash
   git clone <your-repository-url>
   cd online-meet5
   ```

2. **Create a virtual environment**

   ```bash
   # Windows
   python -m venv venv
   venv\Scripts\activate

   # Linux/macOS
   python3 -m venv venv
   source venv/bin/activate
   ```

3. **Install dependencies**

   ```bash
   pip install -r requirements.txt
   ```

4. **Configure environment variables**
   ```bash
   cp env.example .env
   # Edit .env file with your configuration
   ```

## Setup

### Automated Setup (Recommended)

Run the setup script to automatically configure the application:

```bash
python setup.py
```

This script will:

- Create virtual environment (if not exists)
- Install dependencies
- Run database migrations
- Create a superuser account
- Collect static files

### Manual Setup

If you prefer manual setup:

1. **Run database migrations**

   ```bash
   python manage.py migrate
   ```

2. **Create superuser**

   ```bash
   python manage.py createsuperuser
   ```

3. **Collect static files**
   ```bash
   python manage.py collectstatic --noinput
   ```

## Running the Application

### Start Redis Server

The application requires Redis for real-time features. Start Redis before running the application:

```bash
# Windows (if installed via Chocolatey or similar)
redis-server

# Linux/macOS
redis-server
```

### Run the Development Server

#### Windows

```bash
run.bat
```

#### Linux/macOS

```bash
chmod +x run.sh
./run.sh
```

Or manually:

```bash
python manage.py runserver
```

The application will be available at: http://127.0.0.1:8000

## Usage

### Accessing the Application

1. Open your browser and navigate to http://127.0.0.1:8000
2. Register a new account or login with existing credentials

### Default Credentials

After running setup.py, you can login with:

- **Username**: admin
- **Password**: admin123

### API Endpoints

The application provides REST API endpoints for integration:

- `GET /api/meetings/` - List meetings
- `POST /api/meetings/` - Create meeting
- `GET /api/meetings/{id}/` - Meeting details
- `POST /api/meetings/{id}/join/` - Join meeting

For complete API documentation, visit the admin panel or use tools like Postman.

## Project Structure

```
online-meet5/
├── accounts/          # User authentication and profiles
├── chat/             # Real-time messaging
├── core/             # Core application views
├── meetings/         # Meeting management
├── media/            # User uploaded files
├── templates/        # HTML templates
├── static/           # Static files (CSS, JS)
├── onlinemeet/       # Django project settings
├── requirements.txt  # Python dependencies
├── manage.py         # Django management script
├── setup.py          # Setup script
├── run.bat           # Windows run script
└── run.sh            # Linux/macOS run script
```

## Development

### Key Technologies

- **Backend**: Django 4.x, Django REST Framework
- **Real-time**: Django Channels, Redis
- **Frontend**: HTML5, CSS3, JavaScript, Bootstrap 5
- **Video**: WebRTC
- **AI/ML**: DeepFace, OpenCV for face recognition
- **Database**: SQLite (development), PostgreSQL/MySQL (production)

### Environment Variables

Configure the following in your `.env` file:

```env
SECRET_KEY=your-secret-key-here
DEBUG=True
ALLOWED_HOSTS=localhost,127.0.0.1
DATABASE_URL=sqlite:///db.sqlite3
REDIS_URL=redis://127.0.0.1:6379
```

## Deployment

For production deployment:

1. Set `DEBUG=False` in settings.py
2. Configure a production database (PostgreSQL/MySQL)
3. Set up Redis for production
4. Configure HTTPS for video calls
5. Use a production web server (Gunicorn/Nginx)
6. Set up proper static file serving

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Support

For support and questions:

- Create an issue in the repository
- Contact the development team

---

**Note**: Make sure Redis is running before starting the application for real-time features to work properly.
