# ⚡ [Week 14] OP Amp Differentiator 및 Integrator 회로 분석

> **과목명:** 2026-1 전자회로1 실습  
> **실험 일자:** 2026.06.02 (Week 14)  
> **실험 주제:** Differentiator & Integrator OP Amp Application  
> **사용 소자:** Operational Amplifier  

---

## 1. 🎯 프로젝트 목표

* **Experiment 1:** OP Amp differentiator 회로를 구성하고, ramp input voltage에 대한 pulse-shaped output voltage를 관찰.
* **미분기 동작 확인:** 입력 신호의 기울기가 양수 또는 음수일 때 출력 전압의 극성이 어떻게 변화하는지 분석.
* **Experiment 2:** OP Amp integrator 회로를 구성하고, square input voltage에 대한 ramp-shaped output voltage를 관찰.
* **적분기 동작 확인:** 입력 전압의 부호에 따라 출력 전압의 기울기가 어떻게 달라지는지 분석.
* **Capacitance 변화 비교:** $C=1\mu F$와 $C=10\mu F$ 조건에서 출력 waveform의 amplitude와 기울기 변화를 비교.
* **SPICE와 비교:** 실제 breadboard 측정 결과와 SPICE transient simulation 결과의 유사점과 차이점을 분석.
* **오차 원인 분석:** OP Amp의 non-ideal characteristic, resistor 및 capacitor tolerance, breadboard wiring condition, 측정 장비 오차가 waveform에 미치는 영향을 분석.

---

## 2. 🧱 Experiment 1: OP Amp Differentiator 회로 분석

### 📊 측정 조건 (Setup)

* **회로 구조:** OP Amp Differentiator
* **입력 신호:** Ramp waveform
* **출력 신호:** Pulse-shaped waveform
* **Capacitor 조건:** $C=1\mu F,\ 10\mu F$
* **관찰 항목:** 입력 기울기 변화에 따른 출력 전압의 크기 및 극성
* **목표:** 입력 전압의 시간 미분값이 출력에 반영되는지 확인

---

### 📷 실험 사진

<img width="743" height="742" alt="미분기회로" src="https://github.com/user-attachments/assets/a5fc9f22-47fc-42cb-93fb-3f6315f77e1c" />

<img width="721" height="720" alt="1uF미분기" src="https://github.com/user-attachments/assets/6af4c6d2-02a4-4e03-a945-c194407911a0" />

<img width="733" height="733" alt="10uF미분ㄱ디" src="https://github.com/user-attachments/assets/7ae0661b-7c89-42c4-9eb3-e6bf97e4faa2" />

---

### 📐 이론적 배경

OP Amp differentiator는 입력 전압의 시간에 따른 변화율을 출력으로 나타내는 회로이다.

Differentiator의 출력 전압은 다음 식으로 표현된다.

$$
V_{out}(t)=-RC\frac{dV_{in}(t)}{dt}
$$

입력 전압이 일정한 기울기로 증가하면 $\frac{dV_{in}}{dt}$는 양수가 된다.  
이때 output voltage는 음수로 나타난다.

반대로 입력 전압이 일정한 기울기로 감소하면 $\frac{dV_{in}}{dt}$는 음수가 된다.  
이때 output voltage는 양수로 나타난다.

따라서 ramp-shaped input signal을 differentiator 회로에 인가하면, 출력은 입력 기울기의 방향에 따라 극성이 바뀌는 pulse-shaped waveform으로 나타난다.

```text
Ramp Input Voltage
 ├─ Positive Slope
 │   └─ Negative Output Pulse
 │
 └─ Negative Slope
     └─ Positive Output Pulse
```

---

### 📊 Experiment 1 결과

실험에서는 ramp input waveform을 differentiator 회로에 인가하고, $C=1\mu F$와 $C=10\mu F$ 조건에서 출력 waveform을 관찰하였다.

두 조건 모두에서 입력 신호의 기울기가 양수일 때 output voltage는 음수 방향으로 나타났고, 입력 신호의 기울기가 음수일 때 output voltage는 양수 방향으로 나타났다.

즉, ramp input voltage가 pulse-like output voltage로 변환되는 것을 확인하였다.

