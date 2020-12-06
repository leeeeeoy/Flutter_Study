장요엘

```dart
import 'package:flutter/material.dart';
import 'package:flutter_api_practice/quiz.dart';

const myStyle = TextStyle(
  fontWeight: FontWeight.bold,
  fontSize: 20.0,
);
void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      home: MyHomePage(),
    );
  }
}

class MyHomePage extends StatefulWidget {
  @override
  _MyHomePageState createState() => _MyHomePageState();
}

class _MyHomePageState extends State<MyHomePage> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Loooooooooooooool'),
      ),
      body: SafeArea(
        child: Padding(
          padding: const EdgeInsets.all(10),
          child: Column(
            crossAxisAlignment: CrossAxisAlignment.stretch,
            children: <Widget>[
              Expanded(
                child: FlatButton(
                  child: Align(
                    alignment: Alignment.centerLeft,
                    child: Text(
                      'Chapter 1',
                      style: myStyle,
                    ),
                  ),
                  color: Colors.lightGreenAccent,
                  onPressed: () {
                    Navigator.push(
                      context,
                      MaterialPageRoute(builder: (context) => QuizPage()),
                    );
                  },
                ),
              ),
              SizedBox(
                height: 5.0,
              ),
              Expanded(
                child: FlatButton(
                  child: Text('2번'),
                  color: Colors.blue,
                  onPressed: () {
                    print("2");
                  },
                ),
              ),
              SizedBox(
                height: 5.0,
              ),
              Expanded(
                child: FlatButton(
                  child: Text('3번'),
                  color: Colors.green,
                  onPressed: () {
                    print("3");
                  },
                ),
              ),
              SizedBox(
                height: 5.0,
              ),
              Expanded(
                child: FlatButton(
                  child: Text('4번'),
                  color: Colors.deepPurpleAccent,
                  onPressed: () {
                    print("4");
                  },
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

변규리

```dart
import 'package:flutter/cupertino.dart';
import 'package:flutter/material.dart';

void main() {
  return runApp(
    MaterialApp(
    home: FlashCardPage(),
  ));
}

class FlashCardPage extends StatefulWidget {
  _FlashCardState createState() => _FlashCardState();
}

class Quiz1 extends StatelessWidget{
  int i = 1;
  List<String> dicE = ['apple', 'banana', 'kiwi', 'strawberry'];
  List<String> dicK = ['사과', '바나나', '키위', '딸기'];
  List<String> texts = ['apple', 'banana', 'kiwi', 'strawberry'];

  Padding mk_card(int n) {
    return Padding(
      padding: const EdgeInsets.all(8.0),
      child: FlatButton(
        height: 100,
        child: Text(
          texts[n],
          style: TextStyle(
            fontSize: 18,
            fontWeight: FontWeight.bold,
            color: Colors.white,
          ),
        ),
        color: Colors.black38,
        onPressed: () {
          // setState(() {
          //   texts[n] = dicK[n];
          //   print(texts[n]);
          // });
        },
      ),
    );
  }

  Widget build(BuildContext context) {
    return MaterialApp(
        home: Scaffold(
          body: SafeArea(
        child: Padding(
        padding: EdgeInsets.all(10.0),
          child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            crossAxisAlignment: CrossAxisAlignment.stretch,
            children: <Widget>[
              mk_card(0),
              mk_card(1),
              mk_card(2),
              mk_card(3),
          ],
          ),
       ),
        ),),);
  }
}

class Quiz2 extends StatelessWidget{
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        body: SafeArea(
          child: Text('Quiz2'),),
      ),);
  }
}

class Quiz3 extends StatelessWidget{
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        body: SafeArea(
          child: Text('Quiz3'),),
      ),);
  }
}

class _FlashCardState extends State<FlashCardPage> {
  /*
Card chap_card(int n) {
    int last = n *  30;
    int beginning = last - 29;
    return Card(
      child: Column(
        children: <Widget>[
          ListTile(
            title: Text('chap$n'),
            subtitle: Text('`$beginning~$last'),
          ),
        ],
      ),
    );
  }
*/

