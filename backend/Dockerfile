# Use an official Python image as the base image

FROM python:3.10

# Update and install pip
# RUN apt-get update && apt-get install -y python3-pip

# Install Poetry
RUN curl -sSL https://install.python-poetry.org | python3 - --git https://github.com/python-poetry/poetry.git@master

# Install sqlmodel using pip
# RUN pip install sqlmodel

# Add the directory containing uvicorn to the PATH
ENV PATH="/root/.local/bin:$PATH"

# Set the working directory in the container
WORKDIR /app

# Copy the entire project to the working directory
COPY . /app

# Copy the poetry files and install the dependencies
COPY pyproject.toml poetry.lock ./
RUN poetry install

# Expose port 8000
EXPOSE 8000

# Command to start the FastAPI server
# CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]
CMD ["bash", "-c", "poetry run bash ./prestart.sh && poetry run uvicorn app.main:app --reload --host 0.0.0.0"]