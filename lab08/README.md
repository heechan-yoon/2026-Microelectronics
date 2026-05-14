# ⚡ [Week 11] MOSFET(1) 공통 소스 증폭기 분석

> **과목명:** 2026-1 전자회로1 실습  
> **실험 일자:** 2026.05.12 (Week 11)  
> **실험 주제:** MOSFET(1) / Common-Source Amplifier  
> **사용 소자:** 13N10 NMOS Transistor  

---

## 1. 🎯 프로젝트 목표

* **Experiment 1:** 13N10 NMOS transistor를 이용한 공통 소스 증폭기 회로를 구성하고, 입력 전압 $V_{in}$ 변화에 따른 출력 전압 $V_{out}$을 측정.
* **DC sweep 분석:** $V_{in}$을 0V부터 5V까지 변화시키며 $V_{DS}$와 $I_{DS}$의 변화를 관찰.
* **Saturation point 확인:** MOSFET이 saturation region에서 동작하는 bias point를 찾고, 조건 $V_{GS}-V_{TH} \leq V_{DS}$를 만족하는지 확인.
* **Experiment 2:** Experiment 1에서 찾은 saturation point를 기준으로 DC bias를 설정한 뒤, small-signal input을 인가하여 공통 소스 증폭기의 증폭 동작을 관찰.
* **SPICE와 비교:** 이상적인 SPICE 시뮬레이션에서 기대되는 common-source amplifier 동작과 실제 측정 결과의 차이를 분석.
* **실패 원인 분석:** saturation point가 명확히 추출되지 않은 이유와 small-signal output waveform이 제대로 관찰되지 않은 원인을 고찰.

---

## 2. 🧱 Experiment 1: NMOS DC Sweep 및 Saturation Point 분석

### 📊 측정 조건 (Setup)

* **소자:** 13N10 NMOS Transistor
* **회로 구조:** Common-Source Amplifier
* **공급 전압:** $V_{DD}=5V$
* **Drain resistor:** $R_D=1k\Omega$
* **입력 전압 sweep:** $V_{in}=0V \sim 5V$
* **측정 항목:** $V_{out}$, $V_{DS}$, $I_{DS}$
* **목표:** $I_{DS}-V_{DS}$ 특성을 확인하고 saturation region에 해당하는 bias point를 찾는 것

---

### 📷 실험 사진

<img width="500" height="500" alt="실험1회로도" src="https://github.com/user-attachments/assets/33df5e6a-6e3f-454d-a3fd-fa19ddcf693f" />

<img width="500" height="500" alt="0" src="https://github.com/user-attachments/assets/9349923b-9fd7-46b1-8796-b2620ad4adc6" />

<img width="500" height="500" alt="0 5" src="https://github.com/user-attachments/assets/f6f5abcb-2f71-42ef-ac39-9bdcaa6940ef" />

<img width="500" height="500" alt="1" src="https://github.com/user-attachments/assets/2fe205e4-3fd0-4c35-bb71-dab36274f67d" />

<img width="500" height="500" alt="1 5" src="https://github.com/user-attachments/assets/430e8c3b-186e-49cf-b0be-abca5fba030f" />

<img width="500" height="500" alt="2" src="https://github.com/user-attachments/assets/ed429472-847d-4b23-8ad6-fce5710e38ec" />

<img width="500" height="500" alt="2 5" src="https://github.com/user-attachments/assets/dd55fbf6-2488-4fd9-8cee-99b5affda422" />

<img width="500" height="500" alt="3" src="https://github.com/user-attachments/assets/f89b1705-d88d-4c0a-a795-c9e05de25baa" />

<img width="500" height="500" alt="3 5" src="https://github.com/user-attachments/assets/e6ea5833-60fb-49b8-95af-6a009da78f91" />

<img width="500" height="500" alt="4" src="https://github.com/user-attachments/assets/b3f916b8-aa13-40ec-9191-bd4b5c4f7288" />

