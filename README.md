# Silayar - Digital Archive Application

Silayar is a web-based digital archive system built to simplify document storage, indexing, retrieval, and user-based access management in one centralized platform.

![Desain Layout](https://raw.githubusercontent.com/Albaaaaaa/Web-Based-Digital-Archive-Management-System-with-CodeIgniter-4/main/public/assets/desain%20laayout.gif)
---

## Table of Contents
- [Overview](#overview)
- [Key Features](#key-features)
- [Tech Stack](#tech-stack)
- [System Requirements](#system-requirements)
- [Project Structure](#project-structure)
- [Quick Start](#quick-start)
- [Detailed Setup Guide](#detailed-setup-guide)
- [Configuration Notes](#configuration-notes)
- [How to Use](#how-to-use)
- [Deployment Notes](#deployment-notes)
- [Troubleshooting](#troubleshooting)
- [Roadmap Ideas](#roadmap-ideas)
- [Contributing](#contributing)
- [Template Credit](#template-credit)

---

## Overview
Silayar is designed for organizations that need a practical and user-friendly archive management workflow.  
The application is developed using CodeIgniter 4 and Bootstrap 5, with MySQL/MariaDB as the database engine.

It helps teams:
- Store archive metadata and documents in a structured way
- Search archives quickly and accurately
- Manage users and role-based permissions
- Organize records by categories and storage location

---

## Key Features
- **Archive Management**: Create, edit, and delete archive records.
- **Document Search**: Locate archives quickly using filtering and search.
- **User & Role Management**: Manage user accounts and access levels.
- **Category Organization**: Group records into archive categories.
- **Location-Based Storage**: Organize archive placement logically.
- **Download Activity Logging**: Track document download activity.

---

## Tech Stack
- **Backend**: CodeIgniter 4 (PHP)
- **Frontend**: Bootstrap 5
- **Database**: MySQL / MariaDB
- **Runtime**: Apache/Nginx or CodeIgniter built-in server

---

## System Requirements
Minimum recommended environment:
- PHP **7.4+** (recommended: PHP 8.0+)
- MySQL / MariaDB
- Web server (Apache or Nginx)
- Extensions commonly required by CodeIgniter:
  - `intl`
  - `mbstring`
  - `json`
  - `mysqli`
  - `curl` (recommended)
  - `openssl`

Optional tools:
- phpMyAdmin (for easier SQL import)
- XAMPP / Laragon / WAMP (local development stack)

---

## Project Structure
Important directories/files:

- `app/` - Main application logic (controllers, models, config, views)
- `public/` - Public web root and static assets
- `system/` - CodeIgniter framework core
- `writable/` - Logs, cache, session data, uploads
- `app/Config/App.php` - Base URL and app-level configuration
- `app/Config/Database.php` - Database connection configuration
- `.env` - Environment-level overrides
- `spark` - CodeIgniter CLI entry point
- `Silayar (Create Database in phpmyadmin (aplikasi_arsip).sql` - Database dump

---

## Quick Start
1. Place project in your local server root (e.g., `htdocs`).
2. Create database `aplikasi_arsip`.
3. Import SQL file: `Silayar (Create Database in phpmyadmin (aplikasi_arsip).sql`.
4. Verify database config in `app/Config/Database.php`.
5. Adjust `baseFolder` in `app/Config/App.php` if folder name is not `Silayar`.
6. Run with Apache/Nginx or `php spark serve`.

---

## Detailed Setup Guide

### 1) Get the source code
Clone/download this repository to your local machine, then place it in your web server root directory.

Example local locations:
- XAMPP: `C:/xampp/htdocs/`
- Laragon: `C:/laragon/www/`

If you rename the folder, remember to update `baseFolder` in `app/Config/App.php`.

### 2) Create database
Create a new database named:
- `aplikasi_arsip`

### 3) Import database schema + data
Import this SQL file from project root:
- `Silayar (Create Database in phpmyadmin (aplikasi_arsip).sql`

You can import via:
- phpMyAdmin import UI, or
- MySQL CLI import command.

### 4) Configure database credentials
Open `app/Config/Database.php` and update:
- `hostname`
- `username`
- `password`
- `database` (should be `aplikasi_arsip`)
- `port` (default `3306`)

Current defaults in source:
- host: `localhost`
- db: `aplikasi_arsip`
- user: `root`
- password: empty

### 5) Configure app base URL behavior
In `app/Config/App.php`, base URL is dynamically constructed and uses:
- `baseFolder = 'Silayar'`

If your folder is named differently, change it to your actual folder name.

### 6) Review environment file
The `.env` file exists and can be used for environment-specific overrides.

For local development, you can optionally uncomment and customize:
- `app.baseURL`
- `database.default.hostname`
- `database.default.database`
- `database.default.username`
- `database.default.password`

### 7) Ensure writable directories are writable
Make sure the web server can write to:
- `writable/cache`
- `writable/logs`
- `writable/session`
- `writable/uploads`

### 8) Run the app

#### Option A: Through Apache/Nginx (recommended for this project structure)
- Start Apache and MySQL services.
- Access the app from browser:
  - `http://localhost/Silayar/`
  - or your custom folder path.

#### Option B: CodeIgniter built-in server
From project root:

```bash
php spark serve
```

Then open:
- `http://localhost:8080`

### 9) Login
After SQL import, user data is available in database table `user`.

Note:
- Passwords are stored as hashes.
- If you do not know the plain password for seeded accounts, reset one directly in database or create a new user through your preferred admin workflow.

---

## Configuration Notes

### Application config
- Main file: `app/Config/App.php`
- Relevant part: dynamic base URL and custom folder mapping

### Database config
- Main file: `app/Config/Database.php`
- Default database name in code: `aplikasi_arsip`

### Environment mode
- Defined in `.env`:
  - `CI_ENVIRONMENT = development`
- For production, switch to `production` and review error display/security settings.

---

## How to Use
Typical usage flow:
1. Open the application URL.
2. Login with a valid user account.
3. Create archive records and upload/attach files where applicable.
4. Assign categories and storage/location metadata.
5. Use search to retrieve documents quickly.
6. Manage users/roles according to organizational access policy.
7. Monitor download activity logs for traceability.

---

## Deployment Notes
For production deployment:
- Use a dedicated web server with HTTPS enabled.
- Set `CI_ENVIRONMENT` to `production`.
- Restrict direct access to sensitive files and directories.
- Confirm `writable/` permissions are secure and minimal.
- Use strong DB credentials (do not keep default root/no-password setup).
- Configure regular database and file backups.

---

## Troubleshooting

### 1) Database connection error
- Verify credentials in `app/Config/Database.php`.
- Ensure MySQL/MariaDB service is running.
- Ensure database `aplikasi_arsip` exists and import is complete.

### 2) 404 / base URL mismatch
- Check folder name and adjust `baseFolder` in `app/Config/App.php`.
- Ensure your web server document root/path is correct.

### 3) Session/log/cache write failures
- Fix filesystem permissions for `writable/` subfolders.
- On Windows local setups, try running web server with proper privileges.

### 4) SQL import errors
- Recreate empty `aplikasi_arsip` database and re-import SQL.
- Ensure MySQL/MariaDB version compatibility.

### 5) Unable to login with imported users
- Seeded passwords are hashed; plain password may be unknown.
- Reset a user password in DB to a known hash or create a new account.

---

## Roadmap Ideas
Potential enhancements:
- Document versioning and approval workflow
- Full audit trail dashboard
- Advanced search indexing
- API endpoints for external integrations
- Unit and integration test coverage

---

## Contributing
Contributions are welcome. Suggested workflow:
1. Fork the repository.
2. Create a feature branch.
3. Make focused changes with clear commit messages.
4. Test your changes locally.
5. Open a pull request with a concise summary.

---

## Template Credit
This application was originally based on a template from **Jago Web Dev**, developed by **Alba** and **Apip**.

