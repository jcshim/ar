# **TD3 (Twin Delayed Deep Deterministic Policy Gradient)**
---

## 🎯 TD3를 한 줄로 설명하면?
> "DDPG의 단점을 보완해서 **더 안정적이고, 더 잘 배우도록 만든** 강화학습 알고리즘입니다."

---

## 💡 TD3가 왜 나왔을까?
기존의 **DDPG**는 연속적인 행동을 다룰 수 있는 좋은 알고리즘이었지만,
- 정책(policy)이 너무 빨리 바뀌거나
- Critic(가치 평가)이 부정확하면  
👉 **학습이 불안정해지고 망가지는** 문제가 있었어요.

그래서 TD3는 이걸 **세 가지 방법**으로 해결했습니다.

---

## 🔧 TD3의 핵심 아이디어 (3가지 개선점)

| 개선점 | 설명 | 쉽게 말하면 |
|--------|------|-------------|
| ✅ **두 개의 Critic 네트워크 사용** | Q-value를 2개 계산하고, 더 작은 값을 선택 | 너무 낙관적으로 학습하는 걸 막음 |
| 🕒 **정책(Actor)을 덜 자주 업데이트** | Critic은 매 스텝 학습하지만, Actor는 몇 스텝마다 한번 | 덜 흔들리고 안정적으로 학습 |
| 🔉 **Target에 노이즈 추가** | 목표 Q값에 살짝 노이즈를 더함 | 너무 정확한 예측을 피해서 더 일반화된 학습 유도 |

---

## ⚙️ TD3 작동 순서 (쉬운 설명)

1. **환경과 상호작용**  
   에이전트가 상태를 보고 행동을 선택해서 환경에 적용합니다.

2. **경험 저장**  
   상태, 행동, 보상, 다음 상태 정보를 리플레이 버퍼에 저장합니다.

3. **두 개의 Q 네트워크 학습 (Critic 1, Critic 2)**  
   둘 다 같은 데이터를 보고 Q값(가치)을 예측하지만,  
   👉 **더 작은 Q값**을 사용해서 보수적으로 학습합니다.

4. **정책 네트워크 업데이트 (Actor)**  
   일정 간격으로 한 번씩 업데이트합니다.  
   Critic이 안정적으로 Q값을 줄 때만 정책을 바꿔요.

5. **타깃 네트워크 업데이트**  
   서서히(main → target 네트워크로) 따라가도록 해서 안정성 유지.

---

## 📊 TD3와 DDPG 차이 정리

| 항목 | DDPG | TD3 |
|------|------|-----|
| Critic | 1개 | 2개 사용 (더 작은 Q값 선택) |
| Policy 업데이트 | 자주 | **드물게 (지연)** |
| Target에 노이즈 | 없음 | 있음 (학습 안정화) |
| 안정성 | 낮음 (불안정) | **높음 (안정적 수렴)** |
| 성능 | 보통 | **우수 (특히 연속 제어 문제)** |

---

## 📌 TD3를 왜 이 논문에서 사용했을까?
- PCB 부품 배치 문제는 **위치(x, y)** 같은 **연속된 행동 공간**을 다루기 때문에,
- DQN 같은 이산형 알고리즘보다 TD3 같은 연속형 정책 기반 알고리즘이 적합하고,
- TD3는 DDPG보다 **안정적이고 더 성능이 잘 나오는** 알고리즘이라 선택된 거예요.

---

## 🧠 참고 이미지 (비유)

- **Critic 1과 Critic 2는 두 명의 조언자**  
  한 명이 너무 낙관적이면? → 더 **보수적인** 쪽의 의견을 따라요.
  
- **Actor는 행동을 선택하는 본체**  
  자주 바꾸지 않고, **조심조심 업데이트**해요.

---

필요하시면 **수식 기반 정리**, **PyTorch 예제 코드**, **SAC와의 차이점**도 설명드릴 수 있어요. 더 깊이 들어가보고 싶은 부분 있으신가요?
