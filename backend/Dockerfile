# backend/Dockerfile

FROM python:3.11-slim

# Install system dependencies and Chrome
RUN apt-get update && apt-get install -y \
    wget curl unzip gnupg libxss1 libappindicator1 libnss3 \
    libatk-bridge2.0-0 libgtk-3-0 libx11-xcb1 libxcomposite1 \
    fonts-liberation libasound2 libgbm1 libxdamage1 libxrandr2 xdg-utils \
    libu2f-udev chromium chromium-driver \
    && rm -rf /var/lib/apt/lists/*

# Set Chrome path for Plotly Kaleido
ENV CHROME_BIN=/usr/bin/chromium

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy backend code into container
COPY . /app



CMD ["uvicorn", "backend.app:app", "--host", "0.0.0.0", "--port", "4000"]