<img width="500" height="500" alt="4 5" src="https://github.com/user-attachments/assets/b5bb7699-86ba-437d-9adc-3c31a60c2b2b" />

<img width="500" height="500" alt="5" src="https://github.com/user-attachments/assets/f9de9a09-2a03-46a0-8573-82bcc37193d9" />

---

### 📐 이론적 배경

Experiment 1에서는 source terminal이 ground에 연결되어 있으므로 다음 관계가 성립한다.

$$
V_{GS}=V_{in}
$$

또한 drain 쪽 출력 전압을 측정하므로,

$$
V_{DS}=V_{out}
$$

Drain current는 drain resistor에 걸리는 전압강하를 이용하여 다음과 같이 계산할 수 있다.

$$
I_{DS}=\frac{V_{DD}-V_{out}}{R_D}
$$

MOSFET이 saturation region에서 동작하기 위한 조건은 다음과 같다.

$$
V_{GS}-V_{TH} \leq V_{DS}
$$

따라서 입력 전압을 변화시키면서 $V_{out}$을 측정하면 $V_{DS}$와 $I_{DS}$를 계산할 수 있고, 이를 통해 saturation point를 찾을 수 있다.

---

### 📊 Experiment 1 결과 요약

실험에서는 $V_{in}$을 0V부터 5V까지 변화시키며 $V_{out}$을 측정하였다. 그러나 측정 결과에서 $I_{DS}-V_{DS}$ 특성이 명확하게 나타나지 않았고, saturation region을 판단할 수 있을 만큼 안정적인 transition을 확인하지 못했다.

따라서 saturation point는 실험적으로 추출하지 못하였다.

| 항목 | 결과 |
| :--- | :--- |
| $V_{in}$ | Not obtained |
| $g_m$ | Not extracted |
| $I_{DS}$ | Not extracted |
| $V_{TH}$ | Not extracted |
| Gain | Not applicable |
| Saturation point | Not experimentally obtained |

> **Saturation point:** Not experimentally obtained  
> **Reason:** DC sweep 결과가 충분히 안정적이지 않아 $V_{GS}-V_{TH} \leq V_{DS}$ 조건을 만족하는 지점을 명확히 판단할 수 없었다.

---

### 📉 결과 해석

| 관찰 항목 | 기대 결과 | 실제 결과 |
| :--- | :--- | :--- |
| $V_{in}$ sweep | $V_{out}$ 변화에 따라 $I_{DS}-V_{DS}$ 곡선 확인 | 신뢰할 수 있는 curve를 얻지 못함 |
| Saturation region | $V_{GS}-V_{TH} \leq V_{DS}$ 조건 만족 지점 확인 | saturation point 미검출 |
| $I_{DS}$ 계산 | $I_{DS}=\frac{V_{DD}-V_{out}}{R_D}$로 계산 가능 | 안정적인 분석값으로 사용하기 어려움 |
| $g_m$ 추출 | 동작점 주변 기울기를 통해 추출 | 추출 불가 |
| Gain 예측 | $A_v\approx -g_mR_D$로 예측 가능 | 적용 불가 |

> **Note:** 공통 소스 증폭기의 small-signal gain을 측정하기 위해서는 먼저 MOSFET이 적절한 DC operating point, 특히 saturation region에서 bias되어야 한다. 그러나 이번 실험에서는 DC sweep에서 안정적인 saturation point를 찾지 못했기 때문에 이후 small-signal 실험의 기준이 되는 $V_{DC}$도 결정할 수 없었다.

---

## 3. 🧪 Experiment 2: Small-Signal Common-Source Amplifier 측정

### 📊 측정 조건 (Setup)

* **회로 구조:** Common-Source Amplifier
* **Drain resistor:** $R_D=1k\Omega$
* **입력 신호 주파수:** 1kHz
* **입력 AC amplitude:** 20mV
* **입력 신호 형태:**

