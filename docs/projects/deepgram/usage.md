# Usage

The bulk of the bot usage will be done by "helpers" - people identified by roles that are configured by the bot owner.

## Move a Post

> [!NOTE]
> Only helpers can use this command.
> ![Discord message responding to a command stating that only helpers may use the command](https://cdn.nhcarrigan.com/projects/deepgram/helper-only-command.png)

If a message is asking for help, and isn't in your help forum channel, you can use the `help` context command to move it. Right click on the message (or long-press on mobile), select "Apps", and select "help".

![A Discord message, with the context menu exposed. The sub menu 'Apps' is highlighted, and the 'help' command is highlighted.](https://cdn.nhcarrigan.com/projects/deepgram/help-command.png)

After running this command, the bot will create a new thread in the configured forum channel. The bot will ping the author of the message, so they know where their question has gone. Then, if the AI system is configured, the bot will request an AI response to the question and post it in the thread.

![A Discord forum thread, containing a post from a bot tagging a user and reposting their question, and a second message from the bot indicating the AI has not been configured. The second message has a green button reading "This helps!" and a red button reading "This is incorrect."](https://cdn.nhcarrigan.com/projects/deepgram/help-post.png)

## AI Feedback

The AI response will include two buttons. The first marks the response as helpful. The second marks the response as unhelpful.

![Discord message indicating that the AI has not been configured](https://cdn.nhcarrigan.com/projects/deepgram/button-success.png)

### When a Post is Helpful

If you found the AI response to your question to be helpful, click the "This was helpful" button. This will send a response to the AI to train it that this response was helpful. The bot will then remove the buttons to avoid spam.

> [!NOTE]
> Only helpers or the original question author can use this button.
> ![Discord message responding to a button click stating that only helpers or the author may mark the response helpful](https://cdn.nhcarrigan.com/projects/deepgram/helper-or-author.png)

### When a Post is Inaccurate

Sometimes AI gets things wrong. If the AI response to a question is inaccurate, click the "This is inaccurate" button. This will send a response to the AI to train it that the response was off the mark. The bot will then remove the buttons to avoid spam.

> [!NOTE]
> Only helpers can use this button.
> ![Discord message responding to a button click stating that only helpers may mark a response inaccurate](https://cdn.nhcarrigan.com/projects/deepgram/helper-only-button.png)
