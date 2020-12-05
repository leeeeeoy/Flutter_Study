# 12/06 내용정리

## 새로 알게된 내용

- 앱 전체 테마 설정 가능 -> 위젯마다 다시 재설정 가능
- final, const 쓰는 습관 들이기
- const는 컴파일 단계에서 값 대입
- final은 런타임 단계에서 값 대입 -> const가 조금 더 빠름
- class에서 1회 설정할 값은 final 할당
- Color나 TextStyle 등 고정 값들에는 const 할당
- Enum, 3항 연산자도 사용법 비슷

## 궁금한 내용

## 같이 공유하고 싶은 내용

## BLoC 패턴 ex)

### 1. BlocBuilder

```dart
BlocBuilder<ExampleBloc, ExampleState>(
    bloc : \_exampleBloc;
    builder : (BuilderContext cotext, ExampleState state){
    return ...
    }
)
```

- BlocBuilder의 필수 요건은 bloc과 builder 옵션
- bloc: widget에서 사용하게 되는 bloc을 받게 됨
- builder: state들이 업데이트 될 때 새로이 그려지게 되는 부분
- return값은 Widget

### 2. BlocProvider

```dart
BlocProvider<ExampleBloc>(
     create: (BuildContext context) => ExampleBloc(),
     child: Widget...
)

BlocProvider<ExampleBloc>.value(
    value : BlocProvider.of<ExampleBloc>(context),
    child : Widget...
)
```

- 새로운 bloc을 만들거나, 만들어진 bloc을 다른 페이지로 넘겨 계속 사용할 수 있도록 해주는 역할
- 새로운 bloc을 만들 때는 위의 코드(create)처럼 사용
- 원래 있던 bloc을 다른 곳에서 사용하고 싶을 때는 아래 코드(value)처럼 사용

### 3. MultiBlocProvider

```dart
MultiBlocProvider(
    povider : [
        BlocProvider<ExampleBlocA>(
            create : (BuildContext context) => ExampleBlocA(),
        ),
        BlocProvider<ExampleBlocB>(
            create : (BuildContext context) => ExampleBlocB(),
        ),
        BlocProvider<ExampleBlocC>(
            create : (BuildContext context) => ExampleBlocC(),
        ),
    ],
    child : Widget...
)
```

- bloc을 여러 곳에서 사용할 때 사용
- BlocProvider 중첩 사용 대신 MultiBlocProvider 사용 -> 코드 가독성 상향

### 4. BlocListner

```dart
BlocListener<ExampleBloc, ExampleState>(
    bloc : exampleBloc,
    listener : (BuildeContext context, ExampleState state){
       //state의 변경에 따라 실행 되어야 하는것들
    }
)
```

- state의 변화에 대해 반응을 하는 부분
- 상태 변경 시 한번씩 발생해야 하는 기능에 대해서 사용 ex) 다른 페이지로 라우팅
- state의 변화가 생겼을 때 한번 불려서 사용됨

### 5. MultiBlocListener

```dart
MultiBlocListener(
    listener : [
        BlocListener<ExampleBlocA, ExampleStateA>(
            listener : (BuildContext context){},
        ),
        BlocListener<ExampleBlocB, ExampleStateB>(
            listener : (BuildContext context){},
        ),
        BlocListener<ExampleBlocC, ExampleStateC>(
            listener : (BuildContext context){},
        ),
    ],
    child : Widget...
)
```

- 여러개의 bloc이 존재할 때 사용할 용도 -> MultiBlocProvider와 비슷
