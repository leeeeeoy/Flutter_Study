# 11/29 내용정리

## 새로 알게된 내용

- 배경화면 넣는 거, 알림 창 생성 생각보다 간편하다
- 생성자 인자 구분넣는거 습관 들이면 디버깅 할 때 편할 것 같다
- 배열, 클래스 등은 기존 OOP랑 비슷해서 크게 어렵지 않다
- 화면이 점점 늘어난다 -> 분리해서 설계해야 할 필요가 있어보인다

## 궁금한 내용

### BLoC 패턴

- 구글에서 미는 디자인 패턴 -> MVC or MVVM 과 비슷??
- 프로젝트의 중앙에서 데이터에 엑세스 -> Controller??
- Flutter에서는 상태에 따라서 렌더링 -> 상태관리가 매우 중요
- UI 와 Bussiness Logic을 분리 -> 코드 의존성을 줄인다

#### BLoC의 형태

- 각 UI 객체들은 BLoC객체를 구독(참조)?? -> BLoC 상태가 변경되면 UI객체들은 해당 상태로 UI를 변경
- BLoC 객체는 UI객체로부터 이벤트를 전달받음 -> 필요한 Provider or Repository부터 데이터 처리
- 이후 UI 객체로 전달 -> 상태 변경
- Flutter에서는 Stream을 이용해서 BLoC 구현

#### BLoC의 특징

- UI에서는 여러 BLoC가 존재 할 수 있음
- UI는 화면, BLoC는 로직에 집중
- UI는 BLoC이 어떻게 설계 되었는지 알 필요 없음
- 한개의 BLoC를 여러 UI가 구독 가능
- BLoC만 분리해서 Test 가능

## 같이 공유하고 싶은 내용

## 챌린지 코드

```dart
import 'package:flutter/material.dart';

import 'story_brain.dart';

void main() => runApp(Destini());

class Destini extends StatelessWidget {
  Widget build(BuildContext context) {
    return MaterialApp(
      theme: ThemeData.dark(),
      home: StoryPage(),
    );
  }
}

StoryBrain storyBrain = StoryBrain();

class StoryPage extends StatefulWidget {
  _StoryPageState createState() => _StoryPageState();
}

class _StoryPageState extends State<StoryPage> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Container(
        decoration: BoxDecoration(
            image: DecorationImage(
          image: AssetImage('images/background.png'),
          fit: BoxFit.cover,
        )),
        padding: EdgeInsets.symmetric(vertical: 50.0, horizontal: 15.0),
        constraints: BoxConstraints.expand(),
        child: SafeArea(
          child: Column(
            crossAxisAlignment: CrossAxisAlignment.stretch,
            children: <Widget>[
              Expanded(
                flex: 12,
                child: Center(
                  child: Text(
                    storyBrain.getStory(),
                    style: TextStyle(
                      fontSize: 25.0,
                    ),
                  ),
                ),
              ),
              Expanded(
                flex: 2,
                child: Visibility(
                  child: FlatButton(
                    onPressed: () {
                      setState(() {
                        storyBrain.nextStory(1);
                      });
                    },
                    color: Colors.red,
                    child: Text(
                      storyBrain.getChoice1(),
                      style: TextStyle(
                        fontSize: 20.0,
                      ),
                    ),
                  ),
                ),
              ),
              SizedBox(
                height: 20.0,
              ),
              Expanded(
                flex: 2,
                child: Visibility(
                  visible: storyBrain.buttonShouldBeVisible(),
                  child: FlatButton(
                    onPressed: () {
                      setState(() {
                        storyBrain.nextStory(2);
                      });
                    },
                    color: Colors.blue,
                    child: Text(
                      storyBrain.getChoice2(),
                      style: TextStyle(
                        fontSize: 20.0,
                      ),
                    ),
                  ),
                ),
              ),
            ],
          ),
        ),
      ),
    );
  }
}

```
