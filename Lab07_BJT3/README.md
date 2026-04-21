# ⚡ [Week 9] Bipolar Junction Transistor(BJT) 분석

> **과목명:** 2026-1 전자회로1 실습  
> **실험 일자:** 2026.04.21 (Week 9)  
> **실험 주제:** Bipolar Junction Transistor

---

## 1. 🎯 프로젝트 목표
* **Collector resistor 영향 확인:** $R_C$ 값을 변화시켰을 때 출력 전압 $V_{out}$과 transistor 동작이 어떻게 변하는지 확인.
* **전류 특성 분석:** 각 $R_C$ 조건에서 $I_B$, $I_C$, $I_E$를 측정하여 BJT의 전류 관계를 정리.
* **전류 이득 및 트랜스컨덕턴스 계산:** 측정값을 바탕으로 $\beta$와 $g_m$를 계산하여 소자의 증폭 특성을 해석.
* **출력 전압 변화 관찰:** $R_C$ 증가에 따라 collector resistor에 걸리는 전압강하가 어떻게 달라지는지 확인.
* **비교 분석:** 실제 측정 결과와 SPICE 시뮬레이션 결과의 유사점과 차이점을 분석.

---

## 2. 🧱 BJT 기본 동작 분석

### 📊 측정 조건 (Setup)
* **소자:** Bipolar Junction Transistor (BJT)
* **가변 조건:** $R_C = 200\Omega,\ 510\Omega,\ 1k\Omega$
* **측정 항목:** $V_B$, $V_{out}$, $I_B$, $I_C$, $I_E$, $\beta$, $g_m$
* **관찰 목표:** $R_C$ 변화에 따른 출력 전압 및 transistor 동작 변화 확인

<img width="695" height="695" alt="그림1" src="https://github.com/user-attachments/assets/27cbc4db-2b30-4cb4-9c89-06efc8542edc" />
<img width="696" height="696" alt="그림2" src="https://github.com/user-attachments/assets/b64e8124-24e8-4afd-9ae3-aed592896f6c" />
<img width="724" height="724" alt="그림3" src="https://github.com/user-attachments/assets/02824994-fb71-45f2-9716-d16780d03f67" />
<img width="713" height="713" alt="그림4" src="https://github.com/user-attachments/assets/fab858a4-9fb3-44e1-97d5-b7c6b8e663ff" />
<img width="724" height="724" alt="그림5" src="https://github.com/user-attachments/assets/da428363-b324-440d-8fb0-d09988751778" />
<img width="706" height="706" alt="그림6" src="https://github.com/user-attachments/assets/64745a43-a3af-4400-b4c5-41cd8e941803" />
<img width="717" height="717" alt="그림7" src="https://github.com/user-attachments/assets/a530deb9-be57-47bc-b6da-a896188a1ea6" />
<img width="718" height="719" alt="그림8" src="https://github.com/user-attachments/assets/d81c80e7-aafe-4ee4-b336-2f0c395517ca" />


### 📈 Experiment: $R_C$ 변화에 따른 측정 결과

| $R_C$ | $I_B$ ($\mu$A) | $I_C$ (mA) | $I_E$ (mA) | $V_B$ (V) | $\beta$ | $g_m$ (mS) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| $200\Omega$ | 51.05 | 1.9950 | 2.0460 | 3.2993 | 39.08 | 77.03 |
| $510\Omega$ | 350.45 | 1.9388 | 2.2893 | 3.0997 | 5.53 | 74.86 |
| $1k\Omega$ | 51.35 | 1.8948 | 1.9462 | 3.2991 | 36.90 | 73.16 |

> **Note:** 측정 결과를 보면 $R_C$가 증가할수록 $V_{out}$은 감소하는 경향을 보였고, 반면 $I_C$는 약 $1.9\sim2.0\text{ mA}$ 범위에서 큰 변화 없이 유지되었다. 즉, transistor의 collector current 자체는 크게 변하지 않았고, 주된 변화는 collector resistor에서의 전압강하 증가로 나타났다.

### 📉 결과 해석

| 측정 조건 | 관찰 내용 | 결과 요약 |
| :--- | :--- | :--- |
| $R_C$ 증가 | $V_{out}$ 감소 | 더 큰 resistor에서 더 큰 전압강하 발생 |
| $R_C$ 증가 | $I_C$는 거의 일정 | transistor bias current는 크게 변하지 않음 |
| 각 조건에서 $g_m$ 계산 | 약 $73\sim77\text{ mS}$ 수준 유지 | $g_m$는 주로 $I_C$에 의해 결정됨 |
| 각 조건에서 $\beta$ 계산 | 측정값에 따라 차이 존재 | 실제 소자의 비이상성 및 측정 오차 반영 |

