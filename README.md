# mysite

Base Django project with a `blog` app.

- Repository: https://github.com/cjristian/mysite.git
- Default branch: `main`
- `.gitignore` for Python/Django (ignores `__pycache__/`, `db.sqlite3`, virtual envs, etc.)

## Requirements
- Python 3.11 or 3.12
- `pip` and optionally `venv`

## Getting Started (local)
1) Clone the repo
    git clone https://github.com/cjristian/mysite.git
    cd mysite

2) Create and activate a virtual environment
    # Windows (PowerShell)
    python -m venv .venv
    .\.venv\Scripts\Activate.ps1
    # macOS/Linux (bash/zsh)
    # python -m venv .venv
    # source .venv/bin/activate

3) Install minimal dependencies
    pip install "Django>=4.2,<5.0"

4) Prepare the database (SQLite by default)
    python manage.py migrate

5) (Optional) Create a superuser for admin
    python manage.py createsuperuser

6) Run the server
    python manage.py runserver

- Admin: http://127.0.0.1:8000/admin/
- Local DB file (`db.sqlite3`) is ignored by Git.

## Project Structure
- `manage.py`: Django management utility.
- `mysite/`: project settings (`settings.py`), URLs, WSGI/ASGI.
- `blog/`: example app with `models.py`, `views.py`, `admin.py`, `migrations/`.

## Tests
    python manage.py test

## Git Workflow (team-friendly)
- `main`: always stable and deployable.
- `dev`: integration branch before promoting to `main`.
- `feature/*`: work per task/issue → PR into `dev` → review → merge → PR from `dev` to `main` for release.

Useful commands to start the suggested flow:
    # Create integration branch
    git checkout -b dev
    # Push and set upstream
    git push -u origin dev

    # Create a feature branch and open PR against dev
    git checkout -b feature/task-name
    # ... commits ...
    git push -u origin feature/task-name

## Continuous Integration (GitHub Actions)
Recommended to add a workflow that installs deps and runs tests on every push/PR to `dev` and `main`.

Suggested path: `.github/workflows/ci.yml`.

## Deployment
TBD (e.g., Render, Fly.io, Railway, Docker, etc.).

## Notes
- Repo initialized and published on GitHub.
- If you add dependencies, consider `requirements.txt` or `pyproject.toml`.
