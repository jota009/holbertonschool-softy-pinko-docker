# Start from the latest Ubuntu base image
FROM ubuntu:latest
# Update package metadata and upgrade installed packages
RUN apt-get update
RUN apt-get upgrade -y
# Install Python + pip
RUN apt-get install -y python3 python3-pip
# Remove the externally managed restriction FIRST
RUN rm -f /usr/lib/python*/EXTERNALLY-MANAGED || true
# Now install packages in the correct order
RUN python3 -m pip install --no-cache-dir flask
RUN python3 -m pip install --no-cache-dir flask-cors
# App directory
WORKDIR /app
# Copy the Flask app
COPY ./api.py /app/api.py
# Optional (self-documenting): the port our app listens on
EXPOSE 5252
# Start the server
CMD ["python3", "api.py"]
