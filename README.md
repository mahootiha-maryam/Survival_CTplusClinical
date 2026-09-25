# Survival_CTplusClinical
Multimodal Deep Learning for Personalized Renal Cell Carcinoma Prognosis: Integrating CT Imaging and Clinical Data<br>

## Corrected importance-score experiment inputs

The Experiment 8 and Experiment 9 scripts now keep the survival event indicator
only in the LogisticHazard target; it is not supplied as a clinical predictor.
Their assembled inputs contain the intended 17 and 29 clinical variables,
respectively, without duplicated variables. The random-forest feature-selection
script also excludes survival duration, event status, and exported CSV index
columns from its predictor matrix.

These input corrections change the survival-network dimensions. Legacy
Experiment 8 and Experiment 9 model weights and generated input CSV files are
not compatible with the corrected pipelines. Regenerate the CSV files, retrain
both models, and save the new weights as `merged_IF0.01_corrected.pt` and
`merged_IF0.001_corrected.pt` before evaluating or plotting corrected results.

Renal cell carcinoma represents perilous cancer worldwide, characterized by a low survival rate. In this study, we develop a multimodal deep-learning approach for estimating survival probabilities in renal cell carcinoma patients, leveraging CT imaging and clinical data. We attempt to facilitate the identification of patients requiring urgent treatment by estimating survival probabilities. Our framework comprises three modules: a 3D image feature extractor, clinical variable selection, and survival prediction. Based on the Efficient-Net B7 3D architecture, the feature extractor module extracts the features of CT images by predicting the ISUP grade (defined by the International Society of Urological Pathology) of renal cell carcinoma tumors, which is linked to mortality rates. In order to boost the feature extractor's performance, we utilize a number of preprocessing techniques. In the clinical variable selection module, the selection of the most relevant clinical variables to prognosis for integration with CT images is conducted systematically, utilizing the Spearman score and random forest importance score as the criteria. The survival prediction module is a DL-based network trained with discrete LogisticHazard-based loss. A total of nine distinct experiments are performed, employing varying numbers of clinical variables determined by diverse thresholds of the Spearman and importance scores. Our findings show that the suggested strategy outperforms the state-of-the-art literature in the prognosis of renal cancer based on CT scans and clinical factors. The best experiment yielded a concordance index of 0.84 and an area under the curve value of 0.8 on the test subset.