$$
V_{in}=V_{DC}+20mV\sin(\omega t)
$$

* **목표:** saturation region에 bias된 MOSFET에 small-signal을 인가하여 inverted amplified output waveform 관찰
* **특이사항:** $R_D=10k\Omega$ 조건은 교수님 지시에 따라 수행하지 않음

---

### 📷 실험 사진

<img width="687" height="687" alt="회로도2" src="https://github.com/user-attachments/assets/b01b5b28-1d78-47a6-85eb-9b3e501f11f0" />

<img width="689" height="690" alt="파형2" src="https://github.com/user-attachments/assets/f8172f6e-3a84-4321-8aec-5743737bd0a1" />

---

### 📊 Experiment 2 결과

Experiment 2에서는 Experiment 1에서 구한 saturation point를 기준으로 $V_{DC}$를 설정해야 했다. 그러나 Experiment 1에서 valid saturation point를 찾지 못했기 때문에 적절한 $V_{DC}$를 실험적으로 결정할 수 없었다.

그 결과 small-signal input을 인가했을 때 안정적인 input-output waveform pair를 얻지 못했고, output waveform도 제대로 관찰되지 않았다. 따라서 voltage gain 역시 계산할 수 없었다.

| $R_D$ | $V_{DC}$ | Frequency | Input amplitude | Output waveform | Gain |
| :--- | :--- | :--- | :--- | :--- | :--- |
| $1k\Omega$ | Not determined from Exp. 1 | 1kHz | 20mV | Not properly observed | Not extracted |
| $10k\Omega$ | Not performed | Not performed | Not performed | Not performed | Not performed |

> **Note:** $R_D=10k\Omega$ 조건은 실험할 필요가 없다고 안내받아 수행하지 않았다.

---

### 📉 결과 해석

| 측정 조건 | 관찰 내용 | 결과 요약 |
| :--- | :--- | :--- |
| $R_D=1k\Omega$ | $V_{DC}$를 saturation point에서 결정해야 함 | Exp. 1 실패로 $V_{DC}$ 결정 불가 |
| 1kHz, 20mV input | small-signal 증폭 waveform 관찰 목표 | output waveform이 제대로 관찰되지 않음 |
| Gain 계산 | $A_v=\frac{v_{out}}{v_{in}}$ 또는 $A_v\approx -g_mR_D$ | gain 추출 불가 |
| $R_D=10k\Omega$ | 더 큰 gain 기대 가능 | 실험 미수행 |

---

## 4. 🧪 SPICE 결과와 실험 결과 비교

### 📌 SPICE에서 기대되는 동작

SPICE 시뮬레이션에서는 MOSFET이 saturation region에 적절히 bias되어 있다면 전형적인 common-source amplifier 동작이 나타날 것으로 예상된다.

입력 전압 $V_{in}$이 증가하면 drain current $I_{DS}$가 증가한다. 그 결과 drain resistor $R_D$에 걸리는 전압강하가 증가하고, 출력 전압 $V_{out}$은 감소한다. 따라서 common-source amplifier의 출력은 입력에 대해 반전된 형태로 나타난다.

이상적인 전압 이득은 다음과 같이 근사할 수 있다.

$$
A_v \approx -g_mR_D
$$

즉, MOSFET이 saturation region에서 적절히 bias되어 있고 충분한 transconductance $g_m$를 가진다면, output waveform은 input sine wave에 대해 위상이 반전된 amplified sine wave로 나타나야 한다.

---

### 📊 비교 요약

| Item | SPICE expectation | Experimental result |
| :--- | :--- | :--- |
| DC sweep | Clear $I_{DS}-V_{DS}$ curve should be obtained | Reliable curve was not obtained |
| Saturation point | A point satisfying $V_{GS}-V_{TH} \leq V_{DS}$ should be found | Not experimentally obtained |
| Small-signal output | Inverted sine wave should appear at $V_{out}$ | Output waveform was not properly observed |
| Gain | $A_v=-g_mR_D$ | Not extracted |
| $R_D=10k\Omega$ case | Higher gain expected if properly biased | Not performed |

