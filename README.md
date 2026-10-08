# Flask Blog

A **blog website with user accounts, comments and an admin role**, built with Flask and SQLAlchemy. The admin writes posts with a rich-text editor, and registered users can comment on them.

## Features

- User registration and login with hashed passwords (Werkzeug)
- **Admin-only** create, edit and delete for posts (the first registered user, `id = 1`, is the admin)
- Rich-text post editor and comments with Flask-CKEditor
- Comments on posts, with Gravatar avatars
- Contact form that sends messages by email (SMTP)
- Responsive Bootstrap 5 theme
- Ready to deploy with Gunicorn (`Procfile` included)

## Tech Stack

- **Backend:** Python, Flask
- **Database:** SQLite with Flask-SQLAlchemy (PostgreSQL driver included for deployment)
- **Forms:** Flask-WTF, WTForms, Flask-CKEditor
- **Auth:** Flask-Login
- **UI:** Bootstrap-Flask (Bootstrap 5), Flask-Gravatar
- **Deployment:** Gunicorn

## Getting Started

### 1. Clone and install

```bash
git clone https://github.com/PRiNCeKUsHW/Flask-blog.git
cd Flask-blog
python -m venv venv
venv\Scripts\activate          # macOS/Linux: source venv/bin/activate
pip install -r requirements.txt
```

### 2. Add your secrets

The app imports its keys from a `pas.py` file that is not committed. Create it in the project root:

```python
# pas.py
keysec = "your-flask-secret-key"
keymail = "your-email@gmail.com"
keypass = "your-gmail-app-password"
```

### 3. Run

```bash
flask --app main run
```

Open http://127.0.0.1:5000. Register first so your account becomes the admin.

## Routes

| Route | Access | Description |
|-------|--------|-------------|
| `/` | Everyone | All posts |
| `/post/<id>` | Everyone (logged in to comment) | Read a post and its comments |
| `/register`, `/login`, `/logout` | Everyone | Authentication |
| `/new-post` | Admin | Create a post |
| `/edit-post/<id>` | Admin | Edit a post |
| `/delete/<id>` | Admin | Delete a post |
| `/about` | Everyone | About page |
| `/contact` | Everyone | Contact form (sends an email) |

## Project Structure

```
Flask-blog/
├── main.py           # App, models (User, BlogPost, Comment) and routes
├── forms.py          # WTForms: post, register, login, comment
├── requirements.txt
├── Procfile          # web: gunicorn main:app
├── templates/        # Jinja2 templates
├── static/           # CSS, JS, images
└── instance/         # SQLite database (posts.db)
```
