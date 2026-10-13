# UploadX

A lightweight, self-hosted PHP application for managing and hosting PDF documents and images through a web dashboard.

UploadX includes an installer, authenticated dashboard, file upload and management tools, QR-code support, and optional two-factor authentication (2FA).

## Features

- Upload and manage supported PDF and image files
- Rename and delete uploaded files from the dashboard
- Generate/share file links and QR codes
- Login protection with rate limiting
- Optional two-factor authentication (2FA)
- CSRF checks and security-related HTTP headers
- File type validation and upload size limits
- Simple file-based storage; no MySQL database is required
- Responsive interface with theme support

## Tech Stack

- PHP 8+
- HTML, CSS, and vanilla JavaScript
- File-based JSON/PHP storage
- Apache `.htaccess` rules for directory protection and upload handling

## Requirements

- PHP 8 or newer
- PHP extensions: `fileinfo` (required for file type validation); `session` and standard file handling support
- A web server with PHP support
- Apache is recommended because the project uses `.htaccess`
- Write permissions for the application's `data/` and `uploads/` directories during operation

Check your hosting provider's PHP upload limits before uploading large files.

## Installation

1. Download or clone this repository to your PHP hosting environment.
2. Upload the project files to the desired website directory.
3. Ensure the `data/` and `uploads/` directories are writable by PHP.
4. Open `https://your-domain.example/path/setup.php` in your browser.
5. Follow the setup wizard to configure the application and create the initial login.
6. Sign in and review the security settings.
7. After installation, confirm that the setup wizard/installer is no longer accessible. If `setup.php` remains on the server, remove it unless the application explicitly manages its safe removal.
8. Use HTTPS for all logins and file management.

> Exact permissions and PHP limits depend on your hosting provider. Avoid setting directories to `777`; use the narrowest permissions that work for your server.

## Security Notes

- Use a unique, strong administrator password.
- Enable 2FA if available.
- Always deploy behind HTTPS.
- Keep PHP and your hosting environment updated.
- Restrict access to backups and configuration files.
- Review whether uploaded file links should be publicly accessible before using this application for sensitive documents.
- Test the installation and upload behavior on your own server before relying on it in production.
- Apache `.htaccess` protections do not automatically apply on Nginx; configure equivalent server rules if using Nginx.
- Do not commit live credentials, private configuration, real user data, uploaded documents, or production secrets to GitHub.

## Supported Upload Types

The application is designed for PDF files and common image formats, including JPEG, PNG, GIF, WebP, and AVIF. Actual support can depend on the server's PHP/file-info capabilities and configuration.

## Project Structure

```text
.
├── assets/
│   ├── app.css
│   ├── app.js
│   ├── login.js
│   ├── qr.js
│   └── theme.js
├── data/          # Runtime data; keep private and out of public version control
├── inc/
│   ├── auth.php
│   ├── core.php
│   ├── files.php
│   └── views/
├── uploads/       # Uploaded files; do not commit user uploads
├── index.php
└── setup.php
```

## License

No license has been specified yet. Unless a license is added to this repository, others do not automatically receive permission to reuse, distribute, or modify the code. Add a license file if you want to grant those permissions.

## Disclaimer

UploadX is provided as a self-hosted software project. You are responsible for configuring the server securely, deciding whether shared file links are appropriate for your use case, and testing the application before production deployment.
