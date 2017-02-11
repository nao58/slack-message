# slack-message

A very simple wrapper to send a message to slack.

## Usage

Very simple payload

```
slack-message -h https://hook.slack.com/services/xxxxxxxxxxxx --username "Test bot" --text "This is a test message to slack."
```

More complex payload

```
cat <<EOF | slack-message -h https://hooks.slack.com/services/xxxxxxxxxxxxxxx
  "attachments": [
    {
      "fallback": "Required plain-text summary of the attachment.",
      "color": "#36a64f",
      "pretext": "Optional text that appears above the attachment block",
      "author_name": "Bobby Tables",
      "author_link": "http://flickr.com/bobby/",
      "author_icon": "http://flickr.com/icons/bobby.jpg",
      "title": "Slack API Documentation",
      "title_link": "https://api.slack.com/",
      "text": "Optional text that appears within the attachment",
      "fields": [
        {
          "title": "Priority",
          "value": "High",
          "short": false
        }
      ],
      "image_url": "http://my-website.com/path/to/image.jpg",
      "thumb_url": "http://example.com/path/to/thumb.png",
      "footer": "Slack API",
      "footer_icon": "https://platform.slack-edge.com/img/default_application_icon.png",
      "ts": 123456789
    }
  ]
EOF
```

## Options

| Option     | Description                                       |
| ---------- | ------------------------------------------------- |
| d          | Debug mode (Just show the payload json to send)   |
| f filename | Specify payload file                              |
| h url      | Slack webhook URL                                 |
| o          | Open the web browser to confirm message format    |

Slack webhook URL `h` is required unless defining environment variable `$SLACK_WEBHOOK_URL` .

You cannot put payload by multiple ways at same time.

## References

* [Incoming Webhooks](https://api.slack.com/incoming-webhooks)
* [An introduction to messages](https://api.slack.com/docs/messages)
