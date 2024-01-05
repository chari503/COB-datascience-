import pandas as pd
from sklearn.model_selection import train-train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error
from sklearn.impute import SimpleImputer
train_df=pd.read_csv('/content/train dataset - Sheet1.csv')
test_df=pd.read_csv('/content/test dataset - Sheet1 (1).csv')
print('train columns:',train_df.columns)
print('test columns:',test_df.columns)
target_columns="unnamed: 2"
common_feature=None
for feature_name in train_df.columns:
  if features_name!= target_column and feature_name in test_df.columns and not train_df[feature_name].isnull().all():
    common_feature=feature_name
    break
if common_feature is none:
  print(set(train_df.columns)& set(test_df.columns))
  raise ValueError('check your data')
  x_train=train_df[[common_features]]
  y_train=train_df[target_column]
  x_test=test_df[[common_feature]]
  y_test=test_df[target_column]

  if not pd.to_numeric(x_train[common_feature],errors='coerce').notnull().all():
    imputer =Simpleimputer(strategy='most_frequent')
  else:
    imputer=SimpleImputer(strategy='mean')
  x_train_imputed=imputer.fit_transform(x_train)
  x_test_imputed=imputer.transform(x_test)
  if pd.DataFrame(x_train_imputed).isnull().any().any() or pd.DataFrame(x_test_imputed).isnull().any().any():
    raise ValueError('after imputation, the selected feature column contains missing values')
  model=LinearRegtression()
  model.fit(x_train_imputed,y_train)
  y_pred=model.predict(x_test_imputed)
  print('predictions:',y_pred)