| 입력 신호 상태 | $\frac{dV_{in}}{dt}$ 부호 | 출력 전압 극성 | 관찰 결과 |
| :--- | :--- | :--- | :--- |
| Ramp voltage 증가 | Positive | Negative | 음의 pulse 출력 |
| Ramp voltage 감소 | Negative | Positive | 양의 pulse 출력 |
| 일정한 입력 구간 | 약 0 | 약 0 | 출력 변화가 작음 |

---

### 📉 Capacitor 변화에 따른 이론적 영향

Differentiator의 출력 전압은 다음 식에 따라 capacitor 값에 비례한다.

$$
|V_{out}(t)|=RC\left|\frac{dV_{in}(t)}{dt}\right|
$$

따라서 동일한 input slope와 resistor 조건에서 capacitor 값이 증가하면 출력 amplitude의 절댓값도 증가할 수 있다.

| Capacitor | 이론적 영향 | 해석 |
| :--- | :--- | :--- |
| $1\mu F$ | 기준 출력 amplitude | 입력 기울기에 비례하는 pulse 출력 |
| $10\mu F$ | 더 큰 출력 amplitude 예상 | $RC$ 값 증가로 미분 출력 크기 증가 가능 |

> **Note:** 실제 회로에서는 OP Amp의 output-voltage limitation, slew rate, bandwidth 등의 영향으로 인해 이론적인 비례 관계가 완벽하게 나타나지 않을 수 있다.

---

## 3. 🧪 Experiment 2: OP Amp Integrator 회로 분석

### 📊 측정 조건 (Setup)

* **회로 구조:** OP Amp Integrator
* **입력 신호:** Square waveform
* **출력 신호:** Ramp-shaped waveform
* **Capacitor 조건:** $C=1\mu F,\ 10\mu F$
* **관찰 항목:** 입력 전압의 부호에 따른 출력 전압 기울기 변화
* **목표:** 입력 전압의 시간 적분값이 출력에 반영되는지 확인

---

### 📷 실험 사진

<img width="733" height="734" alt="적분기회로" src="https://github.com/user-attachments/assets/6ee87e1a-95e9-4477-a17b-b9dc53f38b63" />

<img width="735" height="735" alt="1uF적분기" src="https://github.com/user-attachments/assets/46b4a5b6-0d6e-4af4-bfa2-8f56cf854b6e" />

<img width="741" height="741" alt="10uF적분기" src="https://github.com/user-attachments/assets/5a9a6022-d64b-42d7-bceb-105fe36af3c7" />

---

### 📐 이론적 배경

OP Amp integrator는 입력 전압을 시간에 대해 적분한 값을 출력으로 나타내는 회로이다.

Integrator의 출력 전압은 다음 식으로 표현된다.

$$
V_{out}(t)=-\frac{1}{RC}\int V_{in}(t)\,dt
$$

입력 전압이 일정한 양의 값을 유지하면 출력 전압은 시간에 따라 선형적으로 감소한다.

반대로 입력 전압이 일정한 음의 값을 유지하면 출력 전압은 시간에 따라 선형적으로 증가한다.

따라서 square input voltage를 integrator 회로에 인가하면, 출력은 일정한 기울기를 가지는 ramp-shaped waveform으로 나타난다.

```text
Square Input Voltage
 ├─ Positive Input Level
 │   └─ Linearly Decreasing Output
 │
 └─ Negative Input Level
     └─ Linearly Increasing Output
```

출력 전압의 기울기는 다음과 같이 표현할 수 있다.

$$
\frac{dV_{out}(t)}{dt}=-\frac{V_{in}(t)}{RC}
$$

---

### 📊 Experiment 2 결과

실험에서는 square input waveform을 integrator 회로에 인가하고, $C=1\mu F$와 $C=10\mu F$ 조건에서 출력 waveform을 관찰하였다.

두 조건 모두에서 square input voltage가 ramp-shaped output voltage로 변환되는 것을 확인하였다.

입력 전압이 양의 값을 유지하는 동안 output voltage는 선형적으로 감소하였고, 입력 전압이 음의 값을 유지하는 동안 output voltage는 선형적으로 증가하였다.

