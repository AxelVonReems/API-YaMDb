[![Django-app workflow](https://github.com/AxelVonReems/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg?branch=master)](https://github.com/AxelVonReems/yamdb_final/actions/workflows/yamdb_workflow.yml)

# YaMDb Project

API for the YaMDb service - a platform for collecting user reviews on books, movies, and music.

Project URL: http://51.250.23.204/admin/

Documentation URL: http://51.250.23.204/redoc/

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
[https://github.com/AxelVonReems/yamdb_final.git](https://github.com/AxelVonReems/yamdb_final.git)
```

Navigate to the project folder:

```bash
cd yamdb_final
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

## Author

Aleksei Smirnov. GitHub: https://github.com/AxelVonReems/
