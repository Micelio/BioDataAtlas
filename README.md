# BioDataAtlas

Landing page for an informal, ongoing effort connecting biodiversity data —
iNaturalist, GBIF, BHL (Biodiversity Heritage Library), Plazi TreatmentBank —
to Wikidata and the wider Semantic Web, via QLever and related RDF tooling.

## Participants

Alphabetically by last name. ORCID is the primary identifier; a Wikidata item
is linked where one exists.

| Name | ORCID | Wikidata |
|---|---|---|
| Donat Agosti | [0000-0001-9286-1200](https://orcid.org/0000-0001-9286-1200) | [Q20650434](https://www.wikidata.org/wiki/Q20650434) |
| Hannah Bast | [0000-0003-1213-6776](https://orcid.org/0000-0003-1213-6776) | [Q18642047](https://www.wikidata.org/wiki/Q18642047) |
| Jerven Bolleman | [0000-0002-7449-1266](https://orcid.org/0000-0002-7449-1266) | [Q56888653](https://www.wikidata.org/wiki/Q56888653) |
| Alberto Cámara Ballesteros | [0000-0001-5613-9704](https://orcid.org/0000-0001-5613-9704) | — ([lab page](https://wilkinsonlab.info/people/alberto-camara.html)) |
| Siobhan Leachman | [0000-0002-5398-7721](https://orcid.org/0000-0002-5398-7721) | [Q54823671](https://www.wikidata.org/wiki/Q54823671) |
| Rod Page | [0000-0002-7101-9767](https://orcid.org/0000-0002-7101-9767) | [Q7356570](https://www.wikidata.org/wiki/Q7356570) |
| Andra Waagmeester | [0000-0001-9773-4008](https://orcid.org/0000-0001-9773-4008) | [Q19845625](https://www.wikidata.org/wiki/Q19845625) |
| Mark D Wilkinson | [0000-0001-6960-357X](https://orcid.org/0000-0001-6960-357X) | [Q37392357](https://www.wikidata.org/wiki/Q37392357) |
| Lars Willighagen | [0000-0002-4751-4637](https://orcid.org/0000-0002-4751-4637) | [Q45907528](https://www.wikidata.org/wiki/Q45907528) |
| Yasunori Yamamoto | [0000-0002-6943-6887](https://orcid.org/0000-0002-6943-6887) | [Q59490274](https://www.wikidata.org/wiki/Q59490274) |

## Related repositories

| Repository | What it is |
|---|---|
| [wikiproject-biodiversity/wikiproject-biodiversity.github.io](https://github.com/wikiproject-biodiversity/wikiproject-biodiversity.github.io) | Hosts the iNaturalist × Wikidata/Wikipedia/GBIF/BHL curation dashboard (`inat-wikidata-dashboard/`) |
| [wikiproject-biodiversity/treatmentbot](https://github.com/wikiproject-biodiversity/treatmentbot) | Bot syncing Plazi TreatmentBank with Wikidata |
| [wikiproject-biodiversity/taxonname-wpstubmaker](https://github.com/wikiproject-biodiversity/taxonname-wpstubmaker) | Jupyter notebook drafting Wikipedia stubs from extracted taxon data |
| [wikiproject-biodiversity/iNotListed](https://github.com/wikiproject-biodiversity/iNotListed) | CLI tool for finding taxa missing a Wikipedia article (dev on [Codeberg](https://codeberg.org/wikiproject-biodiversity/iNotListed)) |
| [Koetai/koetai-platform](https://github.com/Koetai/koetai-platform) | FAIR SPARQL endpoint platform — multi-tenant QLever with ORCID auth, ShEx/SHACL, SPARQList (dev on [Codeberg](https://codeberg.org/andrawaag/koetai-platform)); hosts the BHL → RDF pipeline and its live QLever endpoint |
| [wilkinsonlab/FLAIR-GG](https://github.com/wilkinsonlab/FLAIR-GG/tree/main/SemanticModel) | Related YARRRML-mapping-plus-data-model-diagram semantic model (Location/Germplasm/Administrative) |
| [Micelio/gbif_parquet](https://github.com/Micelio/gbif_parquet) | GBIF occurrence Parquet snapshots → RDF/Turtle, with its own ShEx shape graph |

## Resources consulted

Live SPARQL/data endpoints this effort queries against.

| Resource | Endpoint |
|---|---|
| UniProt | [sparql.uniprot.org/sparql](https://sparql.uniprot.org/sparql) |
| GBIF (QLever mirror) | [qlever.dev/api/gbif](https://qlever.dev/api/gbif) |
| SynoSpecies (Plazi TreatmentBank, QLever mirror) | [qlever.ld.plazi.org/sparql](https://qlever.ld.plazi.org/sparql) |
| Plazi TreatmentBank | [tb.plazi.org](https://tb.plazi.org) |
| BHL (Biodiversity Heritage Library) at Koetai | [koetai.semscape.org/u/0000-0001-9773-4008/bhl/sparql](https://koetai.semscape.org/u/0000-0001-9773-4008/bhl/sparql) |
| Bionames (Rod Page's own Koetai instance — Bionomia, BHL, registry datasets) | [koetai.bionames.org/endpoints](https://koetai.bionames.org/endpoints) |

## Semantic artefacts

Mappings, shapes, and reconciliation logic already produced by this effort.

**[koetai-platform](https://github.com/Koetai/koetai-platform) — BHL → RDF pipeline** (`pipelines/bhl/artifacts/`):
| Artefact | Purpose |
|---|---|
| [`bhl-mapping.yarrrml.yml`](https://github.com/Koetai/koetai-platform/blob/main/pipelines/bhl/artifacts/bhl-mapping.yarrrml.yml) | YARRRML/RML mapping, BHL TSVs → RDF |
| [`bhl-shape.shex`](https://github.com/Koetai/koetai-platform/blob/main/pipelines/bhl/artifacts/bhl-shape.shex) | ShEx shapes the output must satisfy |
| [`reconcile-wikidata.rq`](https://github.com/Koetai/koetai-platform/blob/main/pipelines/bhl/artifacts/reconcile-wikidata.rq) | Wikidata reconciliation query: `dwc:scientificName` → taxon (`wdt:P225`) |
| [`lookups.py`](https://github.com/Koetai/koetai-platform/blob/main/pipelines/bhl/artifacts/lookups.py) | Identifier → URI resolution |
| [`provenance.ttl.j2`](https://github.com/Koetai/koetai-platform/blob/main/pipelines/bhl/artifacts/provenance.ttl.j2) | Provenance template for the Zenodo bundle |

**[Micelio/gbif_parquet](https://github.com/Micelio/gbif_parquet) — GBIF occurrences → RDF**:
| Artefact | Purpose |
|---|---|
| [ShEx shape graph](https://github.com/Micelio/gbif_parquet#gbif-parquet----rdf-shex-shape-graph) (4 shapes, incl. `OccurrenceShape`) | Shapes the generated occurrence RDF must satisfy |
| [`SPARQL/federatedWikidata.rq`](https://github.com/Micelio/gbif_parquet/blob/main/SPARQL/federatedWikidata.rq) | Federated query against Wikidata |
| [`SPARQL/geoQuery.rq`](https://github.com/Micelio/gbif_parquet/blob/main/SPARQL/geoQuery.rq) | Geographic query |
| [`SPARQL/institution_counts.rq`](https://github.com/Micelio/gbif_parquet/blob/main/SPARQL/institution_counts.rq) | Occurrence counts per institution |
| [`SPARQL/predicates.rq`](https://github.com/Micelio/gbif_parquet/blob/main/SPARQL/predicates.rq) | Predicate inventory |
