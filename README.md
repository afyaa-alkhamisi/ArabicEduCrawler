# ArabicEduCrawler: Arabic Educational Web Corpus Sample

Version: 1.0 
Year: 2026

================================================================================

## 1. Dataset Overview

ArabicEduCrawler is a structured Arabic educational web corpus developed to support research in Arabic natural language processing, semantic search, focused web crawling, corpus construction, and linguistic annotation.

The dataset was created from Arabic educational content collected from diverse live web sources through an AI-assisted focused crawling framework. The pipeline combines domain-aware source selection, Arabic language filtering during crawling using FastText, metadata preservation, sentence-aware chunking, and automatic linguistic annotation using GateNLP and Stanza.

This repository provides a public sample release of the ArabicEduCrawler dataset. The sample is intended to be representative, diverse across sources, and suitable for GitHub distribution, while the full dataset is openly available on Zenodo at https://doi.org/10.5281/zenodo.19996297.

================================================================================ 
## 2. Dataset Purpose

The primary objectives of the ArabicEduCrawler dataset are:

- To support research in Arabic corpus construction from live web sources.
- To enable experiments in Arabic semantic search and retrieval.
- To provide a structure for sentence-aware chunking analysis.
- To support research in Arabic linguistic annotation, including token-level,
  sentence-level, POS, and named-entity analysis.
- To provide a reproducible public subset of a larger thesis corpus while
  preserving the link between document metadata and chunked text.

================================================================================ 
## 3. Dataset Structure

This release is organized into three aligned dataset files:

#### chunks_text.json
A JSON file containing final cleaned chunk text without linguistic annotations.
Each record contains:

- global_id
A stable identifier for the source document.

- chunk_id
A stable identifier for the chunk within the source document.

- title
The document title.

- chunk_text
The final cleaned text of the chunk.

#### chunks_annotated.jsonl
A JSONL file containing the same chunk subset enriched with automatic
linguistic annotations. Each record contains the chunk text together with
fields such as:

global_id
chunk_id
title
chunk_text
token_count
chunk_length
sentence_count
tokens
sentences
ner_entities
pos_distribution

#### metadata.jsonl
A JSONL file containing document-level metadata exported from MongoDB and
aligned to the sample through chunk_ids. Each record contains:

global_id
A stable identifier for the source document.

chunk_ids
A list of all chunk identifiers associated with the document in this sample.

title
The document title.

url
The original source URL.

source_domain
The source website domain.

spider_name
The spider used to collect the document.

crawl_date
The recorded crawl date.

created_at
updated_at
content_length
content_hash_md5
metadata
lang_labels
lang_confidences

#### Example metadata.jsonl record:
{
"global_id": "20260287-6375-4904-8ae8-045d22fc9474",
"chunk_ids": ["20260287-6375-4904-8ae8-045d22fc9474_0"],
"title": "المهارات والقدرات المستهدفة بتبني نهج التقصي في تدريس العلوم",
"https://www.alukah.net/social/0/170873/المهارات-والقدرات-المستهدفة-بتبني-نهج-التقصي-في-تدريس-العلوم/",
"source_domain": "www.alukah.net",
"spider_name": "alukah"
}

#### Example chunks_text.json record:

