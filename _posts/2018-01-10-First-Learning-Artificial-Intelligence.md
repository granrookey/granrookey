---
layout: post
title: 처음 배우는 인공지능 <타당성 검증>
excerpt: "These are open dataset links from <First learning Machine Learning>"
categories: [Basic ML]
comments: true
image:
  feature: http://image.kyobobook.co.kr/images/book/large/318/l9788968483318.jpg
  credit: Kyobo Books
  creditlink: http://www.kyobobook.co.kr/index.laf
---


### 식별 모델의 평가와 ROC 곡선

* ROC (Receiver Operating Characteristic) Curve

  ![ROC Curve Image](https://www.google.co.kr/url?sa=i&rct=j&q=&esrc=s&source=images&cd=&cad=rja&uact=8&ved=0ahUKEwi2zra4tcvYAhXDJpQKHS82BsEQjRwIBw&url=https%3A%2F%2Fwww.ibm.com%2Fsupport%2Fknowledgecenter%2Fen%2FSSLVMB_sub%2Fspss%2Ftutorials%2Froc_curve_bankloan_01.html&psig=AOvVaw2zB1WF3e72nLre-afsRXs9&ust=1515605701005863)

  식별 모델의 성능을 평가하는 방법으로 제2차 세계 대전 때 수신된 레이저 신호에서 적 전투기르 찾으려느 미국의 레이더 연구에서 탄생하 개념
  
  ROC Curve를 만드 위해서는 양성과 음성 결과세트와 식별 결과세트를 준비 혼동행렬 Confusion Matrix를 만듦

  혼동 행렬으 TP True Positive, FN False Negative, FP False Positive, TN True Negative의 2 * 2 행렬입니다.
  
  정밀도 Precision : 식별결과가 양성인 수를 분모로 했을 때의 TP의 비율 (양성적중률) TP / (TP + FP)
  
  특이도 Specificity : 식별결과가 음성인 수를 분모로 했을 때의 TN의 비율 (진음성률) FP / (FP + TN)
  
  민감도 Sensitivity : 양성인 수를 분모로 했을 때 TP의 비율 TP / (TP + FN)
  
  정확도 Accuracy : 전체 수에서 식별 결과가 올바른 수의 비율
  
  재현율 Recall : 양성인 수를 어느정도 비율로 제대로 식별했는지 TP / (TP + TN)
  
  F값 F-measure: 이율배반적인 관계인 정밀도와 재현율의 조화 평균을 계산한 종합지표 2 * (정밀도 * 재현율) / (정밀도 + 재현율)
  
* ROC Curve를 이용한 평가

  AUC Area Under Curve : AUC는 ROC Curve의 아랫부분 면적 값으로 이 값이 0.9 이상이면 정확도가 높다고 함
  
  왼쪽 위에서 곡선까지 거리 : AUC 값이 높으면 높을 수록 ROC Curve는 왼쪽 위에 가까운 형태가 되므로 왼쪽 모서리에서 곡선까지의 거릭 짧을 수록 성능이 좋음
  
  Youden Index : AUC값과 길이 0.5의 대각선 사이 거리가 가장 멀 때 '진양성률 + 거짓 양성율'을 Youden Index라고 하며, 이 값이 큰 모델은 가장 좋은 평가
