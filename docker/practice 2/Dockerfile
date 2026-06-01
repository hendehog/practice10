From cr.yandex/mirror/python:3.11-slim

Workdir /app

Env REGISTRY="Yandex Mirror"

COPY app.py .

EXPOSE 8080

RUN useradd -m noroot

USER noroot

CMD ["python", "app.py"]