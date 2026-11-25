# YaMDb Project

API for the YaMDb service - a platform for collecting user reviews on books, movies, and music.

Deployed on Yandex Cloud in 2022. The server is no longer running, and the deploy workflow has been disabled; the workflow file is kept as an example of the CI/CD pipeline.

## Project Description

The YaMDb project collects user reviews on various works. Works are divided into categories: "Books", "Movies", and "Music". Each category contains specific works: books, movies, or music. A work can be assigned a genre. New genres can only be created by an administrator. Users can leave text reviews for works and rate them on a scale of one to ten. An average score (rating) is calculated based on user ratings. There is also a feature to comment on reviews.

API Features:
1) Browsing works (movies, music, books), categorized by genres and categories.
2) Ability to leave reviews on works and rate them, forming the basis of the rating system.
3) Commenting on submitted reviews.

The project was developed by a team of three using Git as part of the Yandex.Practicum training course.

## Tech Stack

Python 3.9
Django 2.2.16
Django REST Framework 3.12.4
Django REST Framework simplejwt 5.1.0

## How to Run the Project

Clone the repository and navigate to it via the command line:

```bash
git clone https://github.com/AxelVonReems/API-YaMDb.git
```

Navigate to the project folder:

```bash
cd API-YaMDb
```

Create and activate a virtual environment:

```bash
WIN: python -m venv venv
MAC: python3 -m venv venv
```

```bash
WIN: source venv/scripts/activate
MAC: source venv/bin/activate
```

Install dependencies from the `requirements.txt` file:

```bash
WIN: python -m pip install --upgrade pip
MAC: python3 -m pip install --upgrade pip
```

```bash
pip install -r requirements.txt
```

In the `infra` folder, create and populate a `.env` file using the following template:

```env
DB_ENGINE=django.db.backends.postgresql - specifies that we are working with PostgreSQL
DB_NAME=postgres - database name
POSTGRES_USER=postgres - login for database connection
POSTGRES_PASSWORD=postgres - password for database connection
DB_HOST=db - service (container) name
DB_PORT=5432 - port for database connection 
SECRET_KEY=XXXXXXXXXXXXXXXXX - Django project secret key
DEBUG='False' - debugger setting
```

Build and start the container using Docker Compose:

```bash
docker-compose build
docker-compose up
```

Apply migrations via Docker Compose:

```bash
docker-compose exec web python manage.py makemigrations users  
docker-compose exec web python manage.py migrate --noinput
```

Collect static files:

```bash
docker-compose exec web python manage.py collectstatic --no-input
```

Create a superuser via Docker Compose:

```bash
docker-compose exec web python manage.py createsuperuser
```

Populate the database with initial data:

```bash
docker-compose exec web python manage.py loaddata fixtures.json
```

## Authors

Team project (3 developers) built in 2022 for the Yandex Practicum Python Developer course.
My part: Review and Comment models, their views and endpoints, request permissions and the rating system.
Aleksei Smirnov - GitHub: https://github.com/AxelVonReems
