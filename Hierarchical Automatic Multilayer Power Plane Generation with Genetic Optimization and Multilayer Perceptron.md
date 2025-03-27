# Hierarchical Automatic Multilayer Power Plane Generation with Genetic Optimization and Multilayer Perceptron

---

## 논문 제목
계층적 유전자 최적화와 다층 퍼셉트론(MLP)을 이용한 자동 다층 전력 평면 생성 방법론

## 연구 배경 및 목적
PCB(Printed Circuit Board) 설계 과정에서 전력 평면 생성(power plane generation)은 매우 중요하지만 여전히 많은 부분이 수동으로 진행되어 시간과 노력이 많이 소요된다. 본 연구는 유전자 알고리즘(Genetic Optimization, GO)과 다층 퍼셉트론(Multi-Layer Perceptron, MLP)을 결합한 방법론(GOMLP)을 제안하여 PCB 전력 평면 생성 과정을 자동화하고 효율적으로 최적화하는 것을 목표로 한다.

## 주요 개념 및 접근법

### 1. 문제 정의
- PCB 전력 평면 생성은 핀들을 연결하여 전력 공급 면적을 나누는 공간 분할 문제(space partitioning)로 정의된다.
- 목표는 동일 네트(net)에 속한 핀을 단일 연결 평면(single connected plane)으로 구성하고, 서로 다른 네트 간의 핀을 분리하는 것이다.
- 각 네트의 핀이 여러 개의 분리된 '섬(island)'으로 분할되는 것을 최소화하는 것이 중요하다.

### 2. 제안된 방법론: GOMLP
- GOMLP는 크게 두 가지 모듈로 구성된다:
  - **외부 루프**: 유전자 알고리즘(GO)을 이용하여 핸들(handle)의 최적 위치를 탐색한다.
  - **내부 루프**: MLP를 활용하여 핸들과 핀의 위치를 입력 데이터로 삼아 2차원 공간을 세그먼테이션(segmentation) 한다.

- **핵심 요소**
  - 핀 및 핸들 위치 정보의 확장된 특징(feature expansion)을 통해 복잡한 경계 생성 가능.
  - 섬의 개수를 최소화하기 위한 거리 기반 맞춤형 비용 함수(distance metric) 설계.
  - 핸들의 위치를 최적화하여 최적의 공간 분할을 유도.

### 3. 확장된 방법론: H-GOMLP
- 단일층(single layer) PCB에서 다층(multilayer) PCB 설계로 확장.
- 각 네트 간 거리 측정(metric)을 사용하여 계층적 군집화(hierarchical clustering)를 수행하고, 각 네트를 효율적으로 서로 다른 층에 배치하는 방법을 제안.
- 하우스도르프 거리(Hausdorff Distance, HD) 및 Earth Mover 거리(EMD)를 사용하여 네트의 군집화를 효율적으로 수행.

## 실험 결과 및 평가
- GOMLP는 기존에 사용되던 A* 알고리즘 기반의 방법과 비교하여 **71%의 사례에서 더 우수한 성능**을 보였다.
- 실험은 6~8개의 네트로 구성된 129개 PCB 설계 문제에서 진행되었으며, 핀 개수 증가에 따라 난이도가 증가하는 문제에서 GOMLP가 좋은 확장성을 보였다.
- 특히 확장된 특징(feature expansion), 거리 기반 비용 함수(distance metric)의 추가가 성능 향상에 크게 기여했다.

### 다층 문제 해결 결과 (H-GOMLP)
- 20개의 네트로 이루어진 실제 산업용 PCB 설계 문제에서도 H-GOMLP가 효과적으로 작동함을 입증.
- 계층적 군집화 기반의 층 배치 방법을 통해 설계 초기에 층 수를 유연하게 결정할 수 있어 설계 효율성이 크게 향상됨.
- 하우스도르프 거리 기반 방법(HD)이 Earth Mover 거리(EMD) 기반 방법보다 더 효율적이고 균형 잡힌 층 배치를 제공함.

## 결론 및 연구 의의
- 본 논문은 PCB 전력 평면 생성을 최초로 완전히 자동화한 연구로, 실질적인 PCB 설계에서의 수작업을 크게 줄이고 설계 품질을 향상시키는 데 기여한다.
- 제안된 방법론(GOMLP, H-GOMLP)은 기존 방법에 비해 성능, 확장성, 실용성이 뛰어나며, 향후 IR-drop과 같은 더 복잡한 설계 조건을 추가하여 발전 가능성이 높다.

---
