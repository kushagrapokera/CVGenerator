# CV Generator

## Overview
CV Generator is a Django-based web application that allows users to create, store, and download professional resumes in PDF format. The application features a form for users to input their details, a database for storing multiple profiles, and a list view to access or download stored resumes.

## Features
- **Form Submission**: Users can fill out a form with their details, including name, email, phone, education, skills, and work experience.
- **Profile Storage**: All submitted profiles are stored in a database.
- **PDF Generation**: Resumes are generated in PDF format using `pdfkit` and `wkhtmltopdf`.
- **Resume List**: A page listing all stored profiles with options to download resumes.

## Prerequisites
To run this project locally, ensure you have the following installed:

- Python (3.6 or higher)
- Django (3.0 or higher)
- wkhtmltopdf (for PDF generation)
- Bootstrap (for frontend styling)

## Installation
1. Clone the repository:
    ```bash
    git clone https://github.com/yourusername/cv-generator.git
    cd cv-generator
    ```

2. Install the required Python packages:
    ```bash
    pip install -r requirements.txt
    ```

3. Configure wkhtmltopdf:
   - Download and install `wkhtmltopdf` from [https://wkhtmltopdf.org/downloads.html](https://wkhtmltopdf.org/downloads.html).
   - Note the installation path, e.g., `C:\wkhtmltox\bin\wkhtmltopdf.exe`.

4. Apply database migrations:
    ```bash
    python manage.py migrate
    ```

5. Run the development server:
    ```bash
    python manage.py runserver
    ```

6. Open your browser and navigate to `http://127.0.0.1:8000/`.

## Usage

### Submitting a Profile
1. Visit the home page (`/`).
2. Fill out the form with your details.
3. Submit the form to save the profile.

### Viewing and Downloading Resumes
1. Navigate to `/list/` to view a list of all profiles.
2. Click the "Download CV" button to download a profile’s resume in PDF format.

## File Structure
```
project_root/
|-- mysite/
|   |-- settings.py
|   |-- urls.py
|   |-- wsgi.py
|-- pdf/
|   |-- migrations/
|   |-- templates/
|   |   |-- pdf/
|   |   |   |-- accept.html
|   |   |   |-- resume.html
|   |   |   |-- list.html
|   |-- models.py
|   |-- views.py
|   |-- admin.py
|-- manage.py
|-- requirements.txt
```

### Key Files
- `views.py`: Contains the main logic for handling requests and generating PDFs.
- `models.py`: Defines the `Profile` model for storing user data.
- `templates/`: Contains the HTML templates for rendering pages.
- `urls.py`: Maps URLs to views.

## Configuration

### Setting Up wkhtmltopdf
Update the `resume` view in `views.py` with the correct path to `wkhtmltopdf`:
```python
config = pdfkit.configuration(wkhtmltopdf=r'C:\path\to\wkhtmltopdf.exe')
```

### Updating Database
If you modify the `Profile` model, apply migrations to update the database schema:
```bash
python manage.py makemigrations
python manage.py migrate
```

## Dependencies
- Django
- pdfkit
- wkhtmltopdf
- Bootstrap

## Future Enhancements
- Add authentication for profile management.
- Support multiple resume templates.
- Provide options to customize PDF styles.

## Troubleshooting
- **PDF Generation Error**: Ensure `wkhtmltopdf` is correctly installed and configured.
- **Static Files Not Loading**: Confirm Bootstrap is linked properly in the templates.

## License
This project is open-source and available under the MIT License.

