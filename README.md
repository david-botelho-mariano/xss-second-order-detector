# Second-Order XSS detector

This project is designed to detect second-order XSS vulnerabilities. Burp Suite is used to inject XSS payloads, and for each request, Selenium opens a specific page to check if the payload triggers an HTTP call to the Burp Collaborator.

## Workflow
1. Burp Suite: Sends XSS payloads through normal requests.
2. Flask & Selenium: For every outgoing request, the Burp Suite extension triggers the Flask app, which opens a specific page using Selenium.
3. XSS Detection: The Selenium browser observes whether the payload triggers an action on the target page (e.g., an HTTP call to Burp Collaborator).
4. Burp Collaborator: If the payload triggers an HTTP call, it is captured by the Burp Collaborator, confirming that the XSS vulnerability exists.

## Prerequisites

- Python 3.x
- Flask
- Selenium
- WebDriver Manager
- Burp Suite with Collaborator
- Chrome Browser (for Selenium)

## Installation

```bash
git clone https://github.com/david-botelho-mariano/xss-second-order-checker/
cd your-repo
pip install Flask selenium webdriver-manager
python xss-second-order-detector-server.py
```

