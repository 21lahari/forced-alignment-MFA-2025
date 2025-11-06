# Forced Alignment with Montreal Forced Aligner (MFA)

## Overview
This repository provides a complete pipeline for forced alignment of speech audio and transcripts using **Montreal Forced Aligner (MFA)**. It outputs Praat-compatible TextGrids with word and phoneme boundaries. Workflow and scripts enable direct reproduction and adaptation for similar datasets.

***

## Requirements
- Python 3.8–3.11 (recommended via Miniconda/Anaconda)
- Montreal Forced Aligner (see [MFA GitHub])[1]
- Praat (optional, for viewing `.TextGrid` outputs)
- Windows or Linux OS

***

## Installation
Create and activate a dedicated environment using Conda:
```bash
conda create -n aligner -c conda-forge montreal-forced-aligner
conda activate aligner
```
For Windows users: to avoid SQLite errors, use PostgreSQL backend flags in alignment commands.

Download necessary models and dictionaries:
```bash
mfa model download acoustic english_us_arpa
mfa model download dictionary english_us_arpa
```

***

## Dataset Preparation
Organize your audio (.wav) and transcript (.txt) files in a folder, e.g. `corpus/`. Each transcript filename must match its audio (apart from the extension):
```bash
corpus/
  ├── sample1.wav
  └── sample1.txt
```
Prepare an empty output folder, e.g. `output/`.

***

## Running Alignment
Run forced alignment and generate `.TextGrid` files:
```bash
mfa align corpus english_us_arpa english_us_arpa output --use_postgres --auto_server
```
Outputs will appear in the `output/` folder, one `.TextGrid` per input audio file.

***

## Viewing Results in Praat
1. Open Praat software.
2. "File" → "Open" → "Read from file..."; load a `.wav` and its matching `.TextGrid`.
3. Select both in the Objects window, then click "View & Edit" to see word/phoneme boundaries.
4. Zoom and play audio to inspect accuracy.

***

## Troubleshooting
- **SQLite errors on Windows:** Always use `--use_postgres --auto_server` flags.
- Corpus files must have matching base names; ensure no missing files or typos.
- See [MFA documentation] and [tutorials] for advanced usage.[3][6]
  ***
  
## References
- [MFA Official GitHub][1]
- [MFA Documentation][3]
- [Praat Software]

***

**Contact:** Maintainer: Pasham Lahari / Email: pashamlahari21@gmail.com
