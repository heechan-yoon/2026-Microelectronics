# ⚡ [Week 12] MOSFET(2) 공통 소스 증폭기 분석

> **과목명:** 2026-1 전자회로1 실습  
> **실험 일자:** 2026.05.19 (Week 12)  
> **실험 주제:** MOSFET(2) / Common-Source Amplifier with Source Degeneration  
> **사용 소자:** NMOS Transistor  

---

## 1. 🎯 프로젝트 목표

* **Experiment 1:** NMOS common-source amplifier에서 $R_D=1k\Omega$와 $R_D=2k\Omega$ 조건에 대해 적절한 DC bias point를 설정.
* **DC offset 확인:** SPICE simulation에서 얻은 bias point를 기준으로 function generator의 DC offset을 조정하고, 실제 실험에서 가능한 bias 조건을 확인.
* **Source resistor 영향 확인:** source resistor $R_S$를 추가하여 negative feedback이 amplifier의 bias 안정성과 voltage gain에 미치는 영향을 분석.
* **Experiment 2:** small-signal input을 인가하여 output waveform이 입력에 대해 반전 및 증폭되는지 확인.
* **Gain 비교:** $R_D$ 값이 증가할 때 voltage gain이 어떻게 변화하는지 분석.
* **SPICE와 비교:** 실제 실험 결과와 SPICE simulation 결과의 유사점과 차이점을 분석.

---

## 2. 🧱 Experiment 1: DC Bias Point 설정

### 📊 측정 조건 (Setup)

* **회로 구조:** NMOS Common-Source Amplifier with Source Degeneration
* **Drain resistor:** $R_D=1k\Omega,\ 2k\Omega$
* **Source resistor:** 설계값 $R_S=250\Omega$
* **실제 사용한 source resistor:** 약 $255\Omega$
* **구성 방법:** $550\Omega$ 저항 2개 병렬 연결
* **목표:** $V_{out}$이 약 5V가 되도록 input DC bias를 설정

> **Note:** 원래 $R_S=250\Omega$를 사용해야 했지만, $500\Omega$ 저항이 없어 $550\Omega$ 저항 2개를 병렬로 연결하였다. 따라서 실제 사용한 source resistance는 약 $255\Omega$가 되었다.

---

### 📷 실험 사진

> 아래 이미지 링크는 GitHub에 업로드한 후 교체하면 됨.

<img width="587" height="783" alt="실험1 회로도" src="https://github.com/user-attachments/assets/b77026d1-1fb5-4b7d-ae90-c1799d1639f6" />

<img width="599" height="800" alt="RD1kohm" src="https://github.com/user-attachments/assets/a58cdaf2-88b2-4866-9472-65e0c7a75393" />

<img width="597" height="796" alt="RD2kohm" src="https://github.com/user-attachments/assets/f889d446-9f28-4a54-a9a1-7b39ff0c19ca" />

---

### 📐 이론적 배경

Common-source amplifier에서는 gate에 입력 신호가 인가되고, drain에서 output voltage를 측정한다. NMOS가 적절한 bias point에서 동작하면 입력 신호의 변화에 따라 drain current가 변하고, 이 변화가 drain resistor $R_D$에 걸리는 전압강하 변화를 만든다.

따라서 출력 전압은 다음과 같이 해석할 수 있다.

$$
V_{out}=V_{DD}-I_D R_D
$$

입력 전압이 증가하면 drain current $I_D$가 증가하고, $R_D$에 걸리는 전압강하가 커진다. 그 결과 $V_{out}$은 감소한다. 따라서 common-source amplifier는 입력과 출력이 반전되는 특성을 가진다.

Source resistor $R_S$가 추가되면 source degeneration이 발생한다. 이는 회로에 negative feedback을 제공하여 bias point를 안정화시키지만, 동시에 voltage gain을 감소시킬 수 있다.

Source degeneration이 있는 경우, 이상적인 common-source gain은 대략 다음과 같이 표현할 수 있다.

$$
A_v \approx -\frac{g_m R_D}{1+g_m R_S}
$$

즉, $R_D$가 커질수록 gain은 증가할 수 있지만, $R_S$에 의한 feedback 때문에 gain이 제한된다.

---

### 📊 DC Bias 설정 결과

SPICE simulation에서는 $V_{out}$이 약 5V가 되도록 $V_{in}$ bias를 설정하였다. 그 결과 필요한 DC offset은 다음과 같았다.

