# OSS_FinalTerm
이번 Final Project에서는 Face recognition 에서 가장 높은 정확도를 가지는 machine learning model 을 만들어 보았다.

주어진 training dataset 은 1992년 4월과 1994년 4월 사이에 AT&T 연구소의 캠브리지에서 찍은 얼굴 이미지 세트로,
이를 machine learning algorithm을 통해 학습하여 test data가 주어졌을 때 가장 정확하게 분류할 수 있도록 하는 것이 목표이다.

나는 우선 Scikit Learn package 중에서 모든 hyper parameter 가 default 일 때, 가장 높은 정확도를 가지는 algoritym을 찾기 위해
SVM 의 LinearSVC, KNeighborsClassifier, GaussianNB, Logistic Regression 총 4가지 algorithm 을 비교해보았다.

LinearSVC 의 경우, 0.97

GaussianNB 의 경우, 0.74

KNeighborsClassifier 의 경우, 0.69

Logistic Regression 의 경우, 0.94 의 정확도가 나타났다.

위 결과를 바탕으로, hyper parameter 가 default 값일 때 가장 높은 정확도를 보였던 LinearSVC algorithm 을 선택하여
hyper parameter 들을 차례로 조정해가며 산출된 정확도를 비교하였다.

default 에서 LinearSVC 를 실행하였을 때, 아래와 같은 error 가 발생하였다.

ConvergenceWarning: Liblinear failed to converge, increase the number of iterations. "the number of iterations."

이를 해결하기 위해 max_iter 값을 조정하였고, max_iter 값이 약 7500 이상일 때 해당 error 가 발생하지 않음을 확인하였다.

이후, hyper parameter C 의 값을 조정해보았다. C=1(default) : 정확도 0.97 이 나타났고, 이를 기준으로 이보다 높은 C 값에는 정확도의 차이가
나타나지 않았고, 낮은 값에는 기준값의 경우보다 더 낮은 정확도가 나타났다. C=0.01 : 0.94 (더 낮은 값에는 더 낮은 정확도가 나타남)

다음으로는 hyper parameter tol 을 조정해보았다. tol=0.0001(default) : 정확도 0.97 을 기준으로 조금씩 값을 증가시키다
tol=0.1 : 0.98 를 확인하였다. 이와 같은 정확도는 0.1 과 0.2 사이의 tol 값에서 나타났고 이후 tol 값이 증가함에 따라 정확도는 크게 낮아졌다.

이후, 다른 hyper parameter 를 조정하고 서로 다르게 조합해본 결과, 
최종적으로 tol=0.2 , fit_intercept = False , random_state = 0 , max_iter = 7500 일 때 0.99 의 정확도가 나타났다.

![accuracy99](https://user-images.githubusercontent.com/92919490/146687123-70f0125f-ba6b-41e1-ae47-88ca4829e145.png)

