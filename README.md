# E-Waste Management System

A comprehensive web application for managing electronic waste disposal and collection. This platform connects **Disposers** (individuals or organizations with e-waste) with **Collectors** (recyclers or collection agencies) to facilitate efficient and eco-friendly e-waste management.

## 🚀 Features

*   **Role-Based Access**:
    *   **Disposers**: Submit e-waste requests, upload images, and track status.
    *   **Collectors**: View pending requests, filter by radius/location, claim requests, and mark them as completed.
*   **Geolocation Services**:
    *   Integrated with **PostGIS** for location-based querying.
    *   **Radius Filter**: Collectors can find requests within a specific distance.
    *   **Interactive Maps**: View locations of disposers and collectors.
*   **Real-Time Chat**:
    *   Built-in chat functionality using **Socket.IO**.
    *   Enables direct communication between Disposers and Collectors for coordination.
*   **Request Management**:
    *   Full lifecycle tracking: Pending -> Accepted -> Completed.
    *   Image uploads for e-waste items.
*   **User Profiles**:
    *   Manage multiple profiles (Disposer/Collector) under a single account.
    *   Location updates and address management.
*   **Notifications**: In-app notifications for important updates.

## 🛠️ Tech Stack

*   **Backend**: Python, Flask
*   **Database**: PostgreSQL (with PostGIS extension)
*   **ORM**: SQLAlchemy, GeoAlchemy2
*   **Real-time**: Flask-SocketIO
*   **Authentication**: Flask-Login, Flask-Bcrypt
*   **Frontend**: HTML, CSS, JavaScript (Leaflet.js for maps)

## 📋 Prerequisites

Before running the project, ensure you have the following installed:

1.  **Python 3.8+**
2.  **PostgreSQL**: [Download & Install](https://www.postgresql.org/download/)
3.  **PostGIS Extension**: Required for geolocation features. [Installation Guide](https://postgis.net/install/)

## ⚙️ Installation & Setup

### 1. Clone the Repository
```bash
git clone <repository-url>
cd <repository-folder>
```

### 2. Set Up Virtual Environment (Recommended)
```bash
# Create virtual environment
python -m venv venv

# Activate it
# Windows:
venv\Scripts\activate
# Mac/Linux:
source venv/bin/activate
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```
*Note: If `requirements.txt` is missing or has issues, ensure you have the following packages:*
`Flask`, `Flask-Login`, `Flask-SQLAlchemy`, `Flask-Migrate`, `Flask-SocketIO`, `Flask-Bcrypt`, `Flask-Cors`, `GeoAlchemy2`, `geopy`, `psycopg2-binary`

### 4. Database Configuration

1.  Open **pgAdmin** or your preferred SQL tool.
2.  Create a new database named `ewaste_db`.
3.  Enable PostGIS extension in the database:
    ```sql
    CREATE EXTENSION postgis;
    ```
4.  Update the database URI in `app.py`:
    Open `app.py` and find the line:
    ```python
    app.config['SQLALCHEMY_DATABASE_URI'] = 'postgresql://postgres:YourPassword@localhost:5432/ewaste_db'
    ```
    Replace `YourPassword` with your actual PostgreSQL password.

### 5. Run the Application
```bash
python app.py
```
The application will start at `http://localhost:5000`.

## 📖 Usage Guide

1.  **Register**: Create a new account.
2.  **Create Profile**: Choose to be a **Disposer** or **Collector**.
    *   *Note: You can have one of each profile type per account.*
3.  **Disposer Flow**:
    *   Click "Submit Request".
    *   Enter item details and upload photos.
    *   Wait for a collector to claim the request.
4.  **Collector Flow**:
    *   View "Pending Requests" on the dashboard.
    *   Use the "Radius" filter to find nearby items.
    *   "Claim" a request.
    *   Use the **Chat** feature to coordinate pickup.
    *   Mark the request as "Completed" after pickup.

## 📂 Project Structure

*   `app.py`: Main application entry point, contains routes, models, and socket events.
*   `templates/`: HTML files for the frontend.
*   `static/`: CSS, JavaScript, and uploaded images.
*   `migrations/`: Database migration files.
*   `requirements.txt`: List of Python dependencies.

## ⚠️ Troubleshooting

*   **Database Connection Error**: Double-check your username, password, and database name in `app.py`. Ensure PostgreSQL service is running.
*   **PostGIS Error**: Make sure you ran `CREATE EXTENSION postgis;` in your `ewaste_db`.
*   **Map Not Loading**: Ensure you have an internet connection (Leaflet loads tiles from OpenStreetMap).

---
*Developed for E-Waste Management Project*
