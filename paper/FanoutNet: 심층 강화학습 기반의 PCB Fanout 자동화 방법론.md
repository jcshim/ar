# FanoutNet: A Neuralized PCB Fanout Automation Method Using Deep Reinforcement Learning

---

## 논문 제목
FanoutNet: 심층 강화학습 기반의 PCB Fanout 자동화 방법론

## 연구 배경 및 목적
현대 PCB 설계는 수백 개의 네트(net)와 핀(pin), 다층 구조를 포함하며 복잡한 토폴로지(topology)와 라우팅 제약사항으로 인해 자동화가 매우 어렵다. 특히 Fanout(팬아웃)은 PCB 라우팅의 사전 설계 단계로, 자원 할당과 라우팅을 미리 계획하여 라우팅 복잡성을 줄이는 핵심 기법이지만, 아직 산업계에서는 자동화된 방법이 존재하지 않아 숙련된 엔지니어의 수작업에 의존한다. 본 논문에서는 심층 강화학습(DRL)을 활용해 PCB Fanout 자동화 문제를 해결하는 방법론을 제안한다.

## 연구 방법
- PCB Fanout 문제를 마르코프 결정 프로세스(MDP)로 정의하여, 심층 강화학습 기반의 모델을 통해 Fanout의 최적화를 수행한다.
- Convolutional Neural Network(CNN)와 어텐션 기반 신경망(attention-based network)을 결합하여 PCB 레이아웃과 네트리스트(netlist)의 정보를 효과적으로 표현(representation)하고 정책(policy) 모델과 가치(value) 모델을 학습시킨다.
- 학습 모델은 Proximal Policy Optimization(PPO) 알고리즘을 통해 최적화된다.
- 또한, Fanout 결과의 품질 검증을 위해 다중 제약 기반 라우터(Multi-Constraint Router, MCR)를 개발하여 다양한 산업 현장에서 요구되는 복잡한 라우팅 제약 조건을 만족시키도록 설계하였다.

## 주요 아이디어 및 접근법
- **상태(State)**: 공간적 특징(Spatial Feature, PCB 레이아웃을 이진 이미지로 표현)과 구조적 특징(Structured Feature, 네트리스트 및 Fanout 정보를 벡터로 표현)을 조합하여 사용.
- **행동(Action)**: 각 핀에 대한 Fanout 위치 결정(층, 방향, 거리)을 통해 수행.
- **보상(Reward)**: Fanout 완료 후 성공적으로 라우팅된 네트의 비율로 측정된 라우팅 가능성(routability)을 사용하여 최종적인 평가를 진행.

## 실험 결과 및 성과
- 산업 현장의 실제 PCB 벤치마크를 이용한 실험에서 제안된 FanoutNet 방법론은 모든 사례에서 **100%의 라우팅 성공률**을 달성하였으며, 최신 알고리즘 대비 평균적으로 **6.8%의 배선 길이 단축** 효과를 보였다.
- 기존 상용 PCB 라우팅 도구(FreeRouting, ELECTRA)와 강화학습 기반 최신 알고리즘들과 비교했을 때, 제안된 FanoutNet은 복잡한 산업용 PCB 설계에서도 일관성 있게 우수한 성능을 보여주었다.
- 특히 기존 방법 대비 와이어 길이, 비아(via) 개수 등의 핵심 지표에서 우수한 성과를 기록했다.

## 연구의 기여점
- 최초로 심층 강화학습을 통해 PCB Fanout 자동화 문제를 해결한 연구로서, PCB 라우팅의 효율성을 대폭 향상시킴.
- 공간적 및 구조적 특징의 효과적인 조합과 CNN 및 어텐션 네트워크를 통해 PCB 설계 정보를 효과적으로 표현할 수 있음을 입증함.
- 산업 현장에서 실질적으로 적용 가능한 Multi-Constraint Router를 개발하여 FanoutNet의 결과를 검증하고 실용성을 높임.

## 결론 및 향후 연구 방향
- 본 연구에서 제안된 FanoutNet 방법론은 산업 현장에서 매우 효과적이며, 앞으로 보다 다양한 PCB 설계 및 시스템 패키징 분야로 확장 가능성을 가지고 있다.
- 향후 다양한 PCB 레이아웃 문제와 시스템 패키지(System-in-Package, SiP) 영역으로의 연구 확장을 계획하고 있다.

---
