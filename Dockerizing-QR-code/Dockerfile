# Use the official Python image from the Python Docker Hub repository as the base image
FROM python:3.12-slim-bullseye

# Set the working directory to /app in the container
WORKDIR /app

# Copy the requirements.txt file to the container to install Python dependencies
COPY requirements.txt ./

# Install the Python packages specified in requirements.txt
RUN useradd -m myuser && pip install --no-cache-dir -r requirements.txt && \
    mkdir logs qr_codes && chown myuser:myuser logs qr_codes

# Copy the rest of the application's source code into the container, setting ownership to 'myuser'
COPY --chown=myuser:myuser . .

# Switch to the 'myuser' user to run the application
USER myuser

# Use the Python interpreter as the entrypoint and the script as the first argument
ENTRYPOINT ["python", "main.py"]
CMD ["--url","http://github.com/kaw393939"]
