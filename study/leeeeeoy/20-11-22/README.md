# 11/15 내용정리

## 새로 알게된 내용

- 소리 파일이 재생이 잘 안됨...
- 애뮬에서는 잘 안되는데 폰으로 하니까 잘되는 듯...원인은 못 찾았다
- 많이 써보진 않았지만 그래도 있을 패키지는 다 있는듯...
- 시간 나면 한번 찾아봐야 겠다
- 공식 doc보는 습관도 들여야겠다(영알못...)
- 함수는 크게 다를건 없는 것 같다
- 인자에 위젯 옵션을 넣으려면 중괄호로 감싸는 거 조심
- Arrow function -> 익명함수 사용법에 좀 더 익숙해져야겠다!! Java 쓸때도 많이 안써서...

## 궁금한 내용

- 지난주에 찾아보고 싶었는데 아직 못찾아봤다...
- Provider Pattern
- 기존의 BLoc 패턴은 사용하기 너무 어렵다
- 관심사의 분리: 클래스가 하나의 역할만 갖도록, 클래스를 나눈다
- 데이터의 공유: 하나의 데이터를 여러 페이지에서 공유한다
- 좀 더 간결한 코드: Bloc 패턴에 비해 코드가 간결하다, 중규모 프로젝트에서는 프로바이더, 대규모 프로젝트에서는 Bloc 패턴
- 프로바이더는 데이터의 생산과 소비로 이루어져 있다.
- 개인적인 느낌으론 MVVM, MVC와 비슷한 형태의 구조적 패턴이 아닌가 싶은 생각...
- 관련해서 더 찾아봐야 겠다

## 같이 공유하고 싶은 내용

## 챌린지 코드

```dart
import 'package:audioplayers/audio_cache.dart';
import 'package:flutter/material.dart';

void main() => runApp(XylophoneApp());

class XylophoneApp extends StatelessWidget {
  void playSound(int soundNumber) {
    final player = AudioCache();
    player.play('note$soundNumber.wav');
  }

  Expanded buildKey({Color color, int soundNumber}) {
    return Expanded(
      child: FlatButton(
        onPressed: () {
          playSound(soundNumber);
        },
        color: color,
      ),
    );
  }

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        backgroundColor: Colors.black54,
        body: SafeArea(
          child: Column(
            crossAxisAlignment: CrossAxisAlignment.stretch,
            children: <Widget>[
              buildKey(color: Colors.red, soundNumber: 1),
              buildKey(color: Colors.orange, soundNumber: 2),
              buildKey(color: Colors.yellow, soundNumber: 3),
              buildKey(color: Colors.lightGreenAccent, soundNumber: 4),
              buildKey(color: Colors.green, soundNumber: 5),
              buildKey(color: Colors.blue, soundNumber: 6),
              buildKey(color: Colors.deepPurpleAccent, soundNumber: 7),
            ],
          ),
        ),
      ),
    );
  }
}
```
