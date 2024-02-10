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

- Manage Messages
- Create Public Threads

Be sure to invite it to your server with both the `bot` and `application.commands` scopes.

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
- `GENERAL_CHANNEL_ID`: This is the ID for your general chat channel. The sticky message will be posted here. Daily posts of 3 most recent unanswered questions will be posted here.
- `MOD_CHANNEL_ID`: This is the ID for your moderator chat channel. Weekly posts of **answered** threads, and daily posts of **all** unanswered threads, will be posted here.
- `STICKY_MESSAGE_FREQUENCY`: This is the number (in **minutes**) between sticky message updates. The bot will wait this long before sending the sticky message again.
- `AI_URL`: This is the base URL for API requests to your AI service. This should not include any paths. For example: `https://docs.nhcarrigan.com`.
- `GITHUB_TOKEN`: This is the PAT for the account you would like to create discussions.
- `GITHUB_OWNER`: This is the user/organisation that owns the repository you would like to create discussions on.
- `GITHUB_REPO`: This is the repository you would like to create discussions on.
- `PRODUCT_BOARD_API_KEY`: This is the API token for the ProductBoard.com account you would like to create notes with.

> [!TIP]
> The following keys are entirely optional.
> `AI_URL`: Without this, the `move to help channel` context command will not generate AI responses. Will still complete all other functions.
> `GITHUB_*`: If ANY of the GitHub values are missing, the `Mark as answered` command will not generate a GitHub discussion. Will still complete all other functions.
> `PRODUCT_BOARD_API_KEY`: Without this, the `Send to Product Board` context command will not function.

## Help Channel

The help channel **must** be a forum channel. In order for the bot to function, it also needs to have the following **case-sensitive** tags:

- `Question`
- `Answered`
- `Inactive`

> ![DANGER]
> These tags MUST be marked as "Only allow moderators to apply tag", or the bot will not be able to find them.

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
