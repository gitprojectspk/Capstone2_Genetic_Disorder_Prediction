![This is an image](https://github.com/gitprojectspk/Capstone2_Genetic_Disorder_Prediction/blob/main/images/Genetics_main.jpg)
# Genetic Disorder Prediction
Genetic disorders are leading, causes and treatment of most of which is still unknown. Researchers and medical professionals are continuously doing research to find out the causes and treatment methods for such diseases. These diseases are caused by the mutations in the DNA of a human which is irreversible by traditional medical procedures and medicines. Which is also the reason such diseases are difficult to cure and patients having such diseases end up with their lives. We can prevent or decrease the trend of such diseases by decreasing with in family marriages trend, genetic testing before marriages and precautionary measures which can help in reduction of increasing trend of genetic diseases.  

Studies suggest that chromosomal abnormalities occur in about 1 of 200 live births.

### What is Human genetic disorders or genetic diseases?
A genetic disorder or a genetic disease is a condition which is caused by the error in someone’s DNA. And these errors in a DNA can be of different type, either single base mutation, single gene or multiple gene or it can involve the addition or subtraction of entire chromosome causing the genetic disease. Genetic disorders can be caused by single or multiple errors in an individual’s genome. Which are categorized as Single gene disorders, Chromosomal disorders or complex disorders.

Genetic disorders occur when a mutation affects your genes. There are many types of Genetic disorders. 

##### Single-gene inheritance diseases:
Single gene inheritance diseases are diseases that occur because one defective gene is present. They are known as monogenetic disorders. Currently there are about 4000 genetic disorders according to the scientists which are caused by the mutation in one gene. And some of these genetic diseases can be transferred from parents to the offspring. e.g. 
  - Cystic fibrosis
  - Sickle-cell anemia
  - Polycystic kidney disease types 1 and 2
  - Tay-Sachs disease etc.
  
##### Multifactorial genetic inheritance disorders:
Multifactorial conditions tend to run in families. This is because they are partly caused by genes. Your risk for a multifactorial trait or condition depends on how close you are to a family member with the trait or condition.
  - Cancers of the breast, ovaries, bowel, prostate, and skin
  - High blood pressure and high cholesterol
  - Diabetes
  - Alzheimer disease
  - Schizophrenia
  - Bipolar disorder
  - Arthritis
  - Osteoporosis


##### Mitochondrial genetic inheritance disorders:
Mitochondrial genetic inheritance disorders are caused by mutations in the DNA of mitochondria, small particles within cells. This DNA is unique in that it is not located on the chromosomes in the cell nucleus. Mitochondrial DNA is always inherited from the female parent since egg cells (unlike sperm cells) keep their mitochondrial DNA during the process of fertilization. e.g
  - Hereditary optic atrophy
  - Barth syndrome
  - Co-enzyme Q10 deficiency
  - Myoclonic epilepsy with ragged red fibers (MERRF)
  - MELAS syndrome, a rare form of dementia
  - Kearns-Sayre syndrome
  - Pearson syndrome
  - Neuropathy, ataxia, retinitis pigmentosa (NARP)

##### Chromosome abnormalities:
Chromosome abnormalities usually result from a problem with cell division and arise because of duplications or absences of entire chromosomes or pieces of chromosomes. 
  - Down syndrome
  - Cri-du-chat syndrome
  - Klinefelter syndrome
  - Patau syndrome (trisomy 13)
  - Edwards syndrome (trisomy 18)
  - Turner syndrome

### Machine learning in Genetics :
Machine learning methods have been applied to a huge variety of problems in genomics and genetics. 
A machine learning algorithm is provided with a dataset with possible genetic disorders.  
The algorithm processes this labeled data and stores a model
The model learns and predict labels for each record. If the learning was successful, then all or most of the predicted labels will be correct
![This is an image](https://github.com/gitprojectspk/Capstone2_Genetic_Disorder_Prediction/blob/main/images/machine_learning_genetics.jpg)


## 1. Data  
  We will analyze the dataset provided on Kaggle to predict the genetic disorder.
  This dataset contains medical information about children who have genetic disorders.
  Source : https://www.hackerearth.com/challenges/competitive/hackerearth-machine-learning-challenge-genetic-testing/
  
  ![image](https://user-images.githubusercontent.com/96436449/167469019-1f1977ab-073e-4f53-a508-5fd82b565765.png)
  
## 1. Data Cleaning
  Original Dataset contains 22K records and 45 variables.
  There are few variables which are not very useful for our prediction. I dropped them.
  There are variables representing Nan or incorrect values. e.g. values like 'Not applicable', 'None', '-', 'No Record' which I replaced with Nan. 
  I renamed Columns for simplicity
  Filled the missing values with 'missing' for categorical variables
  Filled missing values with mean value for numeric variables
  The Target variables Genetic Disorder, Disorder Subclass, have many rows with null values. Dropped these as they are of not any use.
  After implementing above steps, Dataset rows reduced to 18047
 
## 2. Exploratory Data Analysis  

##### Percentage Distribution of Genetic Disorder amonst the given set of childeren's data.

![image](https://user-images.githubusercontent.com/96436449/167471279-022f71c3-02d0-4a17-a94d-e9a632e5058f.png)

##### Pair plot shows relationship between variables
![image](https://user-images.githubusercontent.com/96436449/167471296-e27369b0-e0f0-4982-a623-648d0b499224.png)

##### Genetic Disorder count vs Mother’s Side distribution
![image](https://user-images.githubusercontent.com/96436449/167471497-b19ef9fe-d41b-41f3-be8b-cd29d4dc1292.png)

##### Genetic Disorder vs Blood cell count distribution
![image](https://user-images.githubusercontent.com/96436449/167471530-41539b98-4976-498e-9a0e-dee3e94a0210.png)


## 3. Data Preprocessing 

Before feeding the data to model, we need to converted the categorical column into a numerical one using One-Hot-Encoding and label encoder
The dataset has been separated in a Train dataset (12632 samples) and a Test dataset (5415 samples). 
The data was scaled before feeding into the respective models such as SVM, Logistic regression etc.


## 4. Model Selection
For all the models under study, to avoid over-fitting, we optimized the corresponding hyper-parameters by a 5-fold cross-validation on the Train set. We then evaluated on the Test set the models trained on the entire Train set.
![image](https://user-images.githubusercontent.com/96436449/167471155-1fa538f9-d8e9-40db-962e-8bf492428a00.png)

as we can see, Random Forest shows better accuracy and F1 score


## 5. Imbalance Data Handling

There is lot of imbalance amongst the Genetic Disorder classes 
 Mitochondrial     9241
 Single gene       6929
 Multifactorial    1877
Oversampling is one of the most widely used techniques to deal with imbalance classes. Using SMOTE method, and class weight adjusted to balanced , f1 score improved to 42.65


## 6. Hyper Parameter Tunning

I applied GridsearchCV and RandomizedSearchCV to select the best hyperparameters. Using which the accuracy increased to 49.18 with F1 score : 41.69

## 7. Feature Importance
Feature Importance graph shows that almost all of the features are important.

![image](https://user-images.githubusercontent.com/96436449/167470698-2ca8c64e-5acf-4a35-987e-6e1549eea5e1.png)


## 8. Takeaways
- The dataset is too small. It also with lot of missing values. 
- After handling the missing values, we applied different models. Random Forest classifier showed better performance
    - Random Forest Classifier Accuracy : 48.72 
    - F1 Score : 40.89 
- As the dataset is imbalanced, using SMOTE Oversampling and handling the Class_weight, helped to improve the score. Using RandomizedSearchCV, the hyperparameters are selected, using which the accuracy increased to 49.18 with F1 score : 41.69
- Feature Importance graph shows that almost all of the features are important.


## 9. Future Research
- Expand the Data volume
- Get balanced and correct (less missing values) data 
- Include more parameters

## 10. Crdits
  Thank you Dipanjan Sarkar for guidance during project.
