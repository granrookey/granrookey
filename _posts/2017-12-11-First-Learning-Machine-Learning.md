---
layout: post
title: 처음 배우는 머신러닝 Keywords
excerpt: "These are open dataset links from <First learning Machine Learning>"
categories: [Basic ML]
comments: true
image:
  feature: http://image.kyobobook.co.kr/images/book/large/045/l9791162240045.jpg
  credit: Kyobo Books
  creditlink: http://www.kyobobook.co.kr/index.laf
---


### 군집화 Clustering

* 중심 기반 군집화 prototype-based clustering : 클러스터를 클러스터 중심점으로 정의하는 기법

  K-중심 군집화 K-centroid clustering, K-medoid clustering
  
* 계층적 군집화 hierachical clustering : 클러스터의 크기에 따라 클러스터의 계층을 정의하고 계층의 상하위를 이용하는 기법

  단일 연결법 : 두 클러스터에 속하는 데이터들의 거리 중에 가장 짧은 거리를 클러스터 사이의 거리로 간주
  
  완전 연결법 : 두 클러스터에 속하는 데이터들의 거리 중에 가장 먼 거리를 클러스터 사이의 거리로 간주
  
  평균 연결법 : 두 클러스터에 속하는 데이터들의 거리 평균을 클러스터 사이의 거리로 간주
  
  
* 밀도 기반 군집화 density-based clustering : 클러스터를 데이터가 높은 밀도로 모여 있는 공간으로 보는 기법

  평균이동 군집화, DBSCAN density-based spatial clustering of application with noise
  
  중심 포인트 core point : 반경 $$ e $$ 안에 일정 개수 이상의 데이터가 존재하는 데이터
  
  경계 포인트 border point : 반경 $$ e $$ 안에 있는 데이터 수는 중심 포인트보다 적지만, 중심 포인트로부터 반경 $$ e $$ 안에 존재한는 데이터
  
  노이즈 포인트 noise point : 중심 포인트도 경계 포인트도 아닌 데이터
  
  
* 유사도 계산

  민코스키 거리 : 벡터 공간 안의 두 점 사이의 거리 $$ d(X, Y) \sqrt[p]{\sum_{i=1}^m |x_i - ㅛ_i|^p} $$
   
                 여기서 p가 1일 때는 맨해튼 거리 Manhanttan distance 2일 때는 유클리드 거리 Euclidean distance
                 
  마할라노비스 거리 : 점들의 분포를 고려한 거리 $$ d(x,y) = \sqrt{(x_i - y_i)^T S^{-1}(x_i-y_i)} $$
  
                    공분산 $$ Cov(X, Y) = E[(X - \mu_x)(Y - \mu_y)] $$
                    

### 문서 분류에 많이 사용하는 피쳐

* 단어 빈도 피쳐

  단어 빈도 Word Frequency, 단어 카운팅 Word Counting, 단어 출현 Word Occurrence(문서를 긍정 부정으로 평가 할 때 좋은 성능)
   
  $$ i번째 단어 빈도 피쳐 = i번째 단어가 문서에 나타난 횟수 \over 문서의 총 단어 수 $$

* TF-IDF Term-Frequency Inverse-Document Frequency

  단어 빈도 피쳐의 문제점인 하나하나의 중요도가 동일한 점을 개선하여 단어의 희귀도를 고려해서 피쳐를 생성
  
  $$ TF-IDF = 단어 빈도 * 역문서 빈도 $$
  
  역문서 빈도 $$ 가능한 모든 단어 중 i번째 IDF 피쳐 = \log 전체 문서 수 \over i번째 단어가 나타나는 문서 수
  
  단어의 로그값이 너무 작아서 IDF가 예외적으로 커지는 것을 막기 위해 변형된 식을 적용하기도 함
  
  $$ 스무딩된 IDF 피쳐 = \log \left(1 +\frac{전체 문서 수}{i번째 단어가 나타나는 문서 수} \right)
  
* SVM 문서 분류에 사용하는 표준적인 분류모델 __확률을 직접 계산하지 않고 데이터가 어떤__ ___경계선___ __을 넘는지 넘지 않는지 검사하여 분류__

  따라서 __확률값이 아닌 분류값을 출력__
  
  SVM은 데이터와 경계선 사이의 최소 간격을 최대화하는 경계선을 선택하게 만듭니다
  
  단점은 확률이 나오지는 않는다는 점
  
  장점은 경계선 근처의 데이터들만 고려하기 때문에 모델이 가볍고 노이즈에 강함
  
* 결정트리와 그레디언트 부스티드 트리도 많이 사용

#### 토픽 모델링

