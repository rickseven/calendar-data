# Indonesia Holidays Calendar Data

Data hari libur nasional dan cuti bersama Indonesia dalam format JSON.

## API Endpoint

```
https://[your-username].github.io/calendar-data/holidays-{year}.json
```

Contoh:
- `holidays-2026.json`
- `holidays-2027.json`

## Struktur Data

```json
{
  "year": 2026,
  "holidays": [...],
  "collective_leave": [...]
}
```

### Field Description

- `date`: Format ISO 8601 (YYYY-MM-DD)
- `name`: Nama hari libur
- `type`: Tipe libur (`national_holiday` atau `collective_leave`)
- `day`: Nama hari dalam bahasa Indonesia
