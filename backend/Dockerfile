# Use an official Python image as the base image

FROM python:3.10

# Set the working directory in the container
WORKDIR /app

# Install Poetry
RUN curl -sSL https://install.python-poetry.org | python3 - --git https://github.com/python-poetry/poetry.git@master

# Add Poetry to the PATH
ENV PATH="/root/.local/bin:$PATH"

# Copy the entire project to the working directory
COPY . /app

# Install the dependencies using Poetry
RUN poetry install

# # Make sure the prestart script is executable
RUN chmod +x ./prestart.sh

# Expose port 8000
EXPOSE 8000

# Command to start the FastAPI server
CMD ["bash", "-c", "poetry run bash ./prestart.sh && poetry run uvicorn app.main:app --reload --host 0.0.0.0"]
