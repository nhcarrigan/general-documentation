# Self-Hosting

This guide is for setting up and managing your own instance of the bot.

## Prerequisites

- Node.js 20
- `pnpm` version 8 (check the `package.json` file for the specific version required)
- A Discord bot configured in the [Discord Developer Portal](https://discord.com/developers/applications)

> [!TIP]
> This code is intended to run in a single server. You should disable the `Public Bot` option in your application's bot settings.

## Bot Permissions

> [!NOTE]
> The bot requires the `Message Content` intent - ensure that is enabled in your application's bot settings.

The bot requires the following permissions:

- Send Messages
- View Channels/Read Messages

Be sure to invite it to your server with both the `bot` scope.

## Installation

First, clone the repository to the location you want to host the bot (e.g. a VPS).

```bash
git clone git@github.com:nhcarrigan/100-days-of-code-bot.git
```

Next, change to the project directory and install the dependencies.

```bash
cd 100-days-of-code-bot
pnpm install
```

## Environment Variables

You will need to configure a few environment variables. The repository includes a template to start from:

```bash
cp sample.env .env
```

> [!WARNING]
> Do not add your secrets to the `sample.env` file - this file is version controlled and you may inadvertently leak the contents.

Fill in the environment variables with the following values:

- `TOKEN`: This is the bot token obtained from the Discord Developer portal.
- `DEBUG_HOOK`: This is a URL to a Discord webhook where error messages will be sent. You can create a webhook in the channel settings, under `Integrations`.
- `HOME_GUILD`: This is the ID for the Discord server you want the bot to run in. [Don't know how to get that?](https://dis.gd/findid)
- `POST_CHANNEL`: This is the ID for the channel you want the bot to post daily reminders in.

## Configuration

In the `src/config/DailyMessage.ts` file, you can set the message that is posted every day. If you would like to ping a role, use the `<@&${role.id}>` syntax.

In the `src/index.ts` file, you can edit the `scheduleJob()` call to set the time (based on the system time where the code is running) that the post should be made.

In the `src/index.ts` file, you can edit the `message.author.id` check to look for *your* ID, allowing you to trigger manual posts if desired.

## Build the Code

> [!WARNING]
> You will need to build the code every time it is updated. Updates happen when:
>
> - You change the responses mentioned above
> - You pull changes from the repository with `git pull`
>
> Updates do NOT happen when you change the environment variables. You will only need to restart, not rebuild.

Because the project uses TypeScript, you need to compile it to JavaScript.

```bash
pnpm run build
```

## Run the Bot

You can run the bot directly from the command line:

```bash
pnpm start
```

However, we **strongly** recommend using `pm2` to manage the process in the background. You can install `pm2` with:

```bash
pnpm install -g pm2
```

Then, you can start the background process with:

```bash
pm2 start "pnpm start"
```

You can optionally name the process:

```bash
pm2 start "pnpm start" --name "100DoC"
```
