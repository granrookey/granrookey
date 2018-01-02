---
layout: post
title: 파이썬 데이터 사이언스 핸드북
excerpt: "These are open dataset links from <First learning Machine Learning>"
categories: [Basic ML]
comments: true
image:
  feature: http://image.kyobobook.co.kr/images/book/large/730/l9791158390730.jpg
  credit: Kyobo Books
  creditlink: http://www.kyobobook.co.kr/index.laf
---


### Feature Engineering 이란?

* 문제에 대해 가지고 있느 정보를 모두 취해 특지 행렬을 구축하느 데 사용할 수 있는 숫자로 변환하는 것

  범주 데이터(Categorical data), 텍스트, 이미지에 대해서 살펴봄
  
* 모델의 복잡도를 증가시키느 방법
  
  유도 특징(Derived Feature)과 누락 데이터 대체에 대해서 논의
  
  핵심적으로 임의의 데이터르 벡터로 전환하기 때문에 Vectorization (벡터화)한다고 하는 경우가 많음


1. 범주 특징

비수치 데이터의 일반적인 유형 중 하나느 범주 데이터. 

ex) 주택 가격 데이터를 탐색하는데 사용되는 가격과 방의 개수

지역의 정보르 수치 데이터로 표현 하는 것은 간단하지만, 불가능... 

> { 'Queen Anne: 1, 'Fremont': 2, 'Wallingford':3 } 이 표현방식은 일반적이지 않으며,

> scikit-Learn의 DictVectorizer를 사용해 이 작업을 수행 가능 - ** One-Hot Encoding **

* 이 방식의 단점

범주에 들어갈 수 있는 값이 많은 경우 데이터 세트으 크기가 엄청나게 커질 수 있으며, 대부분의 값이 0이기 때문에 Sparse Matrix를 사용해야 한다.

1. 텍스트 특징

텍스트를 대표 수치값의 집합으로 변환하는 과정

가장 대표적인 방법 중의 하나는 Word Count를 이용하는 방법

ex) sample = [ 'Problem of evil', 'evil queen', 'horizon problem' ] 에서 'problem, evil, horizon' 등으 단어를 나타내야 함

> scikit-Learn의 CountVectorizer를 사용하여 해결 할 수 있음

* 이 방식의 단점

원시 단어 개수가 매우 자주 등장하는 단어에 너무 많은 가중치를 부여하는 특징을 가지게 함

이 방식을 개선하는 한 가지 방법은 단어가 문서에서 얼마나 자주 등장하느냐에 따라 단어 수에 가중치를 부여하는 TF-IDF 방식

> scikit-Learn의 TfidfVectorizer를 사용하여 해결 할 수 있음

1. 이미지 특징

이미지를 적절하게 인코딩 하는 것으로 가장 간단한 방식은 간단히 픽셀값 자체를 사용하는 것이나 응용 프로그램에 따라 그러한 방식은 최적이 아니 수 있음

>  [scikit-Learn Image](http://scikit-image.org) 에서 여러 표준 접근 방식을 이용한 탁월한 구현물을 찾을 수 있음

가장 대표적인 방법 중의 하나는 Word Count를 이용하는 방법

ex) sample = [ 'Problem of evil', 'evil queen', 'horizon problem' ] 에서 'problem, evil, horizon' 등으 단어를 나타내야 함

> scikit-Learn의 CountVectorizer를 사용하여 해결 할 수 있음

1. 유도 특징

입력 특징으로 부터 수학적으로 유도된 특징

ex) 모델을 바꾸지 않고, 입력 값을 변환해서 선형회귀를 다항회귀로 바꾸는 것과 같은 방식

1. 누락 데이터의 대체

Nan과 같이 누락된 데이터를 처리하는 것. 이르 imputation이라고 하며, 

간단히는 누락된 값을 해당열의 평균으로 대체 하느 방식이 있으며,

> 간단한 누락 대체 방법은 scikit-Learn의 Imputer 클래스를 통해 평균, 중앙값, 최빈값을 사용하느 방식이 있음

정교한 방법으로는 행렬 완성이나 그러하 데이터르 처리하는 견고한 모델을 사용하는 방법 등이 있음
                    

### Feature Pipeline

* 앞선 여러 단계르 하나로 묵고자 한다면 파이프라인을 통한 접근이 필요

> scikit-Learn의 pipeline 객체르 통해서 간결하게 사용이 가능
  
  ex) 누락된 값을 평균으로 대체, 특징을 이차 형태로 전환, 선형 회귀르 적합
      
{% highlight python %}
   from sklearn.pipeline import make_pipeline
   model = make_pipeline(Imputer(strategy='mean'), PolynomialFeatures(degree=2), LinearRegression())
{% endhighlight %}
