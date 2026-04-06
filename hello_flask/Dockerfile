# Stage 1: Build dependencies
FROM python:3.8-slim AS build

WORKDIR /app

RUN apt-get update && apt-get install -y \
    gcc \
    python3-dev \
    libmariadb-dev \
    pkg-config

COPY requirements.txt .

# Install into a custom location
RUN pip install --prefix=/install -r requirements.txt



# Stage 2: Runtime (minimal)
FROM python:3.8-slim

WORKDIR /app

# Only runtime dependency (no gcc etc.)
RUN apt-get update && apt-get install -y \
    libmariadb3 \
    && apt-get clean

# Copy only installed Python packages
COPY --from=build /install /usr/local

# Copy app code
COPY . .

EXPOSE 5000
CMD ["python", "app.py"]