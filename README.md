# OSS_FinalTerm
이번 Final Project에서는 Face recognition 에서 가장 높은 정확도를 가지는 machine learning model 을 만들어 보았다.

주어진 training dataset 은 1992년 4월과 1994년 4월 사이에 AT&T 연구소의 캠브리지에서 찍은 얼굴 이미지 세트로,
이를 machine learning algorithm을 통해 학습하여 test data가 주어졌을 때 가장 정확하게 분류할 수 있도록 하는 것이 목표이다.

나는 우선 Scikit Learn package 중에서 모든 hyper parameter 가 default 일 때, 가장 높은 정확도를 가지는 algoritym을 찾기 위해
SVM 의 LinearSVC, KNeighborsClassifier, GaussianNB, Logistic Regression, Perceptron, 총 5가지 algorithm 의 정확도를 비교해보았다.

LinearSVC 의 경우, 0.97 GaussianNB 의 경우, 0.74

KNeighborsClassifier 의 경우, 0.69

Logistic Regression 의 경우, 0.94 

Perceptron의 경우, 0.72

위와 같은 정확도가 나타났다.

위 결과를 바탕으로, hyper parameter 가 default 값일 때 가장 높은 정확도를 보였던 LinearSVC algorithm 을 선택하여
hyper parameter 들을 차례로 조정해가며 산출된 정확도를 비교하였다.

default 에서 LinearSVC 를 실행하였을 때, 아래와 같은 error 가 발생하였다.

ConvergenceWarning: Liblinear failed to converge, increase the number of iterations. "the number of iterations."

이를 해결하기 위해 max_iter 값을 조정하였고, max_iter 값이 약 7500 이상일 때 해당 error 가 발생하지 않음을 확인하였다.

hyper parameter 를 조정하는 과정에서 다음과 같은 결과를 얻을 수 있었다.

  C: default 값에서 정확도 0.97 
     C=0.01 에서 0.94 이고 이보다 낮은 값은 더 낮은 정확도를 가짐 
     default 보다 높은 값에서는 정확도에 변화가 나타나지 않음
  
  tol: default 값에서 정확도 0.97
       [0.1,0.2] 에서 0.98
       이보다 높은 값에서는 정확도가 크게 낮아짐
  
  이외의 개별 parameter 조정을 통한 유의미한 변화는 확인할 수 없었음
  
  여러 parameter 들을 함께 조정하는 과정에서 
  tol=0.2 , fit_intercept = False , random_state = 0 , max_iter = 7500 일 때 0.99 의 정확도를 확인할 수 있었다.
  
최종적으로 구한 가장 높은 정확도는 위 경우에서 0.99 이었다. 
(소수점 3번째 자리까지 나타내면 0.992 의 정확도를 가진다는 것을 확인할 수 있다)

![accuracy99](https://user-images.githubusercontent.com/92919490/146687123-70f0125f-ba6b-41e1-ae47-88ca4829e145.png)