| 입력 신호 상태 | $V_{in}$ 부호 | 출력 전압 변화 | 관찰 결과 |
| :--- | :--- | :--- | :--- |
| Positive input level | Positive | 선형 감소 | 음의 기울기를 갖는 ramp 출력 |
| Negative input level | Negative | 선형 증가 | 양의 기울기를 갖는 ramp 출력 |
| Square waveform 반복 | 주기적 변화 | 증가와 감소 반복 | Triangle-like waveform 출력 |

---

### 📉 Capacitor 변화에 따른 이론적 영향

Integrator의 출력 기울기는 다음 식에 따라 capacitor 값에 반비례한다.

$$
\left|\frac{dV_{out}(t)}{dt}\right|=\frac{|V_{in}(t)|}{RC}
$$

따라서 동일한 input amplitude와 resistor 조건에서 capacitor 값이 증가하면 출력 ramp의 기울기는 작아진다.

| Capacitor | 이론적 영향 | 해석 |
| :--- | :--- | :--- |
| $1\mu F$ | 상대적으로 큰 ramp slope | 출력 전압의 증가 및 감소가 비교적 빠름 |
| $10\mu F$ | 상대적으로 작은 ramp slope | 출력 전압의 증가 및 감소가 완만함 |

> **Note:** $C=10\mu F$ 조건에서는 $RC$ time constant가 증가하므로 같은 시간 동안 output voltage의 변화량이 더 작게 나타날 수 있다.

---

## 4. 📊 주요 측정 결과 정리

| 회로 | 입력 waveform | 출력 waveform | $C=1\mu F$ | $C=10\mu F$ |
| :--- | :--- | :--- | :--- | :--- |
| Differentiator | Ramp waveform | Pulse-shaped waveform | 입력 기울기에 따른 pulse 출력 확인 | 입력 기울기에 따른 pulse 출력 확인 |
| Integrator | Square waveform | Ramp-shaped waveform | 비교적 빠른 ramp 변화 확인 | 비교적 완만한 ramp 변화 확인 |

### 📉 결과 해석

| 측정 조건 | 관찰 내용 | 결과 요약 |
| :--- | :--- | :--- |
| Differentiator | Ramp input에 대해 pulse-like output 출력 | 입력 신호의 기울기가 출력에 반영됨 |
| Positive input slope | Negative output voltage 발생 | Inverting differentiator 특성 확인 |
| Negative input slope | Positive output voltage 발생 | Inverting differentiator 특성 확인 |
| Integrator | Square input에 대해 ramp-shaped output 출력 | 입력 신호의 적분 결과가 출력에 반영됨 |
| Positive input level | Output voltage 선형 감소 | Inverting integrator 특성 확인 |
| Negative input level | Output voltage 선형 증가 | Inverting integrator 특성 확인 |
| Capacitor 변화 | Output amplitude 및 ramp slope 변화 | $RC$ 값이 회로 응답에 영향을 줌 |

---

## 5. 🧪 SPICE 결과와 실험 결과 비교

### 📌 SPICE에서 기대되는 동작

SPICE simulation에서는 differentiator 회로에 ramp input voltage를 인가했을 때 pulse-shaped output voltage가 나타날 것으로 예상하였다.

입력 전압의 기울기가 양수인 경우 출력 전압은 음수 방향으로 나타나고, 입력 전압의 기울기가 음수인 경우 출력 전압은 양수 방향으로 나타난다.

이는 다음 이론식과 일치한다.

$$
V_{out}(t)=-RC\frac{dV_{in}(t)}{dt}
$$

Integrator 회로에서는 square input voltage를 인가했을 때 ramp-shaped output voltage가 나타날 것으로 예상하였다.

입력 전압이 양수인 동안 출력 전압은 감소하고, 입력 전압이 음수인 동안 출력 전압은 증가한다.

이는 다음 이론식과 일치한다.

$$
V_{out}(t)=-\frac{1}{RC}\int V_{in}(t)\,dt
$$

---

### 📊 비교 요약

