# Contributing

In addition to our standard contribution guidelines, there are some extra notes for this project.

## Adding Tags

Tags are used to respond to frequently asked questions. New tags can be added to `/src/data/tags`, and should be added in alphabetical order by
`name`.

Tags require the following properties:

- `name`: The name of the tag. This is used to trigger the tag with `hf.<name>`.
- `content`: This is the main body of the tag. You can insert line breaks with `\n`.
- `title`: This is the title of the tag, which **should take the form of a question**.
- `aliases`: These serve as alternate names for triggering the tag.

## Adding Phrases to the Bot

To add new responses to the bot, navigate to the `src/data/phrases.ts` file. Within the array, add the phrases you'd like the bot to potentially respond with.

## Adding Hearts to the Bot

All of our hearts are generously provided by [Luke's DevHearts project](https://github.com/lukeocodes/dev-hearts). Before you add a heart to this project, you need to submit it there and have it approved. Be sure to follow their contributing guidelines!

Once your heart is approved and merged, add the _name_ of your new heart file to the `src/data/hearts.ts` file - do _not_ include the file extension.

## Adding new users

To add a new user to respond to, navigate to the `src/data/loveData.ts` file. Create a new object with the corresponding data - if you are adding a corporate sponsor, exclude the `id` field.

Then, add a new array with the user's phrases in `src/data/phrases.ts`.