  Container chap_card(int n){
    int last = n *  30;
    int beginning = last - 29;
    return Container(
      margin: EdgeInsets.all(3.0),
      child: FlatButton(
        child: Column(
          children: <Widget>[
            ListTile(
              title: Text('chap$n'),
              subtitle: Text('`$beginning~$last'),
            )
          ],
        ),
      onPressed: (){
          switch(n){
            case 1:
              Navigator.push(context, MaterialPageRoute(builder: (context)=> Quiz1(),));
              break;
            case 2:
              Navigator.push(context, MaterialPageRoute(builder: (context)=> Quiz2(),));
              break;
            case 3:
              Navigator.push(context, MaterialPageRoute(builder: (context)=> Quiz3(),));
              break;
          };
        },
      ),
    );
  }
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar:AppBar(
          title: Text('Adjust your chapter selection.'),
          backgroundColor: Colors.black,
        ),
        body: SafeArea(
          child: Column(
            crossAxisAlignment: CrossAxisAlignment.stretch,
            children: <Widget> [
              chap_card(1),
              Divider(height: 1.0),
              chap_card(2),
              Divider(height: 1.0),
              chap_card(3),
              Divider(height: 1.0,),
              Padding(
                padding: EdgeInsets.symmetric(horizontal: 100),
                child: RaisedButton(
                  child: Text('go to Vocab page'),
                  color: Colors.blue.shade200,
                  onPressed: (){},)
              ),
            ],
          ),


          /*
          child: Padding(
            padding: EdgeInsets.all(10.0),
            child: Column(
              mainAxisAlignment: MainAxisAlignment.center,
              crossAxisAlignment: CrossAxisAlignment.stretch,
              children: <Widget>[
                mk_card(0),
                mk_card(1),
                mk_card(2),
                mk_card(3),
              ],
            ),
          ),*/
        ),
      ),
    );
  }
}
```

김동현

```dart
import 'package:flutter/material.dart';
import 'package:get/get.dart';
import 'package:practice1206/widgets/build_switch_listtile.dart';

import 'chap1_screen.dart';
import 'chap2_screen.dart';
import 'chap3_screen.dart';
import 'chap4_screen.dart';
import 'chap5_screen.dart';
import 'chap6_screen.dart';

class TabScreen extends StatefulWidget {
  @override
  _TabScreenState createState() => _TabScreenState();
}

class _TabScreenState extends State<TabScreen> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Column(
        children: <Widget>[
          SizedBox(
            height: 30,
          ),
          Container(
            padding: EdgeInsets.all(20),
            child: Text(
              'Adjust your chapter selection.',
              style: Theme.of(context).textTheme.title,
            ),
          ),
          FlatButton(onPressed: () {
            Navigator.push(context, MaterialPageRoute(builder: (context)=>Chap1Screen()));
          }, child: Text('아무꺼'),),
          Expanded(
            child: ListView(
              children: <Widget>[
                Column(
                  crossAxisAlignment: CrossAxisAlignment.start,
                  children: [
                    GestureDetector(child: BuildSwitchListTile('chap1', '1~30'),onTap: () {
                      Navigator.push(context, MaterialPageRoute(builder: (context)=> Chap1Screen()));
                    },),
                    SizedBox(height: 10,),
                    GestureDetector(child: BuildSwitchListTile('chap2', '31~60'),onTap: () {
                      Get.to(Chap2Screen());
                    },),
                    SizedBox(height: 10,),
                    GestureDetector(child: BuildSwitchListTile('chap3', '61~90'),onTap: () {
                      Get.to(Chap3Screen());
                    },),
                    SizedBox(height: 10,),
                    GestureDetector(child: BuildSwitchListTile('chap4', '91~120'),onTap: () {
                      Get.to(Chap4Screen());
                    },),
                    SizedBox(height: 10,),
                    GestureDetector(child: BuildSwitchListTile('chap5', '121~150'),onTap: () {
                      Get.to(Chap5Screen());
                    },),
                    SizedBox(height: 10,),
                    GestureDetector(child: BuildSwitchListTile('chap6', '151~180'),onTap: () {
                      Get.to(Chap6Screen());
                    },),
                  ],
                ),
                SizedBox(
                  height: 30,
                ),
              ],
            ),
          ),
                Align(
                  alignment: Alignment.bottomCenter,
                  child: FlatButton(
                      color: Colors.lime,
                      onPressed: () {},
                      child: Text('go to VocaPage')),
                ),
          SizedBox(height: 20,),
        ],
      ),
    );
  }
}
```