| Item | SPICE expectation | Experimental result |
| :--- | :--- | :--- |
| Differentiator input | Ramp waveform | Ramp waveform 인가 |
| Differentiator output | Pulse-shaped waveform | Pulse-like output waveform 확인 |
| Positive input slope | Negative output voltage | 음의 output pulse 확인 |
| Negative input slope | Positive output voltage | 양의 output pulse 확인 |
| Integrator input | Square waveform | Square waveform 인가 |
| Integrator output | Ramp-shaped waveform | Ramp-shaped output waveform 확인 |
| Positive input level | Output voltage 선형 감소 | 선형 감소 경향 확인 |
| Negative input level | Output voltage 선형 증가 | 선형 증가 경향 확인 |
| Waveform sharpness | Ideal waveform 예상 | 실제 측정에서는 일부 차이 발생 가능 |
| Output amplitude | Simulation 조건에 따른 amplitude | 실제 측정에서는 소자 및 장비 영향으로 차이 발생 가능 |

---

### 🔍 차이 원인 분석

실험 결과는 SPICE simulation과 전반적으로 유사하였다. Differentiator와 integrator 회로 모두 이론적으로 예상한 waveform 변환 특성을 보였다.

그러나 실제 측정 waveform의 sharpness와 amplitude는 이상적인 SPICE 결과와 완전히 일치하지 않을 수 있다.

1. **Limited bandwidth**
   * 실제 OP Amp는 무한한 bandwidth를 가지지 않는다.
   * 급격하게 변하는 입력 신호의 고주파 성분이 완벽하게 전달되지 않을 수 있다.

2. **Finite slew rate**
   * 실제 OP Amp의 output voltage는 무한히 빠르게 변할 수 없다.
   * Pulse edge나 ramp slope가 이상적인 waveform보다 완만하게 나타날 수 있다.

3. **Output-voltage limitation**
   * OP Amp의 출력 전압은 공급 전압 범위를 초과할 수 없다.
   * Differentiator의 출력 amplitude가 큰 경우 clipping이 발생할 수 있다.

4. **Resistor 및 capacitor tolerance**
   * 실제 $R$과 $C$ 값은 nominal value와 완전히 같지 않을 수 있다.
   * 이로 인해 $RC$ time constant와 output amplitude가 달라질 수 있다.

5. **Breadboard wiring condition**
   * Breadboard의 contact resistance, parasitic capacitance, wiring 상태가 회로 응답에 영향을 줄 수 있다.

6. **Measurement equipment noise**
   * Function generator와 oscilloscope의 noise 및 probe 연결 상태에 따라 waveform에 작은 오차가 포함될 수 있다.

---

## 6. 🔍 트러블슈팅 및 고찰 (Error Analysis) ⭐

### 6.1 Differentiator에서 Input Slope의 중요성

Differentiator의 출력은 입력 전압의 절댓값이 아니라 **입력 전압의 변화율**에 의해 결정된다.

따라서 ramp input이 일정하게 증가하는 동안에는 일정한 음의 output voltage가 나타나고, ramp input이 일정하게 감소하는 동안에는 일정한 양의 output voltage가 나타난다.

입력 전압이 빠르게 변화할수록 $\left|\frac{dV_{in}}{dt}\right|$가 커지므로 output pulse의 amplitude도 커질 수 있다.

$$
|V_{out}(t)|=RC\left|\frac{dV_{in}(t)}{dt}\right|
$$

---

### 6.2 Integrator에서 RC Time Constant의 영향

Integrator의 output slope는 $RC$ 값에 의해 결정된다.

$$
\frac{dV_{out}(t)}{dt}=-\frac{V_{in}(t)}{RC}
$$

$RC$ 값이 작으면 output voltage가 빠르게 변화하고, $RC$ 값이 크면 output voltage가 천천히 변화한다.

따라서 $C=10\mu F$ 조건은 $C=1\mu F$ 조건보다 더 완만한 ramp-shaped waveform을 만들 수 있다.

---

### 6.3 실제 OP Amp의 비이상적 특성

이론적인 OP Amp는 infinite gain, infinite bandwidth, zero output impedance를 가진다고 가정한다.

그러나 실제 OP Amp는 limited bandwidth, finite slew rate, output-voltage limitation을 가진다.

이러한 특성은 differentiator에서 pulse edge를 완만하게 만들거나, integrator에서 ramp waveform의 기울기를 이상적인 값과 다르게 만들 수 있다.

---

