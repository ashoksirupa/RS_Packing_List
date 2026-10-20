# Wedding Packing List

A packing list for every wedding event, stored in your own Google Sheet. Runs on iPhone, Android and desktop from one GitHub Pages link.

## What it does

- **Events:** Vadugu, Haldi, Main Wedding, Miami Reception, Dallas Reception. Add more any time.
- **Categories:** Puja Items, Clothing, Gifts, Cosmetics, Photography. Add more any time.
- **People:** Rohit, Neha, Vani, Ashok, Common, In-Laws, Relatives. Add more any time.
- **Suitcases:** Suitcase 1–3 and Carry-on 1–2 to start. Rename them (e.g. "Neha blue trunk") or add more.
- **Add an item to several events at once.** Pick Haldi + Main Wedding and it makes one entry for each.
- **Tick an item as packed** and the app asks which suitcase it went in. You can also tap the suitcase button on any item.
- **Bulk packing:** tap **Select**, pick items (or "Select N" for a whole group), then assign a suitcase or mark them packed.
- **Filters** on the Pack screen: event, person, category, suitcase, packed/not packed, search.
- **Reports:** filter by Events, Categories, People, Suitcases and Packed Y/N; group by any of them. Each report shows totals and a progress summary, then the item list. **Print / Save PDF** or **Export CSV**.
  - Quick reports: *By event*, *What's in each suitcase*, *Still to pack*, *By person*, *By category*.
- **Manage:** add, rename, reorder or delete events, categories, people and suitcases. Renaming updates every item. A value that is still used by items can't be deleted.
- **Works with poor signal:** changes save on the phone first and go to the sheet when the connection is back. The header shows "Offline · 2 changes waiting" until then.
- **Several people at once:** everyone sees each other's changes (refreshes every 45 seconds and whenever the app is reopened). The sheet refuses a duplicate item (same item, person and event).

## Files

| File | Where it goes |
|---|---|
| `AppsScript.gs` | Pasted into the Google Sheet's Apps Script |
| `index.html`, `manifest.webmanifest`, `icon-180.png`, `icon-512.png`, `README.md` | Uploaded to GitHub |

## Setup

### 1. Google Sheet + Apps Script
1. Go to https://sheets.new and name it **Wedding Packing List Data**.
2. Open **Extensions → Apps Script**. Delete the starter code, paste in all of `AppsScript.gs`, and click Save.
3. Choose **Deploy → New deployment**. Click the gear and pick **Web app**:
   - Execute as: **Me**
   - Who has access: **Anyone**
4. Click Deploy, authorize (if Google warns, choose **Advanced → Go to project**), and copy the **Web app URL** ending in `/exec`.

The script creates two tabs on first use:
- **Items**: ID, Item, Event, Category, Person, Qty, Suitcase, Packed (Y/N), Notes, Updated
- **Lists**: the events, categories, people and suitcases shown in the app

You can type rows straight into the Items tab too (leave ID blank; the app fills it in). Extra columns you add to the right are left alone.

### 2. GitHub Pages
1. Create a new repository, for example `wedding-packing`.
2. Choose **Add file → Upload files**, drag in `index.html`, `manifest.webmanifest`, `icon-180.png`, `icon-512.png` and this README, then **Commit**.
3. Go to **Settings → Pages**. Set Source to **Deploy from a branch**, Branch **main**, folder **/ (root)**, and Save.
4. After a minute your link appears there, like `https://<your-username>.github.io/wedding-packing/`.

### 3. Connect each device
1. Open the GitHub Pages link, paste the `/exec` URL, and tap **Connect & continue**.
2. **After** it connects, add it to your home screen:
   - iPhone (Safari): Share → **Add to Home Screen**
   - Android (Chrome): ⋮ → **Add to Home screen** / **Install app**
   - Desktop (Chrome or Edge): the install icon in the address bar
3. To share with family: **Manage → Copy app link**. That link opens the app already connected, so they skip step 1.

> Anyone with the app link can view and edit the list, so share it only with family.

## Updating later
- **Changed the script?** Paste it in Apps Script, then **Deploy → Manage deployments → Edit (pencil) → Version: New version → Deploy**. The URL stays the same.
- **Changed the app?** Upload the new `index.html` to GitHub, replacing the old one.
