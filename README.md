# alcatelz-db
A simple JSON "database" for the Alcatelz web app store.

##  overview
This repository holds the `apps.json` file, which acts as the single source of truth for all applications listed on the [Alcatelz app store](https://[your-app-store-url.com]).

The Next.js application fetches this file directly from the GitHub raw content URL to populate the store's pages.

## How to Add or Update an App

To add a new app to the store, or to update an existing one, simply edit the `apps.json` file in this repository.

1.  **Open `apps.json`:** Click on the `apps.json` file in the repo.
2.  **Edit the File:** Click the pencil (edit) icon.
3.  **Add/Update Data:**
    * **To add a new app:** Copy an existing app's JSON object (from `{` to `}`), paste it at the end of the list (make sure to add a comma `,` after the previous object), and update all the fields for your new app.
    * **To update an app:** Find the app's object in the JSON array and modify its fields (e.g., update the `version` and `downloadUrl`).
4.  **Commit Changes:** Save your changes by clicking "Commit changes..." at the bottom of the page.

The app store fetches this data with a cache. Your changes may take up to **1 hour** to appear on the live site.

## App Data Structure

Each app object in the `apps.json` array **must** follow this structure:

```json
{
  "slug": "my-new-app",
  "title": "My New App",
  "tagline": "A short, catchy description for the app card.",
  "iconUrl": "/images/my-app-icon.png",
  "downloadUrl": "[https://github.com/Designrpros/my-new-app/releases/download/v1.0.0/my-new-app.zip](https://github.com/Designrpros/my-new-app/releases/download/v1.0.0/my-new-app.zip)",
  "version": "1.0.0",
  "category": "Productivity",
  "longDescription": "<p>A <strong>full HTML description</strong> for the app's detail page.</p><ul><li>You can use lists!</li><li>And other HTML tags.</li></ul>",
  "screenshots": [
    "/images/screenshots/my-app-1.png",
    "/images/screenshots/my-app-2.png"
  ]
}