# Andiamo al cinema? 🎬

La programmazione dei cinema di Milano, resa semplice.

## File structure

```
andiamo-al-cinema/
├── index.html    ← page structure — don't touch
├── style.css     ← visual design — don't touch
├── app.js        ← app logic — don't touch
├── data.json     ← ALL THE DATA — edit this every Monday
└── README.md     ← this file
```

---

## How to update schedules (every Monday, ~20 min)

### 1. Open the data source
Go to [mymovies.it/cinema/milano](https://www.mymovies.it/cinema/milano)

### 2. Open data.json in a text editor
Use VS Code (free): code.visualstudio.com

### 3. Update the `showtimes` array
Each entry looks like this:
```json
{
  "c": "anteo",
  "f": "michael",
  "days": [1, 2, 3, 4],
  "t": ["19:30", "22:00"],
  "lang": "it"
}
```

- `"c"` = cinema ID (see cinemas list below)
- `"f"` = film ID (see films list below)
- `"days"` = weekdays: 0=Dom, 1=Lun, 2=Mar, 3=Mer, 4=Gio, 5=Ven, 6=Sab
- `"t"` = showtimes as "HH:MM"
- `"lang"` = `"it"` (italiano) or `"ov"` (versione originale)

### 4. Update the date
Change `"updated"` at the top:
```json
"updated": "2026-05-11"
```

### 5. Add a new film
Add an entry to the `"films"` array:
```json
{
  "id": "myfilm",
  "title": "Titolo del Film",
  "genre": "Drammatico",
  "dur": 110,
  "dir": "Nome Regista",
  "cast": "Attore 1, Attrice 2",
  "synopsis": "Breve descrizione del film.",
  "emoji": "🎬",
  "tmdbId": 123456
}
```
Find the `tmdbId` by searching the film on [themoviedb.org](https://www.themoviedb.org) and copying the number from the URL.

### 6. Remove a film that's no longer showing
Delete its entries from `"showtimes"`. Leave it in `"films"` (harmless) or delete it there too.

---

## Publishing to GitHub + Netlify

### First time setup

**1. Install Git:** https://git-scm.com/downloads

**2. Create GitHub account:** https://github.com

**3. Create a new repository:**
- Click "New" on GitHub
- Name it `andiamo-al-cinema`
- Set to Public
- Click "Create repository"

**4. Push your files (run in Terminal / Command Prompt):**
```bash
cd path/to/your/folder
git init
git add .
git commit -m "primo deploy"
git branch -M main
git remote add origin https://github.com/YOURUSERNAME/andiamo-al-cinema.git
git push -u origin main
```

**5. Deploy on Netlify:**
- Go to [netlify.com](https://netlify.com), create free account
- Click "Add new site" → "Import from Git" → "GitHub"
- Select your repository
- Leave all settings default → click "Deploy"
- Your site is live at `yourname.netlify.app` in ~30 seconds

### Every Monday update
```bash
# Edit data.json, then:
git add data.json
git commit -m "programmazione settimana 11 maggio"
git push
```
Netlify auto-deploys within 30 seconds. Done.

---

## Cinema IDs
| ID | Cinema |
|---|---|
| anteo | Anteo Palazzo del Cinema |
| ariosto | Ariosto spazioCinema |
| centrale | Centrale |
| arlecchino | Cineteca Arlecchino |
| mic | Cineteca Milano MIC |
| arcobaleno | Arcobaleno Filmcenter |
| mexico | Mexico |
| gloria | Gloria Notorious Cinemas |
| colosseo | Colosseo |
| plinius | Plinius Multisala |
| palestrina | Palestrina |
| bicocca | Uci Cinemas Bicocca |
| cinelandia | Cinelandia Milano Certosa |
| citylife | CityLife Anteo |
| merlata | Notorious Cinemas Merlata |
| beltrade | Beltrade |
| orfeo | Orfeo Multisala |
| ducale | Ducale Multisala |
| eliseo | Eliseo |
| cinemino | Il Cinemino |
| asteria | Auditorium Asteria |
| gregorianum | Gregorianum |
| osoppo | Osoppo |

## Genre values
`Animazione` `Avventura` `Biografico` `Commedia` `Documentario` `Drammatico` `Horror` `Thriller`
