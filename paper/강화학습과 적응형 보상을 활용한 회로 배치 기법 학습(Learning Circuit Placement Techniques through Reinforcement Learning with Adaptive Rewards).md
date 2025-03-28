### [Learning Circuit Placement Techniques through Reinforcement Learning with Adaptive Rewards](https://www.lukevassallo.com/wp-content/uploads/2024/01/Learning-Circuit-Placement-Techniques-through-Reinforcement-Learning-with-Adaptive-Rewards.pdf)

---

### 🔧 논문 제목  
**강화학습과 적응형 보상을 활용한 회로 배치 기법 학습**

### 🧠 저자  
Luke Vassallo, Josef Bajada (University of Malta)

---

## 📌 연구 목적
- **PCB(인쇄회로기판) 부품 배치(Placement)**는 물리적 설계의 첫 단계로, 품질이 이후 배선(routing)에 큰 영향을 미침.
- 이 배치 작업은 **NP-완전 문제**로 최적해 탐색이 매우 어려움.
- 기존 휴리스틱이나 시뮬레이티드 어닐링(SA)은 직관 부족.
- 본 연구는 **강화학습(RL)을 이용해 사람의 경험 없이도 효과적인 배치 정책을 학습**하는 방식을 제안.

---

## 🧩 주요 기여
1. **PCB 부품 배치 문제를 MDP(Markov Decision Process)**로 모델링
2. **TD3, SAC 같은 고급 RL 알고리즘**을 사용해 최적화된 배치 정책 학습
3. **적응형 보상 함수(adaptive reward)** 설계로 학습 안정성과 일반화 향상
4. 기존 **SA-PCB 대비 최대 21%까지 배선 길이 감소** 달성
5. 학습된 정책은 **협력적 행동**을 보이며 빠른 수렴을 유도함

---

## ⚙️ 방법론 요약

### 🏗️ 환경 구성
- 입력: **회로 넷리스트**를 **하이퍼그래프**로 표현
- 목표: **HPWL (Half-Perimeter Wirelength)** 와 **EW (Euclidean Wirelength)** 최소화, **부품 간 겹침 방지**

### 🎯 상태(Observation)
- 부품 주변 환경, 방향성 정보, 위치·회전 정보 포함 (총 23차원 벡터)
- **이미지 기반 마스크 기법**으로 주변 인식

### 🤖 행동(Action)
- 연속 공간 (연속 위치 이동 + 회전 각도)
- 회전은 0°, 90°, 180°, 270°로 이산 처리

### 🪙 보상(Reward)
- 배선 길이 감소, 겹침 최소화, 보드 영역 벗어나지 않기 등 고려
- **과거 최적 값과 비교해 정규화된 보상** 제공 → 점진적 자기 개선 가능

---

## 🧪 실험 결과
- 9개의 실제 회로 기반 테스트
- **SAC**는 HPWL 중심 보상에서 뛰어난 성능, **TD3**는 EW 중심에서 우위
- **학습된 정책이 SA-PCB보다 평균적으로 더 짧은 배선 길이 유도**
- 특히 SAC의 **n=2, m=6, p=2** 구성은 **평균 21.1% 개선**

---

## 🎯 결론 및 의의
- 복잡한 PCB 배치 문제를 강화학습으로 **사람의 개입 없이 자동화 가능**함을 증명
- **일반화 가능한 정책**, **빠른 수렴**, **적응형 보상** 설계가 핵심
- 향후 **EDA 자동화 및 무인 설계 플로우**에 기여할 수 있는 기반 마련
