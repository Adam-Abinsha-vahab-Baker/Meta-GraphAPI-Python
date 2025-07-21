# Facebook Webhook Event Monitor


A Flask-based dashboard to monitor and display Facebook Page webhook events (feed, mention, etc.) in real time, with a modern UI and persistent storage using SQLite.

Make sure your App is Live and approved in Meta Developer Account
https://developers.facebook.com

The App need to have the following permissions 
pages_read_engagement
pages_read_user_content


Also you might need to enable all the pages permissions from the webhook options
<img width="1898" height="846" alt="Screenshot from 2025-07-21 16-35-19" src="https://github.com/user-attachments/assets/c22e0f71-7d4e-450c-8bb6-0c0b074b4b5c" />


## Features

- Receives Facebook webhook events (feed, mention, etc.)
- Fetches and displays post/message details using the Facebook Graph API
- Stores all events in a local SQLite database
- Responsive, dark-themed dashboard UI with event cards
- Highlights important keywords/messages
- Status bar showing webhook status

## Setup

### 1. Clone the repository

```bash
git clone https://github.com/yourusername/facebook-webhook.git
cd facebook-webhook
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Configure environment variables

Create a `.env` file in the project root:

```
VERIFY_TOKEN=your_verify_token_here
PAGE_ACCESS_TOKEN=your_facebook_page_access_token_here
```

### 4. Run the application

```bash
python webhook.py
```

The dashboard will be available at [http://localhost:8080/events](http://localhost:8080/events).

## Facebook Webhook Setup

- Set your webhook URL to `https://your-server/webhook`
- Use the same `VERIFY_TOKEN` as in your `.env`
- Subscribe to the desired Facebook Page events (feed, mention, etc.)

## Example Webhook Test

You can test your webhook locally with:

```bash
curl -X POST http://localhost:8080/webhook \
-H "Content-Type: application/json" \
-d '{
  "entry": [{
    "changes": [{
      "field": "feed",
      "value": {
        "item": "status",
        "post_id": "44444444_444444444",
        "verb": "add",
        "published": 1,
        "created_time": 1752835204,
        "message": "GreenWave Innovations test post"
      }
    }]
  }]
}'
```

## Project Structure

```
facebook-webhook/
├── webhook.py
├── requirements.txt
├── .env
├── .gitignore
├── events.db
├── templates/
│   └── events.html
└── static/
    └── style.css
```

## Security

- **Never commit your `.env` file or access tokens to public repositories.**
- `.gitignore` is set up to protect sensitive files.

## License

MIT License

---

**Made with Flask by Adam Baker &
