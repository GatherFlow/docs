# Understanding the Codebase Structure

- `app/` This folder contains the routes of the app, along with its layout routes such as stack and tab navigation structures
- `assets/` Storing images, fonts, and other assets.
- `components/` This folder contains the components of the app. mainly components used inside the app folder.
- - `components/ui` This folder contains all the UI components and the theme configuration.
- `lib/` This folder contains the core files, such as authentication, localization, storage, and more.

## Importing files

Absolute imports are used to import files using the Babel module resolver plugin and TypeScript path mapping. This approach helps us avoid long relative paths and makes the code cleaner and more readable.
