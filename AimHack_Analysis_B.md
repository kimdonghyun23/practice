# 에임핵 'B' 분석 결과


## 1. 모드 1 (부드러운 조준 이동)

### 📌 동작 순서

1. **내 좌표, 적 좌표를 읽음**
2. **조준 각도 계산**
   - `ToX = ArcTan2(타겟X - 현재X, 타겟Z - 현재Z)`
   - `ToY = ArcTan2(현재Y - 타겟Y, √[(ΔX)^2 + (ΔZ)^2])`
3. **3차원 좌표계 기준 ArcTan2 함수로 각도 계산**
4. **각도 범위 제한: -π ~ +π (각도 왜곡 방지)**
5. **속도 슬라이더 값에 따라 부드럽게 이동 (계산된 값들을 메모리에 반영)**
   - `Temp = 현재각 + (목표각 - 현재각) / 속도계수`

---

## 2. 모드 2 (즉시 조준 이동)

### 📌 동작 순서

- 모든 적을 루프 탐색
- 조건: 적이 **보이고 살아 있으며**, 팀 조건 통과 시
- 가장 가까운 적의 좌표 확보
- 내 위치 기준 조준 각도 **즉시 계산 및 반영**
- 매우 빠르고 정확하지만 **부자연스럽게 보일 수 있음**

---

## ⚙️ 부가 기능

- **팀 구분 기능**
  - 같은 팀은 조준 대상에서 제외
- **클릭 중 조준 작동 조건**
  - 마우스 좌클릭 상태에서만 조준 작동
- **조준 부위 설정 기능**
  - 기본: `Head`
  - 필요 시 다른 뼈대 부위 이름으로 변경 가능

---
