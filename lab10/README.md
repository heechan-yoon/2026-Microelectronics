# ⚡ [Week 13] MOSFET(3) 증폭기 회로 분석

> **과목명:** 2026-1 전자회로1 실습  
> **실험 일자:** 2026.05.26 (Week 13)  
> **실험 주제:** MOSFET(3) / MOSFET Amplifier Circuits  
> **사용 소자:** NMOS Transistor  

---

## 1. 🎯 프로젝트 목표

* **Experiment 1:** MOSFET 증폭기 회로에서 DC bias point를 설정하고, transient 입력에 대한 출력 waveform을 관찰.
* **DC bias 설정:** $V_{in}$을 조정하여 $V_{out}$이 약 $5V$가 되는 동작점을 찾음.
* **전압 이득 측정:** 입력 신호 약 $100mV_{pp}$에 대해 출력 peak-to-peak voltage를 측정하고 voltage gain을 계산.
* **Experiment 2:** Coupling capacitor와 source follower stage가 포함된 회로에서 증폭 및 신호 전달 특성을 확인.
* **SPICE와 비교:** SPICE simulation에서 얻은 bias point 및 gain과 실제 측정 결과를 비교.
* **오차 원인 분석:** 저항 오차, MOSFET parameter variation, breadboard parasitic effect, 측정 장비 오차가 결과에 미치는 영향을 분석.

---

## 2. 🧱 Experiment 1: Circuit 1 MOSFET Amplifier 측정

### 📊 측정 조건 (Setup)

* **회로 구조:** Circuit 1 MOSFET amplifier
* **입력 위치:** Source 입력
* **출력 위치:** Drain 출력
* **동작 방식:** Common-gate amplifier 형태
* **목표 DC output:** $V_{out} \approx 5V$
* **SPICE sweep 범위:** $V_{in}=0V \sim 4V$
* **선정된 bias point:** $V_{in1}=2.86V$
* **Drain current:** $I_{D1}=0.5mA$
* **Transient frequency:** 100Hz
* **입력 신호 크기:** 약 $100mV_{pp}$

---

### 📷 실험 사진

<img width="706" height="706" alt="실험1오프셋회로도" src="https://github.com/user-attachments/assets/d9172fa1-add0-48f4-9e0f-741abe5ae30e" />

<img width="689" height="689" alt="실험1오프셋" src="https://github.com/user-attachments/assets/96f9ca11-bf06-4c80-99c7-7e56b3e5d026" />

<img width="692" height="691" alt="실험1파형회로도" src="https://github.com/user-attachments/assets/40cf7928-c3ab-425a-a96a-be207ccf2b69" />

<img width="680" height="680" alt="실험1파형" src="https://github.com/user-attachments/assets/58691ac8-4f5e-46e0-a9fc-48535b4f2cdd" />

---

### 📐 이론적 배경

Circuit 1은 입력이 source에 인가되고 출력이 drain에서 측정되는 구조이므로 **common-gate amplifier**로 해석할 수 있다.

Common-gate amplifier에서는 gate가 AC ground에 가깝게 고정되고, source에 입력 신호가 들어간다. 이때 drain current의 변화가 drain resistor에 전압 변화를 만들고, drain node에서 증폭된 출력 신호가 나타난다.

Common-gate amplifier의 small-signal voltage gain은 대략 다음과 같이 표현할 수 있다.

$$
A_v \approx g_m R_D
$$

따라서 transconductance $g_m$가 충분하고 drain resistor가 적절히 설정되어 있으면 입력보다 큰 출력 전압을 얻을 수 있다.

또한 DC bias point는 출력 신호가 위아래로 충분히 swing할 수 있도록 설정해야 한다. 이번 실험에서는 $V_{out}$이 약 $5V$가 되도록 $V_{in}$을 조정하였다.

---

### 📊 Experiment 1 결과

SPICE simulation에서 $V_{in}$을 0V부터 4V까지 sweep한 결과, Circuit 1에서는 $V_{out}\approx5V$가 되는 지점이 $V_{in1}=2.86V$로 나타났다.

