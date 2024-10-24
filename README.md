# Second-order XSS detector

This project is designed to detect second-order XSS vulnerabilities. Burp Suite is used to inject XSS payloads, and for each request, Selenium opens a specific page to check if the payload triggers an HTTP call to the Burp Collaborator.

## Workflow
1. Burp Suite: Sends XSS payloads through HTTP requests.
2. Flask & Selenium: For every outgoing request, the Burp Suite extension triggers the Flask app, which opens a specific page using Selenium.
3. XSS Detection: The Selenium browser observes whether the payload triggers an action on the target page (e.g., an HTTP call to Burp Collaborator).
4. Burp Collaborator: If the payload triggers an HTTP call, it is captured by the Burp Collaborator, confirming that the XSS vulnerability exists.

## Installation and configuration of `xss-second-order-detector-server.py`

1. Clone the repository:
```bash
git clone https://github.com/david-botelho-mariano/xss-second-order-detector
```

2. Navigate into the project directory:
```bash
cd xss-second-order-detector
```

3. Install the required dependencies:
```bash
pip install Flask selenium webdriver-manager
```

4. Update the target URL:
The url variable of `xss-second-order-detector-server.py` file should be updated to the page where the user wants to monitor for XSS execution. Change the line to the appropriate target URL that will reflect the response or data where the XSS payload might execute. This page is where Selenium will check if the injected XSS payload triggers a callback or action.

5. Run the Flask server:
```bash
python xss-second-order-detector-server.py
```

## Installation and configuration of `xss-second-order-detector-client.py`

1. Open Burp Suite and go to the Extender tab.
2. In the Extender tab, go to the Extensions sub-tab
3. Click Add.
4. In the Extension Details window, select Extension Type as Python.
5. For Extension File, browse and select the `xss-second-order-detector-client.py` file from this repository.
