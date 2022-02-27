# Usage

This app is designed for a single user. You'll want to clone the repository to the server you want to run on, then complete the following steps.

## Prepare the Environment Variables

You'll need to configure secrets for the various platforms you're connected to.

### Global Values

- `SENTRY_DSN` - This is the DSN for the Sentry.io project that you want to receive errors for this application.
- `GLOBAL_DISCORD_WEBHOOK_URL` - This is the webhook URL used for the boot notification and any error logging.
- `NODE_ENV` - Set this to `production` to enable SSL.

### Twitter Integration

You'll need to set up a developer account with Twitter.

`TWITTER_DISCORD_WEBHOOK_URL` - The webhook URL to use for Twitter notifications.
`TWITTER_USER_ID` - Your twitter account's user ID.
`TWITTER_BEARER_TOKEN` - The secret token used to authenticate your account with the Twitter API.
`TWITTER_NOTIFICATION_ROLE` - The role to ping when a Twitter notification is sent.

### Wakatime Integration

Wakatime is a code time tracking service. You'll need an account with them.

`WAKATIME_API_KEY` - Your Wakatime API key.
`WAKATIME_DISCORD_WEBHOOK_URL` - The webhook URL to use for Wakatime notifications.
`WAKATIME_NOTIFICATION_ROLE` - The role to ping when a Wakatime notification is sent.

### Uptime Robot Integration

Uptime Robot monitors your website and sends you notifications when it goes down. You'll need an account with them.

`UPTIME_SECRET` - A randomly generated string of letters and numbers used to ensure the webhook comes from Uptime Robot.
`UPTIME_DISCORD_WEBHOOK_URL` - The webhook URL to use for Uptime Robot notifications.
`UPTIME_NOTIFICATION_ROLE` - The role to ping when an Uptime Robot notification is sent.

### Sentry Integration

Sentry can monitor your applications for errors.

`SENTRY_SECRET` - A randomly generated string of letters and numbers used to ensure the webhook comes from Sentry.
`SENTRY_DISCORD_WEBHOOK_URL` - The webhook URL to use for Sentry notifications.
`SENTRY_NOTIFICATION_ROLE` - The role to ping when a Sentry notification is sent.

### GitHub Integration

GitHub is a code hosting service. You'll need an account with them.

`GITHUB_SECRET` - A randomly generated string of letters and numbers used to ensure the webhook comes from GitHub.
`GITHUB_DISCORD_WEBHOOK_URL` - The webhook URL to use for GitHub notifications.
`GITHUB_NOTIFICATION_ROLE` - The role to ping when a GitHub notification is sent.

## Configuring Your Integrations

Now you'll need to configure your integrations to work properly.

### Twitter

Your twitter integration is automatic and should begin detecting your tweets.

### Wakatime

Your WakaTime integration is automatic and will begin fetching daily stat reports from your dashboard.

### Uptime Robot

You will need to create a new Alert in your dashboard. Choose the contact type `Web-Hook`, give it a friendly name, and set the URL to `https://<your-domain.com>/uptime?secret=<your-secret>`. Then, set the POST value to `Send as JSON` and paste this:

```json
{
  "monitorID": "*monitorID*",
  "monitorURL": "*monitorURL*",
  "monitorFriendlyName": "*monitorFriendlyName*",
  "alertType": "*alertType*",
  "alertDetails": "*alertDetails*",
  "alertDuration": "*alertDuration*",
  "alertDateTime": "*alertDateTime*",
  "sslExpiryDate": "*sslExpiryDate*",
  "sslExpiryDaysLeft": "*sslExpiryDaysLeft*"
}
```

Enable this alert on any of the monitors you want to set up.

### Sentry

For each project in Sentry, you'll want to navigate to the `Alerts` settings. Under "Inactive Integrations", select "Webhooks". Paste your URL in: `https://<your-domain.com>/sentry?secret=<your-secret>`. You can click `Test Plugin` to confirm it works.

### GitHub

For each repository, navigate to `Webhooks` in the settings. Click `Add webhook`, add your Payload URL as `https://<your-domain.com>/github?secret=<your-secret>`, choose `application/json` for the content type, and select `Send me everything` (the monitor will filter out for specific events).
