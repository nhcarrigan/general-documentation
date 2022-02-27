# Usage

If you'd like to run your own version of this project, you'll need to follow these steps (assuming you have cloned the repository from GitHub).

## Environment Variables

Copy the `sample.env` file to a file named `.env`, and provide the following values:

- `SENTRY_DSN` - This is a DSN from Sentry.io, an error monitoring service.
- `DEBUG_HOOK` - This is a Discord Webhook URL, to send debug messages to a Discord server.

## Running the Application

Use `npm ci` to install the necessary dependencies, `npm run build` to compile the TypeScript, and `npm start` to launch the application.

Note that if you are running your battlesnake locally, you'll need to use a service like `ngrok` to create a tunnel to your server. We recommend hosting your application on a VPS, such as DigitalOcean, and creating a DNS record with your domain to point to the server.

Once you have it running and DNS configured, you can add your battlesnake at https://play.battlesnake.com and start playing!
