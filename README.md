# Telecom OSS Provisioning System

A Django and Django REST Framework foundation for building a telecom Operations Support System (OSS). The project is organized around customer management, service inventory, provisioning workflows, notifications, auditing, and operational dashboards.

> **Project status:** Early development. The Django project structure and domain applications are in place. Business models, REST endpoints, authentication flows, background jobs, and production deployment configuration are planned work.

## Current capabilities

- Django 6.1 project configured with Django REST Framework
- Separate domain applications for accounts, customers, inventory, services, provisioning, audit, notifications, and dashboards
- Django admin available at `/admin/`
- Local SQLite database for development
- Environment-based configuration for `SECRET_KEY` and `DEBUG`
- Python virtual environments, local databases, caches, and `.env` files excluded from Git

## Planned architecture

| Application | Intended responsibility |
| --- | --- |
| `accounts` | Users, roles, permissions, and authentication |
| `customers` | Customer and account information |
| `inventory` | Network resources and available capacity |
| `services` | Telecom service catalogue and service instances |
| `provisioning` | Provisioning requests, workflow state, and orchestration |
| `audit` | Operational and security audit records |
| `notifications` | Provisioning status and failure notifications |
| `dashboard` | Operational summaries and key metrics |

## Technology stack

- Python 3
- Django 6.1
- Django REST Framework
- python-decouple
- SQLite for local development
- PostgreSQL driver included for future production configuration
- Simple JWT dependencies included for planned token authentication

Redis, Celery, Docker, and JWT endpoints are roadmap items and are not configured yet.

## Local setup

### 1. Clone the repository

```bash
git clone https://github.com/sohitmathurkar/telecom-oss-provisioning-system.git
cd telecom-oss-provisioning-system
```

### 2. Create and activate a virtual environment

Windows PowerShell:

```powershell
python -m venv venv
.\venv\Scripts\Activate.ps1
```

macOS or Linux:

```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install dependencies

```bash
python -m pip install -r requirements.txt
```

### 4. Configure the environment

Create a `.env` file in the project root:

```dotenv
SECRET_KEY=replace-with-a-long-random-secret
DEBUG=True
```

The `.env` file is ignored by Git. Never commit production secrets.

### 5. Initialize the database

```bash
python manage.py migrate
python manage.py createsuperuser
```

### 6. Run the development server

```bash
python manage.py runserver
```

Open `http://127.0.0.1:8000/admin/` to access Django admin.

## Validation and tests

Run Django's configuration checks:

```bash
python manage.py check
```

Run the test suite:

```bash
python manage.py test
```

The application test modules are currently placeholders. Adding model and API tests is part of the roadmap.

## Roadmap

- Define customer, service, resource, and provisioning domain models
- Add serializers and versioned REST API routes
- Implement JWT authentication and role-based access control
- Build provisioning state transitions and failure handling
- Add audit events and notifications
- Configure PostgreSQL for production environments
- Add Celery and Redis for asynchronous provisioning jobs
- Add automated tests, API documentation, Docker, and CI
- Build dashboard views and deployment documentation

## Contributing

Keep commits focused and include tests for new behavior. Before opening a pull request, run:

```bash
python manage.py check
python manage.py test
```

## License

See [LICENSE](LICENSE).
