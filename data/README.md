# Data

The original analysis used two Excel versions of a literature-derived metal-oxide nanoparticle cytotoxicity dataset.

Expected local paths for the full notebook:

- `data/version_i.xlsx`
- `data/version_ii.xlsx`

The spreadsheets are not duplicated in this repository. This avoids presenting third-party scientific observations without their complete provenance and licensing context. Researchers with authorized copies can place them at the paths above and run the full notebook.

## Required fields

The modelling workflow expects fields covering:

- physicochemical properties: material type, core size, hydrodynamic size, surface charge and surface area;
- electronic descriptors;
- biological context: cell name, species, origin and type;
- experimental context: assay, mass dose and exposure time;
- endpoints: viability percentage and toxicity class;
- source-study grouping: PubMed identifier.

The self-contained `notebooks/synthetic_demo_pipeline.ipynb` creates a structurally similar synthetic dataset for code review and testing. Synthetic results must not be interpreted as scientific evidence.