| $R_D$ | Required $V_{in}$ bias | 실험 가능 여부 | 비고 |
| :--- | :--- | :--- | :--- |
| $1k\Omega$ | 4.63V | 완전히 맞추기 어려움 | Function generator 최대 DC offset이 4.5V로 제한됨 |
| $2k\Omega$ | 3.89V | 비교적 가능 | Function generator로 설정 가능한 범위 |

$R_D=1k\Omega$ 조건에서는 simulation에서 요구한 DC offset이 4.63V였지만, function generator의 최대 DC offset이 4.5V였기 때문에 동일한 bias point를 정확히 맞출 수 없었다.

반면 $R_D=2k\Omega$ 조건에서는 필요한 DC offset이 3.89V였기 때문에 실제 실험 조건이 SPICE simulation에 더 가깝게 설정될 수 있었다.

---

## 3. 🧪 Experiment 2: Small-Signal Common-Source Amplifier 측정

### 📊 측정 조건 (Setup)

* **회로 구조:** Common-Source Amplifier with Source Degeneration
* **Drain resistor:** $R_D=1k\Omega,\ 2k\Omega$
* **Source resistor:** 약 $255\Omega$
* **입력 신호:** DC offset + small-signal sine wave
* **관찰 항목:** input waveform, output waveform, phase inversion, voltage gain
* **목표:** 출력 신호가 입력에 대해 반전 및 증폭되는지 확인

---

### 📷 실험 사진

<img width="595" height="794" alt="실험2 회로도" src="https://github.com/user-attachments/assets/1958c12e-11e4-4de7-82a1-59676ce1d038" />

<img width="642" height="856" alt="1kohm 파형" src="https://github.com/user-attachments/assets/026f181b-68bd-48ab-b02c-5220e18067b1" />

<img width="645" height="860" alt="1kohm 파형2" src="https://github.com/user-attachments/assets/1f564a56-2988-425f-9795-60d8e49876b2" />

<img width="643" height="858" alt="2kohm 파형" src="https://github.com/user-attachments/assets/8496669f-4bd2-45d6-a2c4-1bbaae1fab08" />

<img width="648" height="863" alt="2kohm 파형2" src="https://github.com/user-attachments/assets/846587a8-43af-4dd1-981a-a70b12ce1049" />

---

### 📊 Experiment 2 결과

실험 결과, NMOS common-source amplifier의 기본적인 특성인 **반전 증폭**을 확인할 수 있었다. 입력 신호가 증가할 때 출력 신호는 감소하는 형태로 나타났으며, output waveform은 input waveform에 대해 위상이 반전되어 나타났다.

SPICE simulation에서 계산된 주요 parameter는 다음과 같다.

| $R_D$ | $V_{in}$ bias | $g_m$ | $I_{DS}$ | $V_{TH}$ | Gain |
| :--- | :--- | :--- | :--- | :--- | :--- |
| $1k\Omega$ | 4.63V | 28.8mS | 5.0mA | 3.01V | -3.45 |
| $2k\Omega$ | 3.89V | 20.4mS | 2.5mA | 3.01V | -6.58 |

> **Note:** $R_D=2k\Omega$ 조건에서 gain의 절댓값이 더 크게 나타났다. 이는 같은 drain current 변화가 더 큰 $R_D$에서 더 큰 output voltage variation을 만들기 때문이다.

---

### 📉 결과 해석

| 측정 조건 | 관찰 내용 | 결과 요약 |
| :--- | :--- | :--- |
| $R_D=1k\Omega$ | 필요한 DC offset은 4.63V | function generator 최대 offset이 4.5V라 simulation과 완전히 동일한 bias 불가 |
| $R_D=2k\Omega$ | 필요한 DC offset은 3.89V | 실제 실험에서 simulation 조건과 비교적 유사하게 설정 가능 |
| $R_D$ 증가 | gain 절댓값 증가 | $R_D=2k\Omega$에서 더 큰 voltage gain 확인 |
| Source resistor 추가 | negative feedback 발생 | bias 안정성은 증가하지만 gain은 감소 가능 |
| Output waveform | 입력 대비 반전 | common-source amplifier의 기본 동작 확인 |

---

## 4. 🧪 SPICE 결과와 실험 결과 비교

### 📌 SPICE에서 기대되는 동작

SPICE simulation에서는 NMOS가 적절한 DC operating point에 bias되어 있을 때, common-source amplifier가 입력 신호에 대해 반전된 output waveform을 출력할 것으로 예상된다.

입력 신호가 증가하면 drain current가 증가하고, drain resistor에 걸리는 전압강하가 커진다. 이로 인해 $V_{out}$은 감소하므로 output은 input에 대해 반전된다.

