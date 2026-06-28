# Computational Neuroscience — Martina Napoli

## Overview

Perceptual decisions are usually based on current sensory information, but previous choices may also influence later judgments. This project examines whether repeated perceptual decisions depend only on new evidence or are biased by previous choices.

Participants performed a visual task in which they classified sequences of oriented stimuli as **cardinal** or **diagonal** across repeated presentations. The design allowed us to test whether decision stability reflected simple response repetition or a biased integration of new sensory evidence.

Behavioral results showed that participants often repeated previous decisions, even when the stimulus order changed. However, they remained sensitive to the current sensory evidence, suggesting that later choices combined new information with previous decisions. Confidence also contributed to this effect, as high-confidence decisions were more likely to be repeated.

Computational modeling showed that previous decisions were better explained as influencing evidence accumulation rather than only the initial response bias. Machine learning and EEG analyses provided complementary evidence that decision history and neural activity contained information about later behavior.

Overall, these findings suggest that perceptual confirmation bias stabilizes previous interpretations and influences how new sensory evidence is used.

---

## TFG Reports

This repository includes the TFG documentation in the `REPORTS/` folder:

- **Initial Report V1** → first initial submission to my supervisor
- **Initial Report V2** → revised version after supervisor feedback and incorporation of comments
- **Progress Report V1** → first progress submission
- **Progress Report V2** → revised version after supervisor feedback and incorporation of comments
- **Final Report** → complete final project report 

---

## Dataset

* `CJ_EEG.csv` → raw dataset: 6600 rows x 36 columns.
* `CJ_EEG_clean.csv` → cleaned dataset after RT outlier removal using mean + 4 SD per participant.

### Key columns

| Column                       | Description                                                                                                                                                             |
| ---------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `subj`                       | Subject ID. The dataset includes 25 participants, although subject labels range from `s01` to `s27` because some subject numbers were not included in the final sample. |
| `nrep`                       | Presentation number: 0 = first, 1 = second, 2 = third.                                                                                                                  |
| `cond`                       | True stimulus condition: 0 = cardinal, 1 = diagonal.                                                                                                                    |
| `deci`                       | Participant decision: 0 = cardinal, 1 = diagonal.                                                                                                                       |
| `rDV`                        | Raw decision variable representing sensory evidence strength.                                                                                                           |
| `d1-d6`                      | Evidence samples per presentation.                                                                                                                                      |
| `confi`                      | Confidence rating.                                                                                                                                                      |
| `RT`                         | Reaction time in seconds.                                                                                                                                               |
| `metad`                      | Meta-d prime, reflecting metacognitive sensitivity per subject.                                                                                                         |
| `deci-1`, `deci-2`, `deci-3` | Previous decisions used to represent decision history.                                                                                                                  |
| `corr-1`                     | Correctness of the previous decision.                                                                                                                                   |

---

## Repository structure

```text
Computational Neuroscience Martina Napoli/
|
|-- REPORTS/
|   |-- Initial_Report_V1.pdf
|   |-- Initial_Report_V2.pdf
|   |-- Progress_Report_V1.pdf
|   |-- Progress_Report_V2.pdf
|   |-- Final_Report.pdf
|
|-- DATA/
|   |-- CJ_EEG.csv
|   |-- CJ_EEG_clean.csv
|   |-- preprocessament/EEG/
|   |   |-- s01/ - s27/                  
|   |   |   |-- sXX_preproc.ipynb        
|   |   |   |-- sXX_bids.ipynb          
|   |   |   |-- sXX_eye.ipynb            
|   |   |   |-- main_epo.fif             # Main task epochs
|   |   |   |-- mainstim_epo.fif         # Stimulus-locked epochs
|   |   |   |-- mainresp_epo.fif         # Response-locked epochs
|   |   |   |-- loc_epo.fif              # Localiser epochs
|   |   |   |-- locstim_epo.fif          # Localiser stimulus-locked epochs
|   |-- decoding_results_*.pkl
|
|-- BEHAVIOURAL ANALYSES/
|   |-- behaviour_analyses_TFG_MARTINA.ipynb
|   |-- behaviour results/
|   |   |-- summary_behavioural.csv
|   |   |-- plot_data_panelA.csv
|   |   |-- plot_data_panelB.csv
|   |   |-- plot_data_panelC.csv
|
|-- EEG ANALYSES/
|   |-- EEG_initial.ipynb
|   |-- EEG_analysis_TFG_MARTINA.ipynb
|   |-- EEG_key_analyses_TFG_MARTINA.ipynb
|   |-- EEG_decoding_decision_TFG_MARTINA.ipynb
|   |-- EEG_decoding_DL_TFG_MARTINA.ipynb
|   |-- eeg results/
|   |   |-- eeg_auc_main_per_subject.csv
|   |   |-- eeg_auc_per_subject.csv
|   |   |-- eeg_decoding_temporal.csv
|
|-- ML ANALYSES/
|   |-- ML_analyses_TFG_MARTINA.ipynb
|   |-- fig_model_comparison.png
|   |-- fig_ablation.png
|   |-- fig_individual_differences.png
|   |-- fig_correlaciones_individuales.png
|   |-- fig_loso_barras.png
|   |-- fig_performance_by_nrep.png
|   |-- fig_permutation_importance.png
|   |-- ml results/
|   |   |-- model_performance.csv
|   |   |-- ml_model_results.csv
|   |   |-- ml_accuracy_per_subject.csv
|   |   |-- ml_accuracy_per_nrep.csv
|   |   |-- ml_permutation_importance.csv
|   |   |-- perm_importance_deci.csv
|   |   |-- perm_importance_switch.csv
|   |   |-- subject_accuracy_deci.csv
|   |   |-- subject_accuracy_switch.csv
|
|-- HSSM ANALYSES/
|   |-- HSSM_TFG_MARTINA.ipynb
```

**Note:** the subject EEG folders (`DATA/preprocessament/EEG/s01/` to `s27/`) are not included in this GitHub repository because they could not be uploaded due to GitHub file size limitations.

---

## Requirements

The analyses were developed using **python 3.10 or higher**.

Packages :

```bash
mne
numpy
scipy
pandas
matplotlib
seaborn
scikit-learn
jupyterlab
```

Additional packages used for the HSSM analyses :

```bash
hssm==0.2.6
pymc
arviz
blackjax
```

**Note:** the HSSM analyses were run in **Google Colab**. GPU acceleration is recommended because Bayesian sampling with HSSM and PyMC can be computationally demanding.

---

## Installation

Install the main dependencies for the HSSM analyses with :

```bash
pip install mne numpy scipy pandas matplotlib seaborn scikit-learn jupyterlab
```

Install the additional HSSM dependencies with:

```bash
pip install hssm==0.2.6 pymc arviz blackjax
```


## Contact

**Author:** Martina Napoli Crespo  
**Email:** martinanapoli012@gmail.com  
**Supervisor:** Alexis Perez Bellido (Basic Psychology Department, UAB)  
**Academic Year:** 2025/26






