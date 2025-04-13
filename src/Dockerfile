FROM python:3.10-slim

# Install system dependencies including ffmpeg
RUN apt-get update && apt-get install -y \
    ffmpeg \
    git \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Set working directory
WORKDIR /app

# Clone the repository
RUN git clone https://github.com/Michele0303/tiktok-live-recorder.git .

# Change to the source directory
WORKDIR /app/src

# Install Python dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Create volume mount points for output videos and configuration
VOLUME ["/app/output", "/app/config"]

# Create symbolic links for configuration files
RUN mkdir -p /app/config && \
    touch /app/config/cookies.json && \
    touch /app/config/telegram.json && \
    ln -sf /app/config/cookies.json /app/src/cookies.json && \
    ln -sf /app/config/telegram.json /app/src/telegram.json

# Set the entrypoint to the Python interpreter
ENTRYPOINT ["python3"]

# Default command shows help
CMD ["main.py", "-h"]