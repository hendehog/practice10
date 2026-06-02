FROM python:3.11-slim

WORKDIR /app

LABEL maintainer="hendehog1"
LABEL description="Пример Dockerfile для практики 1"
LABEL version="1.0.0"

ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1
ENV APP_VERSION=1.0.0
ENV ENVIRONMENT=env/development
ENV STUDENT_NAME=Hendehog1    

COPY requirements.txt .

RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    && pip install --no-cache-dir --upgrade pip \
    && apt-get autoremove -y \
    && apt-get clean -y \
    && rm -rf /var/lib/apt/lists/* \
    && useradd -u 1001 -m testuser \
    && chown -R testuser:testuser /app \
    && pip install --no-cache-dir -r requirements.txt
    
COPY . .
USER testuser
EXPOSE 8080
HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 \
    CMD curl -f http://localhost:8080/health || exit 1
CMD ["python", "app.py"]