Transient 실험에서는 100Hz 입력 신호를 인가하였고, 측정된 출력 peak-to-peak voltage는 약 $2.52V_{pp}$였다. 입력 신호가 약 $100mV_{pp}$였으므로 voltage gain은 다음과 같이 계산된다.

$$
A_{v1}=\frac{2.52V_{pp}}{0.1V_{pp}}=25.2
$$

| 항목 | 측정 / 계산값 |
| :--- | :--- |
| $V_{in1}$ | 2.86V |
| $I_{D1}$ | 0.5mA |
| $g_m$ | 2.52mS |
| Output peak-to-peak voltage | 약 $2.52V_{pp}$ |
| Input peak-to-peak voltage | 약 $100mV_{pp}$ |
| Voltage gain $A_{v1}$ | 25.2 |

> **Note:** Circuit 1은 약 25배의 전압 이득을 보였으며, 이는 common-gate amplifier에서 기대되는 전압 증폭 특성과 잘 맞는다.

---

## 3. 🧪 Experiment 2: Coupling Capacitor 및 Source Follower 포함 회로 측정

### 📊 측정 조건 (Setup)

* **회로 구조:** Circuit 2 MOSFET amplifier with coupling capacitor and source follower stage
* **Coupling capacitor:** $100\mu F$
* **Gate resistor:** $R_G=10k\Omega$
* **Source resistor:** $R_S=1k\Omega$
* **목표 DC output:** $V_{out} \approx 5V$
* **선정된 bias point:** $V_{in2}=1.70V$
* **Drain current:** $I_{D2}\approx5.0mA$
* **Transient frequency:** 100Hz
* **입력 신호 크기:** 약 $100mV_{pp}$

---

### 📷 실험 사진

<img width="674" height="674" alt="실험2오프셋회로도" src="https://github.com/user-attachments/assets/8ad8bcf2-d9f3-42e3-a726-4323c2cc2bed" />

<img width="673" height="673" alt="실험2오프셋" src="https://github.com/user-attachments/assets/c3d0c331-4ec6-4c16-b203-b6d15292ab7c" />

<img width="678" height="678" alt="실험2파형회로도" src="https://github.com/user-attachments/assets/cff54a61-c04a-4529-8c7a-cb2ff91f6220" />

<img width="667" height="667" alt="실험2파형" src="https://github.com/user-attachments/assets/67304605-abde-4055-b626-72c1d9ec78e7" />

---

### 📐 이론적 배경

Circuit 2는 coupling capacitor와 source follower stage가 추가된 구조이다.

Coupling capacitor는 DC 성분을 차단하고 AC 신호만 다음 stage로 전달하는 역할을 한다. 이때 capacitor와 입력 저항이 high-pass filter를 형성하므로 cutoff frequency가 충분히 낮아야 원하는 주파수의 AC 신호가 감쇠 없이 전달된다.

Cutoff frequency는 다음과 같이 표현할 수 있다.

$$
f_c=\frac{1}{2\pi R_G C}
$$

이번 실험에서는 $C=100\mu F$, $R_G=10k\Omega$이므로 cutoff frequency가 매우 낮다. 따라서 100Hz 입력 신호에서는 coupling capacitor에 의한 감쇠가 거의 발생하지 않는다.

또한 source follower stage는 voltage gain이 보통 1에 가깝거나 그보다 작지만, output impedance를 낮추고 다음 stage를 구동하기 쉽게 만드는 역할을 한다.

---

### 📊 Experiment 2 결과

SPICE simulation에서 Circuit 2는 $V_{in2}=1.70V$일 때 $V_{out}\approx5V$가 되는 것으로 나타났다. Circuit 2의 output node는 $R_S=1k\Omega$에 연결되어 있으므로 drain current는 다음과 같이 추정되었다.

$$
I_{D2}\approx5.0mA
$$

Transient 실험에서는 100Hz 입력 신호를 인가하였고, 측정된 출력 peak-to-peak voltage는 약 $2.58V_{pp}$였다. 입력 신호가 약 $100mV_{pp}$였으므로 voltage gain은 다음과 같이 계산된다.

