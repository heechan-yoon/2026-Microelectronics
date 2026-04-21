# ⚡ [Week 7] Bipolar Junction Transistor(BJT) (2) 분석

> **과목명:** 2026-1 전자회로1 실습  
> **실험 일자:** 2026.04.14 (Week 7)  
> **실험 주제:** Bipolar Junction Transistor (2)

---

## 1. 🎯 프로젝트 목표
* **바이어스 포인트 설정:** Common-emitter amplifier에서 $V_{out}$이 약 5 V가 되도록 입력 바이어스 전압 $V_{in}$을 찾는다.
* **소신호 증폭 확인:** 작은 입력 신호를 인가했을 때 출력 신호가 실제로 증폭되는지 확인한다.
* **트랜스컨덕턴스 분석:** 측정된 collector current를 바탕으로 $g_m$를 계산하고 증폭기의 동작 특성을 해석한다.
* **전압 이득 측정:** 입력과 출력의 peak-to-peak voltage를 비교하여 voltage gain을 구한다.
* **비교 분석:** breadboard 실험 결과와 LTSpice 시뮬레이션 결과의 유사점과 차이점을 분석한다.

---

## 2. 🧱 BJT 증폭기 기본 동작 분석

### 📊 측정 조건 (Setup)
* **소자:** Bipolar Junction Transistor (BJT)
* **회로 형태:** Common-emitter amplifier
* **Bias condition:** $V_{out} \approx 5\text{ V}$가 되도록 $V_{in}$ 조정
* **Input signal:** 40 mVpp
* **관찰 항목:** bias point, $g_m$, $I_C$, $V_T$, voltage gain, 출력 파형 형태

<img width="720" height="720" alt="그림1" src="https://github.com/user-attachments/assets/9947bc11-5eec-4ca0-8e46-56b44aa4f602" />
<img width="713" height="713" alt="그림2" src="https://github.com/user-attachments/assets/b12c52d9-270b-40d8-b3c7-320556161106" />

### 📈 Experiment 1: Bias point setting

| 측정 항목 | 측정 결과 | 의미 |
| :--- | :--- | :--- |
| $V_{out}\approx5\text{ V}$가 되도록 조정한 입력 바이어스 | $V_{in}=2.94\text{ V}$ | 증폭기가 선형 동작하기 위한 Q-point 설정 |
| collector current | $I_C=0.5\text{ mA}$ | BJT가 active region에서 동작 중임을 보여줌 |
| thermal voltage | $V_T=25.9\text{ mV}$ | room temperature에서의 전형적인 thermal voltage |
| transconductance | $g_m=19.3\text{ mS}$ | 작은 입력 전압 변화에 대한 collector current 변화 민감도 |

> **Note:** 증폭기가 정상적인 소신호 증폭을 하려면 transistor가 cutoff나 saturation이 아닌 active region에 위치해야 한다. 이번 실험에서는 $V_{out}\approx5\text{ V}$가 되도록 $V_{in}=2.94\text{ V}$를 설정하여 적절한 bias point를 찾았다.

---

## 3. 📡 증폭 동작 분석

### 📐 이론적 배경
* BJT common-emitter amplifier는 작은 입력 신호를 더 큰 출력 전압 변화로 증폭할 수 있다.
* 전압 이득은 일반적으로 출력 peak-to-peak voltage를 입력 peak-to-peak voltage로 나누어 구할 수 있다.
* 이상적인 common-emitter amplifier에서는 출력이 입력에 대해 180° phase inversion을 보인다.
* 실제 breadboard 실험에서는 소자 편차, 배선 기생성분, 측정 설정 등의 영향으로 파형 왜곡이 발생할 수 있다.

### 📊 Experiment 2: 증폭 회로 측정 결과

| 입력 조건 | 출력 관찰 | 결과 요약 |
| :--- | :--- | :--- |
| Input = 40 mVpp | Output $\approx1.2\text{ Vpp}$ | voltage gain 약 30 |
| LTSpice 예측 | clean amplified sinusoidal output | 이상적인 증폭 동작 |
| 실제 오실로스코프 파형 | 왜곡된 형태로 관찰됨 | 증폭은 확인되었지만 파형은 이상적이지 않음 |

> **Measured Parameters**
> * $V_{in}=2.94\text{ V}$
> * $g_m=19.3\text{ mS}$
> * $I_C=0.5\text{ mA}$
> * $V_T=25.9\text{ mV}$
> * Gain $\approx 30$

