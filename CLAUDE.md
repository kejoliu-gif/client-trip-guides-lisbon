# CLAUDE.md

Client trip guide (single static `index.html`, bilingual zh-TW / en, served via GitHub Pages at guides.strolltheworld.com). Advisor: Kejo Liu, Fora Travel.

## Affiliate links

All monetized links use Kejo's own IDs. When adding/editing them, keep these exact identifiers.

### Booking.com — via Awin (NOT a direct `?aid=`)

Booking.com is **not** linked directly. It runs through the Awin network. A bare
`https://www.booking.com/hotel/...?aid=2885393` does **not** track — Booking.com
ignores that param (its own partner IDs look like `2311236`), so commission is lost.

Correct format — wrap the destination URL in the Awin redirect:

```
https://www.awin1.com/cread.php?awinmid=6776&awinaffid=2885393&ued=<URL-ENCODED booking.com destination>
```

- `awinmid=6776` — Awin merchant ID for Booking.com
- `awinaffid=2885393` — Kejo's Awin affiliate ID
- `ued=` — the full Booking.com destination URL, percent-encoded (encode `:` `/` `?` `&` `=`)

Language/currency rule (matches the guide's language toggle):
- **Mandarin view** → `booking.com/hotel/pt/<slug>.zh-tw.html?...&selected_currency=TWD`
- **English view** → `booking.com/hotel/pt/<slug>.en-gb.html?...&selected_currency=USD`

The three hotel buttons are single `<a class="lod-btn bk-link">` elements with
`data-zh` / `data-en` attributes; `setLang()` swaps `href` on toggle. Default
`href` = the zh-tw/TWD link (page loads in Mandarin). Verified hotel slugs:
`do-chiado`, `memmo-alfama`, `bairro-alto`. Trip dates: checkin 2026-11-19,
checkout 2026-11-25.

### Other affiliate IDs (audited, correct — do not change)

- **Klook**: `https://affiliate.klook.com/redirect?aid=121102&aff_adid=1278789&k_site=<encoded klook URL>`
- **Viator**: append `?pid=P00058688&uid=U00806492&mcid=58086&currency=USD` to the tour URL
- **Faye insurance**: `withfaye.com/quote/offer?utm_campaign=KejoLiuForaTravel&utm_source=ForaTravel&utm_medium=bd-traveladvisors&utm_term=glinda`
