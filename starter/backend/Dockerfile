FROM python:3.10-slim

WORKDIR /app

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    build-essential \
    gcc \
    && rm -rf /var/lib/apt/lists/*

RUN pip install --no-cache-dir pipenv

COPY Pipfile /app/

RUN pipenv lock

RUN pipenv install --system --deploy

COPY . /app

EXPOSE 5000

CMD ["flask", "--app", ".", "run", "--host=0.0.0.0", "--port=5000"]
