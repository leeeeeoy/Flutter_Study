## Hot reload

hot reload는 stateless widget안에서만 작동

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(
    MyApp()
  );
}

class MyApp extends StatelessWidget {
  @override
  /* build : create new version of 'MyApp'
  if i change red -> teal, and click hot reload button,
  it check which one is most recently changed, and look the closest build function is and it re-run it. 
  ctrl+s 는 자동 hot reload <- fast as refreshing website
  less errors
  write cod -> test code의 사이클 time consumming 을 줄일 수 있음 
  = almost in real time.
   */
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        backgroundColor: Colors.teal,
        body: Container(),
      ),
    );
  }
}
```

## Single-child layout widgets

### container

Containers with no children try to be as big as possible 

**only have single child!**

```dart
home: Scaffold(
        backgroundColor: Colors.teal,
        body: Container(
                color: Colors.white,
        ),
      ),
```

화면 전체가 흰색으로 바뀐다. beacause our container is taking up all of the space that's available.

만일 밑에 child가 존재할 경우, child 사이즈로 바뀐다. 

```dart
home: Scaffold(
        backgroundColor: Colors.teal,
          child: Container(
            color: Colors.white,
            //container shrink to the size of the child widget
            //지금 child가 text라서 폰트 사이즈만큼의 사이즈를 가지고 있음
            child: Text('Hello'),
          )
	      ),
)
```

### safe area

위아래 바 부분, 베젤에 가리는 부분 제외 정상적으로 앱이 구동되는 범위부터 시작될 수 있도록 하는 위젯

```dart
home: Scaffold(
        backgroundColor: Colors.teal,
        //여기
        body: SafeArea(
          child: Container(
            color: Colors.white,
            child: Text('Hello'),
          ),
        ),
      ),
```

### margin & padding

- margin

```dart
child: Container(
            //size of container
            height: 100.0,
            width: 100.0,
            **//margin**
						// flutter inspector -> 상단에 파란색 네모 박스 누르면 마진이 파란색으로 보임
            //hv margin all 20 pixels left, right, top, bottom
            margin: EdgeInsets.all(20.0),
            // only top&bottom : 50,0, right and left: 10.0
            
            margin: EdgeInsets.symmetric(vertical: 50.0, horizontal: 10.0),
            //각자 설정하는 경우
            margin: EdgeInsets.fromLTRB(30.0, 10.0, 50.0, 20.0),
            //하나만 설정하는 경우. left마진만 30.0이고 나머지는 0.0
            margin: EdgeInsets.only(left: 30.0),
            color: Colors.white,
            //container shrink to the size of the child widget
            //지금 child가 text라서 폰트 사이즈만큼의 사이즈를 가지고 있음
            child: Text('Hello'),
),
```

- padding

container size가 100이고 padding이 좌우 20이면 중간 실제 context는 60만 사용됨. 

limiting child of container

edgeInsets사용방법은 margin과 동일

```dart
//padding
            padding: EdgeInsets.all(20.0),
```

## multi-child layout widgets

### row & coloumn

[medium.com/flutter-community/flutter-layout-cheat-sheet-5363348d037e](http://medium.com/flutter-community/flutter-layout-cheat-sheet-5363348d037e) 

- row

column이랑 같은 원리로 사용됨. 사용되는 function도 동일

- coloumn

```dart
body: SafeArea(
          child: Column(
            children: <Widget>[
              Container(
                height: 100.0,
                width: 100.0,
                color: Colors.white,
                child: Text('Container 1'),
              ),
              Container(
                width: 100.0,
                height: 100.0,
                color: Colors.blue,
                child: Text('Container 2'),
              ),
              Container(
                width: 100.0,
                height: 100.0,
                color: Colors.red,
                child: Text('Container 3'),
              ),
            ],
          )
        ),
```

automatically try and take up as much of the vertical space as possible. But horizontally, it's limiting size of the children. ⇒ mainAxisSize: MainAxisSize.min,

```dart
child: Column(
		mainAxisSize: MainAxisSize.min,
    children: <Widget>[
		    Container( ),
		    Container( ),
		    Container( ),
    ],
)
```

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5b9fed41-598a-470a-b425-35c908381bbd/2020-11-22_01_26_47.jpg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5b9fed41-598a-470a-b425-35c908381bbd/2020-11-22_01_26_47.jpg)

original

밑에서 부터 위로 올라오게 하는 것 : verticalDirection: VerticalDirection.up,ㅇ

위에서부터 아래로 (defalut): verticalDirection: VerticalDirection.down,

start on end of main axis.(일단 밑에서 위로 하는거랑 비슷함.): mainAxisAlignment: MainAxisAlignment.end,

중앙 정렬: mainAxisAlignment: MainAxisAlignment.center,

calculate free space that column has, and it'll space all of our children evely. : mainAxisAlignment: MainAxisAlignment.spaceEvenly,

→ space container space container space container space 형식으로 정렬된다.

mainAxisAlignment: MainAxisAlignment.spaceBetween,

→ container space container space container 순서대로.

crossAxisAlignment: CrossAxisAlignment.end,

→ 우측 정렬. container 사이즈가 다를경우 우측정렬.

crossAxisAlignment: CrossAxisAlignment.end,

```dart
child: Column(
		crossAxisAlignment: CrossAxisAlignment.end,
    children: <Widget>[
		    Container( ),
		    Container( ),
		    Container( ),
		    Container(
				    width: double.infinity, 
//invisible container. 화면에서 차지할 수 있는 최대 범위를 사용한다. crossAxisAlignment때문에 모든 컨테이너들이 화면에서 우측 정렬
		    ),
    ],
)

