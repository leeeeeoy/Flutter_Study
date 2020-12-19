# 12/20 내용정리

## 새로 알게된 내용

- Navigator 화면 이동 -> 스택과 비슷함
- Push 하면 해당 페이지로 이동, Pop 하면 이전 페이지로 이동
- context를 통해 데이터 or 상태 전달 가능
- 화면이 늘어남 -> 프로젝트 구조 설정 필요
- 화면단위로 자르기, 특정 기능마다 잘기
- 후에 전체적인 상태 관리에 대한 공부 필요

## 궁금한 내용

## 같이 공유하고 싶은 내용

## Navigator 사용

- 해당 페이지로 이동
- builder를 통해 해당 페이지로 전달할 요소들 설정

```dart
    BottomButton(
            buttonTitle: 'CALCULATE',
            onTap: () {
              CalculatorBrain calc = CalculatorBrain(
                height: userHeight,
                weight: weight,
              );
              Navigator.push(
                context,
                MaterialPageRoute(
                  builder: (context) => ResultsPage(
                    bmiResult: calc.calculateBMI(),
                    resultText: calc.getResult(),
                    interpretation: calc.getInterpretation(),
                  ),
                ),
              );
            },
          ),
```

- 이전 페이지로 이동

```dart
    BottomButton(
            onTap: () {
              Navigator.pop(context);
            },
            buttonTitle: 'RE-CALCULATE',
          ),
```