### 🔍 차이 원인 분석

실험 결과는 SPICE에서 기대한 공통 소스 증폭기 동작과 일치하지 않았다. 그 이유는 SPICE가 이상적인 wiring, 정확한 device connection, 안정적인 biasing, 정확한 MOSFET model을 가정하기 때문이다.

반면 실제 breadboard 실험에서는 다음 요인들이 결과에 영향을 줄 수 있다.

1. **Incorrect pin connection:** Gate, drain, source 연결이 잘못되면 MOSFET이 정상적으로 동작하지 않을 수 있다.
2. **Unstable bias point:** DC operating point가 saturation region에 위치하지 않으면 small-signal 증폭이 불가능하다.
3. **Function generator offset setting:** DC offset이 제대로 들어가지 않으면 gate voltage가 낮아져 MOSFET이 거의 turn-on되지 않을 수 있다.
4. **Oscilloscope coupling mode:** AC/DC coupling 설정이나 vertical scale 설정이 적절하지 않으면 작은 신호가 보이지 않을 수 있다.
5. **Breadboard parasitic effects:** 브레드보드의 기생 저항, 기생 커패시턴스, 접촉 불량이 측정값에 영향을 줄 수 있다.
6. **Power MOSFET 특성:** 13N10은 power MOSFET이므로 5V supply와 20mV small-signal 조건에서 실험용 small-signal 증폭기로 다루기 어려울 수 있다.

---

## 5. 🔍 트러블슈팅 및 고찰 (Error Analysis) ⭐

### 5.1 13N10 Power MOSFET의 특성

이번 실험에 사용한 13N10은 power MOSFET이므로 작은 신호 증폭 실험에 이상적인 소자가 아닐 수 있다. Power MOSFET은 일반적으로 충분한 gate bias가 필요하고, threshold voltage 역시 소자마다 차이가 있을 수 있다.

Experiment 2의 입력 신호는 20mV로 매우 작았기 때문에 DC operating point가 적절히 설정되지 않았다면 출력에서 변화가 거의 나타나지 않았을 가능성이 있다.

---

### 5.2 DC Bias Point 미확보

Common-source amplifier는 AC small-signal을 인가하기 전에 MOSFET을 saturation region에 bias시켜야 한다.

만약 MOSFET이 거의 off 상태라면 $V_{out}$은 $V_{DD}$ 근처에 머무르게 된다. 반대로 MOSFET이 너무 강하게 on 상태라면 $V_{out}$은 0V에 가까워진다. 이 두 경우 모두 output waveform이 제대로 swing할 수 없기 때문에 voltage gain을 측정할 수 없다.

이번 실험에서는 Experiment 1에서 saturation point를 찾지 못했기 때문에 Experiment 2에서 사용할 $V_{DC}$도 결정할 수 없었고, 결과적으로 안정적인 output waveform을 관찰하지 못했다.

---

### 5.3 측정 장비 설정 문제

Function generator는 DC offset과 AC signal을 동시에 제공해야 한다. 만약 DC offset이 빠져 있으면 MOSFET gate voltage가 너무 낮아져 transistor가 켜지지 않을 수 있다.

또한 oscilloscope의 coupling mode와 voltage scale도 중요하다. 입력 신호가 매우 작기 때문에 vertical scale이 적절하지 않으면 실제 신호가 존재하더라도 화면상에서는 거의 변화가 없는 것처럼 보일 수 있다.

---

### 5.4 배선 및 핀 연결 문제

공통 소스 증폭기에서는 각 단자가 다음과 같이 연결되어야 한다.

| MOSFET 단자 | 연결 위치 |
| :--- | :--- |
| Gate | $V_{in}$ |
| Drain | $R_D$ 및 $V_{out}$ |
| Source | Ground |