> **Note:** 입력이 40 mVpp일 때 출력이 약 1.2 Vpp로 측정되어, 회로가 실제로 약 30의 voltage gain을 가진다는 것을 확인할 수 있었다. 다만 실제 오실로스코프 파형은 LTSpice에서 기대한 이상적인 정현파보다 더 왜곡된 형태로 나타났다.

<img width="728" height="728" alt="그림3" src="https://github.com/user-attachments/assets/427b8f6f-e5e3-425c-8c09-a2868a87983a" />
<img width="722" height="723" alt="그림4" src="https://github.com/user-attachments/assets/d8d90db9-6664-4bf3-9e4a-e6345806dc88" />

### 🔍 트러블슈팅 및 고찰 (Error Analysis) ⭐
1. **Transistor parameter variation:** 실제 transistor의 $\beta$, $V_{BE}$, 내부 저항 값은 SPICE 모델과 정확히 일치하지 않을 수 있다.
2. **Breadboard parasitic effects:** breadboard 배선에는 기생 capacitance와 resistance가 존재하여 고주파 응답과 파형 품질에 영향을 줄 수 있다.
3. **Imperfect biasing:** 이론상 Q-point를 잘 맞추더라도 실제 회로에서는 작은 오차로 인해 완전히 선형 영역을 유지하지 못할 수 있다.
4. **Measurement setting issues:** function generator amplitude/Vpp 설정, oscilloscope scaling, probe connection 등의 문제로 파형이 더 왜곡되어 보일 수 있다.

---

## 4. 🧪 SPICE 결과와 실험 결과 비교

### 📌 비교 요약
* LTSpice에서는 $V_{out}\approx5\text{ V}$로 bias된 common-emitter amplifier가 깨끗한 증폭된 정현파를 출력할 것으로 예상되었다.
* 실제 실험에서는 $V_{out}=5\text{ V}$가 되도록 $V_{in}=2.94\text{ V}$를 찾았고, 입력 40 mVpp에 대해 출력 약 1.2 Vpp가 측정되어 gain이 약 30으로 확인되었다.
* 따라서 증폭 동작 자체는 시뮬레이션과 전반적으로 일치했다고 볼 수 있다.
* 그러나 실제 오실로스코프 파형은 LTSpice 결과보다 더 많이 왜곡되어 보였으며, 이는 실제 회로의 비이상적 요소 때문이라고 해석할 수 있다.

### 🔍 차이 원인 분석
1. **측정 해상도 및 수치 오차:** 실제 측정에서는 작은 파형이나 전압을 완벽하게 읽기 어려워 SPICE와 미세한 차이가 날 수 있다.
2. **비이상적 BJT 동작:** 실제 트랜지스터의 특성은 단순화된 시뮬레이션 모델과 완전히 같지 않다.
3. **기생 성분의 영향:** breadboard와 배선에 존재하는 기생 저항 및 기생 커패시턴스가 고주파 신호에 영향을 준다.
4. **실험 장비 설정 문제:** function generator와 oscilloscope의 설정이 완벽하지 않으면 출력 파형이 이상적으로 나타나지 않는다.

---

## 5. ✅ 결론 및 느낀 점

* 이번 실험에서는 common-emitter BJT amplifier의 bias point를 직접 설정하고, 실제 증폭 동작을 확인하였다.
* $V_{out}\approx5\text{ V}$가 되도록 조정한 결과 $V_{in}=2.94\text{ V}$의 bias point를 얻었다.
* 측정된 $I_C=0.5\text{ mA}$와 $V_T=25.9\text{ mV}$를 이용해 $g_m=19.3\text{ mS}$를 확인할 수 있었다.
* 입력 40 mVpp에 대해 출력 약 1.2 Vpp가 측정되어 voltage gain은 약 30으로 계산되었다.
* 시뮬레이션과 비교했을 때 증폭 동작 자체는 잘 일치했지만, 실제 파형은 여러 비이상적인 요소들 때문에 왜곡이 발생하였다.
* 결과적으로 이번 실험을 통해 BJT amplifier의 기본 원리뿐 아니라, proper DC biasing과 accurate measurement condition이 amplifier analysis에서 매우 중요하다는 점을 함께 이해할 수 있었다.

---
*본 문서는 2022067101 윤희찬의 Week 7 실습 데이터를 기반으로 작성되었습니다.*
