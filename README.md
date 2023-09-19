# Car_Insurance_Fraud_Prediction

// Improved the csv file to take account for imbalanced classification using SMOTE.
// uploaded the file to mindsdb online and created a predictive model to run on the dataset.

// creating predicitive model on mindsdb.

CREATE MODEL mindsdb.insurance_claims_fraud_predictor
FROM files
    (SELECT * from fraud_dataset)
PREDICT fraud_reported;

*********************************************************
// making batch predictions to visualize the accuracy.

SELECT t.policy_number,t.fraud_reported AS EXPECTED_TARGET, m.fraud_reported AS PREDICTED_FRAUD_REPORTED, m.fraud_reported_explain
FROM files.fraud_dataset AS t
JOIN mindsdb.insurance_fraudulent_claims_predictor AS m
LIMIT 10;
