Forced Alignment with Montreal Forced Aligner
Overview
This project demonstrates a complete forced alignment pipeline using the Montreal Forced Aligner (MFA) tool. It automatically matches speech audio with text transcripts at word and phoneme levels, outputting Praat-compatible TextGrids. The workflow and scripts provided enable easy reproduction and extension for similar datasets.

Setup Instructions
Requirements:

Python 3.8–3.11 (recommended via Miniconda)

Montreal Forced Aligner

Praat (optional, for viewing results)

Windows or Linux OS

Installation:

bash
conda create -n aligner -c conda-forge montreal-forced-aligner
conda activate aligner
# (Optional) If on Windows, use PostgreSQL backend to avoid SQLite errors
# Download models and dictionary
mfa model download acoustic english_us_arpa
mfa model download dictionary english_us_arpa
Dataset Preparation
Place your .wav audio and corresponding .txt transcript files in a folder, e.g. corpus/, ensuring each audio/transcript pair shares the same base filename.

Example:

text
corpus/
  ├── sample1.wav
  └── sample1.txt
Running the Alignment
bash
# Basic command (use PostgreSQL flags for best compatibility on Windows)
mfa align corpus english_us_arpa english_us_arpa output --use_postgres --auto_server
Output .TextGrid files will be saved to the output/ folder for each audio input.

Viewing Results
Open output .TextGrid and .wav in Praat:

In Praat, open both files via File > Open > Read from file...

Select both in the Objects window, then View & Edit to inspect word and phoneme boundaries.
