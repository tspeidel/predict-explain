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


<br>

# References

•	Efron, B. (2020). Prediction, estimation, and attribution. JASA, 115(530), 636–655.
Shows how prediction and attribution can diverge. The prostate cancer example illustrates that accurate prediction can arise from combinations of weak predictors, making attribution (e.g. feature importance) unreliable.

•	Berk, R. A. (2016). Statistical learning from a regression perspective. Springer.
Provides a clear continuum between data modeling and algorithmic modeling cultures. His guidance (use data modeling when explanation is the goal, and algorithmic modeling when prediction is) informs the predict/explain distinction.

•	Shmueli, G. (2010). To explain or to predict? Statistical Science, 25(3), 289–310.
Formalizes the explanation vs. prediction distinction and shows how goals drive different methodological choices. Core reference.

•	Breiman, L. (2001). Statistical modeling: The two cultures. Statistical Science, 16(3), 199–231.
Frames the historical roots of the predict/explain divide. Useful context because Breiman argued the statistical community was too narrow. Ironically, the opposite is happening now. 

•	Cynthia Rudin (2019). Stop explaining black box machine learning models for high stakes decisions and use interpretable models instead. Nature Machine Intelligence, 1(5), 206–215. Argues that post-hoc explainability methods (SHAP, LIME, saliency maps) are not reliable and can be misleading, and that we should build inherently interpretable models instead. She also makes the empirical claim that for high-stakes decisions, interpretable models do not sacrifice accuracy over black.

•	Solari/University of Milano-Bicocca. (n.d.). Prediction, Estimation, and Attribution [PDF]. https://aldosolari.github.io/SL/docs/SLIDES/EfronPEA.pdf

•	Achen, C. H. (2000, July 13). Why lagged dependent variables can suppress the explanatory power of other independent variables. The University of Michigan, Ann Arbor. https://websites.umich.edu/~franzese/Achen.2000.LDVstealingExplanPower.pdf
Explains why lagged variables help prediction but undermine explanation: they boost fit by absorbing autocorrelation yet have no clear causal meaning, and their inclusion often collapses or reverses the substantive coefficients. It’s a clear example of how a variable can improve prediction while distorting inference, reinforcing the need to be explicit about whether the modelling goal is explanatory or predictive.
