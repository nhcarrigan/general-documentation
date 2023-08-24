# Create Your Own Discord RPC

Start by cloning this code base to your local machine using `git`, or downloading the `.zip` file directly with GitHub's GUI.

You will also need to have `node.js` and `npm` installed and available on your machine.

## Creating your Application

Log in to the [Discord Developer Portal](https://discord.com/developers/) and select `Applications` in the side-bar. If you have an existing application (such as a bot), you may use that - otherwise, create an application.

> [!NOTE]
>
> Your application name will appear as the first line of text in the rich presence.

Copy the `Client ID` for the application and pass that to the `clientId` property for the `loginOptions` object in `src/index.ts` - you will replace the existing client ID there.

## Configuring Your Choices

There are a few places you'll need to make changes to customise your activity choices.

The first is the `src/interfaces/ActivityChoice.ts` file. This is a type definition file used to ensure that all of your other configurations have the correct values. Change the strings here to reflect the choices you want to see in the CLI.

The second is in the `src/config/ActivityChoices.ts` file. This is an array containing all of the available choices - it should _match_ your type definition file exactly. That is, each string in the interface should also be in this array.

The third is in the `src/config/activityStates.ts` file. This is an object that maps the available choices to specific state values. These values will appear in your presence when you select the related choice.

The fourth is in the `src/config/activityImages.ts` file. This is an object that maps the available choices to specific images. These images will appear in your presence when you select the related choice.

> [!NOTE]
>
> The `Signing Off` key is used to shut down the application and should not be removed.

## Uploading an Asset

Navigate to your application's page on the Developer Portal again. Select `Rich Presence` from the sidebar. You should see a section titled `Rich Presence Assets`.

Click the `Add Image(s)` button to upload an image. Select your image - Discord will upload it and you will be able to set the name of that asset. **This name is what you give to the `activityImages` value in the code.** Select `Save Changes` when you are done.

> [!NOTE]
>
> The asset can take up to a couple of hours to be live and available in your RPC. If you refresh the developer portal page and the asset is not there, it has not finished processing yet.

## Other Tweaks

Within the `src/modules/getActivity` file, you may want to update the `baseActivity` object. This object contains the common values for the presence data. The important values are:

- `details` - This sentence will appear above your `state` that you set earlier.
- `buttons` - These buttons will appear below your presence and can be clicked by users. The `label` is the text that displays, and the `url` is the website that opens when the button is clicked.
- `largeImageText` - This is the text that appears if someone hovers over your activity's image.

## Running the Code

Once you have done all of this, you can run the code. Open your terminal within the project's root directory, then use `npm ci` to install the dependencies, `npm run build` to compile the TypeScript, and `npm start` to launch the code.

You'll now see a prompt to select your activity state. When you select one, the tool will update your presence and you should be able to see it on your Discord profile. The prompt is set up to continue to appear, so you can quickly switch between activities depending on what you are doing or want to display.

Enjoy your new toy!

> [!NOTE]
>
> This needs to run on the same computer that you are running Discord on, so it cannot be hosted remotely. Additionally, it is confirmed to work with the Desktop client but has not been tested on the web client.