* LDA(잠재 디리클레 할당) : 확률모델을 통해 문서의 토픽과 토픽에 분포하는 단어들을 분석
  1. 문서에 단어가 몇 개 있는지 결정
  1. 문서마다 토픽이 어떻게 분포되어 있는지, 토픽마다 단어 분포가 어떤지 디리클레 분포 Dirichlet distribution에 따라 정의
  1. 문서의 제일 첫 단어부터 끝 단어까지 다음 과정을 거침
     a. 현재 위치의 단어가 어떤 토픽과 관계있는지 정함
     a. a에서 정한 현재 위치의 토픽에 따라 단어의 분포를 결정하고 그중에서 가장 높은 확률의 단어를 선택
     
#### 문법 분석
* 품사 태깅 POS (Part of Speech) Tagging

  현재 단어와 이전 단어에 따라 품사가 결정 따라서 순차 모델링 Sequential modeling
  
  순차 모델링의 대표기법은 CRF와 RNN, 특히 LSTM Long short-term Memory
  
* 고유명사 추출 NER (Named Entity Recognition)

  NER은 텍스트에서 인물, 조직, 장소, 일정 등을 찾아내는 문법 분석 방법
  
  책이나 웹 페이지에서 이름, 장소, 주소, 제품명을 인식하는데 사용 가능
  
  1. 품사 문제 POS Tagging과 같이 사전 정보를 사용하면 많은 도움 (유명한 사람의 이름이나 장소 같은 고유명사가 중요)
  1. 품사 문제와 마찬가지로 앞뒤 나열된 단어에 따라 영향을 받음
  
  + LSTM에 NER에 도움이 되는 장소사전이나 품사를 넣고, 출력값으로 NER 항목들을 주어서 학습하는 방식
    
    단점은 문장을 하나하나 돌려야하기 때문에 속도가 그렇게 빠르지 않음
    
  + 머신러닝 이외에도 정규표현식이나 신문기사, 포털사이트 등에서 인물이나 장소에 자동으로 태깅하는 방식도 있음
  
#### 단어 임베딩 학습
  
  컴퓨터로 단어의 의미를 나타내는 방법은 크게 이산 표현 discrete representation과 분산 표현 distributed representation이 있습니다
  
  이산 표현은 단어 그 자체를 이용하여 의미를 나타냄 : 고양이라는 단어가 있다면 사전을 이용해 단어를 정의 따라서 말뭉치에 든 모든 단어수를 벡터 크기로하는 원-핫 인코딩 벡터로 표현
  
  분산 표현은 한 단어의 주변 단어를 이용해서 의미를 표현 : 분산표현은 단어를 실수값으로 이루어진 벡터로 표현
  
* Word2Vec은 뉴럴넷을 이용하여 분산 표현을 학습하는 모델
  
  스킵 - 그램 Skip-gram 단어 하나를 받아서 그 주변에 같이 나타날 확률이 높은 단어들 Context를 구함 $$ P(context|x_t) $$
  
  COW Continuous bag of words 주변 단어들을 받아서 그 단어들과 같이 나타날 확률이 높은 단어를 구함 $$ P(x_t|context) $$
  
### 다양한 시각화
* scikit-learn.org/stable/auto_example

### 데이터 문제
* 머신러닝에는 데이터가 많을 수록 좋으나, 데이터가 많으면 처리시간이 오래 걸리고 중복되는 데이터가 많이 들어오는 경우도 고려해야함
* 과소표집 Undersampling 전체 데이터셋에서 데이터를 무작위 확률로 선택해서 선택된 작아진 데이터셋을 사용하는 방식
* 중요도표집 Importance sampling 은 데이터의 중요도에 따라 선택 확률을 변동하여 샘플링하는 기법
* 피처선택 Feature selection 중요한 피처만 선택해서 전체 학습률과 성능을 증가시키는 방법
  1. 카이제곱 피처 선택법 Chi-squared : 피쳐와 성능 간의 통계학적 독립성을 테스트하는 방법
  1. 상호-정보 피처 선택법 Mutual Information : 선택한 피처 한 쌍이 서로 예측하는 데 얼마나 도움이 되느냐를 검토, 
  
                                              결과적으로 카이제곱 선택법보다 좀 더 자주 나오는 피처를 선택
  1. 검증셋에서의 성능 : 학습용, 검증용 데이터를 따로 분리하여 피처의 일부만을 사용해서 모델을 학습한 후 검증셋에서의 성능 평가를통해 피처를 측정
  
* 데이터가 너무적을 때
  1. 표현형학습 : 일반적인 리뷰의 패턴을 먼저추출하여 간명한 표현을 만든다음 실제 레이블을 가진 리뷰를 표현형으로 변환한 뒤 이를 이용해 분류
  
                 표현형 학습 Representation Learning 혹은 비지도 선행학습 Unsupervised pretraining 등의 분야에서 다룸 대표방식은 Auto-Encoder, 토픽모델링
  1. 전이학습 Transfer learning : 성격이 다른 데이터셋을 이용해서 학습시킨 모델을 현재 데이터셋에 적용하는 방법
                                 
                                 딥러닝에서는 중간 레이어를 공유하는 방식으로 생각보다 쉽게 정보를 이용할 수 
