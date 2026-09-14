# PHP-Extract-PDF-Text

A simple PHP web app that lets you upload a PDF file and extracts its text content, displayed directly on the page.

**A ready-to-use desktop build is available in [`/dist`](./dist) — `run-extract-pdf-text.exe` (a PHP Desktop/CEF-wrapped app bundling PHP itself, so no separate PHP or web server install is required).**

## Description

The app presents a single upload form. Once a PDF is selected and submitted, it's parsed server-side using the `smalot/pdfparser` library, and the extracted text is displayed on the same page.

## Features

- Upload a PDF file through a simple web form
- Validates that only `.pdf` files are accepted
- Extracts and displays the PDF's text content on the page
- Clear status messages for invalid file types or missing selections

## Tech Stack

- **PHP**
- [`smalot/pdfparser`](https://github.com/smalot/pdfparser) `^2.11` (via Composer)
- [Bulma CSS](https://bulma.io/) (bundled) — page styling
- [Font Awesome](https://fontawesome.com/) (via CDN) — icons
- Packaged desktop build via **PHP Desktop** (Chrome/CEF-based wrapper)

## Prerequisites

- **To run the packaged desktop build:** none — it's self-contained (Windows only)
- **To run as a standard PHP web app:** PHP with Composer

## Installation

Clone the repository:

```bash
git clone https://github.com/paoradox/PHP-Extract-PDF-Text.git
cd PHP-Extract-PDF-Text
```

Install PHP dependencies:

```bash
composer install
```

(A `composer.phar` is also bundled in the repo if Composer isn't installed globally — run `php composer.phar install` instead.)

## Usage

### Option 1: Run the packaged desktop build (recommended, Windows)

Run `run-extract-pdf-text.exe` from [`/dist/PHP Desktop Chrome_Extract_PDF_Text`](./dist) directly — it bundles its own PHP runtime and opens the app in a desktop window, no separate PHP or server setup needed.

### Option 2: Run as a PHP web app

Start a local PHP server from the project root:

```bash
php -S localhost:8000
```

Then open `http://localhost:8000` in your browser.

### Using the app

1. Click **Choose a file** and select a PDF.
2. Click **Extract Text**.
3. The extracted text appears under "Extracted Text Result."

## Project Structure

```
PHP-Extract-PDF-Text/
├── dist/
│   └── PHP Desktop Chrome_Extract_PDF_Text/   # Packaged desktop app (PHP Desktop/CEF wrapper)
│       ├── run-extract-pdf-text.exe            # Packaged executable
│       ├── www/                                 # Bundled copy of the app + PHP runtime
│       ├── php/                                 # Bundled PHP runtime
│       └── settings.json                        # PHP Desktop window/runtime settings
├── css/
│   ├── bulma.css / bulma.min.css / bulma.css.map
├── js/
│   ├── bulma.file.js
│   ├── bulma.modal.js
│   ├── bulma.navbar.js
│   └── bulma.tab.js
├── index.php               # Main app — upload form and PDF text extraction
├── composer.json            # Declares the smalot/pdfparser dependency
├── composer.lock
└── composer.phar             # Bundled Composer executable
```

## Credits

The PDF-extraction approach is based on a tutorial by [CodexWorld](https://www.codexworld.com/extract-text-from-pdf-using-php/) ("Extract Text from PDF using PHP," 2024), as credited in the app's own footer.

## License

Apache License 2.0
