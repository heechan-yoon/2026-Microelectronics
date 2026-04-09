# ⚡ [Week 6] Bipolar Junction Transistor(BJT) 분석

> **과목명:** 2026-1 전자회로1 실습  
> **실험 일자:** 2026.04.07 (Week 6)  
> **실험 주제:** Bipolar Junction Transistor  

---

## 1. 🎯 프로젝트 목표
* **출력 특성 확인:** $V_{BE}$를 0.7 V로 고정하고 $V_C$를 변화시켰을 때, BJT의 collector current 특성이 어떻게 나타나는지 확인.
* **입력 특성 확인:** $V_C$를 5 V로 고정하고 $V_{BE}$를 증가시켰을 때, $I_B$와 $I_C$가 어떻게 변하는지 측정.
* **전류 이득 및 트랜스컨덕턴스 분석:** 측정값을 통해 BJT의 전류 제어 특성과 증폭 특성을 정리.
* **증폭 동작 확인:** 소신호 입력을 인가했을 때 실제로 전압 이득이 발생하는지 확인.
* **비교 분석:** 실제 측정 결과와 SPICE 시뮬레이션 결과의 유사점과 차이점을 분석.

---

## 2. 🧱 BJT 기본 동작 분석

### 📊 측정 조건 (Setup)
* **소자:** Bipolar Junction Transistor (BJT)
* **Experiment 1:** $V_{BE}=0.7\text{ V}$, $V_C = 0 \sim 5\text{ V}$, step size = 0.5 V
* **Experiment 2:** $V_C=5\text{ V}$, $V_{BE} = 0 \sim 1.0\text{ V}$, step size = 0.2 V
* **Experiment 3:** Input signal = 100 kHz, 40 mVpp, DC offset = 0.7 V

