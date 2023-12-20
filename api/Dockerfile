# Use an official Python runtime as the base image
FROM python:3.10

# Set the working directory to /api
WORKDIR /api

# Set PYTHONPATH to include the directory where your modules are
ENV PYTHONPATH /api/app
ENV DJANGO_SETTINGS_MODULE 'app.settings'

# Copy the lockfile and pyproject.toml
COPY poetry.lock pyproject.toml /api/

# Install Poetry and dependencies
RUN pip install poetry
RUN poetry config virtualenvs.create false
RUN poetry install --no-root

# Copy the application code
COPY . /api/

# Collect the static files
# WORKDIR /api/app is not needed since WORKDIR has already been set to /api

# Запускаем приложение
CMD ["python", "app/manage.py", "runserver", "0.0.0.0:8000"]
