---
license: cc-by-4.0
language:
  - fr
pretty_name: "Protocole & Référentiel Open-Science (2026-2027) — Diarisation Multi-Locuteurs & Sigles Institutionnels Francophones (FR, BE, CH, CA-QC)"
size_categories:
  - n<1K
tags:
  - french
  - diarization
  - multi-speaker
  - francophonie
  - belgium
  - switzerland
  - quebec
  - speech-recognition
---

# Protocole Méthodologique & Référentiel Open-Science (2026-2027) — Diarisation Multi-Locuteurs en Salle Réverbérante & Terminologie Institutionnelle Francophone (`FR`, `BE`, `CH`, `CA-QC`)

[![HAL CNRS](https://img.shields.io/badge/CNRS_HAL-hal--05865820-003366.svg)](https://hal.science/hal-05865820)
[![Parent Benchmark DOI](https://img.shields.io/badge/Benchmark%20DOI-10.5281%2Fzenodo.24215193-blue.svg)](https://doi.org/10.5281/zenodo.24215193)
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC_BY_4.0-emerald.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Frictionless Data](https://img.shields.io/badge/Standard-Frictionless_Data_Package-4f46e5.svg)](./datapackage.json)

**FR** · Référentiel terminologique ouvert (`CSV` — **48 sigles et termes institutionnels** en France, Belgique, Suisse romande et Québec), protocole d'évaluation de la diarisation multi-locuteurs (`4 à 12 voix` en acoustique de salle réverbérante) et corpus synthétique anonymisé (`JSON`) publiés sous licence **Creative Commons Attribution 4.0 (`CC-BY-4.0`)** par [**LE SCRIBE AUDIO**](https://lescribeaudio.com/benchmark-diarisation-multi-locuteurs-salle-reverberante-francophonie), en complément direct du benchmark national déposé sur **CNRS HAL (`⟨hal-05865820⟩`)** et **CERN Zenodo (`10.5281/zenodo.24215193`)**.

**EN** · Open-science methodological protocol and 48-term francophone institutional lexicon (`FR`, `BE`, `CH`, `CA-QC`) released under **`CC-BY-4.0`** by [**LE SCRIBE AUDIO**](https://lescribeaudio.com/benchmark-diarisation-multi-locuteurs-salle-reverberante-francophonie) as a companion supplement to our open French ASR benchmark on **CNRS HAL (`⟨hal-05865820⟩`)** and **CERN Zenodo (`10.5281/zenodo.24215193`)**, documenting 1-pass acoustic homophone traps versus 2-pass contextual disambiguation and multi-speaker room diarization.

---

## Contenu du Dépôt (`v1.0.0`)

| Fichier | Format | Description |
| :--- | :---: | :--- |
| `dataset/referentiel_sigles_francophonie_diarisation.csv` | `CSV` (`UTF-8`) | **48 entrées institutionnelles vérifiées** (`12 FR`, `12 BE`, `12 CH`, `12 CA-QC`) : prononciation orale réelle (épelée ou syllabique), hallucinations homophoniques typiques en ASR 1 passe et indices co-occurrents exploités en 2 passes. |
| `dataset/corpus_synthetique_multilocuteurs_francophonie_anonymise.json` | `JSON` (`UTF-8`) | **Corpus synthétique multi-locuteurs 100 % anonymisé** (`M. Martin`, `Mme Dubois`, `M. Bernard`, `Enquêté P1`) simulant 4 séances délibérantes francophones (CSE/CGCT France, CPPT/Collège communal Belgique, Grand Conseil/nLPD Suisse, BAPE/CNESST/Loi 25 Québec). |
| `datapackage.json` | `JSON` | Descripteur standard *Frictionless Data* compatible `data.gouv.fr`, OpenAIRE et Python/R. |
| `zenodo.json`, `.zenodo.json` & `CITATION.cff` | `JSON` / `YAML` | Métadonnées bibliographiques reliées au dépôt parent CNRS HAL `https://hal.science/hal-05865820` et Zenodo `10.5281/zenodo.24215193`. |

---

## Synthèse Méthodologique & Règles de Vérité Opérationnelle

1. **Pourquoi les sigles institutionnels francophones piègent-ils l'ASR acoustique 1 passe ?**
   - À l'oral spontané dans une salle présentant un `RT60` de `0,7 s` à `1,4 s`, un acronyme épelé (`C-P-P-T`, `C-N-E-S-S-T`, `n-L-P-D`) ou prononcé en mot (`BAPE`, `SUVA`, `PLUi`, `DUERP`) est acoustiquement indiscernable d'une séquence de petits mots fréquents (*« c'est pépé té »*, *« la scène est restée »*, *« le pape »*, *« sous va »*, *« pluie »*).
   - Sans liste lexicale ad hoc pré-injectée avant calcul, une **architecture séquentielle en 2 passes** opérant sur des **fenêtres de 20 minutes avec recouvrement (*overlap*) de 5 secondes** résout ces homophonies grâce aux co-occurrences lexicales de la séance entière.
   - Sur la table ronde multi-intervenants Canal-U (`sample3`) évaluée au Suivi des modifications Microsoft Word : **`72` révisions** sur Le Scribe Audio (`/docs/benchmark/lescribe-sample3.pdf`) contre **`116` à `248` révisions** sur les 9 moteurs concurrents (et **`47` révisions** contre `123` et `151` sur l'entretien CNRS d'1h16 — script reproductible : `/docs/benchmark/evaluate_benchmark_reproducibility.py`).
2. **Distinction stricte entre Codage de la Diarisation et Pseudonymisation du Corps du Texte** :
   - Le lecteur synchronisé permet le **codage/renommage global en 1 clic des étiquettes d'intervenants** (`Intervenant 1` → `M. Martin`, `Mme Dubois` ou `Enquêté P1`) avant export vers un **fichier Microsoft Word (`.docx`) standard 100 % modifiable** (les exports générés par IA comportent en bas de page la mention transparente : *« Transcription générée par intelligence artificielle sur lescribeaudio.com, une vérification humaine est recommandée »*, librement modifiable après relecture).
   - Ce codage des étiquettes de diarisation **ne remplace pas** la vérification humaine des noms propres cités à l'intérieur même des phrases prononcées : une **réécoute intégrale avec mise en forme demande 2 à 3 heures par heure d'audio** (contre **4 à 7 heures** de frappe manuelle à partir de zéro, soit un **temps de rédaction divisé par 2**), ou peut être confiée à l'option de **correction humaine à 60 € HT/h** par **deux transcripteurs successifs**.
   - La synthèse IA optionnelle en 1 clic produit une **synthèse exécutive** suivie d'un **développement chrono-thématique** horodaté `[hh:mm:ss - hh:mm:ss]`, sans liste d'actions extrapolée.
3. **Transparence Juridique RGPD (UE), nLPD (Suisse), Loi 25 (Québec) & US Cloud Act** :
   - **Stockage au repos en France chez OVHcloud (`AES-256`)** et **suppression définitive en 1 clic** par l'utilisateur, sans aucun bot de visioconférence ni accès OAuth calendrier.
   - **Inférence via Google Cloud Vertex AI (en région Europe)** sous engagement contractuel **Zero Data Retention** (aucune conservation, aucun entraînement sur les données), en précisant avec exactitude pour les DPO/RPRP que l'éditeur Google Cloud demeure une société américaine soumise en droit au *US Cloud Act*.

---

## Références Parentes & Ressources Vérifiées

- **Archive Ouverte Nationale CNRS HAL** : [https://hal.science/hal-05865820](https://hal.science/hal-05865820) (`⟨hal-05865820⟩`)
- **Dépôt CERN Zenodo (Benchmark Français `v1.1.0`)** : [https://doi.org/10.5281/zenodo.24215193](https://doi.org/10.5281/zenodo.24215193)
- **Étude complète Diarisation & Francophonie** : [https://lescribeaudio.com/benchmark-diarisation-multi-locuteurs-salle-reverberante-francophonie](https://lescribeaudio.com/benchmark-diarisation-multi-locuteurs-salle-reverberante-francophonie)
- **Matrice DPO 15 Solutions (RGPD, nLPD, Loi 25, Cloud Act)** : [https://lescribeaudio.com/matrice-conformite-rgpd-nlpd-loi-25-cloud-act-logiciels-transcription](https://lescribeaudio.com/matrice-conformite-rgpd-nlpd-loi-25-cloud-act-logiciels-transcription)
- **Éditeur** : **LE SCRIBE AUDIO** (`RCS Rennes 890 049 927`) · `Jérémie TERRAL — Assistant de direction, LE SCRIBE AUDIO` · `09 61 44 46 64` (`+33 9 61 44 46 64`) · `info@lescribeaudio.com`