$$
A_{v2}=\frac{2.58V_{pp}}{0.1V_{pp}}=25.8
$$

| 항목 | 측정 / 계산값 |
| :--- | :--- |
| $V_{in2}$ | 1.70V |
| $I_{D2}$ | 5.0mA |
| $g_m$ | 2.52mS |
| Coupling capacitor | $100\mu F$ |
| $R_G$ | $10k\Omega$ |
| Output peak-to-peak voltage | 약 $2.58V_{pp}$ |
| Input peak-to-peak voltage | 약 $100mV_{pp}$ |
| Voltage gain $A_{v2}$ | 25.8 |

> **Note:** $100\mu F$ coupling capacitor는 100Hz에서 충분히 큰 capacitance로 동작하였기 때문에 AC 신호를 거의 감쇠 없이 전달하였다. 그 결과 Circuit 2의 output waveform은 Circuit 1과 유사한 증폭 특성을 보였다.

---

## 4. 📊 주요 측정 결과 정리

| $V_{in}$ | $g_m$ | $I_{D1}$ | $I_{D2}$ | $A_{v1}$ | $A_{v2}$ |
| :--- | :--- | :--- | :--- | :--- | :--- |
| $V_{in1}=2.86V,\ V_{in2}=1.70V$ | 2.52mS | 0.5mA | 5.0mA | 25.2 | 25.8 |

### 📉 결과 해석

| 측정 조건 | 관찰 내용 | 결과 요약 |
| :--- | :--- | :--- |
| Circuit 1 | $V_{in1}=2.86V$에서 $V_{out}\approx5V$ | 적절한 DC bias point 확보 |
| Circuit 2 | $V_{in2}=1.70V$에서 $V_{out}\approx5V$ | source follower 및 coupling capacitor 포함 조건에서 bias 설정 |
| 100Hz transient | 두 회로 모두 약 $2.5V_{pp}$ 출력 | 약 25배 수준의 voltage gain 확인 |
| $100\mu F$ capacitor | 100Hz에서 감쇠가 거의 없음 | Circuit 2의 waveform이 Circuit 1과 유사하게 나타남 |
| 오차 요인 | 실제 소자 및 측정 환경의 비이상성 | SPICE와 완전히 동일하지는 않음 |

---

## 5. 🧪 SPICE 결과와 실험 결과 비교

### 📌 SPICE에서 기대되는 동작

SPICE simulation에서는 $V_{in}$을 0V부터 4V까지 sweep하여 $V_{out}$이 약 $5V$가 되는 DC operating point를 먼저 찾았다.

* Circuit 1: $V_{in}=2.86V$에서 $V_{out}\approx5V$
* Circuit 2: $V_{in}=1.70V$에서 $V_{out}\approx5V$

이러한 bias point는 output signal이 clipping 없이 위아래로 swing할 수 있도록 하기 위한 조건이다.

Transient simulation에서는 두 회로 모두 선택된 DC operating point 주변에서 voltage amplification이 나타날 것으로 예상되었다. 실제 실험에서도 두 회로 모두 약 25배 수준의 전압 이득이 측정되어 SPICE에서 기대한 증폭 동작과 유사한 결과를 보였다.

---

### 📊 비교 요약

| Item | SPICE expectation | Experimental result |
| :--- | :--- | :--- |
| DC sweep | $V_{out}\approx5V$가 되는 $V_{in}$ 선택 | Circuit 1: 2.86V, Circuit 2: 1.70V |
| Circuit 1 drain current | $I_{D1}=0.5mA$ | 0.5mA 수준으로 계산 |
| Circuit 2 drain current | $I_{D2}\approx5.0mA$ | 5.0mA 수준으로 추정 |
| Transient output | 선택된 bias point에서 전압 증폭 발생 | Circuit 1: $2.52V_{pp}$, Circuit 2: $2.58V_{pp}$ |
| Voltage gain | 큰 전압 이득 예상 | $A_{v1}=25.2$, $A_{v2}=25.8$ |
| Coupling capacitor effect | 100Hz에서 감쇠 거의 없음 | Circuit 2 waveform이 Circuit 1과 유사 |

