# Use an official Python runtime as a parent image
FROM python:3.9

# Set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# Set work directory
WORKDIR /django

# Install dependencies
COPY ../requirements.txt /django/
RUN pip install --no-cache-dir -r requirements.txt

# Copy the current directory contents into the container at /code
COPY ../ /django/
