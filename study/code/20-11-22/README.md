장요엘

```dart
import 'package:audioplayers/audio_cache.dart';
import 'package:flutter/material.dart';

void main() => runApp(XylophoneApp());

class XylophoneApp extends StatelessWidget {
  Color myColor = const Color(0xedc7af);
  void playSound(int soundNumber) {
    final player = AudioCache();
    player.play('note$soundNumber.wav');
  }

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        backgroundColor: Colors.white,
        body: SafeArea(
          child: Column(
            children: <Widget>[
              Container(
                child: Row(
                  children: <Widget>[
                    Container(
                      padding: EdgeInsets.all(20),
                      child: Text(
                        '김동현',
                        style: TextStyle(
                            fontSize: 20, fontWeight: FontWeight.bold),
                      ),
                    ),
                    ClipRRect(
                      borderRadius: BorderRadius.circular(10),
                      child: Container(
                        color: Colors.grey,
                        padding: EdgeInsets.all(5),
                        child: Text(
                          '내 계좌',
                          style: TextStyle(fontWeight: FontWeight.bold),
                        ),
                      ),
                    ),
                  ],
                ),
              ),
              SizedBox(
                height: 10,
              ),
              ClipRRect(
                borderRadius: BorderRadius.circular(15),
                child: Container(
                  color: Colors.grey,
                  padding: EdgeInsets.all(10),
                  width: 400,
                  child: Align(
                    child: Text(
                      '정부24 시스템 점검\n주민등록증을 이용한 서비스 불가 안내',
                      style: TextStyle(
                        fontWeight: FontWeight.bold,
                      ),
                    ),
                    alignment: Alignment.centerLeft,
                  ),
                ),
              ),
              SizedBox(
                height: 20,
              ),
              ClipRRect(
                borderRadius: BorderRadius.circular(15.0),
                child: Container(
                  padding: EdgeInsets.all(10),
                  width: 400,
                  height: 200,
                  color: Colors.pinkAccent,
                  child: Column(
                    children: <Widget>[
                      Container(
                        padding: EdgeInsets.all(10),
                        child: Align(
                          child: Text(
                            '김동현의 통장\n3333-07-738646',
                            style: TextStyle(fontWeight: FontWeight.bold),
                          ),
                          alignment: Alignment.topLeft,
                        ),
                      ),
                      SizedBox(
                        height: 30,
                      ),
                      Container(
                        child: Text(
                          '금액보기',
                          style: TextStyle(fontSize: 17),
                        ),
                      ),
                      SizedBox(
                        height: 15,
                      ),
                      Container(
                        child: Row(
                          mainAxisAlignment: MainAxisAlignment.spaceAround,
                          children: <Widget>[
                            Container(
                              child: FlatButton(
                                child: Text(
                                  '이체',
                                  style: TextStyle(
                                      color: Colors.black,
                                      fontWeight: FontWeight.bold),
                                ),
                                onPressed: () {
                                  playSound(1);
                                },
                              ),
                            ),
                            Container(
                              child: FlatButton(
                                child: Text(
                                  '카드이용내역',
                                  style: TextStyle(
                                      color: Colors.black,
                                      fontWeight: FontWeight.bold),
                                ),
                              ),
                            ),
                          ],
                        ),
                      )
                    ],
                  ),
                ),
              ),
              SizedBox(
                height: 20,
              ),
              ClipRRect(
                borderRadius: BorderRadius.circular(15),
                child: Container(
                  child: Row(
                    mainAxisAlignment: MainAxisAlignment.spaceBetween,
                    children: <Widget>[
                      Container(
                        child: Align(
                          alignment: Alignment.centerLeft,
                          child: Text(
                            '세이프박스',
                            style: TextStyle(
                                fontWeight: FontWeight.bold, fontSize: 15),
                          ),
                        ),
                      ),
                      Container(
                        child: Text('금액보기'),
                      )
                    ],
                  ),
                  color: Colors.pinkAccent,
                  padding: EdgeInsets.all(20),
                  width: 400,
                  height: 70,
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

김동현

```dart
import 'package:flutter/material.dart';
import 'package:hexcolor/hexcolor.dart';

class MyPageScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: SafeArea(
        child: Padding(
          padding: const EdgeInsets.all(10.0),
          child: SingleChildScrollView(
            child: Column(
              mainAxisAlignment: MainAxisAlignment.center,
              children: [
                SizedBox(
                  height: 40,
                ),
                Row(
                  mainAxisAlignment: MainAxisAlignment.spaceBetween,
                  children: [
                    Text('김동현'),
                    ClipRRect(
                      borderRadius: BorderRadius.all(Radius.circular(10)),
                      child: Container(
                        alignment: Alignment.center,
                        width: 50,
                        height: 30,
                        color: Colors.grey.withOpacity(0.3),
                        child: Text('내 계좌'),
                      ),
                    ),
                    SizedBox(
                      width: 240,
                    ),
                    CircleAvatar(
                      backgroundImage: NetworkImage(
                          'https://search.pstatic.net/common/?src=http%3A%2F%2Fblogfiles.naver.net%2F20150116_214%2Fthemcqueen_1421356573336eW2ch_JPEG%2F%25BE%25CB%25C6%25C4%25C4%25AB%25BC%25D2%25C0%25E7_10.JPG&type=sc960_832'),
                    ),
                  ],
                  // listTile하려다가 중간에 피봇
                  // leading: Text('김동현'),
                  // title: Container(
                  //   width: 50,
                  //   child: ClipRRect(
                  //     borderRadius: BorderRadius.all(Radius.circular(10)),
                  //     child: Container(
                  //       width: 30,
                  //       height: 50,
                  //       color: Colors.grey,
                  //       child: Text('내 계좌'),
                  //     ),
                  //   ),
                  // ),
                  // trailing: CircleAvatar(
                  //   backgroundImage: NetworkImage(
                  //       'https://search.pstatic.net/common/?src=http%3A%2F%2Fblogfiles.naver.net%2F20150116_214%2Fthemcqueen_1421356573336eW2ch_JPEG%2F%25BE%25CB%25C6%25C4%25C4%25AB%25BC%25D2%25C0%25E7_10.JPG&type=sc960_832'),
                  // ),
                ),
                SizedBox(height: 30),
                ClipRRect(
                  borderRadius: BorderRadius.all(Radius.circular(10)),
                  child: Container(
                    color: Colors.grey.withOpacity(0.3),
                    width: double.infinity,
                    height: 50,
                    child: ListTile(
                      leading: Column(
                        mainAxisAlignment: MainAxisAlignment.center,
                        crossAxisAlignment: CrossAxisAlignment.start,
                        children: [
                          Text('정부24 시스템점검'),
                          SizedBox(
                            height: 2,
                          ),
                          Text('주민등록증을 이요한 서비스 불가안내'),
                        ],
                      ),
                      trailing: Image.network(
                          'https://search.pstatic.net/common/?src=http%3A%2F%2Fblogfiles.naver.net%2FMjAxNzAzMDJfMjMw%2FMDAxNDg4NDM0NjAzMDc1.JscHVxNE4a1tD-FU4EDekszapyR5cPFn358wZ5fo0C8g.5_lwdYaB7NMO26UEVlA6YvZa78U5wsPfXTalPQDZ03Qg.JPEG.mjskin1%2F%25C4%25AB%25C4%25AB%25BF%25C0%25C5%25E5_%25C1%25F8%25B7%25E1_%25BF%25B9%25BE%25E0_%25BE%25C8%25B3%25BB.jpg&type=sc960_832'),
                    ),
                  ),
                ),
                SizedBox(height: 30),
                SizedBox(
                  height: 200,
                  width: double.infinity,
                  child: Card(
                    color: HexColor('#edc7af'),
                    shape: RoundedRectangleBorder(
                        borderRadius: BorderRadius.circular(15)),
                    child: Column(
                      mainAxisAlignment: MainAxisAlignment.spaceAround,
                      children: [
                        Row(
                          children: [
                            Column(
                              children: [
                                Row(
                                  children: [
                                    Text(
                                      '  김동현의 통장',
                                      style: TextStyle(fontWeight: FontWeight.bold),
                                    ),
                                    SizedBox(width: 270,),
                                    Icon(Icons.wrap_text_outlined)
                                  ],
                                )
                              ],
                            )
                          ],
                        ),
                        Text(
                          '금액보기',
                          style: TextStyle(),
                        ),
                        Row(
                          mainAxisAlignment: MainAxisAlignment.spaceAround,
                          children: [Text('이체'), Text('카드이용내역')],
                        ),
                      ],
                    ),
                  ),
                ),
                SizedBox(height: 10),
                SizedBox(
                  height: 80,
                  width: double.infinity,
                  child: Card(
                    color: HexColor('#edc7af'),
                    shape: RoundedRectangleBorder(
                        borderRadius: BorderRadius.circular(15)),
                    child: Row(
                      mainAxisAlignment: MainAxisAlignment.spaceAround,
                      children: [
                        Text('세이프박스'),
                        Text(''),
                        Text(
                          '금액보기',
                          style: TextStyle(color: Colors.grey.withOpacity(0.6)),
                        )
                      ],
                    ),
                  ),
                ),
                SizedBox(height: 10),
                SizedBox(
                  height: 80,
                  width: double.infinity,
                  child: Card(
                      color: Colors.grey.withOpacity(0.3),
                      shape: RoundedRectangleBorder(
                          borderRadius: BorderRadius.circular(15)),
                      child: Center(
                        child: Text(
                          '+',
                          style: TextStyle(
                              fontWeight: FontWeight.bold,
                              fontSize: 40,
                              color: Colors.black.withOpacity(0.3)),
                        ),
                      )),
                ),
                SizedBox(height: 10),
                Text(
                  '화면 편집',
                  style:
                      TextStyle(color: Colors.grey, fontWeight: FontWeight.bold),
                ),
                SizedBox(height: 80),

                Row(
                  mainAxisAlignment: MainAxisAlignment.spaceBetween,
                  children: [
                    Column(
                      crossAxisAlignment: CrossAxisAlignment.start,
                      children: [
                        Text(
                          '이번달 총 카드값',
                          style: TextStyle(fontWeight: FontWeight.bold),
                        ),
                        Text('궁금하면 내 신용정보에서 확인하세요.')
                      ],
                    ),
                    SizedBox(
                        height: 40,
                        child: Image.network(
                            'https://search.pstatic.net/common/?src=http%3A%2F%2Fblogfiles.naver.net%2FMjAxODAyMDFfMjcg%2FMDAxNTE3NDgxNjQ2MTA1.8IGFTqdUjfMxyEBjMaPYCeFaOPIUyfU0pW90TtZ_xqUg.AxIIQU-Ma1lcTath0bXauTOxmrU4csailLXnjpuQ4VMg.JPEG.baekhyun101%2FattachImage_2389077453.jpeg&type=sc960_832'))
                  ],
                )
              ],
            ),
          ),
        ),
      ),
    );
  }
}
```

변규리

```dart
import 'package:flutter/cupertino.dart';
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        body: SafeArea(
          child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            children: <Widget>[
              Row(
                mainAxisAlignment: MainAxisAlignment.center,
                children: <Widget>[
                  Container(
                    width: 100.0,
                    height: 30.0,
                    child: Text(
                      'NAME',
                      style: TextStyle(
                        fontSize: 20.0,
                        fontWeight: FontWeight.bold,
                      )
                    ),
                  ),
                  Container(
                    width: 50.0,
                    height: 30.0,
                    child: Text('내 계좌'),
                  ),
                  SizedBox(
                    width: 100.0,
                  ),
                  CircleAvatar(
                    radius: 30.0,
                    backgroundImage: AssetImage('images/profile.jpg'),
                  ),
                ],
              ),

              Column(
                mainAxisAlignment: MainAxisAlignment.spaceAround,
                children: <Widget>[
                  Container(
                  color: Colors.blue.shade300,
                  padding: EdgeInsets.all(50),
                  margin: EdgeInsets.all(30),
                  child: Column(
                    children: <Widget>[
                      Row(
                        mainAxisAlignment: MainAxisAlignment.spaceBetween,
                        children: <Widget>[
                          Column(
                            crossAxisAlignment: CrossAxisAlignment.start,
                            children: <Widget>[
                              Text('name의 통장',
                              ),
                              Text('3333-299488-29398'),
                            ],
                          ),
                          const Icon(
                            Icons.more_vert,
                            size: 16.0,
                          ),
                        ],
                      ),
                      Container(
                        padding: EdgeInsets.all(50),
                        child: Text('100000',
                        style: TextStyle(
                          fontSize: 30,
                        ),),
                      ),
                      Row(
                        mainAxisAlignment: MainAxisAlignment.spaceEvenly,
                        children: <Widget>[
                          Text('이체'),
                          SizedBox(
                            height: 20.0,
                            width: 10.0,
                            child: VerticalDivider(color : Colors.black),
                          ),
                          Text('카드이용내역'),
                        ],
                      )
                    ],
                  ),
                  ),
                ],
              ),
            ],
          ),
        ),
      ),
    );
  }
}
```

안준규

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
        title: 'Flutter Demo',
        home: Scaffold(
          body:SafeArea(
            child: Column(
              children: <Widget>[
              Container(height:50.0,
                width: 1000.0,
                padding: EdgeInsets.all(10.0),
                color: Colors.blueGrey,
                child: Text('안준규',
                    style: const TextStyle(
                    color:  Colors.black87,
                    fontWeight: FontWeight.w700,
                    fontFamily: "Rockness",
                    fontStyle:  FontStyle.normal,
                    fontSize: 20.0
                    ),
                ),
                   alignment: Alignment(-1.0,0.0),
                   ),
              Container(
                margin: EdgeInsets.all(10),
                padding: EdgeInsets.all(10),
                child: Align(
                  child: Text(
                    '정부24 시스템 점검\n주민등록증을 이용한 서비스 불가 안내',
                    style: TextStyle(
                      fontWeight: FontWeight.bold,
                    ),
                  ),
                  alignment: Alignment.centerLeft,
                ),
              ),
              ClipRRect(
                borderRadius: BorderRadius.circular(12.0),
                child: Container(
                  padding: EdgeInsets.all(10),
                  width: 400,
                  height: 200,
                  color: Colors.blueGrey,
                  child: Column(
                    children: <Widget>[
                      Container(
                        child: Align(
                          child: Text(
                            '안준의 통장\n3333-07-738646',
                            style: TextStyle(fontWeight: FontWeight.bold),
                          ),
                          alignment: Alignment.topLeft,
                        ),
                      ),
                      SizedBox(
                        height: 50,
                      ),
                      Container(
                        child: Text('금액보기'),
                      ),
                      SizedBox(
                        height: 20,
                      ),
                      Container(
                        child: Row(
                          mainAxisAlignment: MainAxisAlignment.spaceAround,
                          children: <Widget>[
                            Container(
                              child: FlatButton(
                                child: Text(
                                  '이체',
                                  style: TextStyle(
                                      color: Colors.black,
                                      fontWeight: FontWeight.bold),
                                ),
                              ),
                            ),
                            Container(
                              child: FlatButton(
                                child: Text(
                                  '카드이용내역',
                                  style: TextStyle(
                                      color: Colors.black,
                                      fontWeight: FontWeight.bold),
                                ),
                              ),
                            ),
                          ],
                        ),
                      )
                    ],
                  ),
                ),
              ),

                 Container(
                   child: Text('세이프박스'),
                   color: Colors.blueGrey,
                   padding: EdgeInsets.all(10),
                   margin: EdgeInsets.all(10),
                   width: 400,
                   height: 100,
               ),

                ]
              )
           ),

          ),

        );
  }
}

class MyHomePage extends StatefulWidget {
  MyHomePage({Key key, this.title}) : super(key: key);

  // This widget is the home page of your application. It is stateful, meaning
  // that it has a State object (defined below) that contains fields that affect
  // how it looks.

  // This class is the configuration for the state. It holds the values (in this
  // case the title) provided by the parent (in this case the App widget) and
  // used by the build method of the State. Fields in a Widget subclass are
  // always marked "final".

  final String title;

  @override
  _MyHomePageState createState() => _MyHomePageState();
}

class _MyHomePageState extends State<MyHomePage> {
  int _counter = 0;

  void _incrementCounter() {
    setState(() {
      // This call to setState tells the Flutter framework that something has
      // changed in this State, which causes it to rerun the build method below
      // so that the display can reflect the updated values. If we changed
      // _counter without calling setState(), then the build method would not be
      // called again, and so nothing would appear to happen.
      _counter++;
    });
  }

  @override
  Widget build(BuildContext context) {
    // This method is rerun every time setState is called, for instance as done
    // by the _incrementCounter method above.
    //
    // The Flutter framework has been optimized to make rerunning build methods
    // fast, so that you can just rebuild anything that needs updating rather
    // than having to individually change instances of widgets.
    return Scaffold(
      appBar: AppBar(
        // Here we take the value from the MyHomePage object that was created by
        // the App.build method, and use it to set our appbar title.
        title: Text(widget.title),
      ),
      body: Center(
        // Center is a layout widget. It takes a single child and positions it
        // in the middle of the parent.
        child: Column(
          // Column is also a layout widget. It takes a list of children and
          // arranges them vertically. By default, it sizes itself to fit its
          // children horizontally, and tries to be as tall as its parent.
          //
          // Invoke "debug painting" (press "p" in the console, choose the
          // "Toggle Debug Paint" action from the Flutter Inspector in Android
          // Studio, or the "Toggle Debug Paint" command in Visual Studio Code)
          // to see the wireframe for each widget.
          //
          // Column has various properties to control how it sizes itself and
          // how it positions its children. Here we use mainAxisAlignment to
          // center the children vertically; the main axis here is the vertical
          // axis because Columns are vertical (the cross axis would be
          // horizontal).
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            Text(
              'You have pushed the button this many times:',
            ),
            Text(
              '$_counter',
              style: Theme.of(context).textTheme.headline4,
            ),
          ],
        ),
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: _incrementCounter,
        tooltip: 'Increment',
        child: Icon(Icons.add),
      ), // This trailing comma makes auto-formatting nicer for build methods.
    );
  }
}
```
