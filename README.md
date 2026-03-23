# predict-explain
A comparison table outlining key differences between explanatory (inferential) models and predictive/ML models. Intended as a reference that can be updated over time.

| **Aspect** | **Explanatory / Inferential Model** | **Predictive / ML Model** |
|------------|--------------------------------------|-----------------------------|
| **Primary goal** | Understand relationships | Predict unseen outcomes |
| **Target / focus** | Parameters (sign, magnitude, uncertainty) | Predictions (accuracy on new data) |
| **Role of theory** | Theory/domain/substantive knowledge drives specification | Data drives specification |
| **Causal claims** | Supports causal inference (with appropriate design) | Generally agnostic to causal inference |
| **Variable / Feature selection** | Based on DAGs, prior and substantive knowledge | Based on predictive contribution |
| **Emphasis** | Bias control, interpretability, functional form | Variance control, accuracy |
| **Decision Making** | May identify causal levers; supports intervention design and accountability | Drives operational decisions (allocation, classification, forecasting); limited basis for causal intervention |
| **Coefficients** | Substantively interpreted; sign, magnitude, significance matter | Often incidental or unexamined |
| **Complexity** | Yes, if theoretically motivated | Yes, if it improves accuracy |
| **Transparency** | Model is the product; fully inspectable | Model may be a black box; interpretability added post‑hoc |
| **Risk at Scale** | Bias is visible in coefficients and subject to scrutiny; deployment is typically limited in scope | Bias can be hidden, systematically applied at scale, and amplified through feedback loops |
| **Overfitting concern** | Mitigated by parsimony, pre‑specification, sample size and power calculations, optimism bootstrap | Mitigated by regularization and holdout validation. Leakage may still occur in subtle and non‑obvious ways, leading to overfitting |
| **Collinearity** | Serious problem (inflates SEs, distorts estimates), leads to difficulties in interpretation | Often tolerable if predictions remain stable |
| **Evaluation** | SEs, CIs, ICCs, hypothesis tests; AIC/BIC; c‑index for model selection | Cross‑validation error, RMSE, AUC, F1 |
| **Residual diagnostics** | Central to model checking | Rarely examined beyond aggregate loss |
| **Missing data treatment** | Model‑based (e.g. multiple imputation) with missingness mechanism assumptions | Pragmatic (imputation, surrogate splits, dropping) |
| **Generalizability basis** | External validity via theory and design | External validity via representative test sets |
| **Interaction with domain knowledge** | Required throughout | Optional; can be purely algorithmic |
| **Size of data** | Thrives in small‑to‑moderate data via distributional assumptions and efficient estimation (MLE, REML) | Thrives in large data (data‑hungry) |
| **Typical disciplines** | Statistics, econometrics, epidemiology, social science, medicine | ML, MLOps, AI, business applications |
| **Example methods** | GLM, Cox proportional hazards, multilevel/Bayesian models | Random forests, gradient boosting, neural nets |
| **Software ecosystem** | R, SAS, Stata, Mplus, markdown/Quarto, Shiny | Python (scikit‑learn, PyTorch, TensorFlow), Spark, Git, Docker |
| **Effort** | Heavy upfront (theory, specification, diagnostics, interpretation) | Heavy downstream (tuning, validation, deployment in production) |
| **Typical practitioner** | Scientist, statistician, methodologist, econometrician, social scientist | Computer scientist, software developer, ML/data engineer |
