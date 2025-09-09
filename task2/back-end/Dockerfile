# Start from the latest Ubuntu base image
FROM ubuntu:latest

# Update package metadata and upgrade installed packages
RUN apt-get update
RUN apt-get upgrade -y


# Install Python + pip
RUN apt-get install -y python3 python3-pip

# On some recent Ubuntus, pip installs inside system Python are blocked.
# This removes the "externally managed" sentinel so pip can install Flask.
RUN rm -f /usr/lib/python*/EXTERNALLY-MANAGED || true

# App directory
WORKDIR /app

# Copy the Flask app
COPY ./api.py /app/api.py

# Install Flask with pip (not apt)
RUN python3 -m pip install --no-cache-dir Flask

# Optional (self-documenting): the port our app listens on
EXPOSE 5252

# Start the server
CMD ["python3", "api.py"]
