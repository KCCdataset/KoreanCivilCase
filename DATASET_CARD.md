# Dataset Card: KCC (Korean Civil Case Dataset)



## 1. Dataset Overview

KCC is a benchmark dataset for legal information retrieval constructed from publicly accessible Korean civil court decisions. The dataset is designed to support evaluation of case retrieval and similarity modeling in statutory-law systems, where explicit citation links between cases are limited. KCC provides expert-annotated graded relevance labels that jointly reflect factual similarity and legal reasoning.





## 2. Data Sources

All cases in KCC are derived from publicly released and anonymized court decisions provided by official government platforms in the Republic of Korea, including the Supreme Court of Korea. The data were collected from AIhub and the Ministry of Government Legislation. No additional personal data processing or re-identification was performed by the authors.



## 3. Dataset Structure

The released dataset is organized as 20 JSON files, where each file corresponds to one query case (i.e., one representative civil dispute type). Each JSON file contains the query case and a set of candidate cases pooled for evaluation. For each query–candidate pair, the dataset provides:

- Precedent number (`query_precedentNumber`, `candidate_precedentNumber`): unique case identifier

- Case number (`query_caseNumber`, `candidate_caseNumber`): official court case number

- Sentence date (`query_sentenceDate`, `candidate_sentenceDate`): date of the judgment

- Case name (`query_caseName`, `candidate_caseName`): type of civil dispute

- Judgment abstract (`query_precedentAbstract`, `candidate_precedentAbstract`): summary of the key legal point

- Judgment note (`query_precedentNote`, `candidate_precedentNote`): explanatory note on the legal reasoning

- Judgment full text (`query_precedentText`, `candidate_precedentText`): full text of the court decision

- Graded relevance label (`label`): integer 0–3 assigned to the candidate with respect to the query

Each JSON file is a dictionary keyed by unique string identifiers. Each value is an object containing the fields listed above. The file naming convention is `KCCdataset_{precedentNumber}.json`, where `precedentNumber` corresponds to the query case.



Each query–candidate pair is annotated with a four-level graded relevance label:

- Label 3: Highly relevant (identical legal reasoning applied)

- Label 2: Relevant (legal reasoning present but not decisive)

- Label 1: Weakly relevant (shared keywords or surface similarity)

- Label 0: Not relevant



## 4. Annotation Process

Relevance labels were assigned through a multi-stage annotation process. Initial annotations were conducted by legally trained annotators with formal legal education. All labels were subsequently reviewed and verified by qualified legal experts. Detailed annotation guidelines are provided to ensure transparency and to support potential adaptation to other statutory-law contexts.

The provided annotation guidelines and data schema are designed to support straightforward adaptation to other statutory-law jurisdictions with minimal modification.


## 5. Intended Use

KCC is intended for research and evaluation purposes in legal information retrieval. Typical use cases include:

- Benchmarking legal case retrieval systems  

- Studying relevance modeling under graded relevance settings  



## 6. Not Intended Use

KCC is not intended to serve as a balanced training dataset for supervised learning. It should not be used for tasks requiring fine-grained factual reconstruction or evidence analysis. The dataset is also not intended for commercial deployment or real-world legal decision-making.



## 7. Limitations

The dataset includes a limited number of query cases and is predominantly composed of Supreme Court decisions, reflecting constraints in public data availability. Relevance labels are highly imbalanced, with relatively few highly relevant cases, mirroring realistic legal retrieval scenarios.



## 8. Ethical Considerations

All data originate from publicly available court records that were anonymized prior to release. The dataset does not contain personal data beyond legally disclosed information. Annotation focused solely on legal relevance and did not involve profiling of individuals.



## 9. License and Access

The dataset, annotation guidelines, and evaluation scripts will be released under a research-friendly license at a public repository to support immediate reuse by the community. 

The dataset is provided for research and evaluation purposes only. Commercial use and deployment for real-world legal decision-making are not permitted.