---

### 🔍 차이 원인 분석

실험 결과는 SPICE simulation에서 기대한 MOSFET amplifier의 증폭 특성과 비교적 유사하였다. 그러나 실제 회로에서는 다음과 같은 요인들로 인해 small difference가 발생할 수 있다.

1. **Resistor tolerance**
   * 실제 저항값은 nominal value와 완전히 일치하지 않을 수 있다.
   * 이로 인해 drain current, bias point, voltage gain이 달라질 수 있다.

2. **MOSFET parameter variation**
   * 실제 MOSFET의 threshold voltage와 transconductance는 SPICE model과 다를 수 있다.
   * 특히 $V_{TH}$와 $g_m$ 차이는 bias point와 output amplitude에 직접적인 영향을 준다.

3. **Breadboard parasitic effects**
   * Breadboard의 parasitic capacitance, contact resistance, wiring resistance가 waveform에 영향을 줄 수 있다.

4. **Measurement error**
   * Function generator의 input amplitude와 oscilloscope에서 측정한 peak-to-peak value에는 작은 오차가 포함될 수 있다.
   * Probe 접촉 상태나 scale 설정에 따라서도 측정값이 달라질 수 있다.

5. **Coupling capacitor의 실제 특성**
   * Circuit 2에서 사용한 $100\mu F$ capacitor는 100Hz에서 충분히 큰 값이지만, 실제 capacitor의 tolerance나 ESR에 따라 작은 차이가 발생할 수 있다.

---

## 6. 🔍 트러블슈팅 및 고찰 (Error Analysis) ⭐

### 6.1 DC Bias Point 설정의 중요성

이번 실험에서 가장 중요한 과정은 두 회로 모두 $V_{out}$이 약 $5V$가 되도록 $V_{in}$을 조정하는 것이었다.

이는 $V_{DD}$가 약 $10V$일 때 output node를 중간 전압 근처에 위치시켜 출력 신호가 위아래로 swing할 수 있도록 하기 위함이다. 만약 bias point가 $V_{DD}$나 ground에 너무 가까우면 output waveform은 clipping되거나 심하게 왜곡될 수 있다.

따라서 MOSFET amplifier에서는 transient 측정보다 먼저 DC operating point를 안정적으로 설정해야 한다.

---

### 6.2 Circuit 1의 Common-Gate Amplifier 특성

Circuit 1은 source에 입력을 인가하고 drain에서 출력을 측정하는 common-gate amplifier로 동작한다.

Common-gate amplifier에서는 small-signal voltage gain이 주로 $g_mR_D$에 의해 결정된다.

$$
A_v \approx g_mR_D
$$

이번 실험에서 Circuit 1의 gain은 약 25.2로 계산되었으며, 이는 선택된 DC operating point에서 충분한 전압 증폭이 이루어졌음을 보여준다.

---

### 6.3 Circuit 2의 Coupling Capacitor와 Source Follower 영향

Circuit 2는 coupling capacitor와 source follower stage를 포함한다.

Coupling capacitor는 DC 성분을 차단하여 이전 stage의 DC bias가 다음 stage에 직접 전달되지 않도록 하고, AC 신호만 전달한다. 이번 실험에서 사용한 $100\mu F$ capacitor는 충분히 큰 값이므로, $R_G=10k\Omega$와 함께 형성하는 cutoff frequency가 매우 낮다.

따라서 100Hz 입력 신호에서는 capacitor에 의한 감쇠가 거의 없었고, output waveform도 Circuit 1과 유사하게 나타났다.

Source follower stage는 voltage gain을 크게 만들기보다는 output impedance를 낮추고 다음 stage를 안정적으로 구동할 수 있도록 도와주는 역할을 한다. 따라서 전체 회로의 신호 전달과 구동 능력을 개선하는 데 의미가 있다.

