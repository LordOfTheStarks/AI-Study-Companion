# DOCKERFILE

## Use an official Python image

FROM python:3.12-slim

## Set working directory

WORKDIR /app

## Copy requirements first for caching

COPY requirements.txt .

## Install dependencies

RUN pip install --no-cache-dir -r requirements.txt

## Copy the rest of the application code

COPY . .

## Expose port 80

EXPOSE 80

## Command to run Uvicorn

CMD ["uvicorn", "mypythonapp:app", "--host", "0.0.0.0", "--port", "80"]