```

crossAxisAlignment: CrossAxisAlignment.stretch, 

← 모든 컨테이너들이 width: double.infinity와 같은 결과를 내고 있음. 

```dart
child: Column(
            crossAxisAlignment: CrossAxisAlignment.stretch,
            children: <Widget>[
              Container(
                width: 100.0,
                color: Colors.white,
                child: Text('Container 1'),
              ),
              Container(
                height: 100.0,
                color: Colors.blue,
                child: Text('Container 2'),
              ),
              Container(
                height: 100.0,
                color: Colors.red,
                child: Text('Container 3'),
              ),
            ],
          )
```

SizedBox ← 대충 컨테이너 사이 빈공간... 만들기...

```dart
child: Column(
		crossAxisAlignment: CrossAxisAlignment.stretch,
    children: <Widget>[
		    Container( ),
				SizedBox(
                height: 20.0,
        ),
		    Container( ),
		    Container( ),
    ],
)
```

- flutter layouts challenge

단축키

ctrl+Q: open quick doc

ctrl+ /: 주석 제거(yaml)

### font

1. download new font and put font in the project/new_directory
2. in pubspec.yaml add this under flutter:

```yaml
fonts:
    - family: Pacifico
      fonts:
      - asset: fonts/Pacifico-Regular.ttf

```

3. put get

4. main.dat에서 fontFamily: 'Pacifico', 사용.

### make name card using column and container

- code

    ```dart
    import 'package:flutter/cupertino.dart';
    import 'package:flutter/material.dart';

    void main() {
      runApp(
        MyApp()
      );
    }

    class MyApp extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return MaterialApp(
          home: Scaffold(
            backgroundColor: Colors.teal,
            body: SafeArea(
              child: Column(
                children: <Widget>[
                  //ctrl + Q : open quick doc
                  CircleAvatar(
                    radius: 50.0,
                    //radius가 화면보다 커지면...진짜...이상한... 타원 윗부분..처럼 된다...
                    backgroundImage: AssetImage('images/pic.jpg'),
                  ),
                  Text(
                    'Gyuri',
                    style: TextStyle(
                      fontFamily: 'Pacifico',
                      fontSize: 40.0,
                      color: Colors.white,
                    ),
                  ),
                  Text(
                    'FLUTTER DEVELOPER',
                    style: TextStyle(
                      fontFamily: 'SourseSansPro',
                      color: Colors.teal.shade100,
                      fontSize: 20,
                      letterSpacing: 2.5,
                      fontWeight: FontWeight.bold,
                    ),
                  ),
                  Container(
                    color: Colors.white,
                    padding: EdgeInsets.all(10),
                    margin: EdgeInsets.symmetric(
                        vertical: 10,
                        horizontal: 25),
                    child: Row(
                      children: <Widget>[
                        Icon(
                            Icons.phone,
                            //size: 10,//사이즈가 너무 크면 대충 화면 넘어감
                            color: Colors.teal,
                        ),
                        SizedBox(
                          width: 10,
                        ),
                        Text(
                          '+86 010 2134 2353',
                          style: TextStyle(
                            color: Colors.teal.shade900,
                            fontFamily: 'SourceSansPro',
                            fontSize: 20,
                          ),
                        )
                      ],
                    ),
                  ),
                  Container(
                    color: Colors.white,
                    padding: EdgeInsets.all(10,0),
                    margin: EdgeInsets.symmetric(
                        vertical: 10,
                        horizontal: 25),
                    child: Row(
                      children: <Widget>[
                        Icon(
                          Icons.email,
                          //size: 10,//사이즈가 너무 크면 대충 화면 넘어감
                          color: Colors.teal,
                        ),
                        SizedBox(
                          width: 10,
                        ),
                        Text(
                          'abcd@gmail.com',
                          style: TextStyle(
                            color: Colors.teal.shade900,
                            fontFamily: 'SourceSansPro',
                            fontSize: 20,
                          ),
                        )
                      ],
                    ),
                  ),
                ],
              )
            ),
          ),
        );
      }
    }
    ```