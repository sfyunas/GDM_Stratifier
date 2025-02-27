# Gestational Diabetes Risk Stratification

## Introduction

Gestational Diabetes Mellitus (GDM) is a diabetic condition, in which a harmone produced by placenta prevents the body from using insulin effectively. Resultantly, the glucose starts accumulating in the blood stream instead of being absorbed by the cells. Gestational diabetes affects 1 in 8 pregnancies worldwide, and this risk stratification is clinically useful because it sensitively identifies women who would benefit from closer monitoring during pregnancy [1].

Gestational diabetes is for the first time diagnosed during pregnancy (gestation). If left untreated, it can affect the pregnancy and cause problems in baby's health, such as macrosomia (fat baby), premature birth or even still birth.

Gestational diabetes usually goes away after the baby is born, however, in some cases it may continue even after delivery as type II diabetes.

Proper management/treatment of gestational diabetes can significantly reduce risk factors associated with it. Hence, early diagnosis of the GDM can helpful in this regards. 

This GDM predictor is a web-based application that can help in prediction of gestational diabetes. It asks for several key information that corresponds to the risk factors associated with GDM. The input are passed to a machine learning model, which outputs either 'GDM predicted' or 'No GDM'. It uses Random Forest classifier for prediction. The application is dockerized.

Reference:
[1] Zhang C, Catalano P. Screening for Gestational Diabetes. JAMA. 2021;326(6):487–489. doi:10.1001/jama.2021.12190


## Use case

The web-based application when deployed on cloud can prove to be very helpful especially in the developing countries where majority of the population lives in rural areas and do not have access to proper hospitals. For instance, the web-based application can be used by public health workers in order to timely predict GDM in high risk pregnant females and hence refer them for proper medical care.


## Data

The dataset used for training the model is available on Kaggle and can be accessed here: https://www.kaggle.com/datasets/sumathisanthosh/gestational-diabetes-mellitus-gdm-data-set/code. The dataset is stored in a postgres relational database.

## Services

The project repository has four components:

- A container running Jupyter notebooks with common machine learning libraries (available @ localhost:8888).  The notebook persists in a mounted volume (./volumes/notebooks)
- A container running Postgres in the event a relational database is useful (available @ localhost:5432).  Any transformations will persist between containers in a mounted volume (./volumes/postgres)
- A container running FastAPI to serve predictions from the ML model (available @ localhost:8080)
- A container running Streamlit to access the predictions from the ML model based on user inputs (available at localhost:8501)

## Usage

turn on the application 
```
docker-compose up 
```

turn off the application
```
docker-compose down
```

rebuild the application
```
docker-compose down
```


## Structure

```
|-- containers - code
|   |-- python      # interactive jupyter notebooks
|   |-- fastapi     # deploy pickled model as a REST API 
|   |-- streamlit   # access REST API in a user interface 
|-- volumes         # persistent data
|   |-- notebooks   # jupyter notebooks persisted here
|   |-- postgres    # database files persisted here, not in version control
|   |-- static      # static files that are loaded into postgres or jupyter
```


## Streamlit User Interface

![](./resources/streamlit.png)