---

### 6.4 측정 오차 및 비이상적 요인

실험에서 측정된 gain은 SPICE와 완전히 동일하지 않을 수 있다. 그 이유는 실제 회로가 ideal simulation과 다르기 때문이다.

* 실제 저항값 오차
* MOSFET threshold voltage 차이
* MOSFET transconductance 차이
* Breadboard parasitic capacitance
* Contact resistance
* Function generator amplitude 오차
* Oscilloscope peak-to-peak 측정 오차

이러한 요인들이 합쳐져 DC bias point와 output amplitude에 작은 차이를 만들 수 있다.

---

## 7. 🛠 개선 방안

이번 실험을 더 정확하게 수행하기 위해서는 다음과 같은 개선이 필요하다.

1. **실제 저항값 측정 후 SPICE 반영**
   * Multimeter로 실제 사용한 저항값을 측정하고, 그 값을 SPICE simulation에 반영하면 비교 정확도가 높아진다.

2. **DC bias point 세밀 조정**
   * $V_{out}$이 정확히 $5V$ 근처가 되도록 $V_{in}$을 천천히 조정한다.
   * Bias point가 조금만 변해도 gain과 output amplitude가 달라질 수 있다.

3. **Input amplitude 정확히 확인**
   * Function generator에서 설정한 $100mV_{pp}$가 실제 회로 입력단에서 동일하게 나타나는지 oscilloscope로 확인한다.

4. **Oscilloscope scale 및 coupling mode 확인**
   * 입력과 출력을 동시에 관찰하여 phase 관계와 gain을 정확하게 비교한다.
   * Vertical scale, coupling mode, probe setting을 동일 조건으로 맞춘다.

5. **Capacitor 영향 추가 확인**
   * Circuit 2에서 주파수를 변화시키며 coupling capacitor가 저주파 신호를 얼마나 감쇠시키는지 확인하면 high-pass 특성을 더 명확하게 분석할 수 있다.

---

## 8. ✅ 결론 및 느낀 점

* 이번 실험에서는 MOSFET amplifier의 두 가지 회로를 구성하고, DC bias point 설정과 transient response를 통해 voltage amplification을 확인하였다.
* Circuit 1에서는 $V_{in1}=2.86V$일 때 $V_{out}\approx5V$가 되었고, drain current는 $I_{D1}=0.5mA$로 계산되었다.
* Circuit 2에서는 $V_{in2}=1.70V$일 때 $V_{out}\approx5V$가 되었고, $R_S=1k\Omega$를 기준으로 $I_{D2}\approx5.0mA$로 추정되었다.
* 100Hz transient 실험에서 Circuit 1의 output peak-to-peak voltage는 약 $2.52V_{pp}$, Circuit 2는 약 $2.58V_{pp}$로 측정되었다.
* 입력 신호가 약 $100mV_{pp}$였기 때문에 voltage gain은 각각 $A_{v1}=25.2$, $A_{v2}=25.8$로 계산되었다.
* 두 회로 모두 선택된 DC operating point 주변에서 충분한 voltage amplification을 보였다.
* Circuit 2에서 사용한 $100\mu F$ coupling capacitor는 $R_G=10k\Omega$와 함께 매우 낮은 cutoff frequency를 만들기 때문에, 100Hz에서는 AC 신호를 거의 감쇠시키지 않았다.
* 실험 결과는 SPICE simulation에서 예상한 증폭 동작과 비교적 유사하였으며, 작은 차이는 저항 오차, MOSFET parameter variation, breadboard parasitic effect, 측정 장비 오차 등으로 설명할 수 있다.
* 결과적으로 이번 실험을 통해 MOSFET amplifier에서 **적절한 DC bias point 설정**, **common-gate amplifier의 전압 이득**, **coupling capacitor의 AC 전달 역할**, **source follower의 구동 능력 개선 효과**를 이해할 수 있었다.

---

*본 문서는 2022067101 윤희찬의 Week 13 MOSFET(3) 실습 데이터를 기반으로 작성되었습니다.*