### 6.4 Breadboard 및 측정 환경의 영향

Breadboard에 회로를 구성하면 배선 길이, 접촉 상태, parasitic capacitance의 영향을 받을 수 있다.

특히 differentiator 회로는 입력 신호의 빠른 변화를 강조하기 때문에 외부 noise에도 민감할 수 있다.

따라서 측정 시 probe ground 연결을 짧게 유지하고, 배선 길이를 최소화하며, capacitor의 polarity와 실제 capacitance를 확인하는 것이 중요하다.

---

## 7. 🛠 개선 방안

이번 실험을 더 정확하게 수행하기 위해서는 다음과 같은 개선이 필요하다.

1. **실제 $R$ 및 $C$ 값 측정**
   * Multimeter 또는 LCR meter로 실제 resistor와 capacitor 값을 확인한다.
   * 측정값을 SPICE simulation에도 반영하면 비교 정확도가 높아진다.

2. **입력 waveform 조건 통일**
   * SPICE와 실제 실험에서 input frequency, amplitude, offset을 동일하게 설정한다.
   * Function generator의 실제 출력값을 oscilloscope로 먼저 확인한다.

3. **Oscilloscope scale 조정**
   * Differentiator pulse와 integrator ramp가 화면에 명확히 나타나도록 vertical scale과 time scale을 조정한다.
   * Input과 output을 동시에 확인하여 polarity와 phase relationship을 비교한다.

4. **OP Amp output clipping 확인**
   * Differentiator에서 capacitor 값이 커질 때 output amplitude가 공급 전압 범위를 넘지 않는지 확인한다.
   * Clipping이 발생하면 입력 amplitude 또는 frequency를 조정한다.

5. **Breadboard wiring 단순화**
   * 배선 길이를 줄이고 접촉 상태를 점검한다.
   * Probe ground를 짧게 연결하여 외부 noise 영향을 줄인다.

6. **주파수 변화 추가 실험**
   * Input frequency를 변화시키면서 differentiator output amplitude와 integrator output slope가 어떻게 변화하는지 비교한다.
   * 이를 통해 $RC$ time constant와 frequency response의 관계를 더 명확하게 확인할 수 있다.

---

## 8. ✅ 결론 및 느낀 점

* 이번 실험에서는 OP Amp differentiator와 integrator 회로를 구성하고, transient input에 대한 output waveform을 관찰하였다.
* Differentiator 회로에서는 ramp input voltage가 pulse-shaped output voltage로 변환되는 것을 확인하였다.
* Ramp input의 기울기가 양수일 때 output voltage는 음수로 나타났고, 입력 기울기가 음수일 때 output voltage는 양수로 나타났다.
* 이러한 결과는 $V_{out}(t)=-RC\frac{dV_{in}(t)}{dt}$ 관계식과 일치한다.
* Integrator 회로에서는 square input voltage가 ramp-shaped output voltage로 변환되는 것을 확인하였다.
* 입력 전압이 양의 값을 유지하는 동안 output voltage는 선형적으로 감소하였고, 입력 전압이 음의 값을 유지하는 동안 output voltage는 선형적으로 증가하였다.
* 이러한 결과는 $V_{out}(t)=-\frac{1}{RC}\int V_{in}(t)\,dt$ 관계식과 일치한다.
* $C=1\mu F$와 $C=10\mu F$ 조건을 비교함으로써 capacitor 값이 differentiator output amplitude와 integrator output slope에 영향을 줄 수 있음을 확인하였다.
* 실제 waveform은 SPICE simulation과 전반적으로 유사하였지만, waveform sharpness와 amplitude에는 작은 차이가 나타날 수 있었다.
* 이러한 차이는 OP Amp의 limited bandwidth, finite slew rate, output-voltage limitation, resistor 및 capacitor tolerance, breadboard wiring condition, 측정 장비 noise 등으로 설명할 수 있다.
* 결과적으로 이번 실험을 통해 OP Amp differentiator와 integrator의 기본 동작 원리와 $RC$ time constant의 영향을 이해할 수 있었다.

---

*본 문서는 2022067101 윤희찬의 Week 14 OP Amp Differentiator 및 Integrator 실습 데이터를 기반으로 작성되었습니다.*
