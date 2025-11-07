# Cinemania_IMDB_Sentiment_Analysis

# 🎬 Cinemania — IMDB 영화 리뷰 감정 분석 프로젝트

## 📌 프로젝트 개요
**Cinemania**는 신규 스트리밍 서비스에서 사용자 리뷰를 자동으로 **긍정(positive)** 또는 **부정(negative)** 으로 분류하기 위한 인공지능(AI) 모델을 개발하는 프로젝트입니다.  
본 프로젝트에서는 두 가지 서로 다른 접근 방식인 **RNN**과 **Transformer(DistilBERT)** 모델을 비교하여 가장 효율적인 감정 분류 모델을 찾는 것을 목표로 합니다.

---

## 🎯 프로젝트 목표
- IMDB 영화 리뷰 데이터셋을 이용하여 리뷰의 감정(긍정/부정)을 자동 분류하는 모델 개발  
- **RNN**과 **Transformer(DistilBERT)** 두 모델의 성능 비교  
- 학습 손실(loss), 평가 지표(metric), 예측 결과를 기반으로 한 **최종 비교 보고서 작성**

---

## 📂 데이터셋
- 사용 데이터: **Kaggle – IMDB Dataset of 50K Movie Reviews**  
- 총 50,000개의 영어 리뷰와 감정 레이블(positive/negative)로 구성  
- 각 범주에서 1000개씩 샘플링하여 학습용 데이터 구성  

---

## 🧠 모델 구성

### 🔹 SentimentRNN
- **임베딩 차원(embedding_dim)**: 128  
- **은닉 차원(hidden_dim)**: 256  
- **구조**: `Embedding → RNN → Linear → Sigmoid`  
- **손실 함수**: `BCELoss`  
- **최적화기**: `Adam(lr=0.001)`  
- **학습 횟수(epochs)**: 10  

### 🔹 DistilBERT (Transformer)
- 사전학습 모델: `distilbert-base-uncased`  
- 입력 길이: `max_length=256`  
- 학습 설정:
  - `num_train_epochs=3`
  - `logging_steps=100`
- 학습 도구: `Trainer` API  
- 평가 메트릭: `eval_loss`, `accuracy`

---

## ⚙️ 학습 및 평가 과정
1. 데이터 전처리 (토크나이징, 패딩, 시퀀스 변환)  
2. RNN 모델 학습 및 손실 모니터링  
3. Transformer(DistilBERT) 모델 학습  
4. 두 모델 성능 비교 및 평가  

---

## 📈 결과 및 분석
- **DistilBERT(Transformer)** 모델은 **RNN보다 높은 정확도**와 **문맥 이해 능력**을 보였다.  
- **RNN** 모델은 학습 속도가 빠르고 단순하지만, 세밀한 감정 차이를 구분하기에는 한계가 있었다.  
- **우즈베크어 리뷰 분석**에서는 약간의 오차가 있었지만, **영어 리뷰**에서는 매우 높은 성능을 기록하였다.  

> ✅ 결론: Cinemania 프로젝트에서는 **Transformer 기반 모델(DistilBERT)** 이 더 신뢰할 수 있는 감정 분석 솔루션으로 판단된다.

---

## 📜 파일 구성
