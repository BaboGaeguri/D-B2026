# Harness Engineering 기반 기업 공시문서 검토 Agent의 비용-신뢰도 효과 분석

## 부제

소형 LLM과 Harness Engineering 조합이 고성능 LLM을 대체할 수 있는가?

---

# 1. 연구 배경

최근 GPT-4, Claude, Gemini 등 대규모 언어모델(LLM)의 성능이 빠르게 발전하면서 기업 업무에 AI를 적용하려는 시도가 증가하고 있다.

그러나 실제 기업 환경에서는 단순한 모델 성능보다 다음과 같은 문제가 더 중요하다.

* 결과를 신뢰할 수 있는가?
* 왜 그런 결론을 내렸는지 설명 가능한가?
* 환각(Hallucination)을 통제할 수 있는가?
* 비용 대비 효과가 있는가?

특히 기업 문서 검토 업무는 수백 페이지에 달하는 사업보고서, 감사보고서, 공시문서를 분석해야 하며, 잘못된 판단은 투자 실패, 리스크 관리 실패, 규제 위반 등의 문제로 이어질 수 있다.

따라서 본 연구는 단순히 더 큰 모델을 사용하는 것이 아니라, Harness Engineering을 통해 더 작은 모델의 신뢰도를 향상시켜 실제 기업 업무에 활용 가능한 수준으로 만들 수 있는지를 검증하고자 한다.

---

# 2. 연구 문제

## Research Question 1

Harness Engineering은 기업 문서 검토 업무에서 LLM의 신뢰도를 향상시키는가?

## Research Question 2

소형 LLM + Harness 조합은 대형 LLM 단독 사용을 어느 정도 대체할 수 있는가?

## Research Question 3

Harness 적용 시 비용 대비 성능(Cost-Reliability Tradeoff)은 얼마나 개선되는가?

---

# 3. 연구 대상 업무

## 기업 공시문서 리스크 검토 업무

실제 수행 주체

* 증권사 애널리스트
* VC 투자심사역
* PE 투자심사역
* 회계법인
* 기업 내부감사팀
* 리스크관리 부서

실제 업무

* 사업보고서 검토
* 감사보고서 검토
* 정정공시 검토
* 기업 리스크 식별
* 리스크 근거 확보

---

# 4. 데이터셋 구축

## 데이터 출처

DART(OpenDART)

수집 문서

* 사업보고서
* 감사보고서
* 정정공시

---

## 표본 규모

예시

상장기업 200~500개

기업당

* 사업보고서
* 감사보고서

수집

---

## Ground Truth

### 방법 1

감사보고서 내 Key Audit Matter

### 방법 2

계속기업 불확실성 문구

### 방법 3

강조사항 문단

### 방법 4

감사의견 유형

* 적정
* 한정
* 부적정
* 의견거절

---

## 최종 Ground Truth

문서 내 실제 존재하는 리스크 항목

예

* 계속기업 리스크
* 유동성 리스크
* 내부통제 리스크
* 소송 리스크
* 재무건전성 리스크

---

# 5. Harness 설계

## Baseline

### Group A

LLM Only

입력

사업보고서

출력

리스크 목록

---

## Harness 1

### Group B

Retrieval-Augmented Analysis

추가 기능

* 문서 검색
* 근거 문장 추출

---

## Harness 2

### Group C

Evidence Validation

추가 기능

* 모든 주장에 근거 요구
* 근거 미존재 시 제거

---

## Harness 3

### Group D

Cross-document Validation

추가 기능

사업보고서

VS

감사보고서

VS

정정공시

비교

---

## Harness 4

### Group E

Self-Correction Loop

추가 기능

* 근거 부족 시 재분석
* 문서 재탐색

---

# 6. 실험군 구성

## Group A

소형 모델 단독

예

GPT-4o-mini

---

## Group B

소형 모델 + Harness

GPT-4o-mini

*

Retrieval

*

Validation

*

Cross-check

*

Self-Correction

---

## Group C

대형 모델 단독

GPT-5급 모델

---

핵심 비교

Group B vs Group C

---

# 7. 평가 지표

## Accuracy

실제 리스크 식별 정확도

---

## Recall

실제 리스크 중 발견 비율

---

## Precision

발견 리스크 중 정답 비율

---

## Evidence Precision

제시된 근거의 정확도

---

## Hallucination Rate

근거 없는 주장 비율

---

## Reliability

동일 문서 반복 실행 시 결과 일관성

---

## Cost

토큰 비용

API 비용

---

# 8. 핵심 가설

## H1

Harness 적용 시 Precision이 향상된다.

---

## H2

Harness 적용 시 Hallucination Rate가 감소한다.

---

## H3

소형 모델 + Harness는 대형 모델 단독과 유사한 성능을 달성한다.

---

## H4

소형 모델 + Harness가 비용 대비 효율 측면에서 가장 우수하다.

---

# 9. 기대 효과

## 경영학적 기여

AI를 단순 모델이 아닌 기업 운영 자산으로 활용하는 방안을 제시

---

기업 문서 검토 업무 자동화 가능성 검증

---

AI Governance 및 Risk Management 관점의 시사점 제공

---

## 데이터사이언스 기여

Harness Engineering의 효과 정량 검증

---

LLM 성능 향상보다 운영 아키텍처의 중요성 제시

---

비용-신뢰도 최적화 전략 제안

---

# 10. 연구 의의

본 연구는 더 강력한 모델 개발이 아닌, Harness Engineering을 활용하여 기업 업무에서 AI의 신뢰성과 경제성을 동시에 향상시킬 수 있는지를 검증한다.

이를 통해 기업 AI 도입의 핵심 과제가 모델 성능 경쟁이 아니라 운영 아키텍처 설계임을 실증적으로 제시하고자 한다.
