
---

# Flask Blog Application

This is a simple Flask-based blog application where users can register, log in, create blog posts, comment on posts, and edit or delete posts (admin-only functionality).

## Features

- **User Authentication**: Users can register, log in, and log out.
- **Admin-Only Post Creation**: Admins can create new posts.
- **Comment System**: Users can add comments to blog posts.
- **Post Management**: Admins can edit and delete posts.
- **Profile Image Support**: Gravatar integration for user profiles and comments.
- **Contact Form**: Users can contact the website admin via email.

## Technologies Used

- **Flask**: Web framework for building the application.
- **Flask-Login**: User session management.
- **Flask-SQLAlchemy**: ORM for database interaction.
- **PostgreSQL**: Database for storing user and blog data.
- **Flask-Bootstrap**: To style the app using Bootstrap.
- **Flask-CKEditor**: For rich text editing in blog posts.
- **Flask-Gravatar**: To add profile images via Gravatar.
- **Gunicorn**: WSGI server to run the app in production.
- **Render**: Platform for hosting the web application.

## Deployment

The Flask blog application is deployed on Render.com, a cloud platform for building and running apps.

You can access the live application at:

[**Live Application Link**](https://blog-deployment-27j8.onrender.com/)

### Steps to Deploy on Render (if you wish to deploy it yourself)

1. **Sign up or log in** to [Render.com](https://render.com).
2. **Create a new Web Service** and link it to your GitHub repository containing the Flask app.
3. **Set the environment variables**:
   - `DB_URI`: PostgreSQL database URI (explained below).
   - `EMAIL_KEY`: Email address for sending contact emails.
   - `PASSWORD_KEY`: App password for email.
4. **Set the Build Command**:
   ```bash
   pip install -r requirements.txt
   ```
5. **Set the Start Command**:
   ```bash
   gunicorn app:app
   ```
6. **Deploy** the app, and Render will provide you with a URL where your app is live.

### Database Configuration: PostgreSQL

This application uses **PostgreSQL** as the database to store user data, blog posts, and comments.

1. **Set up PostgreSQL** on Render:
   - Go to [Render's PostgreSQL service](https://render.com/docs/databases) to create a PostgreSQL database.
   - Render will provide a **Database URI** (e.g., `postgres://username:password@host:port/database_name`).

2. **Set the `DB_URI` environment variable**:
   - In your Render dashboard, go to the Environment tab and add the `DB_URI` variable with the connection string provided by Render.

   Example:
   ```env
   DB_URI=postgres://username:password@host:port/database_name
   ```

3. **Update your `.env` file locally** (for local development):
   - Make sure to set your `DB_URI` in the `.env` file to match your PostgreSQL database URI:
   ```env
   DB_URI=postgres://username:password@localhost:5432/database_name
   ```

### Environment Variables

Make sure to set the following environment variables on Render (and locally if developing):

- **DB_URI**: The PostgreSQL database connection string (as explained above).
- **EMAIL_KEY**: Your email address for sending contact emails.
- **PASSWORD_KEY**: Your email password (for sending emails via SMTP).
- **SECRET_KEY**: A secret key used by Flask for secure sessions (already included in the code, but you may want to change it for production).

### Requirements

Before running the app locally, ensure you have the following Python packages installed:

- **Flask**
- **Flask-Login**
- **Flask-SQLAlchemy**
- **Flask-Bootstrap**
- **Flask-CKEditor**
- **Flask-Gravatar**
- **gunicorn** (for production)
- **python-dotenv** (for loading environment variables)
- **psycopg2** (PostgreSQL adapter for Python)

To install the dependencies, run:

```bash
pip install -r requirements.txt
```

## Running Locally

1. Clone the repository:

   ```bash
   git clone https://github.com/your-username/your-repository.git
   cd your-repository
   ```

2. Set up a virtual environment (optional but recommended):

   ```bash
   python -m venv venv
   source venv/bin/activate  # For MacOS/Linux
   venv\Scripts\activate  # For Windows
   ```

3. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

4. Create a `.env` file in the root directory of your project to store sensitive information:

   ```env
   DB_URI=postgres://username:password@localhost:5432/database_name
   EMAIL_KEY=your-email@gmail.com
   PASSWORD_KEY=your-email-password
   SECRET_KEY=your-secret-key
   ```

5. Run the Flask app:

   ```bash
   flask run
   ```

6. Open your browser and visit `http://127.0.0.1:5000/` to view the app.

## Testing

Make sure to test all routes and features locally before deploying:

- **Registration**: Ensure users can sign up and log in.
- **Admin Access**: Check that only admins can create, edit, or delete posts.
- **Commenting**: Ensure users can comment on posts after logging in.
- **Gravatar**: Check if profile images appear correctly in the comments section.
- **Contact Form**: **There is a known issue with the contact form** — emails might not be sent correctly due to SMTP configuration or email service provider limitations. Please check your SMTP settings and ensure they are correctly configured in the `.env` file.

## Contributing

If you’d like to contribute, feel free to fork the repository, submit issues, or open pull requests. 

### Code Style

Please follow PEP8 guidelines for Python code and ensure the HTML is clean and follows best practices.

---


