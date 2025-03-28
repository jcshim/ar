### 3월30일 일요일 오후5시에 특별세미나
1. 강사: University of Malta, Luke Vassallo
2. PCB Auto Routing 전문가이며, 다음 석사논문 저자 입니다.
3. GPT 활용해서 예습 부탁드려요. 1인당 하난씩 질문하기.

---

### [Source Code](https://github.com/LukeVassallo/RL_PCB)
### [석사논문](https://www.lukevassallo.com/wp-content/uploads/2023/09/automated_pcb_component_placement_using_rl_msc_thesis_v2_1_lv.pdf)

---

## **"Automated PCB Component Placement using Reinforcement Learning"**

---

### 📌 논문 주제 요약
이 논문은 **강화학습(Reinforcement Learning, RL)**을 활용해 **PCB(인쇄회로기판) 부품 자동 배치** 문제를 해결하려는 연구입니다.

---

### 1. 🔍 왜 이 연구를 했는가? (연구의 동기)
- PCB 설계에서 부품 배치는 매우 중요한 단계지만, 아직도 수작업에 의존하는 경우가 많습니다.
- 기존 자동화 도구는 직관이 부족하고, 사람처럼 "센스 있게" 배치하기 어려움.
- 그래서 **AI 기술**, 특히 **강화학습**을 사용해서 자동으로 부품을 배치할 수 있는 시스템을 만들고자 함.

---

### 2. 🎯 목표
1. **부품 배치 문제를 RL로 해결**하는 방식 제안.
2. **단일 부품**을 반복적으로 움직이면서 학습하는 환경 설계.
3. **다수의 부품**을 동시에 고려하는 학습 시스템 개발.
4. 기존 방법(Simulated Annealing)과 성능 비교.

---

### 3. 🛠️ 방법
- **MDP(Markov Decision Process)**로 배치 문제를 모델링.
- 강화학습 알고리즘인 **TD3, SAC**를 사용하여 학습.
- **보상 함수**를 조절해가며 학습 성능 향상 시도.
- 부품 간 협업/경쟁하는 행동이 학습되도록 설계.
- 실험에 사용할 데이터셋 30개를 실제 회로로부터 수집.

---

### 4. ✅ 주요 성과
- 강화학습이 기존 기법(SA)보다 **최대 21% 더 짧은 배선 길이**를 만들어냄.
- 적응형 보상 시스템 덕분에 **전문가의 지식 없이도 학습 가능**.
- 훈련된 정책(policy)이 보지 못한 새로운 회로에서도 잘 작동.
- **오픈소스**로 코드와 도구를 공개:  
  👉 [https://github.com/lukevassallo/rl_pcb](https://github.com/lukevassallo/rl_pcb)

---

### 5. 📌 결론
- 강화학습은 PCB 배치 자동화에 매우 유망한 방법임을 보여줌.
- 부품이 협력하며 자연스럽게 배치되는 방식까지 학습 가능.
- 향후 연구는 **오프라인 학습**이나 **보상 함수 개선**, **더 복잡한 회로로의 확장** 등이 있음.

---

필요하시면, 각 장별 세부 요약이나 실험 결과 도표도 한글로 정리해드릴 수 있어요. 어떤 부분이 더 궁금하신가요?