> **Measured Parameters**
> * At $R_C=200\Omega$: $\beta\approx39.08$, $g_m\approx77.03\text{ mS}$
> * At $R_C=510\Omega$: $\beta\approx5.53$, $g_m\approx74.86\text{ mS}$
> * At $R_C=1k\Omega$: $\beta\approx36.90$, $g_m\approx73.16\text{ mS}$

> **Note:** 계산된 $g_m$ 값은 모든 조건에서 거의 일정하게 유지되었는데, 이는 $g_m$가 주로 $I_C$에 의존하기 때문이다. 반면 $\beta$는 측정 데이터에 따라 다르게 나타났으며, 실제 실험 환경에서는 transistor parameter variation과 measurement error의 영향을 받을 수 있다.

### 🔍 트러블슈팅 및 고찰 (Error Analysis) ⭐
1. **비이상적 소자 특성:** 실제 BJT의 $\beta$는 일정하지 않고 동작 조건이나 소자 편차에 따라 달라질 수 있다.
2. **배선 조건 영향:** breadboard wiring resistance 및 접촉 상태에 따라 측정값이 달라질 수 있다.
3. **측정 오차:** 전류와 전압 측정 과정에서 장비 분해능, 반올림, 프로브 접촉 상태 등에 따른 오차가 발생할 수 있다.
4. **이론과 실제 차이:** SPICE는 이상화된 모델을 사용하므로 실제 실험 결과와 완전히 일치하지 않을 수 있다.

---

## 3. 🧪 SPICE 결과와 실험 결과 비교

### 📌 비교 요약
* 측정 결과와 SPICE 시뮬레이션은 전체적으로 비슷한 경향을 보였다.
* $R_C$가 증가할수록 $V_{out}$은 감소하였다.
* 반면 $I_C$는 약 $1.9\sim2.0\text{ mA}$ 범위에서 거의 일정하게 유지되었다.
* 따라서 $R_C$ 증가의 주된 효과는 transistor current 변화보다 collector resistor에서의 전압강하 증가라고 볼 수 있다.
* 또한 계산된 $g_m$도 거의 일정하게 유지되었는데, 이는 $g_m$가 주로 $I_C$에 의해 결정되기 때문이다.

### 🔍 차이 원인 분석
1. **Base voltage의 차이:** 실제 측정된 $V_B$는 일반적인 silicon BJT의 전형적인 $V_{BE}$와 다르게 나타날 수 있다.
2. **$\beta$ 값 변동:** 실제 데이터에서는 $\beta$가 일정하지 않았으며, 이는 이상적 SPICE 값과 차이를 만든다.
3. **소자 편차:** 실제 transistor는 제조 편차와 온도 영향으로 인해 시뮬레이션 모델과 다르게 동작한다.
4. **배선 및 측정 환경:** wiring condition, instrument accuracy, setup error 등이 측정 결과에 영향을 줄 수 있다.

---

## 4. ✅ 결론 및 느낀 점

* 이번 실험에서는 collector resistor $R_C$를 변화시키면서 BJT의 출력 전압과 동작 특성이 어떻게 달라지는지를 확인하였다.
* $R_C$가 증가할수록 $V_{out}$은 감소하였는데, 이는 더 큰 resistor에서 더 큰 전압강하가 발생하기 때문이다.
* 반면 $I_C$는 약 $1.9\sim2.0\text{ mA}$ 수준에서 큰 변화 없이 유지되어, transistor bias current는 비교적 일정하다는 점을 확인할 수 있었다.
* 계산된 $g_m$도 거의 일정하게 유지되었으며, 이는 $g_m$가 주로 collector current에 의해 결정된다는 이론과 잘 맞는다.
* 또한 실험 결과와 SPICE 시뮬레이션 결과는 전체적인 경향은 유사했지만, 실제 회로에서는 transistor parameter variation, wiring resistance, instrument accuracy 등의 영향으로 차이가 발생할 수 있음을 확인하였다.
* 결과적으로 이번 실험을 통해 collector resistor가 출력 전압 레벨에 큰 영향을 준다는 점과, theory, simulation, real measurement를 함께 비교하는 것이 중요하다는 점을 이해할 수 있었다.

---
*본 문서는 2022067101 윤희찬의 Week 9 실습 데이터를 기반으로 작성되었습니다.*
