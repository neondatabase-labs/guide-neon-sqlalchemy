# Running migrations in a Neon-SQLAlchemy project

This application is a simple python API using the FastAPI framework, Neon Postgres database, and SQLAlchemy to interact wiht it. It returns a list of authors and books written by them. We illustrate how to generate and run schema change migrations using the `alembic` tool.

To build this project from scratch, check out the [guide in Neon's documentation](https://neon.tech/docs/guides/sqlalchemy-migrations).

## Set up locally

You will need the following:

- A [Neon](https://neon.tech) account and a project
- Python 3.8 or higher

1. Clone this repository:

```bash
git clone https://github.com/neondatabase/guide-neon-sqlalchemy
```

2. Navigate to the project directory and create a new virtual environment:

```bash
cd guide-neon-sqlalchemy
python -m venv myenv
```

3. Activate the virtual environment and install the project dependencies:

```bash
source myenv/bin/activate
pip install -r requirements.txt
```

4. Create a `.env` file in the root of the project and add the following environment variable with your Neon database URL:

```bash
DATABASE_URL=
```

5. Run the Alembric migrations:

```bash
alembic upgrade head
```

6. Run the seed script to populate the database with some data:

```bash
python seed.py
```

7. Start the FastAPI server:

```bash
python main.py
```

8. Visit `http://localhost:8000` in your browser to see the list of authors and books. Or use curl to access the api from the terminal.

```bash
# Get the list of authors
curl http://localhost:8000/authors

# Get books by author with id 1
curl http://localhost:8000/books/1
```
