# README.md
## Anime Character Offline Database (Data)

Public, versioned static dataset of anime characters for offline use.

- **Latest JSON (minified)**: `https://raw.githubusercontent.com/arda-/anime-character-offline-database/main/latest/characters.min.json`
- **Latest JSON (pretty)**: `https://raw.githubusercontent.com/arda-/anime-character-offline-database/main/latest/characters.json`
- Optionally available (if produced): `characters.min.json.gz`, `characters.json.gz`, `top-character-ids.json`

### Versioned snapshots
When the source pipeline is tagged, files are also published under:
- `https://raw.githubusercontent.com/arda-/anime-character-offline-database/<tag>/releases/<tag>/characters.min.json`

### Schema
Top-level shape:
- **meta**: metadata about the dataset
- **data**: array of character entries

Minimal example:
```json
{
  "meta": {
    "schemaVersion": "1.0.0",
    "generatedAt": "2025-01-01T12:34:56.000Z",
    "license": { "name": "Open Data Commons ODbL 1.0 + DbCL 1.0" },
    "repository": "https://github.com/arda-/anime-character-offline-database",
    "source": { "name": "Jikan v4", "url": "https://docs.api.jikan.moe", "library": "Marika" },
    "totalCharacters": 12345,
    "format": "single-file"
  },
  "data": [
    {
      "mal_id": 1,
      "url": "https://myanimelist.net/character/1",
      "images": {},
      "name": "Character Name",
      "name_kanji": "漢字",
      "nicknames": ["Nick"],
      "favorites": 100,
      "about": "Short bio...",
      "voiceActorsByLanguage": { "Japanese": [] },
      "animeAppearances": [
        { "anime": { "mal_id": 1, "title": "Anime Title" }, "role": "Main" }
      ],
      "lastUpdated": "2025-01-01T00:00:00.000Z"
    }
  ]
}
```

### How to use
- JavaScript:
```js
const url = "https://raw.githubusercontent.com/arda-/anime-character-offline-database/main/latest/characters.min.json";
const res = await fetch(url);
const db = await res.json();
// db.meta, db.data[0].name, etc.
```

- cURL:
```bash
curl -L https://raw.githubusercontent.com/arda-/anime-character-offline-database/main/latest/characters.min.json -o characters.min.json
```

### License
- Data is licensed under the **Open Data Commons Open Database License (ODbL) v1.0** and the **Database Contents License (DbCL) v1.0**.
  - ODbL: https://opendatacommons.org/licenses/odbl/1-0/
  - DbCL: https://opendatacommons.org/licenses/dbcl/1-0/
- Attribution example (ODbL 4.3): “Contains data from the ‘Anime Character Offline Database’ by arda-, licensed ODbL 1.0 and DbCL 1.0.”

Related references:
- Upstream dataset license model: [anime-offline-database LICENSE](https://github.com/manami-project/anime-offline-database/blob/master/LICENSE)
- Toolkit used to generate data: [@shineiichijo/marika (MIT)](https://www.npmjs.com/package/@shineiichijo/marika)

### Integrity
Publishers may include SHA‑256 checksums in the repository alongside files (e.g., `characters.min.json.sha256`).

### Contact
Issues and requests: open an issue on this repository.
