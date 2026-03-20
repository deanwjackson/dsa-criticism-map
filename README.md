# DSA Critics Map

**MEPs Characterizing the EU Digital Services Act as Censorship**

An interactive visualization of European Parliament members who have, in verifiable parliamentary documents or public statements, framed the Digital Services Act (DSA) as a vehicle for censorship or suppression of free speech.

[**View the widget →**](https://your-username.github.io/dsa-critic-map/)

---

## Methodology

### What was collected

This dataset identifies MEPs through four source types:

1. **Oral questions (O-)** filed with the European Commission or Council that explicitly characterize the DSA as censorship
2. **Written questions (E-, P-)** to the European Commission with the same framing
3. **Plenary speeches and debates** (verbatim transcript, January 2025 DSA enforcement debate)
4. **Public conference participation** (ADF International Brussels Report 2022, ADF conference May 2025) and collective expert letters

### Verification process

Every source document was fetched from the European Parliament's official document portal ([europarl.europa.eu](https://www.europarl.europa.eu)) and read in full before being attributed to any MEP. This was necessary because a large group of far-right/euroskeptic MEPs files oral and written questions on many topics (cash payments, Erasmus+, RSF, DSA), with ~80% signatory overlap across these questions. Earlier dataset versions assumed document numbers matched topics without reading the actual documents — a serious error.

### Excluded documents

| Document | Reason for exclusion |
|---|---|
| O-046/2025 | Child protection online — distinct framing, not a DSA-censorship claim |
| O-042/2025 | "Protecting citizens' right to make cash payments" — not DSA-related |
| O-043/2025 | "Manipulation of the Erasmus+ programme" — not DSA-related |
| O-003/2026 | Concerns Reporters Without Borders as a biased NGO — not DSA-related |
| E-005041/2025 | Telegram/Durov prosecution — not a DSA-censorship framing |

### Dataset evolution

The original unverified dataset contained **114 MEPs**. After full document-level verification, **55 MEPs** were confirmed with at least one qualifying source. 59 MEPs were removed due to reliance on wrongly-attributed source documents.

---

## File manifest

| File | Description |
|---|---|
| `index.html` | Self-contained interactive visualization widget |
| `build.py` | Python script to regenerate `index.html` and `data/` from the spreadsheet |
| `dsa-critics-meps-verified.xlsx` | Source spreadsheet (read-only) |
| `data/dsa-critics-meps.json` | Extracted JSON data with all MEP metadata and source hyperlinks |
| `data/dsa-critics-meps-verified.xlsx` | Copy of source spreadsheet |
| `.claude/settings.json` | Claude Code permission settings for this project |

---

## How to replicate

### Prerequisites

```bash
python 3.8+
pip install openpyxl
```

### Steps

1. Clone this repository
2. Place `dsa-critics-meps-verified.xlsx` in the project root (or download fresh from the source)
3. Run the build script:
   ```bash
   python build.py
   ```
4. Open `index.html` in a browser (requires internet for the D3 map to load)

The build script:
- Reads the spreadsheet using `openpyxl`, extracting both cell values and hyperlink targets from source columns
- Saves `data/dsa-critics-meps.json`
- Copies the spreadsheet to `data/`
- Generates `index.html` with all data embedded as a JS variable

### Widget features

- **Interactive map** of Europe with bubble overlay (bubble size = MEP count per country; click to filter)
- **Filter bar**: EP Group pill toggles (color-coded), Country dropdown, name search
- **Card grid**: each MEP card shows name, country, national party, EP Group badge, key quote, notes, and clickable source links opening in a new tab
- **Bar charts**: MEP count by EP Group and by Country, updating dynamically with filters
- Single HTML file, no build tools required

---

## License

[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) — free to share and adapt with attribution.

## Author

*[Your name / organization here]*

---

*Built with [Claude Code](https://claude.ai/claude-code)*
