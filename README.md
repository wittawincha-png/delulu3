# Delulu Coffee POS

Point of service software for Delulu Coffee. The app runs as a local web app from Visual Studio or Visual Studio Code and stores data in Google Sheets through a Google Apps Script web app.

## Features

- Login page for admin and staff
- Selling counter with customer order date/time, menu photos, prices, descriptions, cart, stock checks, and receipt
- Receipt printing and `.docx` saving
- Menu add/edit/delete
- Ingredient stock add/edit/delete with photos, prices, descriptions, warning levels, and menu recipes
- Monthly and yearly sales summaries
- Daily sales summary by date
- Google Sheets persistence for users, menus, ingredients, recipes, orders, order items, and ingredient usage
- Audit log with record name, price, user, date, and time of input

## Local Run

1. Open this folder in Visual Studio or Visual Studio Code.
2. Open `index.html` in a browser.
3. Login with:
   - Admin: `admin` / `admin2026`
   - Staff: `staff` / `staff2026`

The app works offline using browser storage. Connect Google Sheets from the Settings page when you are ready to persist data online.

## Vercel Deployment

Upload these files to the root of your GitHub repository for Vercel:

- `index.html`
- `vercel.json`
- `public/index.html`
- `README.md` if you want setup notes online

`index.html` contains the same HTML, CSS, and JavaScript in one file, so the deployed interface matches the local POS even if Vercel does not load separate CSS or JS files. `public/index.html` is included as a backup for Vercel projects whose Output Directory is set to `public`.

If Vercel still shows 404 after redeploying, open **Vercel > Project Settings > Build & Development Settings** and make sure:

- Framework Preset is `Other`
- Build Command is empty
- Output Directory is empty or `public`
- Root Directory points to the folder that contains `index.html`

## Google Sheets Setup

1. Create a new Google Sheet for the shop.
2. In the Sheet, choose **Extensions > Apps Script**.
3. Paste the contents of `apps-script/Code.gs` into the Apps Script editor.
4. Click **Deploy > New deployment**.
5. Select **Web app**.
6. Set **Execute as** to **Me**.
7. Set **Who has access** to **Anyone with the link**.
8. Deploy and copy the Web App URL.
9. Paste that URL into the POS **Settings > Google Sheets Web App URL** field.
10. Click **Save Settings**, then **Save Local Data to Google Sheets**.

The Apps Script creates these sheets:

- `Users`
- `Menus`
- `Ingredients`
- `Recipes`
- `Orders`
- `OrderItems`
- `IngredientUsage`
- `AuditLog`

## Notes

- Photos are stored as image URLs or uploaded image data. For long-term Google Sheets use, hosted image URLs are lighter than large uploaded images.
- Change the default passwords immediately after setup.
- This is a practical starter POS for a small shop. Before using it for taxes or formal accounting, review the data export and receipt requirements for your local rules.
