# syntax=docker/dockerfile:1

# Use slim Python image
FROM python:3.11-slim AS base

# Prevents Python from writing .pyc files and buffers logs
ENV PYTHONDONTWRITEBYTECODE=1 PYTHONUNBUFFERED=1

# Set working directory inside container
WORKDIR /app

# Install Python dependencies
COPY backend/requirements.txt /app/requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Copy backend source code
COPY backend/ /app/

# Expose Flask/Gunicorn port
EXPOSE 8000

# Run Gunicorn (production WSGI server)
CMD ["gunicorn", "--workers", "3", "--bind", "0.0.0.0:8000", "app:app"]
