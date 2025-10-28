# alcatelz-db
A simple JSON "database" for the Alcatelz web app store.

## overview
This repository holds the **`apps.json`** file, which acts as the single source of truth (your database) for all applications listed on the [Alcatelz app store](https://[your-app-store-url.com]).

The Next.js application fetches this file directly from the GitHub raw content URL to populate the store's pages.

---

## 🛠️ How to Add or Update an App

To add a new app to the store, or to update an existing one, simply edit the `apps.json` file in this repository.

1.  **Open `apps.json`:** Navigate to the file in this repository.
2.  **Edit the File:** Click the pencil (edit) icon.
3.  **Add/Update Data:**
    * **To add a new app:** Copy an existing app's JSON object (from `{` to `}`), paste it at the end of the list, and **make sure to add a comma (`,`) after the previous object** (but not after the very last object). Then update all fields.
    * **To update an app:** Find the app's object in the JSON array and modify its fields (e.g., update the `version` and `downloadUrl`).
4.  **Commit Changes:** Save your changes by clicking "Commit changes..." at the bottom of the page.

> 📝 **Note on Caching:** The Next.js app fetches this data with a cache set for 1 hour. Your changes may take up to **1 hour** to appear on the live site after you commit them.

---

## 🗃️ App Data Structure

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
  ],
  "website": "[https://www.my-app-website.com](https://www.my-app-website.com)"
}
````

| Field | Description | Requirement |
| :--- | :--- | :--- |
| **`slug`** | A unique, URL-friendly ID. (e.g., "peak-browser"). | **Required** |
| **`title`** | The official app name. | **Required** |
| **`tagline`** | The short, one-sentence description for the store page. | **Required** |
| **`iconUrl`** | Path to the app's icon. | Must exist in your Next.js app's `/public` folder. |
| **`downloadUrl`** | The direct, public URL to the app's `.zip` file. | **Required**. See "Best Practice" below. |
| **`version`** | The current version number (e.g., "1.0.1"). | **Required** |
| **`category`** | The app's category (e.g., "Utilities", "Productivity"). | **Required** |
| **`longDescription`** | The full description for the app's detail page. | **Can be raw HTML.** |
| **`screenshots`** | An array of paths to screenshots. | Must exist in your Next.js app's `/public` folder. |
| **`website`** | Optional public URL for a support page or marketing site. | Recommended. |

-----

## 🔗 Best Practice for Download Links (`downloadUrl`)

To avoid storing large `.zip` files in your main Next.js project, use **GitHub Releases** for the `downloadUrl`:

1.  Go to your app's **own** repository (e.g., your separate repository for "TextClip").
2.  Create a "Release" on GitHub and give it a version tag (e.g., `v1.0.3`).
3.  Upload your compiled application's `.zip` file as a release asset.
4.  Publish the release.
5.  **Copy the public URL for the `.zip` asset** and use that full URL in the `downloadUrl` field in this `apps.json` file.

<!-- end list -->

```