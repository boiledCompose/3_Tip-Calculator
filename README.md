<p>

# 상태
> 앱의 상태는 시간이 지남에 따라 변할 수 있는 값입니다.
<br>

## 컴포지션
**Composable**은 일부 텍스트, 공백, 텍스트 상자와 함께 열이 표시된 UI를 설명해주는 기능   
**Compose**는 선언형 UI 프레임워크로, UI의 모습을 코드로 선언하는 것   
**Composition**은 Compose가 Composable을 실행할 때 빌드한 UI에 관한 설명   

1. Compose는 초기 composition 시 처음으로 composable을 실행할 때 composition에서 UI를 기술하기 위해 호출하는 composable을 추적한다.
2. Compose는 데이터 변경사항에 따라 변경될 수 있는 composable을 다시 실행한 다음 변경사항을 반영하도록 Composition을 업데이트한다. 이 업데이트를 **Recomposition**이라고 한다.
> [!NOTE]
> 컴포지션을 수정하는 유일한 방법은 리컴포지션을 통하는 것이다.
<br>

### State & MutableState
Compose에선 이 두 유형을 사용하여 앱의 상태를 관찰 가능하거나 추적 가능한 상태로 설정할 수 있다.
- State 유형은 변경할 수 없어 그 유형의 값만 읽을 수 있다.
- MutableState 유형은 변경이 가능하다.

`mutableStateOf()` 함수를 사용하여 MutableState 유형의 변수를 선언할 수 있다.

> [!WARNING]
> 앱 실행 중 변수값과 UI가 바뀌어야 하는 경우 mutableStateOf()를 써서 변수 내용을 바꿀 순 있지만, 상태가 바뀐 내용을 기억하지 못하면 UI는 변경되지 않는다.    
> 이를 해결하기 위해 `remember` 함수가 사용된다.
<br>

### remember
Composable 함수는 `remember`를 사용하여 recomposition에서 객체를 저장할 수 있다.   
일반적으로 `mutableStateOf()`와 `remember` 함수가 함께 사용되어 Recomposition시 UI에 변경사항을 적용한다.
```
var amountInput by remember { mutableStateOf("") }
```
<br>

## 상태 호이스팅
한 composable에서 다른 composable 내의 상태에 엑세스해야 하는 경우, 다른 composable의 상태를 호이스팅, 추출을 통해 상태를 꺼내는 기법을 사용해야 한다.   
상태를 추출해야 하는 경우는:
 - 상태를 여러 composable과 공유하는 경우
 - 앱에서 재사용할 수 있는 stateless composable을 만드는 경우
>[!NOTE]
> 상태 호이스팅은 구성요소를 스테이트리스(Stateless)로 만들기 위해 상태를 호출자로 이동하는 패턴이다.
- **stateless composable**은 상태가 없는 composable로, 새 상태를 보유하거나 정의하거나 수정하지 않는다.
- **stateful composable**은 시간이 지남에 따라 변할 수 있는 상태를 소유하는 composable이다.

>[!TIP]
> stateless로 변환할 composable에 선언된 변수들을 인자로 받도록 수정하는 것이 호이스팅이다! 이를 통해 stateless composable에서 변경되는 변수 값에 다른 composable이 접근할 수 있게 된다.



</p>
