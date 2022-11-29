# Usage

To use the bot, start by [inviting it](https://discord.com/api/oauth2/authorize?client_id=1046933883641417882&permissions=0&scope=bot%20applications.commands).

The `/about` command will provide helpful links for the bot.

## Configuring Your Server

> [!NOTE]
> Configuring a server requires the `Manage Server` permission.

Use the `/channel` command to set the channel where you'd like AMA submissions to be posted. **Make sure the bot has permissions to post in that channel!**

Use the `/enable` and `/disable` commands to turn the submission system on and off. When the system is disabled, users will not be able to submit questions.

## Submitting Questions

Use the `/ask` command to submit a question. You'll need to fill the question you want to ask into the `question` input, and select the `anonymous` option to determine if you want your avatar+username displayed with the question or not.

## Responding to Questions

> [!NOTE]
> Responding to questions requires the `Manage Server` permission.

Question posts will have three buttons.

- The first button will acknowledge that the question has been answered (e.g. on a live stream) but will not prompt you for the answer.
- The second button will show a modal asking you to provide the answer. Once you submit the answer, the question will be updated to include it.
- The third button will reject the question, prompting you for a reason to reject it (e.g. ran out of time, not relevant, etc).

You can also delete the question post if you receive inappropriate submissions.
