# Self Hosting

This application is designed to support a single Discord server. As such, there are some configurations you will need to adjust to make it work for your server. Assuming you have cloned the GitHub repository...

## Environment Variables

Copy the `sample.env` file to a file named `.env` and complete the following values:

- `DISCORD_TOKEN` - The token for your Discord Bot Application.
- `SENTRY_DSN` - The DSN for your Sentry.io project.
- `DEBUG_HOOK` - The Discord Webhook URL for your debug channel.

## Configuration

Within the `/src/config/roles.ts` file, you'll need to edit the following values.

The `boosterRole` value should be the **ID** of your server's `Server Booster` role.

The `colourRoles` value is an array of Discord role IDs. These are the roles the bot should look for and remove when someone loses the `boosterRole` role.

## Running the Application

Use `npm ci` to install the necessary dependencies, `npm run build` to compile the TypeScript, and `npm start` to launch the application.

Your bot will go online and be ready to monitor your Discord server. Note that you should only add your bot to a single server, or your IDs will not line up properly.
