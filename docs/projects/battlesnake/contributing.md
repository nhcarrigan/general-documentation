# Contributing

In addition to our top-level contributing guidelines, we request that you follow these guidelines when making pull requests to this project.

## API Endpoints

The API endpoints can be found in the `/src/controllers` directory. The code in these files handles the top level logic for the given API endpoint.

- `handleEnd.ts` - This is the `/end` endpoint, which notifies the server that the game has ended.
- `handleIndex.ts` - This is the `/` endpoint, and is used to provide the customisation data for the battlesnake.
- `handleMove.ts` - This is the `/move` endpoint, and is used to request the next move from the battlesnake.
- `handleStart.ts` - This is the `/start` endpoint, and is used to initiate a new game.

## Game Logic

The bulk of the game logic, such as calculating the next move, is all found in the `/src/modules` directory. Most of the changes you make will likely take place in these files.

## Tests

Any changes to the game logic should include updates to the tests in the `/src/tests` directory. You will either need to update existing tests for changes, or write new tests for additional functionality.
