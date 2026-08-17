# Generative AI Governance in Education: Scoping Review Data

Machine-readable data supporting the scoping review *Generative AI Governance in
Education: A Scoping Review of Principles, Mechanisms, and Risks in
English-Language Documents*.

The review analyses **160 English-language governance documents** published from
**January 2020 through December 2025**, identified through a globally scoped
gray-literature search and coded against a 34-category document-level codebook.
Every count and percentage reported in the article can be reproduced from the
files in this repository.

## Files

| File | Contents | Rows |
|---|---|---|
| `document_inventory.csv` | Corpus membership and metadata: issuer, year, title, type and sector codes, citation key, URL, DOI | 160 |
| `codebook.csv` | Inclusion and exclusion rules for all 34 coding categories | 34 |
| `category_frequencies.csv` | Document count and percentage for each category | 34 |
| `document_category_matrix.csv` | The 160-by-34 binary coding matrix with retrieval-status and confidence provenance | 160 |
| `instrument_strata.csv` | The four authority-sensitive instrument-form strata | 4 |
| `instrument_stratified_frequencies.csv` | All 34 category counts recomputed within each stratum | 136 |
| `document_level_cooccurrence.csv` | Principle–mechanism, principle–risk, and mechanism–risk same-document counts | 385 |
| `live_page_temporal_sensitivity.csv` | Effect on every category total of excluding one unrecovered live page | 34 |
| `screening_flow_by_source.csv` | Identification, screening, retrieval, and inclusion counts by source and continent | 21 |
| `PRISMA_title_query_log.csv` | Queried title, date, field, core Boolean query, URL and domain, and corpus metadata for each included document | 160 |

All files are comma-delimited CSV with a single header row. Most carry a UTF-8
byte-order mark, so read them as `utf-8-sig` rather than plain `utf-8`; line
endings are CRLF and are preserved byte-for-byte via `.gitattributes`.

```python
import csv
rows = list(csv.DictReader(open("document_inventory.csv", encoding="utf-8-sig")))
```

`record_id` joins `document_inventory.csv` to `document_category_matrix.csv`, and
`citation_key` joins both to the other tables and to the article's reference list.

## Coding scheme

The 34 categories comprise **11 normative principles** (`P1`–`P11`), **12
governance mechanisms** (`M1`–`M12`), and **11 ethical and pedagogical risk
categories** (`R1`–`R11`). Each code is a **binary document-level indicator**:
it records whether a document contains substantive content meeting the rule in
`codebook.csv`. Keyword presence alone does not qualify. Percentages throughout
use the 160-document denominator.

## Corpus composition

Screening flow: **498** records identified, **255** screened, **243** full texts
retrieved, **160** included.

| Issuer family | n |
|---|---|
| Intergovernmental and regional organizations | 47 |
| Education-sector bodies | 9 |
| Think-tanks, NGOs, and policy labs | 7 |
| National and jurisdiction-based sources | 97 |

| Instrument form | n | % |
|---|---|---|
| Formal legal or regulatory form (REG) | 4 | 2.5 |
| Official policy or national strategy (POL) | 24 | 15.0 |
| Guidance, advisory, or toolkit (GEF/TLK) | 92 | 57.5 |
| Report, analysis, or white paper (REP/WP) | 40 | 25.0 |

Publication years: 2020 (1), 2021 (1), 2022 (2), 2023 (25), 2024 (66), 2025 (65).

## How to read these numbers

Four boundaries govern any reuse of this data. They are stated in the article and
repeated here so the files are not read for more than they support.

1. **Frequencies measure documentary attention, not prevalence.** Counts describe
   attention within this assembled English-language corpus. They are not
   jurisdiction-weighted estimates of worldwide activity, evidence of global
   consensus, or measures of the incidence or severity of harm in practice. The
   corpus is concentrated among U.S. issuers (n = 42) and UNESCO (n = 23).
2. **`M2` is not a count of legal instruments.** Mechanism `M2` records whether a
   document *creates or invokes* legal or regulatory controls, irrespective of
   its own form. It is coded in 131 documents, whereas only **4** documents take
   formal legal or regulatory form (see `instrument_strata.csv`).
3. **Co-occurrence is same-document co-presence only.** The counts in
   `document_level_cooccurrence.csv` identify candidate material for close
   reading. They do not establish clause-level linkage, causation,
   implementation, enforcement, effectiveness, or legal authority.
4. **Coding used calibration, not a formal reliability study.** A third coder
   independently coded a stratified 32-document sample; six documents contained
   at least one discrepancy, definitions were refined, and the full corpus was
   re-examined. **No chance-corrected coefficient was calculated**, and no
   statistical claim of intercoder reliability is made. The per-document
   `coding_confidence` and `retrieval_status` fields in
   `document_category_matrix.csv` record the provenance of each row.

The per-code evidence passages held in the authors' working coding file are not
redistributed here. Requests for that material should be directed to the
corresponding author.

The review maps governance **as written**. It does not measure whether a
framework changes educator behavior, protects learners, improves outcomes, or is
enforced.

## Scope notes

- Eligibility was limited to documents in English or with an official English
  translation, so the corpus is neither linguistically nor geographically
  representative. No South American national document met both the language and
  the substantive education-governance criteria.
- 81 records are general or cross-sector instruments, eligible only where a
  substantive passage applied governance to an education or education-and-research
  context. Aggregate totals therefore combine broad instruments with
  education-specific guidance.
- `PRISMA_title_query_log.csv` covers the 160 **included** documents. Record-level
  queries for candidates excluded before final inclusion were not retained;
  `screening_flow_by_source.csv` carries the aggregate stage arithmetic for all
  498 identified records.
- Full texts of the reviewed documents are not redistributed here.
  `document_inventory.csv` provides source URLs and DOIs where available.

## Citation

Elmahjub, E., Arshad, M. H., Iqbal, W., Tabassum, A., Pathari, S., & Qadir, J.
*Generative AI Governance in Education: A Scoping Review of Principles,
Mechanisms, and Risks in English-Language Documents.*

Please cite the article when reusing this data.

## License

The data files are released for research reuse. Rights in the underlying source
documents remain with their respective issuers.
