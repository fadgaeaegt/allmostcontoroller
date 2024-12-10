# allmostcontoroller

1일차
나비에 스트로크
2일차 스칼라를 멕스웰로 치환
나비에-스토크스 방정식의 구조:
나비에-스토크스 방정식은 공간과 시간 위에 정의된 함수 
𝑢
(
𝑥
,
𝑦
,
𝑧
,
𝑡
)
,
𝑣
(
𝑥
,
𝑦
,
𝑧
,
𝑡
)
,
𝑝
(
𝑥
,
𝑦
,
𝑧
,
𝑡
)
u(x,y,z,t),v(x,y,z,t),p(x,y,z,t)의 속성으로 나타내집니다. 이를 대수기하적으로 해석하면 다음과 같습니다:

다양체의 정의: 유체가 흐르는 공간 
𝑅
3
R 
3
 는 
(
𝑥
,
𝑦
,
𝑧
)
(x,y,z)라는 좌표를 갖는 3차원 유클리드 다양체로 볼 수 있습니다. 시간 
𝑡
t는 이 공간 위의 파라미터로 작용하며, 유체의 상태를 나타내는 스칼라 및 벡터 필드가 이 다양체 위에 정의됩니다.

속도 벡터 필드: 
𝑢
⃗
=
(
𝑢
,
𝑣
,
𝑤
)
u
 =(u,v,w)는 각 지점에서 유체의 속도를 나타내는 벡터 필드로, 다양체의 접다발에 포함됩니다. 접다발의 각 점에서 정의된 이 벡터는 유체의 국소 운동을 나타냅니다.

압력 스칼라 필드: 
𝑝
(
𝑥
,
𝑦
,
𝑧
,
𝑡
)
p(x,y,z,t)는 유체가 차지하는 위치에서의 압력을 나타내는 스칼라 필드로, 다양체의 함수 공간에서 정의됩니다.

라플라시안 및 발산 연산:

∇
2
𝑢
,
∇
⋅
𝑢
⃗
∇ 
2
 u,∇⋅ 
u
 
라플라시안 연산은 다양체의 곡률 정보와 관련되며, 속도 및 압력 필드의 퍼짐(확산) 특성을 반영합니다.

2. 각 숫자의 의미
(1) 밀도 (
𝜌
=
1.0
ρ=1.0)
유체의 질량 밀도 (단위: 
kg/m
3
kg/m 
3
 )를 나타냅니다.
이 값이 클수록 유체의 질량이 증가하며, 가속도 변화에 더 많은 힘이 필요합니다.
설정된 값 
𝜌
=
1.0
ρ=1.0은 단위화된 값으로, 수치 시뮬레이션에서 쉽게 해석될 수 있도록 간소화한 것입니다.
(2) 점성 계수 (
𝜇
=
0.1
μ=0.1)
유체의 내부 마찰을 나타내는 계수 (단위: 
Pa
\cdotp
s
Pa\cdotps).
점성 계수가 클수록 유체의 흐름이 저항을 많이 받으며, 층류 성질을 강하게 나타냅니다.
𝜇
=
0.1
μ=0.1은 공기와 같은 상대적으로 낮은 점성 유체를 모델링한 값입니다.
(3) 맥스웰 수 (
Mach
=
0.3
Mach=0.3)
맥스웰 수는 유체 속도 
𝑢
u와 음속 
𝑐
c의 비율을 나타냅니다:
Mach
=
𝑢
𝑐
Mach= 
c
u
​
 
이 시뮬레이션에서는 
𝑢
=
0.3
𝑐
u=0.3c, 즉 소리의 속도보다 느린 흐름(아음속 상태)을 가정합니다.
실제로는 압축성 효과가 무시될 수 있는 조건에서의 유체 흐름입니다.
(4) 격자 크기 (
𝑛
𝑥
=
𝑛
𝑦
=
41
nx=ny=41)
계산 영역을 
41
×
41
41×41 격자로 나눕니다. 이는 계산의 해상도를 결정하며, 더 많은 격자를 사용할수록 정확도가 높아집니다.
각 격자의 간격은 
𝑑
𝑥
=
𝑑
𝑦
=
2.0
𝑛
𝑥
−
1
dx=dy= 
nx−1
2.0
​
 로, 공간 내 특정 위치를 표현합니다.
(5) 시간 간격 (
𝑑
𝑡
=
0.01
dt=0.01)
시간의 단위 간격을 나타내며, 시뮬레이션의 안정성을 좌우합니다.
𝑑
𝑡
dt가 너무 크면 계산이 발산할 위험이 있고, 너무 작으면 계산 시간이 과도하게 늘어납니다.
설정된 
𝑑
𝑡
=
0.01
dt=0.01은 적절한 안정성을 보장하면서도 효율적인 계산이 가능한 값을 나타냅니다.
3. 대수기하적 관점에서 의미 추가
속도장의 시간적 변화:
나비에-스토크스 방정식의 운동량 방정식은 시간에 따른 속도장의 변화를 설명합니다:

∂
𝑢
⃗
∂
𝑡
+
(
𝑢
⃗
⋅
∇
)
𝑢
⃗
=
−
1
𝜌
∇
𝑝
+
𝜈
∇
2
𝑢
⃗
∂t
∂ 
u
 
​
 +( 
u
 ⋅∇) 
u
 =− 
ρ
1
​
 ∇p+ν∇ 
2
  
u
 
시간적 변화율 
∂
𝑢
⃗
∂
𝑡
∂t
∂ 
u
 
​
 : 속도 벡터 필드의 시간에 따른 변화.
비선형 항 
(
𝑢
⃗
⋅
∇
)
𝑢
⃗
( 
u
 ⋅∇) 
u
 : 유체의 운동이 자기 자신에게 미치는 효과를 나타냄.
점성 확산 
𝜈
∇
2
𝑢
⃗
ν∇ 
2
  
u
 : 유체 내부의 마찰에 의해 속도가 퍼지는 효과.
4. 요약
이 시뮬레이션은 유체 흐름을 단순화된 형태로 모델링하여 숫자의 의미를 명확히 하였고, 이를 대수기하적으로 다양한 필드가 공간과 시간 다양체에서 어떻게 상호작용하는지를 보여줍니다. 
𝜌
,
𝜇
,
Mach
ρ,μ,Mach 등의 파라미터는 유체의 물리적 특성과 흐름의 특성을 규정하며, 격자와 시간 간격은 계산의 정확성과 효율성에 영향을 미칩니다.
