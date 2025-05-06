# Use the official Python image as the base image
FROM python:3.13.2-slim

# Set environment variables
ENV PYTHONDONTWRITEBYTECODE = 1
ENV PYTHONUNBUFFERED = 1
ENV ALLOWED_HOSTS = ["0.0.0.0"]

# Set the working directory in the container
WORKDIR /app

# Install system dependencies
RUN apt-get update && apt-get install -y \
    build-essential \
    libpq-dev \
    && apt-get clean

# Install Python dependencies
COPY requirements.txt /app/
RUN pip install --no-cache-dir -r requirements.txt

# Copy the Django project files into the container
COPY . /app/

# Expose the port the app runs on
EXPOSE 8000

# # Run the Django development server
# CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
# # running migrations python manage.py migrate
# CMD ["python", "manage.py", "migrate"]

ENTRYPOINT [ "sh", "-c", "python manage.py migrate && python manage.py runserver 0.0.0.0:8000" ]

