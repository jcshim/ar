# Auto Routing

## [세미나](seminar/readme.md)

### [PCB 설계 (KiCAD)](https://m.blog.naver.com/sohnet/222629751218)
### [PCB 설계 요약](https://youtu.be/ITiRL_1lt_0?si=1YAq4duNzaVqSNy0)
#### [PCB 설계 자동화를 위한 AI 기반 부품 배치 최적화 프로젝트](https://cafe.naver.com/jcshim/5689)

## 효과적인 PCB 자동 배치 및 배선 방법
---

## ✅ **전체 전략 요약**

| 항목 | 최선의 선택 | 이유 |
|------|--------------|------|
| **배치 알고리즘** | 강화학습 (TD3, SAC, PPO) + 그래프 기반 인코딩 | 회로 연결 정보를 효과적으로 반영하며 일반화와 품질 우수 |
| **배선 알고리즘** | DQN + MCTS + PPO 하이브리드 | 실시간성 + 복잡도 해결 + 성공률 100% 달성 사례 있음 |
| **상태 인코딩** | CNN + GNN 조합 | 공간적 정보 + 구조적 연결성 모두 반영 |
| **행동 공간** | 격자 이동(상하좌우) + 층 이동(via 포함) | 다층 PCB와 현실 배선 제약 대응 가능 |
| **보상 함수** | 배선 길이, via 수, 충돌 여부, 예측 가능성 (Pre-routability) 반영 | 단순 로컬 성능뿐 아니라 미래 배선 성공률까지 유도 |
| **데이터 및 시뮬레이터** | 공개된 JSON 기반 PCB 데이터셋 + RL 라우팅 시뮬레이터 (ISU 환경) | 다양한 회로 지원 + KiCAD 등 툴과 연동 용이 |
| **KiCAD 통합 방식** | 초기에 DSN/SES 파일 I/O → 실시간 제어를 위한 Python API 또는 플러그인 확장 | 구현 난이도 대비 효과적으로 빠른 테스트 가능 |

---
![image](https://github.com/user-attachments/assets/de984f9a-611c-4d75-9dcf-22180cb6f9b5)


## 🧠 **PCB 자동 배치 (Placement)** – 최선의 구성

- **모델 구조**:  
  - 입력: 그래프 기반 인코딩 (GNN or MLP + Netlist)  
  - 알고리즘: **SAC** 또는 **TD3** → 연속 액션(정밀 위치 조정) 대응
- **정책 특징**:
  - 적응형 보상: 전력, 면적, HPWL, overlap 패널티 반영
  - 일반화 훈련: 다양한 회로로 사전학습 → 특정 회로 fine-tuning
- **우수 사례**:
  - [Vassallo et al. (2024)](https://www.lukevassallo.com/wp-content/uploads/2024/01/Learning-Circuit-Placement-Techniques-through-Reinforcement-Learning-with-Adaptive-Rewards.pdf)  
  - [FanoutNet (2023)] – 구성요소 레벨에서 위치 및 방향까지 정책적으로 학습함

---

## 🛠 **PCB 배선 (Routing)** – 최선의 구성

- **정책 알고리즘**:  
  - **DQN** → 빠른 추론 / 경량 모델  
  - **PPO + MCTS 하이브리드** → 고성능 탐색 보장  
- **상태 인코딩**:  
  - 12차원 피처 벡터 (Liao et al.) + 이미지 기반 grid map (FanoutNet)
- **보상 설계**:
  - 배선 성공 여부, 경로 길이, 비아 개수, 충돌 여부, 남은 net 난이도
- **우수 사례**:
  - [DQN Global Router (2019)](https://github.com/haiguanl/DQN_GlobalRouting)  
  - [MCTS + PPO (2022)](https://forrestbao.github.io/publications/Circuit_Routing_Using_Monte_Carlo_Tree_Search_and_Deep_Reinforcement_Learning_VLSI_DAT_2022.pdf)

---

## 🔗 **KiCAD 연동 및 실용화**

### (1) 빠른 프로토타입:
- DSN 내보내기 → RL 라우터 실행 → SES 파일로 결과 반영

### (2) 실시간 인터랙션:
- KiCAD Python API로 RL agent가 실시간으로 트랙, 비아 생성
- 배선 중간에 DRC 결과(설계 규칙 위반 여부)도 API로 받기 가능

### (3) 클라우드화/플러그인화:
- Quilter/DeepPCB 사례처럼, 사용자 보드 업로드 → 자동 처리 → 결과 SES 반환 또는 GUI 내 플러그인 버튼 제공

---

## 🧩 최종 요약

> **그래프 기반 인코딩 + 강화학습 정책(TD3/SAC for 배치, DQN/PPO+MCTS for 배선) + KiCAD Python API 연동**  
> = 현재 가능한 최고의 실용적 자동화 구조

---

### 📎 원하시면…
- 위 구조를 기반으로 한 **아키텍처 설계도**  
- KiCAD 플러그인 개발용 코드 뼈대  
- 발표 자료나 보고서용 비교표  
바로 만들어드릴 수 있어요!

