# Cancer Dataset Tester
***
## This project is a simple implementation of Scikit-learn using pyscript and html


![image](https://github.com/Sankie005/Cancer_Dataset_Tester/assets/89256230/7b1c8a1c-090c-4873-b877-0fd1612ca190)
***
## How to load your own dataset 
pass your own dataset into the `cancer` variable as shown below
~~~python
cancer=datasets.load_breast_cancer()
~~~

***
## Explanation on how it works
* A simple random number generator is used to calculate a random state for splitting the data into test and train segments
  ```python
  from sklearn import datasets 
  from sklearn.model_selection import train_test_split
  cancer=datasets.load_breast_cancer()
  print("Labels:", cancer.target_names)
  import random 
  randomness=random.randrange(0,120)
  print(f"Random state: {randomness}")
  X_train, X_test, y_train, true_test = train_test_split(cancer.data, cancer.target,test_size=0.3,random_state=randomness)
  ```
* A model is trained using scikit-learn's SVM and a prediction is ran
  ```python
  from sklearn import svm 
  classifier= svm.SVC(kernel='linear')
  classifier.fit(X_train,y_train)
  predictor=classifier.predict(X_test)
  print(predictor)
  ```
* The model's accuracy is tested with Scikit learn's accuracy check function
   ```python
       from sklearn import metrics
        accuracy=metrics.accuracy_score(true_test, predictor)
        rounded_accuracy=round(accuracy,2)
        print(f"Accuracy:{rounded_accuracy}%")
        if accuracy>highest_accuracy[0]:
            highest_accuracy=[accuracy,randomness]
     print(f"The Highest accuracy achieved was {round(highest_accuracy[0],2)}% using random state={highest_accuracy[1]}")
   ```
* The best result is stored and displayed
  ```python
  if accuracy>highest_accuracy[0]:
                    highest_accuracy=[accuracy,randomness]
            print(f"The Highest accuracy achieved was {round(highest_accuracy[0],2)}% using random state={highest_accuracy[1]}")
  ```
  ***
Feel free to reach out to me if you have futher questions! 
-Sankie
