# Breast-Cancer-Prediction
## Objective: to predict whether a breast tumor is benign or malignant (Classification Problem)

### What this file will include (after its done)?
- implementation of PCA (Principal Component Analysis)
- four classfication models (Logistic Regression, SVM, Decision Trees, Naive Bayes) trained 4 times for slightly different datasets, 3 times without PCA and one time with PCA
- Final Evaluation (conclusion) Across Models and Data Variations

## Using PCA in Training and Prediction

When PCA is applied for dimensionality reduction (as in this breast cancer detection project), the trained model learns to work with **principal components**, not the original features.

### Key Points:
1. **Fit PCA only on the training data** to avoid data leakage.
2. **Transform both training and test data** using the same PCA transformation.
3. **Save the PCA object** along with your trained model, so any new data can be transformed before making predictions.

This ensures that during deployment, new patient data is projected into the same reduced-dimensional space that the model was trained on.

---

### PCA + Model Workflow

```mermaid
flowchart TD
    A[Original Dataset] --> B[Split into Train/Test]
    B --> C[Transform Train Set -><br/>Principle Components]
    C --> D[Train Model]
    B --> E[Transform Test Set -> <br/>Principle Components] 
    E --> F[Evaluate Model]
    H[New Unseen Data] --> I[Apply Saved PCA<br/>Transformation]
    I --> J[Use Trained Model<br/>for Prediction]

