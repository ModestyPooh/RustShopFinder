# Rust Shop Finder

Unofficial fan tool, not affiliated with Facepunch.

Drop in screenshots of the shop panel from the in-game map. The page reads each shop's name, items, prices and stock, learns the item icons as you name them, pins shops on the server map, and gives you one searchable list of every shop you've scanned.

Everything runs in your browser. Nothing is uploaded anywhere: screenshots are read on your own PC and your shop list is saved in your browser's local storage. Use the Backup tab to copy your data out.

## Put it on GitHub Pages

1. Create a new repository on GitHub (public, or private if your plan allows Pages on private repos).
2. Upload **everything in this folder**, keeping the `ocr` folder and its subfolders as they are. Add file → Upload files works; drag the whole folder in.
3. Go to **Settings → Pages**, set **Source** to *Deploy from a branch*, pick `main` and `/ (root)`, and save.
4. After a minute or two the site is live at `https://<your-username>.github.io/<repo-name>/`.

## Testing on your own PC

Opening `index.html` straight from the folder (double-click) shows the page, but the text reader won't start, because browsers block it for local files. Either test on GitHub Pages, or run a tiny local server in this folder:

```
python -m http.server 8000
```

then open http://localhost:8000.

## How to use

1. **Map tab:** check the map picture loads (Map settings holds the links and map size). Press **+ Add pin** and click the spot where a group of shops stands. Give the pin a nickname if you like; the grid square is worked out for you. Turn on **Grid** to compare with the in-game grid.
2. In game, open the map (G), click the shop marker, expand one or more shops and take a screenshot (F12 in Steam, or Win+Shift+S).
3. **Scan tab:** drop the screenshots in (or paste with Ctrl+V). Pick the map pin, and under **Update which vendor?** choose the vendor each shop belongs to, or New vendor. Name any new item icons once, check boxes marked ⚠, and save.
4. **Find tab:** search an item, then use **Show on map** to see where it is.

Every vending machine is its own vendor, even when several are called "A Shop". Give them nicknames on the Shops tab. Price changes are recorded each time you rescan a shop.

**New wipe or new server:** on the Backup & wipe tab, copy a backup, enter the new server's name, map size and map links, then press **Start new wipe**. Vendors, pins and prices are cleared; learned item icons are kept.

## Credits and licences

- Rust, its item icons and all related game content belong to Facepunch Studios. Icons shown in the tool come from your own screenshots.
- Map pictures are loaded from the links you enter (for example rustmaps.com) or files you upload; they are not included here.
- Text reading uses [tesseract.js](https://github.com/naptha/tesseract.js) 5.1.1 and tesseract.js-core (Apache License 2.0, licence files in `ocr/`) with the English LSTM model from [tessdata](https://github.com/tesseract-ocr/tessdata_best) (Apache License 2.0).
  - `ocr/worker.min.js` has a one-line patch so language data can be passed in directly (5.1.1 read the wrong field).
  - `ocr/lang/eng-traineddata-gz.b64.txt` is the gzipped `eng.traineddata` stored as base64 text.
