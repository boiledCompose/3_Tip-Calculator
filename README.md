# Tip-Calculator

### Composition
**컴포지션**은 Compose가 Composable을 실행할 때 빌드한 UI에 관한 설명이다. 앱이 실행되는 동안 또는 사용자가 앱과 상호작용할 때 UI를 변경하고자 한다면 **리컴포지션**이라는 프로세스를 사용하여 앱의 컴포지션을 업데이트한다.

 다음 과정을 통해 UI를 업데이트한다:
1. Compose은 초기 컴포지션을 통해서 처음으로 Composable 함수를 실행한다. 이때 컴포지션에서 UI를 기술하기 위해 호출하는 Composable을 추적한다.
2. 앱 실행 중간에 데이터가 변경되면 리컴포지션을 통해 Compose가 변경될 수 있는 Composable을 다시 실행한다. 이때 변경사항을 반영하도록 컴포지션을 업데이트한다.

리컴포지션을 통해 컴포지션을 수정하려면 Compose가 추적할 **상태**를 알아햐 한다. 그래야 Compose가 업데이트를 받을 때 리컴포지션을 예약할 수 있다. 이럴 때 사용되는 것이 바로 **State** 및 **MutableState** 유형이다. 

Compose에선 두 유형을 사용하여 앱의 상태를 관찰하거나 추적할 수 있는 상태로 설정할 수 있다. State 유형은 값을 변경할 수 없고, MutableState 유형은 값을 변경할 수 있다.

```
var amountInput:MutableState<String> = mutableStateOf("0")
```
