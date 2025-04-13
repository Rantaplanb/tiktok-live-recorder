FROM python:3.10

# Install system dependencies including ffmpeg
RUN apt-get update && apt-get install -y \
    ffmpeg \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app

COPY . /app

# Install Python dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Create volume mount points for output videos and configuration
VOLUME ["/app/output", "/app/config"]

# Set the entrypoint to the Python interpreter
ENTRYPOINT ["python3"]

# Default command to run the application
CMD ["main.py", "-room_id", "7492759544498817814", "-mode", "automatic", "-output", "/app/output"]