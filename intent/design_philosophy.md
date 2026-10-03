# Design philosophy: intent.yml

Why [intent.yml](intent.yml) is structured the way it is: which frameworks each section borrows from, and which choices are our own without an external source. All links resolved at time of writing (2026-10-03).

## Frameworks used

| Framework | What it contributes | Where in intent.yml | Source |
|---|---|---|---|
| **Google-style design docs** | Context, goals, *non-goals* as a first-class section | `problem`, `goals`, `non_goals` | Malte Ubl, [Design Docs at Google](https://www.industrialempathy.com/posts/design-docs-at-google/) |
| **arc42** | Architecture documentation template. Supplies the section split for stakeholders, constraints, context/scope, risks and glossary | `stakeholders`, `constraints`, `system.inputs/outputs`, `risks`, `glossary` | [arc42 overview](https://arc42.org/overview); sections [1 Goals & stakeholders](https://docs.arc42.org/section-1/), [2 Constraints](https://docs.arc42.org/section-2/), [3 Context](https://docs.arc42.org/section-3/), [11 Risks](https://docs.arc42.org/section-11/), [12 Glossary](https://docs.arc42.org/section-12/) |
| **C4 model (System Context)** | Describe the system as a black box with inputs, outputs and the people around it before designing internals | `system.inputs`, `system.outputs` | [c4model.com](https://c4model.com/) |
| **Volere requirements template** | Separate constraints, assumptions and fit criteria (measurable acceptance) for each requirement | `constraints`, `risks` (assumptions), `success_criteria` | [Volere template](https://www.volere.org/templates/volere-requirements-specification-template/) |
| **FAIR principles** | Findable, Accessible, Interoperable, Reusable: the standard for judging the reusability of scientific data | `problem.sub_problems[].fair`, `system.feasibility_rubric` | Wilkinson et al. 2016, [Scientific Data](https://www.nature.com/articles/sdata201618); [GO FAIR summary](https://www.go-fair.org/fair-principles/) |
| **Jobs to be Done** | Describe users by the progress they want to make, not by demographics | `stakeholders.users[].job_to_be_done` | Christensen et al., [Know Your Customers' "Jobs to Be Done"](https://hbr.org/2016/09/know-your-customers-jobs-to-be-done) (HBR, 2016) |
| **Goal-Question-Metric (GQM)** | Each goal gets a question and a metric, so success is measured, not asserted | `success_criteria` (criterion → metric → target) | Basili, Caldiera & Rombach, [The Goal Question Metric Approach](https://www.cs.umd.edu/~mvz/handouts/gqm.pdf) |
| **Pretotyping** | Test whether people want the thing before building it | `goals.G3`, `glossary.pretotype` | Alberto Savoia, [pretotyping.org](https://www.pretotyping.org/) (book: *The Right It*) |
| **Test Card (hypothesis, metric, criterion)** | Each experiment states a falsifiable hypothesis, what is measured and the pass/fail threshold | `glossary.kill_threshold`, `success_criteria.S6` | Strategyzer, [The Test Card](https://www.strategyzer.com/library/the-test-card) |
| **Product risk framing (SVPG)** | Value risk is assessed before building; inspired framing the system as a "cheap before expensive" filter | `problem.core_insight`, `principles.PR4` | Marty Cagan, [The Four Big Risks](https://www.svpg.com/four-big-risks/); [Assessing Product Opportunities](https://www.svpg.com/assessing-product-opportunities/) |
| **Ubiquitous language (DDD)** | Agree on one meaning per term and use it everywhere | `glossary` | Martin Fowler, [UbiquitousLanguage](https://martinfowler.com/bliki/UbiquitousLanguage.html) |
| **Small-cell suppression** | Precedent for suppressing small counts to prevent re-identification | `constraints.C3` | ResDAC, [CMS Cell Size Suppression Policy](https://resdac.org/articles/cms-cell-size-suppression-policy) (CMS uses a threshold of 11) |

## Choices without an external source

These are judgement calls made while restructuring. Revisit them freely.

- **Splitting anti-goals into `non_goals`, `constraints` and `principles`.** arc42 and Volere separate constraints from goals; the further split between hard rules (constraints) and trade-off guidance (principles) is our own convention.
- **Separating `system_value` from `output_value_example`.** Introduced to keep the discovery system apart from the DMD data product it helps evaluate.
- **Extending FAIR with `quality`, `freshness` and `privacy_risk`** in the feasibility rubric. FAIR does not cover these.
- **Ranking of `sub_problems`.** A hypothesis, to be checked on the first DMD run.
- **All numeric targets** (80% recall, 70% precision, < 1 working day, minimum cell size 10). Placeholders to calibrate.
- **Using the DMD source list in scientific_background.md as a reference set** for discovery recall.
- **Conciseness cuts (v0.3).** Removed `quality_attributes` (they repeated principles and success criteria; "no hallucinated datasets" became constraint C5), `validation_cases` (folded into S1 and S7), `affected_parties` (covered by constraints), the separate `assumptions` list (merged into `risks`), and most glossary terms. The DMD value example is now a pointer to business_case.md. FAIR is explained here rather than in the glossary.

## Markers introduced into intent.yml

Fields that come from a specific framework, so they are recognisable when reading the YAML:

| Field | Framework |
|---|---|
| `fair:` on each sub-problem | FAIR |
| `job_to_be_done:` on each user | Jobs to be Done |
| `metric / target` (and `measurement` where not obvious) on success criteria | GQM, Volere fit criteria |
| `kill_threshold` | Pretotyping, Test Card |
| `id:` prefixes (P, G, C, PR, S) | Convention for traceability between sections; no specific source |
