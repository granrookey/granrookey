---
layout: post
title: 처음 배우는 머신러닝 Keywords
excerpt: "These are open dataset links from <First learning Machine Learning>"
categories: [datasets]
comments: true
image:
  feature: http://image.kyobobook.co.kr/images/book/large/045/l9791162240045.jpg
  credit: Kyobo Books
  creditlink: http://www.kyobobook.co.kr/index.laf
---


### 군집화 Clustering

* 중심 기반 군집화 prototype-based clustering : 클러스터를 클러스터 중심점으로 정의하는 기법
  K-중심 군집화 K-centroid clustering, K-medoid clustering
* 게층적 군집화 hierachical clustering : 클러스터의 크기에 따라 클러스터의 계층을 정의하고 계층의 상하위를 이용하는 기법
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
                  공분산 $$ Cov(X, Y) = E[(X - u_x)(Y - u_y)] $$
