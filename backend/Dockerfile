# Official image
FROM python:3.12-slim

# Install poetry
RUN pip install poetry

# Working directory in the container
WORKDIR /app

# Copies the current directory contents into the container at /app
COPY . .

# Make sure the prestart script is executable
RUN chmod +x ./prestart.sh

# Install any needed packages specified in pyproject.toml
RUN poetry install

ENV PYTHONPATH=/app

# Make port available outside this container
EXPOSE 8000

# Start the application
CMD ["bash", "-c", "poetry run ./prestart.sh && poetry run uvicorn app.main:app --proxy-headers  --host 0.0.0.0 --port 8000 --reload"]