만약 drain과 source가 뒤바뀌거나 gate bias가 제대로 들어가지 않으면 회로는 기대한 증폭기처럼 동작하지 않는다.

---

## 6. 🛠 개선 방안

이번 실험을 개선하기 위해서는 먼저 DC operating point를 안정적으로 잡는 과정이 필요하다.

1. **$V_{out,DC}$를 먼저 관찰하면서 $V_{DC}$ 조정**
   * $V_{DC}$를 천천히 조절하면서 $V_{out,DC}$가 약 2V~3V가 되도록 맞춘다.
   * 이 구간은 출력이 위아래로 swing할 여유가 있어 small-signal 증폭 관찰에 유리하다.

2. **AC 입력을 나중에 인가**
   * DC bias가 잡힌 뒤에 1kHz AC signal을 추가한다.
   * 처음부터 20mV로 보기 어렵다면 100mVpp 정도로 키워서 동작 여부를 먼저 확인한다.

3. **Oscilloscope 설정 확인**
   * coupling mode가 AC인지 DC인지 확인한다.
   * vertical scale을 작은 신호가 보이도록 조정한다.
   * 입력과 출력을 동시에 관찰하여 phase inversion 여부를 확인한다.

4. **MOSFET pinout 재확인**
   * 13N10의 gate, drain, source 방향을 datasheet 기준으로 다시 확인한다.
   * breadboard에서 drain-source가 뒤바뀌지 않았는지 점검한다.

5. **SPICE와 동일한 조건으로 재측정**
   * SPICE에서 사용한 $V_{DC}$, $R_D$, 입력 amplitude, frequency를 실제 실험에 맞게 동일하게 설정한다.
   * 시뮬레이션에서 먼저 동작 가능한 bias point를 찾고, 그 값을 실제 실험의 시작점으로 사용한다.

---

## 7. ✅ 결론 및 느낀 점

* 이번 실험에서는 13N10 NMOS transistor를 이용하여 common-source amplifier를 구성하고, DC sweep과 small-signal 증폭 동작을 확인하고자 하였다.
* Experiment 1에서는 $V_{in}$을 0V부터 5V까지 변화시키며 $V_{out}$을 측정하고, 이를 통해 $V_{DS}$와 $I_{DS}$를 계산하여 saturation point를 찾고자 하였다.
* 그러나 측정 결과에서 신뢰할 수 있는 $I_{DS}-V_{DS}$ curve를 얻지 못했고, saturation point를 실험적으로 추출하지 못하였다.
* Experiment 2에서는 Experiment 1에서 찾은 saturation point를 기준으로 $V_{DC}$를 설정하고 1kHz, 20mV small-signal input을 인가해야 했지만, valid bias point를 얻지 못했기 때문에 output waveform도 제대로 관찰되지 않았다.
* 따라서 voltage gain, $g_m$, $V_{TH}$ 등 주요 parameter를 정량적으로 추출하지 못하였다.
* SPICE에서는 MOSFET이 saturation region에 bias되면 $A_v\approx -g_mR_D$에 따라 입력에 대해 반전된 amplified output이 나타날 것으로 예상되었다.
* 하지만 실제 실험에서는 DC bias point 설정 실패, power MOSFET의 특성, function generator offset 설정, oscilloscope scale, pin connection, breadboard parasitic effect 등이 영향을 주어 기대한 결과를 얻지 못했다.
* 결과적으로 이번 실험을 통해 common-source amplifier에서 가장 중요한 것은 AC 신호를 넣기 전 **적절한 DC operating point를 먼저 확보하는 것**임을 확인하였다.
* 즉, MOSFET이 saturation region에서 안정적으로 bias되지 않으면 small-signal amplifier로 동작할 수 없고, gain 또한 신뢰성 있게 측정할 수 없다는 점을 이해할 수 있었다.

---

*본 문서는 2022067101 윤희찬의 Week 11 MOSFET(1) 실습 데이터를 기반으로 작성되었습니다.*
