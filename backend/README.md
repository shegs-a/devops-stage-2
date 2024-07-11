# Backend - FastAPI with PostgreSQL

This directory contains the backend of the application built with FastAPI and a PostgreSQL database.

## Prerequisites

- Python 3.8 or higher
- Poetry (for dependency management)
- PostgreSQL (ensure the database server is running)

### Installing Poetry

To install Poetry, follow these steps:

```sh
curl -sSL https://install.python-poetry.org | python3 - --git https://github.com/python-poetry/poetry.git@master
```

Add Poetry to your PATH (if not automatically added):

## Setup Instructions

1. **Navigate to the backend directory**:
    ```sh
    cd backend
    ```

2. **Install dependencies using Poetry**:
    ```sh
    poetry install
    ```

3. **Set up the postgres database server**:
    Please refer to the [postgres installation guide](https://www.postgresql.org/download/) for your operating system.
    Also ensure to follow the instructions on the postgress installation guide to create a database and a user with the necessary permissions.
    The database name, user and password are set in the `.env` file.

4.  **Set up the database with the necessary tables**:
    ```sh
    # Add executable permissions to the file
    chmod +x ./prestart.sh

5. **Set up the database with the necessary tables**:
    ```sh
    # Add executable permissions to the file
    chmod +x ./prestart.sh

    # Run the script
    poetry run bash ./prestart.sh # remove the bash command if you are on MacOS. Just 'poetry run ./prestart.sh' will work.
    ```

5. **Run the backend server**:
    ```sh
    poetry run uvicorn app.main:app --reload
    ```

6. **Update configuration**:
   Ensure you update the necessary configurations in the `.env` file, particularly the database configuration.
