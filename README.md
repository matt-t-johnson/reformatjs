# reformatjs

A codemod designed to refactor an existing project to be able to support internationalization (i18n) and localization (l10n) with the FormatJS set of libraries.

## Pre-requisites
Install reformatjs globally: `npm i -g reformatjs`

(for local development, run `npm i -g` to install the local version as reformatjs)
## Running on example projects
1. Navigate to the example project you want to test the tool against. E.g: `cd example-projects/react-app`
2. Run the main program `reformatjs -s ./src -o ./src/i18n -t ./i18n-tools -l zh-CN,de-DE`
3. When the main program finishes, run `node i18n-tools/manage-i18n.js`
4. Navigate to `src/i18n/locales/de-DE.json` in the example project and change some of the message values.
5. Navigate to `src/i18n/i18n-constants.js` and add `locales.germanGermany` to the `releasedLanguages` constant.
6. Start the example app, e.g. `npm start`
7. Open the Application tab in the browser dev tools and set a cookie in the example app with the name `locale` and the value `de-DE`.
8. Refresh the app. You should see the updated messages displayed.


## Files written to source project
This tool copies a few files over to the target project codebase.

`src/files-to-write/i18n-tools` includes scripts used to manage the process of extracting i18n messages from the codebase and compiling them into a format consumable by translation services such as Crowdin as well as the react-intl-translation-manager tool used to keep translation files up to date.
You can think of these as dev dependencies.

`src/files-to-write/source-files` contains files that will be used in the actual client code.
Some project bootstrappers (such as create-react-app) may require that these files to be in a specific directory (such as `/src`).