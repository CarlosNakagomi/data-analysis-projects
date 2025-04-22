Problem Being Addressed:
Queensland University is increasingly vulnerable to sophisticated cyber threats such as DoS, phishing, and malware attacks. Traditional rule-based IDS solutions are ineffective in identifying evolving attack patterns, resulting in data breaches and operational disruptions.




Goal of the Project:
To develop an AI-powered Intrusion Detection System (AI-IDS) using Random Forest (RF) that can detect and classify malicious network traffic in real time, reduce false positives, and adapt to changing threat landscapes.




Data Used:
Source: CICIDS2017 dataset
Rows: ~2.4 million
Features: 122 (e.g., ports, IPs, payload size, TCP flags, IAT times)
Target: label (e.g., Botnet, Benign, DoS, etc.)




Features Selected:
From various feature selection techniques:
Top Categorical: flow_id, src_ip, dst_ip, timestamp, protocol
Top Numerical: src_port, dst_port, duration, packets_count, fwd_packets_count, rst_flag_counts, total_payload_bytes, mean_header_bytes, IAT features




Techniques used: PCA, Chi-Square, ANOVA, Mutual Information, Relief, Random Forest Feature Importance
Model Used: Random Forest Classifier
Imbalance Handling: SMOTE + class weighting
Tuning: GridSearchCV for n_estimators, max_depth, etc.
Threshold adjustment: 0.45 for optimal precision-recall tradeoff
Performance Evaluation: Accuracy, Precision, Recall, F1, AUC-ROC




Model Evaluation:
Baseline Accuracy: 0.9982
Proposed Model: Accuracy: 0.7300
Precision: 0.9661
Recall: 0.7300
F1-Score: 0.8244
AUC-ROC: 0.9294



Insights from SHAP Analysis:
Most impactful features: src_port, duration, total_payload_bytes, packets_count, fwd_packets_count, protocol
These features were crucial in differentiating between benign and malicious activity.
