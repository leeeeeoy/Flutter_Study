# 11/15 내용정리

## 새로 알게된 내용

- 플러터에서는 모든게 위젯이다, 마치 레고 블럭을 쌓는 거랑 비슷...
- Scafford - AppBar, Container - Column - Row - Text, Icon
- 테두리 부드럽게 표현 -> Card 사용
- stateless는 처음 한번만 빌드...
- stateful은 상태 변경마다 빌드?? ex) 버튼 클릭
- 비교적 간단한 코드로도 상당한 기능 구현이 가능하다
- 왜 인기 있는지 조금씩 느껴지는 것 같기도...

## 궁금한 내용

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
import 'dart:math';

import 'package:flutter/material.dart';

void main() => runApp(MagicBall());

class MagicBall extends StatefulWidget {
  @override
  _MagicBallState createState() => _MagicBallState();
}

class _MagicBallState extends State<MagicBall> {
  var num = 1;
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(
          title: Text(
            'Ask Me Anything!',
            style: TextStyle(fontWeight: FontWeight.bold),
          ),
          backgroundColor: Colors.lightBlueAccent,
        ),
        body: Container(
          child: Center(
            child: FlatButton(
              onPressed: () {
                setState(() {
                  num = Random().nextInt(5) + 1;
                  print('$num');
                });
              },
              child: Image.asset('images/ball$num.png'),
            ),
          ),
        ),
        backgroundColor: Colors.lightBlue,
      ),
    );
  }
}

```
