# Use the official Python slim image as a base
FROM python:3.9-slim

# Set the working directory in the container
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . .

# Update the package index and install necessary packages
RUN apt-get update -y && \
    apt-get install -y build-essential libpq-dev && \
    pip install --upgrade pip setuptools wheel && \
    pip install -r requirements.txt

# Set environment variables (if needed)
ENV DB_USERNAME=projectuser
ENV DB_PASSWORD=${POSTGRES_PASSWORD}
ENV DB_HOST=127.0.0.1
ENV DB_PORT=5433
ENV DB_NAME=projectdatabase

# Expose the port the app runs on
EXPOSE 5153

# Run the application when the container launches
CMD ["python", "app.py"]
