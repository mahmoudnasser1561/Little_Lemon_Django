# Little Lemon Django

A Django web app for a restaurant website with menu pages and table reservations.

## Features

- Public pages: home and about
- Menu listing and single menu item view
- Reservation form (`Booking` model via `ModelForm`)
- Reservations page that shows saved bookings in JSON format

## Tech Stack

- Python 3.9+
- Django (from `Pipfile`)
- MySQL
- `mysqlclient` (MySQL driver for Django)

## Project Structure

- `littlelemon/` - project settings and root URLs
- `restaurant/` - main app (models, views, forms, templates, static files)
- `manage.py` - Django management entry point

## Setup

1. Install dependencies:

```bash
pipenv install
```

2. Activate virtual environment:

```bash
pipenv shell
```

3. Create a MySQL database named `reservations`.

4. Update DB credentials in `littlelemon/settings.py`:

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'reservations',
        'HOST': '127.0.0.1',
        'PORT': '3306',
        'USER': 'root',
        'PASSWORD': 'YOUR_PASSWORD',
    }
}
```

5. Run migrations:

```bash
python3 manage.py makemigrations
python3 manage.py migrate
```

6. Start the development server:

```bash
python3 manage.py runserver
```

7. Open:

- `http://127.0.0.1:8000/`

## Routes

- `/` - home page
- `/about/` - about page
- `/menu/` - menu list
- `/menu_item/<int:pk>/` - menu item details
- `/book/` - create reservation (GET form, POST submit)
- `/bookings/` - view reservations

## Models

### Booking

- `first_name` (`CharField`)
- `reservation_date` (`DateField`)
- `reservation_slot` (`SmallIntegerField`)

### Menu

- `name` (`CharField`)
- `price` (`IntegerField`)
- `menu_item_description` (`TextField`)

## Troubleshooting

- `ModuleNotFoundError: No module named 'MySQLdb'`:
  - Ensure `mysqlclient` is installed in your environment (`pipenv install`).
  - On Linux, you may also need system packages like MySQL client dev headers.
- If reservations do not appear, confirm migrations were applied and the app points to the expected MySQL database.

## License

This project is distributed under the terms in `LICENSE`.
