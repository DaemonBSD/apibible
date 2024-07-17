# Webhooks

Webhooks enable instant updates and notifications between systems using HTTP callbacks.

## Key Features

- **Real-Time Communication**: Sends data in real-time between systems.
- **Efficiency**: Reduces the need for constant API polling.
- **Simplicity**: Uses HTTP POST to send data.

## Example Usage

A common example of using Webhooks is in payment platforms that send notifications to a server about the status of a transaction.

### Setting Up a Webhook

1. **Webhook Server**: Create a server to receive notifications.

```javascript
const express = require('express');
const app = express();
app.use(express.json());

app.post('/webhook', (req, res) => {
  console.log('Webhook received:', req.body);
  res.status(200).send('Webhook received');
});

app.listen(3000, () => console.log('Server is running on port 3000'));
```

2. **Webhook Client**: Configure the system to send data to the server.

```bash
curl -X POST http://localhost:3000/webhook -H "Content-Type: application/json" -d '{"message": "Hello, Webhooks!"}'
```

# Applicability and Use Cases

## Applicability

Webhooks are ideal for systems requiring real-time notifications and efficient state updates.

## Use Cases

1. **Payment Platforms**:

   - Notifies servers about changes in payment status, such as a transaction success or failure.

2. **Messaging Services**:

   - Sends notifications when a new message is received or read.

3. **Software Integrations**:

   - Connects different applications, allowing an action in one system to trigger events in another.

# Testing Webhooks

To test Webhooks, you can use tools like Ngrok to expose your local server and test notifications from external services.

## Using Ngrok

1. **Install Ngrok**: Follow instructions on [ngrok.com](https://ngrok.com/).

2. **Expose your server**:

```bash
ngrok http 3000
```

3. **Use the URL provided by Ngrok** to configure the webhook in the system you are testing.

# Additional Resources

[Official Webhooks Documentation](https://en.wikipedia.org/wiki/Webhook)

## Credits

Created by [Carlos Costa](https://www.linkedin.com/in/carlos-costa-0b548675/).

#

[Back to Home](README.en.md)