또한 $R_D$가 커질수록 같은 drain current 변화에 대해 더 큰 output voltage variation이 발생하므로, voltage gain의 절댓값은 증가할 수 있다.

---

### 📊 비교 요약

| Item | SPICE expectation | Experimental result |
| :--- | :--- | :--- |
| DC bias point | $V_{out}\approx5V$가 되도록 $V_{in}$ bias 설정 | $R_D=2k\Omega$는 비교적 유사, $R_D=1k\Omega$는 offset 제한으로 차이 발생 |
| $R_D=1k\Omega$ | Required offset = 4.63V | Function generator 최대 offset 4.5V로 동일 조건 구현 어려움 |
| $R_D=2k\Omega$ | Required offset = 3.89V | 실험에서 비교적 simulation 조건에 가깝게 구현 가능 |
| Output waveform | 입력 대비 반전된 증폭 파형 | 반전 증폭 경향 확인 |
| Gain | $R_D=2k\Omega$에서 더 큰 gain 기대 | $R_D=2k\Omega$에서 gain 절댓값 증가 |
| Source resistor | bias 안정화, gain 감소 효과 | 실제 $R_S\approx255\Omega$로 인해 bias와 gain에 약간의 차이 가능 |

---

### 🔍 차이 원인 분석

실험 결과는 전체적으로 SPICE simulation과 같은 경향을 보였다. 즉, 출력 신호는 입력 신호에 대해 반전되었고, $R_D=2k\Omega$ 조건에서 더 큰 voltage gain이 예상되었다.

하지만 실제 실험과 SPICE 사이에는 다음과 같은 차이 원인이 존재한다.

1. **Function generator DC offset 한계**
   * $R_D=1k\Omega$ 조건에서 필요한 DC offset은 4.63V였지만, function generator는 최대 4.5V까지만 제공할 수 있었다.
   * 따라서 실제 회로의 bias point가 simulation 조건과 다르게 설정되었다.

2. **Source resistor 실제값 차이**
   * 설계값은 $R_S=250\Omega$였지만, 실제로는 $550\Omega$ 저항 2개를 병렬로 연결하여 약 $255\Omega$를 사용하였다.
   * 이 작은 차이가 DC operating point와 voltage gain에 영향을 줄 수 있다.

3. **MOSFET parameter variation**
   * 실제 MOSFET의 threshold voltage, transconductance, drain current 특성은 simulation model과 완전히 같지 않을 수 있다.

4. **Breadboard parasitic effects**
   * 브레드보드 배선, 접촉 저항, 기생 커패시턴스 등이 small-signal waveform에 영향을 줄 수 있다.

5. **Measurement error**
   * Oscilloscope probe, function generator 설정, voltage scale, coupling mode 등에 의해 측정 오차가 발생할 수 있다.

---

## 5. 🔍 트러블슈팅 및 고찰 (Error Analysis) ⭐

### 5.1 DC Bias Point 설정의 중요성

이번 실험에서 가장 중요한 부분은 올바른 DC bias point를 설정하는 것이었다.

Common-source amplifier는 MOSFET이 적절한 operating region에서 동작해야 output signal이 clipping 없이 swing할 수 있다. 만약 bias point가 너무 낮거나 높으면 output waveform이 정상적으로 증폭되지 않고 왜곡될 수 있다.

특히 $R_D=1k\Omega$ 조건에서는 simulation에서 요구한 offset이 4.63V였지만, function generator의 최대 DC offset이 4.5V였기 때문에 simulation과 동일한 조건으로 실험할 수 없었다. 이로 인해 측정된 gain과 output waveform이 SPICE 결과와 완전히 일치하지 않을 수 있다.

---

### 5.2 Source Resistor의 영향

Source resistor $R_S$는 amplifier에 negative feedback을 제공한다. 이 feedback은 bias point를 안정화시키는 장점이 있지만 voltage gain을 낮추는 효과도 있다.

설계상 $R_S$는 $250\Omega$였지만 실제 회로에서는 약 $255\Omega$가 사용되었다. 이 작은 차이는 drain current, $g_m$, voltage gain에 약간의 영향을 줄 수 있다.

Source degeneration이 있는 경우 gain은 대략 다음과 같이 감소한다.

$$
A_v \approx -\frac{g_m R_D}{1+g_m R_S}
$$

따라서 $R_S$가 커질수록 denominator가 증가하여 gain의 절댓값은 작아진다.

---

### 5.3 Drain Resistor 증가의 영향

