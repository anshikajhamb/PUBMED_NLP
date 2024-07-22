Introduction
The sheer volume of published scholarly research online has warranted the need for quick location and retrieval of data. By
converting unstructured abstracts into pre-defined categories such as objective, background, method, and conclusion, our
research aims to streamline the process of skimming through abstracts to reduce time required for researchers to identify
relevant information


Methods
-We utilised the PubMed 20k dataset of
biomedical abstracts focusing on randomised
controlled trials (Dernoncour, 2017).
- Initially, we explored various supervised ML
approaches.
-Subsequently, we employed a hybrid approach:
training a CRF model on labelled training data to
capture sequential information, followed by
developing a CNN model to leverage
embeddings and convolution for enhanced
classification.

Ethics Statement
Since PubMed data is publicly accessible and does not contain sensitive or personal information, this research did not require
additional ethical approval.


Results
- RF and KNN models using GloVe, TF-IDF, and distilBERT embeddings
achieved <50% accuracy using cross-validation, indicating their inability to
capture data's sequential nature.
- The CRF model achieved 63% accuracy on the validation set.
- CRF+CNN model improved performance in ‘BACKGROUND’, ‘METHODS’,
and ‘OBJECTIVE’ classes, but ‘CONCLUSIONS’ and ‘RESULTS’ saw a decline
compared to CRF, resulting in an overall accuracy of 68%. The CNN model may
introduce noise, diluting the impact of custom tags like 'pval' on the 'RESULTS'
class. Confirming this hypothesis requires a t-test comparing models with and
without the p-value tag.


Discussion & Conclusion
- Used CRF predictions as CNN input for enhanced sequential pattern
recognition.
- Effective sequential classification capturing contextual dependencies.
- Utilisation of domain-specific terms like 'p-value' to create custom tags.
- Integration of multiple embeddings for increased model robustness.
- Computational constraints limited fine-tuning of embeddings, impacting model
accuracy across RF, KNN, and CRF.
- Averaged GloVe embeddings for sentence-level suitability; further aggregation
of BERT embeddings could enhance performance.
- Undersampling approach may lead to information loss; alternatives like
SMOTE or class weighting could be explored.
- Implementing domain-specific models like BioBERT (Lee, 2020) could
potentially improve performance.
- Consideration for hyperparameter tuning in CRF for optimised model performance.

References
Dernoncourt, F., & Lee, J.Y. (2017). PubMed 200k RCT: a Dataset for Sequential Sentence Classification in Medical Abstracts. International Joint Conference on
Natural Language Processing.
Lee, J., Yoon, W., Kim, S., Kim, D., Kim, S., So, C. H., & Kang, J. (2020). BioBERT: a pre-trained biomedical language representation model for biomedical text
mining. Bioinformatics (Oxford, England), 36(4), 1234–1240. https://doi.org/10.1093/bioinformatics/btz682
