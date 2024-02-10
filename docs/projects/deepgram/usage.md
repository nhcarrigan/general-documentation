# Usage

The bulk of the bot usage will be done by "helpers" - people identified by roles that are configured by the bot owner.

## Move a Post

> [!NOTE]
> Only helpers can use this command.

If a message is asking for help, and isn't in your help forum channel, you can use the `help` context command to move it. Right click on the message (or long-press on mobile), select "Apps", and select "Move to help channel".

After running this command, the bot will create a new thread in the configured forum channel. The bot will ping the author of the message, so they know where their question has gone. Then, if the AI system is configured, the bot will request an AI response to the question and post it in the thread.

## AI Feedback

The AI response will include two buttons. The first marks the response as helpful. The second marks the response as unhelpful.

### When a Post is Helpful

> [!NOTE]
> Only helpers or the original question author can use this button.

If you found the AI response to your question to be helpful, click the "This was helpful" button. This will send a response to the AI to train it that this response was helpful. The bot will then remove the buttons to avoid spam.

### When a Post is Inaccurate

> [!NOTE]
> Only helpers can use this button.

Sometimes AI gets things wrong. If the AI response to a question is inaccurate, click the "This is inaccurate" button. This will send a response to the AI to train it that the response was off the mark. The bot will then remove the buttons to avoid spam.

## Mark a Post as Answered

> [!NOTE]
> Only helpers can use this command.

When someone's help post has been answered, you may identify the message that contains the solution. Right click on the message, select "Apps", then select "Accept Answer".

When an answer is accepted, the bot will do two things:

- Label the thread as answered
- Create a GitHub discussion with the question, and post a comment with the answer.

## Product Board integration

> [!NOTE]
> Only helpers can use this command.

If a message sent in the server seems like decent feedback that you would like to track internally, you can post it to a ProductBoard.com app.

Right click on the message, select "Apps", and select "Send to Product Board". The bot will create a note on the board, with the Discord user's name in the title, and the message content in the body. The note will also link back to the original Discord message.

## Stats Command

> [!NOTE]
> Only helpers and administrators can use this command.

The `/stats` chat command will generate a list of the following stats:

- How many threads TOTAL have been answered
- How many threads TOTAL have gone unanswered
- How many threads TOTAL have been flagged as inactive
- How many threads are currently open
- How many threads are currently closed
- How many threads were created with the `Move to help channel` command
- Average time for a thread to be flagged as answered (this is coming soon!)
- The total number of threads

The response to this command is **ephemeral**, so you are free to run it in any channel. The only person who will see the response is you.