$R_D$가 $1k\Omega$에서 $2k\Omega$로 증가하면, 같은 drain current 변화가 더 큰 voltage variation을 만든다. 따라서 voltage gain의 절댓값은 증가할 수 있다.

실제로 SPICE 결과에서도 gain은 다음과 같이 나타났다.

* $R_D=1k\Omega$: Gain = -3.45
* $R_D=2k\Omega$: Gain = -6.58

하지만 $R_D$가 커지면 output voltage swing 가능 범위가 줄어들고, bias point error에 더 민감해질 수 있다. 따라서 단순히 gain을 크게 하기 위해 $R_D$를 키우는 것만으로는 안정적인 amplifier 설계를 보장할 수 없다.

---

## 6. 🛠 개선 방안

이번 실험을 더 정확하게 수행하기 위해서는 다음과 같은 개선이 필요하다.

1. **Function generator offset 범위 확인**
   * 실험 전에 필요한 DC offset이 function generator로 설정 가능한 범위인지 확인한다.
   * $R_D=1k\Omega$처럼 필요한 offset이 장비 한계를 넘는 경우, 회로 조건을 조정하거나 외부 DC bias를 별도로 인가하는 방법을 고려할 수 있다.

2. **정확한 source resistor 사용**
   * 가능하다면 설계값인 $250\Omega$에 더 가까운 저항 조합을 사용한다.
   * 실제 저항값을 multimeter로 측정한 뒤 SPICE에도 동일한 값을 반영하면 비교가 더 정확해진다.

3. **DC operating point 먼저 확인**
   * AC input을 인가하기 전에 $V_{out,DC}$가 목표값 근처에 있는지 확인한다.
   * output이 clipping 없이 swing할 수 있는지 DC level을 먼저 조정한다.

4. **Input / output waveform 동시 측정**
   * oscilloscope에서 input과 output을 동시에 확인하여 phase inversion과 gain을 직접 비교한다.
   * voltage scale과 coupling mode를 동일 조건에서 확인한다.

5. **SPICE 조건과 실험 조건 일치**
   * 실제 실험에서 사용한 $R_S$, $R_D$, DC offset, input amplitude를 SPICE에 반영하여 simulation과 experiment를 다시 비교한다.

---

## 7. ✅ 결론 및 느낀 점

* 이번 실험에서는 source degeneration이 포함된 NMOS common-source amplifier를 구성하고, $R_D=1k\Omega$와 $R_D=2k\Omega$ 조건에서 DC bias 및 small-signal 증폭 특성을 확인하였다.
* SPICE simulation에서는 $V_{out}$이 약 5V가 되도록 bias point를 설정했으며, 필요한 input DC offset은 $R_D=1k\Omega$에서 4.63V, $R_D=2k\Omega$에서 3.89V였다.
* 실제 실험에서는 $R_D=1k\Omega$ 조건의 경우 function generator의 최대 DC offset이 4.5V로 제한되어 simulation과 동일한 bias point를 정확히 구현할 수 없었다.
* 반면 $R_D=2k\Omega$ 조건에서는 필요한 DC offset이 3.89V였기 때문에 실험 조건이 simulation과 비교적 유사하게 설정될 수 있었다.
* 실험 결과, output waveform은 input waveform에 대해 반전되어 나타났으며, 이는 common-source amplifier의 기본적인 inverting amplifier 특성과 일치한다.
* $R_D$가 증가하면 같은 drain current 변화에 대해 더 큰 output voltage variation이 발생하므로 voltage gain의 절댓값이 증가한다.
* 실제 SPICE 결과에서도 $R_D=1k\Omega$에서 gain은 -3.45, $R_D=2k\Omega$에서 gain은 -6.58로 나타나 $R_D$ 증가에 따른 gain 증가 경향을 확인할 수 있었다.
* Source resistor는 bias point를 안정화시키는 negative feedback 역할을 하지만, 동시에 voltage gain을 감소시키는 효과를 가진다.
* 이번 실험에서는 이상적인 $R_S=250\Omega$ 대신 실제로 약 $255\Omega$를 사용했으므로, 이 차이가 DC operating point와 gain에 약간의 영향을 줄 수 있다.
* 결과적으로 이번 실험을 통해 common-source amplifier에서 **DC bias point 설정, source degeneration, drain resistor 크기, 장비의 DC offset 한계**가 모두 amplifier 동작에 중요한 영향을 준다는 점을 확인할 수 있었다.

---

*본 문서는 2022067101 윤희찬의 Week 12 MOSFET(2) 실습 데이터를 기반으로 작성되었습니다.*
