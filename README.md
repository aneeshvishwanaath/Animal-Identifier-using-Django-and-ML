# Animal Identifier using Machine Learning

This project is a Django-based web application that identifies animals in images using machine learning models. It provides additional facts about the identified animal. Swagger is used for API testing and documentation.

## Features

- Upload images for animal identification
- Use machine learning models to classify animals
- Provide 10 interesting facts about the identified animal
- API endpoints for image uploads and animal facts retrieval
- Swagger documentation for easy API testing

## Table of Contents

- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [API Documentation](#api-documentation)
- [Contributing](#contributing)
- [License](#license)

## Installation

### Prerequisites

- Python 3.8+
- Django 3.2+
- TensorFlow or PyTorch (depending on the models used)
- MySQL 5.7+
- pip

### Steps

1. **Clone the repository:**

    ```bash
    git clone https://github.com/aneeshvishwanaath/Animal-Identifier-using-ML.git
    cd Animal-Identifier-using-ML
    ```

2. **Create a virtual environment and activate it:**

    ```bash
    python3 -m venv env
    source env/bin/activate  # On Windows, use `env\Scripts\activate`
    ```

3. **Install the required packages:**

    ```bash
    pip install -r requirements.txt
    ```

4. **Configure the database settings in `settings.py`:**

    ```python
    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.mysql',
            'NAME': 'your_database_name',
            'USER': 'your_database_user',
            'PASSWORD': 'your_database_password',
            'HOST': 'localhost',
            'PORT': '3306',
        }
    }
    ```

5. **Run migrations:**

    ```bash
    python manage.py migrate
    ```

6. **Start the development server:**

    ```bash
    python manage.py runserver
    ```

## Configuration

### Main Project Configuration (main project urls.py)

In the main project's `urls.py`, include the app URLs:

```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('animal/', include('animal_identifier.urls')),  # Replace 'animal_identifier' with your app's name
]
```

### App Configuration (app's urls.py)

In your app's `urls.py`, define the URL patterns:

```python
from django.urls import path
from . import views

urlpatterns = [
    path('upload/', views.upload_image, name='upload_image'),
    path('facts/<str:animal>/', views.animal_facts, name='animal_facts'),
]
```

## Usage

1. **Upload Image:**
   - Navigate to `/animal/upload/` to access the upload interface.
   - Select an image file and upload it.

2. **View Animal Facts:**
   - Navigate to `/animal/facts/<animal>/` to view 10 facts about the identified animal. Replace `<animal>` with the identified animal.

## API Documentation

### Endpoints

1. **Upload Image:**
   - **URL:** `/animal/upload/`
   - **Method:** POST
   - **Description:** Uploads an image file and identifies the animal.
   - **Parameters:** `file` (multipart/form-data)

2. **Get Animal Facts:**
   - **URL:** `/animal/facts/<animal>/`
   - **Method:** GET
   - **Description:** Retrieves 10 facts about the identified animal.
   - **Parameters:** `animal` (path parameter)

### Swagger

Swagger is used for API documentation and testing. To access the Swagger UI, navigate to `/swagger/`.

## Contributing

Contributions are welcome! Please open an issue or submit a pull request for any changes or enhancements.

## License

This project is licensed under the MIT License.
