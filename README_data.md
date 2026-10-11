# Data for "A Scientometric Analysis of Artificial Intelligence Literature for Engineering Problems"

This repository contains the aggregated data used in the manuscript submitted to the
*Journal of Scientometric Research*.

## File

`openalex_ai_engineering_data.json`: aggregated indicators retrieved from the OpenAlex API
(https://api.openalex.org) on 11 October 2026 (UTC). It contains:

- `query`: the 16 search terms combined with OR (title and abstract search).
- `N`: corpus sizes (AI corpus, engineering subset, all OpenAlex articles and reviews) and
  counts of documents in the top 10% / top 1% most cited and with international collaboration.
- `termCounts`: number of documents matching each term.
- `years`: documents per publication year (AI corpus, engineering subset, all OpenAlex).
- `fields`, `types`, `oa`: distribution by OpenAlex field, document type and open-access status.
- `countries`: documents per country (full counting), in the top 10% most cited, and
  internationally co-authored (AI corpus and engineering subset).
- `region`: Latin America and Global South aggregates.
- `inst`, `src`, `authors`: top institutions (with lineage), sources and authors.
- `topWorks`: 15 most cited documents in each corpus.
- `kw`, `topicsE`, `subfieldsE`, `period`: keywords, topics and subfields, overall and by period.

## Queries

AI corpus (works endpoint):

    filter=title_and_abstract.search:("artificial intelligence" OR "machine learning" OR "deep learning"
    OR "neural network" OR "reinforcement learning" OR "natural language processing" OR "computer vision"
    OR "large language model" OR "convolutional neural network" OR "generative adversarial network"
    OR "support vector machine" OR "random forest" OR "expert system" OR "fuzzy logic"
    OR "genetic algorithm" OR "swarm intelligence"),publication_year:2006-2026,type:article|review

Engineering subset: add `,primary_topic.field.id:22`.
Indicators: `citation_normalized_percentile.is_in_top_10_percent:true`,
`citation_normalized_percentile.is_in_top_1_percent:true`, `countries_distinct_count:>1`,
`institutions.is_global_south:true`, `authorships.countries:AR|BO|BR|CL|CO|CR|CU|DO|EC|SV|GT|HN|MX|NI|PA|PY|PE|UY|VE`.
Aggregations use the `group_by` parameter.

Validation samples: `sample=100&seed=7` (AI corpus) and `sample=60&seed=11` (engineering subset).

Note: OpenAlex is updated continuously, so re-running the queries at a later date will give
slightly different counts. The JSON file is the snapshot used in the manuscript.

## Licence

[CC BY 4.0]
