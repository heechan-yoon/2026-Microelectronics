# ⚡ [Week 2] 저항의 V-I 특성 및 RC Low Pass Filter 설계 분석

> **과목명:** 2026-1 전자회로1 실습  
> **실험 일자:** 2026.03.10 (Week 2)  
> **사용 장비:** Breadboard, DC Power Supply, Multimeter, Oscilloscope, Function Generator, SPICE

---

## 1. 🎯 프로젝트 목표
* **Experiment 1:** 고정 저항(100Ω) 회로에서 입력 전압에 따른 전류 변화를 측정하여 Ohm's Law 검증 및 SPICE 시뮬레이션과의 오차 분석.
* **Experiment 2:** RC Low Pass Filter(LPF)를 설계하고 주파수 응답 특성(Passband, Transition, Stopband)과 Corner Frequency($f_c$) 관찰.

---

## 2. 🧱 Experiment 1: 저항의 V-I 특성과 오차 분석

### 📊 측정 결과 (Measured vs SPICE)
SPICE 시뮬레이션(이상적인 100Ω 기준)과 실제 브레드보드 측정값을 비교한 결과입니다.

| Input Voltage (V) | SPICE Result (mA) | Measured Result (mA) | Error (%) |
| :--- | :--- | :--- | :--- |
| 0.2 | 2.0 | 1.81 | 9.50% |
| 0.6 | 6.0 | 5.42 | 9.67% |
| 1.0 | 10.0 | 9.04 | 9.60% |

***(평균 오차율: 약 9.68%)***

### 🔍 트러블슈팅 및 고찰 (Error Analysis) ⭐
측정된 전류가 이상적인 값보다 일관되게 낮게(약 10% 오차) 측정되었습니다. 이는 단순한 측정 실수가 아닌 시스템적 요인으로 분석됩니다.

1.  **저항 톨러런스 (Tolerance):** 사용된 100Ω 저항의 실제 값이 약 110Ω에 가까웠을 확률이 높음.
2.  **장비 내부 저항 (Burden Voltage):** 전류계(Multimeter) 자체의 내부 저항이 루프 전류를 감소시킴.
3.  **접촉 저항 (Contact Resistance):** 브레드보드 트랙 및 점퍼선의 기생 저항이 더해짐.

---

## 3. 📉 Experiment 2: RC Low Pass Filter 주파수 응답 특성

### 📐 회로 설계 및 이론적 배경
* **소자 값:** $R = 100\Omega$, $C = 0.1\mu F$
* **차단 주파수 (Corner Frequency) 이론값 계산:**
    $$f_c = \frac{1}{2\pi RC} \approx 15,915 \text{ Hz}$$

### 📊 주파수 대역별 출력 전압($V_{out}$) 측정 결과
입력 신호 $V_{in}$을 1Vpp 사인파로 설정하고 주파수를 변화시키며 출력 전압을 측정했습니다.

| 주파수 (f) | 주파수 영역 (Region) | 이론적 $V_{out}$ (V) | 측정된 $V_{out}$ (V) | 동작 분석 |
| :--- | :--- | :--- | :--- | :--- |
| 10 Hz | Passband | 1.000 | 1.04 | 저주파 통과 (거의 감쇠 없음) |
| 12 kHz | Near Corner | 0.798 | 0.716 | 차단 주파수 근처로 진입하며 감쇠 시작 |
| 1 MHz | Stopband | 0.016 | 0.012 | 고주파 신호 완벽히 차단 확인 |

### 🔍 트러블슈팅 및 고찰 (Error Analysis) ⭐
12kHz 지점에서 이론값