{
"global_id": "20260287-6375-4904-8ae8-045d22fc9474",
"title": "المهارات والقدرات المستهدفة بتبني نهج التقصي في تدريس العلوم",
"chunk_id": "20260287-6375-4904-8ae8-045d22fc9474_0",
"chunk_text": "نهج التقصي أو ما يسمى أيضا التعليم الاستقصائي هو منهجية تعليمية تشجع المتعلمين على استكشاف وتحليل المواضيع بنشاط من خلال طرح الأسئلة وإجراء البحوث والتحريات بحيث يلعب المتعلمون دور المستكشفين والباحثين في مقابل التلقي السلبي للمعلومات،
وهذا النهج يعتمد في الغالب في تدريس العلوم يهدف نهج التقصي إلى تمكين المتعلمين من تطوير مجموعة واسعة من المهارات والقدرات هذه المهارات والقدرات تتنوع بين الفكرية والاجتماعية،
مما يعزز من قدرات المتعلمين في عدة جوانب في هذا المقال سنستعرض أهم هذه المهارات والقدرات المستهدفة
1-المهارات والقدرات المستهدفة في نهج التقصي: صياغة أسئلة التقصي تقديم اقتراحات التوضيح التبرير التفسير تحديد البدائل الممكنة تقييم الأسباب والأدلة التمييز التعريف التصنيف تحديد الاختلافات النوعية تحديد الاختلافات حسب الدرجة صياغة وتطبيق المعايير استخدام الأمثلة استخدام الأمثلة المضادة بناء تجارب فكرية استخدام التفكير الشرطي إجراء الاستنتاجات الاستنباطية إجراء الاستنتاجات الاستقرائية تحديد المقدمات تحديد الفرضيات تحديد الاستنتاجات
2-مهارات وقدرات اجتماعية مستهدفة بالتنمية والتطوير في هذا النهج التعليمي: الاستماع الفعال المساهمة في النقاش السماح للآخرين بالتعبير عن آرائهم الاعتراف بمساهمات الآخرين البناء على مساهمات الآخرين الاعتراف بالأخطاء الاعتراف بتغيير الرأي المساعدة في تركيب الفرضيات وتقديم الاقتراحات العمل بفعالية في فريق لعب دور معين في مجموعة نقاش نهج التقصي هو أسلوب تعليمي فعال يمكن أن يسهم بشكل كبير في تنمية مهارات التفكير النقدي وحل المشكلات لدى المتعلمين، من خلال تعزيز المهارات الفكرية والاجتماعية،
يمكن لهذا النهج أن يعد المتعلمين ليكونوا باحثين مستقلين وقادرين على مواجهة تحديات المستقبل"
}

This structure enables experiments that connect document-level provenance and
metadata with chunk-level text and annotation outputs.

================================================================================ 
## 4. Sample Scope

This public sample contains:

- 500 source documents
- 1080 chunks

The sample is balanced across the four spiders used in the corpus:

- alukah
- adab
- arabic_wiki
- shamela

The selected documents include both single-chunk and moderate multi-chunk
examples in order to expose users to diverse corpus structure without making
the public release too large for repository distribution.

================================================================================ 
## 5. Intended Uses

The ArabicEduCrawler dataset is intended for:

- Arabic semantic search research
- Information retrieval experiments
- Arabic NLP model training and evaluation
- Focused crawling and corpus construction research
- Sentence-aware chunking analysis
- Linguistic annotation research
- Academic and educational use

================================================================================ 
## 6. License

This dataset is licensed under the Creative Commons Attribution 4.0
International License (CC BY 4.0).

You are free to:

- Share — copy and redistribute the material
- Adapt — remix, transform, and build upon the material

Under the condition that appropriate credit is given.

License details:
https://creativecommons.org/licenses/by/4.0/

================================================================================ 
## 7. Citation

If you use this dataset, please cite:

### APA

Alkhamisi, A. A., Bamashmoos, F., & Alsaggaf, W. (2026). *ArabicEduCrawler: AI-Assisted Focused Crawling and Corpus Construction for Arabic Educational Web Content*. Applied Sciences, 16(12), 5964. https://doi.org/10.3390/app16125964

### BibTeX

```bibtex
@Article{app16125964,
  AUTHOR = {Alkhamisi, Afyaa Atyan and Bamashmoos, Fatmah and Alsaggaf, Wafaa},
  TITLE = {ArabicEduCrawler: AI-Assisted Focused Crawling and Corpus Construction for Arabic Educational Web Content},
  JOURNAL = {Applied Sciences},
  VOLUME = {16},
  YEAR = {2026},
  NUMBER = {12},
  ARTICLE-NUMBER = {5964},
  URL = {https://www.mdpi.com/2076-3417/16/12/5964},
  ISSN = {2076-3417},
  DOI = {10.3390/app16125964}
}
```




================================================================================ 
## 8. Author and Contact

Author:
Afyaa Atyan Alkhamisi
MSc Researcher, Information Technology
King Abdulaziz University
Jeddah, Saudi Arabia

Contact:

- aalkhamisi0047@stu.kau.edu.sa
- af.alkhamissi@gmail.com

================================================================================ 
## 9. Disclaimer

This dataset is intended for research and educational purposes only. Although
care was taken to preserve provenance, clean text, and structural consistency,
the corpus was collected and processed automatically from live web sources.
Users are responsible for validating outputs before using them in high-stakes
applications.

================================================================================
