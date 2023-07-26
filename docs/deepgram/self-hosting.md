# Self-Hosting

This guide is for setting up and managing your own instance of the bot.

## Prerequisites

- Node.js 18
- `pnpm` version 8 (check the `package.json` file for the specific version required)
- A Discord bot configured in the [Discord Developer Portal](https://discord.com/developers/applications)

> [!NOTE]
> The bot requires the `Message Content` intent - ensure that is enabled in your application's bot settings.

> [!TIP]
> This code is intended to run in a single server. You should disable the `Public Bot` option in your application's bot settings.

## Installation

First, clone the repository to the location you want to host the bot (e.g. a VPS).

```bash
git clone git@github.com:nhcarrigan/deepgram-bot.git
```

Next, change to the project directory and install the dependencies.

```bash
cd deepgram-bot
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
- `HOME_GUILD_ID`: This is the ID for the Discord server you want the bot to run in. [Don't know how to get that?](https://dis.gd/findid)
- `DEBUG_HOOK`: This is a URL to a Discord webhook where error messages will be sent. You can create a webhook in the channel settings, under `Integrations`.
- `HELPER_ROLE_IDS`: This is a list of role IDs that you want to be identified as server helpers (people with permission to use all of the bot's features). This should be a comma-separated list (NO SPACES). For example: `HELPER_ROLE_IDS="875177422654406707,935355569278181396"`
- `HELP_CHANNEL_ID`: This is the ID for the channel that questions should be reposted in. This **must** be a forum channel, or the bot will error out on loading.
- `GENERAL_CHANNEL_ID`: This is the ID for your general chat channel. The sticky message will be posted here.
- `STICKY_MESSAGE_FREQUENCY`: This is the number (in **minutes**) between sticky message updates. The bot will wait this long before sending the sticky message again.
- `AI_URL`: This is the base URL for API requests to your AI service. This should not include any paths. For example: `https://docs.nhcarrigan.com`.

## Use without AI

If you would like to use this bot without the AI functionality, leave the `AI_URL` value empty in the `.env` file. Without this, the bot will not generate an AI response or create the reply message with the buttons.

You will still be able to use the `help` command to move questions to a forum, and the bot will still send sticky messages in the configured general channel.

## Configuration

Most of the bot's responses can be edited directly in the `src/config/Responses.ts` file. This design decision aims to make it easier for you to customise the bot to your server's needs.

The endpoints used for the AI service can be set in the `src/config/AiEndpoints.ts` file.

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
pm2 start "pnpm start" --name "deepgram"
```
