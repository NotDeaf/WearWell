FROM python:3.11

WORKDIR /app

# Install system dependencies
RUN apt-get update && apt-get install -y \
    libgl1-mesa-glx \
    libglib2.0-0 \
    libsm6 \
    libxext6 \
    libxrender1 \
    && rm -rf /var/lib/apt/lists/*

# Copy backend code
COPY . .

# Install Python dependencies (from app/requirements.txt)
RUN pip install --no-cache-dir -r app/requirements.txt

EXPOSE 5000

# Run Flask app via Gunicorn
CMD ["gunicorn", "--bind", "0.0.0.0:5000", "main:app"]