![breadboard](https://github.com/user-attachments/assets/c8d8cbd0-2a0a-42e7-b27a-6ca9f4efa2b4)

### 📈 Experiment 1: $V_{BE}=0.7\text{ V}$에서 $V_C$ sweep

| 측정 조건 | 관찰 내용 | 결과 요약 |
| :--- | :--- | :--- |
| $V_{BE}=0.7\text{ V}$ 고정, $V_C=0\sim5\text{ V}$ | collector current가 대부분의 구간에서 크게 변하지 않음 | BJT의 active region 출력 특성을 확인 |
| 동일 조건에서 $I_B$, $I_C$ 측정 | collector current는 collector voltage보다 base-emitter voltage의 영향이 더 큼 | $I_C$는 주로 $V_{BE}$에 의해 제어됨 |

> **Note:** $V_{BE}$를 일정하게 유지한 상태에서 $V_C$를 변화시켜도 $I_C$가 크게 변하지 않았으며, 이는 active region에서의 전형적인 BJT 출력 특성과 일치한다.

![그림1](https://github.com/user-attachments/assets/5480c1c2-5a85-46b1-af05-2be7f1019f01)

### 📉 Experiment 2: $V_C=5\text{ V}$에서 $V_{BE}$ sweep

| $V_{BE}$ 구간 | 동작 분석 (Region) | 결과 요약 |
| :--- | :--- | :--- |
| 낮은 $V_{BE}$ 영역 | Cutoff region | $I_B$와 $I_C$가 거의 0에 가까움 |
| $V_{BE}\approx0.6\text{ V}$ 부근 | Turn-on region | collector current가 눈에 띄게 증가하기 시작 |
| 높은 $V_{BE}$ 영역 | Active region | $I_B$, $I_C$ 모두 증가하며 증폭 특성 확인 |

> **Measured Parameters**
> * $g_m \approx 0.74\text{ mS}$
> * DC current gain $\beta \approx 300.7$ at $V_{BE}=0.8\text{ V}$
> * DC current gain $\beta \approx 225.1$ at $V_{BE}=1.0\text{ V}$
> * Incremental current gain $\approx 174$

> **Note:** $V_{BE}$가 증가함에 따라 BJT는 cutoff region에서 active region으로 전이되었고, 이 과정에서 base current와 collector current가 함께 증가하였다.

![그림3](https://github.com/user-attachments/assets/a8bf2c92-2eaf-4287-bff2-c9c9837f0d22)

### 🔍 트러블슈팅 및 고찰 (Error Analysis) ⭐
1. **측정 분해능 한계:** 낮은 $V_{BE}$ 구간에서는 전류가 매우 작아 측정 장비의 분해능에 따라 오차가 크게 보일 수 있다.
2. **비이상적 소자 특성:** 실제 BJT는 이상적인 모델과 다르게 동작하므로, SPICE 결과와 완전히 일치하지 않을 수 있다.
3. **수치 계산 오차:** $\beta$나 $g_m$ 계산 과정에서 측정값 반올림이나 근사에 따른 차이가 발생할 수 있다.

---

## 3. 📡 증폭 동작 분석

### 📐 이론적 배경
* BJT amplifier는 작은 입력 신호 변화를 더 큰 출력 전압 변화로 증폭할 수 있다.
* 전압 이득은 일반적으로 출력 peak-to-peak voltage를 입력 peak-to-peak voltage로 나누어 구할 수 있다.
* 측정 환경이 적절하지 않으면 실제 증폭은 발생하더라도 오실로스코프 화면에서는 왜곡된 형태로 보일 수 있다.

### 📊 Experiment 3: 증폭 회로 측정 결과

| 입력 조건 | 출력 관찰 | 결과 요약 |
| :--- | :--- | :--- |
| 100 kHz, 40 mVpp, 0.7 V DC offset | 출력 peak-to-peak voltage 약 1.76 V | voltage gain 약 44 |
| 실제 오실로스코프 파형 | 왜곡되고 불규칙한 형태로 관찰됨 | 증폭은 확인되었지만 파형은 이상적이지 않음 |

> **Note:** 출력 파형의 peak-to-peak voltage가 약 1.76 V로 측정되어, 입력 40 mVpp에 대해 약 44배의 전압 이득이 발생한 것으로 확인되었다. 따라서 회로가 실제로 증폭 동작을 수행했음을 알 수 있다.

![그림4](https://github.com/user-attachments/assets/5db847c4-50f0-413d-a8e5-884a44c67308)

### 🔍 트러블슈팅 및 고찰 (Error Analysis) ⭐
1. **Time base 설정 문제:** 오실로스코프 time base가 10 ms/div로 설정되어 있었는데, 100 kHz 신호의 주기는 10 $\mu s$이므로 이 설정은 너무 커서 실제 고주파 출력 파형을 정확히 표시하지 못했다.
2. **트리거 설정 영향:** 트리거 조건이 적절하지 않으면 파형이 흔들리거나 불안정하게 보일 수 있다.
3. **프로브 및 접지 문제:** 프로브 연결 상태, grounding condition, channel offset 등에 의해 출력 파형이 왜곡될 수 있다.

---

## 4. 🧪 SPICE 결과와 실험 결과 비교

### 📌 비교 요약
* 실험 결과는 전체적으로 SPICE 시뮬레이션과 유사한 경향을 보였다.
* $V_C=5\text{ V}$에서 $V_{BE}$를 증가시켰을 때, 낮은 $V_{BE}$ 영역에서는 $I_B$와 $I_C$가 거의 0에 가까워 cutoff region 특성이 나타났다.
* $V_{BE}$가 약 0.6 V에 가까워지면서 collector current가 증가하기 시작했고, 이는 BJT의 turn-on 동작과 일치했다.
* 증폭 실험에서도 실제 전압 이득이 발생하여 회로의 amplifier 동작을 확인할 수 있었다.

### 🔍 차이 원인 분석
1. **측정 해상도 및 수치 오차:** 실제 측정에서는 작은 전류나 파형을 완벽하게 읽기 어려워 SPICE와 미세한 차이가 날 수 있다.
2. **비이상적 BJT 동작:** 실제 트랜지스터의 특성은 단순화된 시뮬레이션 모델과 완전히 같지 않다.
3. **오실로스코프 설정 문제:** time base, trigger, probe connection 등 측정 조건이 적절하지 않으면 출력 파형이 이상적으로 나타나지 않는다.
4. **실험 환경의 영향:** 배선 상태, 접지, 노이즈, channel offset 같은 실제 환경 요인이 결과에 영향을 줄 수 있다.

---

## 5. ✅ 결론 및 느낀 점

* 이번 실험을 통해 BJT의 기본적인 출력 특성과 입력 특성을 직접 확인할 수 있었다.
* $V_{BE}$를 일정하게 유지한 상태에서 $V_C$를 변화시키면 collector current가 크게 변하지 않는다는 점을 통해, active region에서의 전형적인 출력 특성을 이해할 수 있었다.
* 또한 $V_C$를 고정하고 $V_{BE}$를 증가시키면 $I_B$와 $I_C$가 증가하며, BJT가 cutoff region에서 active region으로 전이한다는 점도 확인할 수 있었다.
* 측정값을 이용해 $g_m$, $\beta$, incremental current gain을 추정할 수 있었고, 이를 통해 BJT가 전류 제어와 증폭 기능을 동시에 수행하는 소자임을 확인하였다.
* 마지막 증폭 실험에서는 이상적인 출력 파형과 완전히 일치하지는 않았지만, 실제로 약 44의 전압 이득이 나타나 증폭 동작 자체는 분명히 확인할 수 있었다.
* 결과적으로 이번 실험을 통해 BJT의 동작 원리뿐 아니라, accurate measurement condition이 amplifier analysis에서 매우 중요하다는 점도 함께 이해할 수 있었다.

---
*본 문서는 2022067101 윤희찬의 Week 6 실습 데이터를 기반으로 작성되었습니다.*
