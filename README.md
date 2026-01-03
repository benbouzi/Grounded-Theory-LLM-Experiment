# AcademiaOS - Grounded Theory avec LLM

Implémentation automatisée de la **méthodologie Gioia** pour l'analyse qualitative, utilisant un LLM (Gemini) pour le codage et la théorisation.

## Description

AcademiaOS est un outil qui automatise les étapes de la Grounded Theory selon l'approche Gioia :

```
Documents (entretiens)
        │
        ▼
┌─────────────────────────────────────┐
│  PHASE 1: First-Order Coding        │
│  ├─ 1a: Extraction par unité Q/R    │
│  ├─ 1b: Filtre de fréquence         │
│  └─ 1c: Consolidation conceptuelle  │
└─────────────────────────────────────┘
        │
        ▼
┌─────────────────────────────────────┐
│  PHASE 2: Second-Order Coding       │
│  └─ Clustering → Thèmes académiques │
└─────────────────────────────────────┘
        │
        ▼
┌─────────────────────────────────────┐
│  PHASE 3: Aggregate Dimensions      │
│  └─ Dimensions mesurables           │
└─────────────────────────────────────┘
        │
        ▼
┌─────────────────────────────────────┐
│  PHASE 4: Développement théorique   │
│  ├─ 4a: Brainstorm théories         │
│  ├─ 4b: Tuples conceptuels          │
│  ├─ 4c: Interrelations (RAG)        │
│  ├─ 4d: Construction modèle         │
│  └─ 4e: Critique itérative          │
└─────────────────────────────────────┘
        │
        ▼
   Modèle théorique + Diagramme Mermaid
```

## Fonctionnalités

- **Détection automatique Q/R** : Identifie les échanges interviewer/répondant dans les transcripts
- **Codage par unité de réponse** : Code les réponses entières (pas phrase par phrase)
- **Filtre de récurrence** : Identifie les patterns qui apparaissent dans plusieurs sources
- **Consolidation sémantique** : Regroupe les codes similaires
- **Clustering KMeans** : Génère des thèmes de second ordre
- **RAG (Retrieval-Augmented Generation)** : Explore les interrelations avec preuves textuelles
- **Cache embeddings** : Évite de recalculer les embeddings à chaque exécution
- **Export complet** : Excel multi-onglets, fichiers texte, diagramme Mermaid

## Prérequis

- Python 3.8+
- Clé API Google Gemini
- Google Colab (recommandé) ou environnement local

## Installation

```bash
pip install google-generativeai python-docx PyPDF2 scikit-learn pandas numpy
```

## Utilisation

1. Ouvrir `Academios.ipynb` dans Google Colab
2. Remplacer `API_KEY` par votre clé Gemini
3. Exécuter les cellules
4. Charger vos fichiers d'entretien (.txt, .docx, .pdf)
5. Entrer votre question de recherche
6. Suivre le processus étape par étape

## Formats d'entretien supportés

Le système détecte automatiquement les structures Q/R :

```
INTERVIEWER: Comment utilisez-vous ChatGPT ?
RESPONDENT: Je l'utilise tous les jours...

Q: Pourquoi ?
R: C'est plus rapide...
```

## Exports générés

| Fichier | Contenu |
|---------|---------|
| `ACADEMIAOS_IMPROVED_RESULTS.xlsx` | Codes, thèmes, dimensions, théories |
| `EVIDENCE_CHUNKS_TUPLES.txt` | Passages sources pour chaque relation |
| `MODELE_ITERATION_N.txt` | Modèles théoriques avec critiques |
| `DIAGRAM_MERMAID.mmd` | Diagramme des relations |
| `STATISTIQUES_ANALYSIS.txt` | Récapitulatif quantitatif |

## Architecture du code

```
AcademiaOSGioiaAnalyzer
├── Lecture documents
│   ├── read_txt_file()
│   ├── read_docx_file()
│   └── read_pdf_file()
├── Phase 1
│   ├── first_order_coding()
│   ├── filter_by_frequency()
│   └── consolidate_codes()
├── Phase 2
│   └── second_order_coding()
├── Phase 3
│   └── aggregate_dimensions_coding()
├── Phase 4
│   ├── brainstorm_theories()
│   ├── develop_concept_tuples()
│   ├── explore_interrelationships()
│   ├── construct_model()
│   └── critique_model()
└── Export
    └── export_results()
```

## Licence

MIT

## Auteur

Projet de recherche sur l'utilisation des LLM pour l'analyse qualitative.
