장요엘

```dart
import 'package:flutter/material.dart';

const myStyle = TextStyle(
  fontWeight: FontWeight.bold,
  fontSize: 20.0,
);
void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  // This widget is the root of your application.
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
  List<String> words = ['A', 'B', 'C', 'D', 'E', 'F', 'G', 'H'];
  List<String> changeWords = ['에이', '비', '씨', '디', '이', '에프', '쥐', '에이치'];
  List<String> curWords = ['A', 'B', 'C', 'D', 'E', 'F', 'G', 'H'];

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(
          'Loooool',
          style: TextStyle(
            fontWeight: FontWeight.bold,
            color: Colors.red,
          ),
        ),
        backgroundColor: Colors.lightGreen.shade50,
      ),
      body: SafeArea(
        child: Padding(
          padding: const EdgeInsets.all(10),
          child: Column(
            children: <Widget>[
              Expanded(
                child: Row(
                  crossAxisAlignment: CrossAxisAlignment.stretch,
                  children: [
                    myFlatButton(
                      number: 0,
                      color: Colors.limeAccent,
                    ),
                    SizedBox(width: 5),
                    myFlatButton(
                      number: 1,
                      color: Colors.pinkAccent,
                    ),
                  ],
                ),
              ),
              SizedBox(height: 5),
              Expanded(
                child: Row(
                  mainAxisAlignment: MainAxisAlignment.spaceAround,
                  crossAxisAlignment: CrossAxisAlignment.stretch,
                  children: [
                    myFlatButton(
                      number: 2,
                      color: Colors.deepPurpleAccent,
                    ),
                    SizedBox(width: 5),
                    myFlatButton(
                      number: 3,
                      color: Colors.lightBlueAccent,
                    ),
                  ],
                ),
              ),
              SizedBox(height: 5),
              Expanded(
                child: Row(
                  mainAxisAlignment: MainAxisAlignment.spaceAround,
                  crossAxisAlignment: CrossAxisAlignment.stretch,
                  children: [
                    myFlatButton(
                      number: 4,
                      color: Colors.black26,
                    ),
                    SizedBox(width: 5),
                    myFlatButton(
                      number: 5,
                      color: Colors.white38,
                    ),
                  ],
                ),
              ),
              SizedBox(height: 5),
              Expanded(
                child: Row(
                  mainAxisAlignment: MainAxisAlignment.spaceAround,
                  crossAxisAlignment: CrossAxisAlignment.stretch,
                  children: [
                    myFlatButton(
                      number: 6,
                      color: Colors.red,
                    ),
                    SizedBox(width: 5),
                    myFlatButton(
                      number: 7,
                      color: Colors.deepOrangeAccent,
                    ),
                  ],
                ),
              ),
            ],
          ),
        ),
      ),
    );
  }

  Widget myFlatButton({int number, Color color}) {
    return Expanded(
      child: FlatButton(
        onPressed: () {
          setState(() {
            changeWord(number);
          });
        },
        color: color,
        child: Text(
          curWords[number],
          style: myStyle,
        ),
      ),
    );
  }

  void changeWord(int wordNumber) {
    if (curWords[wordNumber] == words[wordNumber]) {
      curWords[wordNumber] = changeWords[wordNumber];
    } else {
      curWords[wordNumber] = words[wordNumber];
    }
  }
}

```

김동현

```dart
import 'package:flutter/material.dart';
import 'package:voca/models/Vocas.dart';


void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(
        primarySwatch: Colors.blue,
        visualDensity: VisualDensity.adaptivePlatformDensity,
      ),
      home: VocaScreen(),
    );
  }
}

class VocaScreen extends StatefulWidget {
  @override
  _VocaScreenState createState() => _VocaScreenState();
}

class _VocaScreenState extends State<VocaScreen> {

  Vocas study = Vocas();
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        backgroundColor: Colors.brown,
        title: Text('Voca'),
      ),
      body: ListView.builder(
        itemCount: study.items.length,
          itemBuilder: (_, i) => Column(
            children: [
              GestureDetector(
                child: Container(
                  alignment: Alignment.center,
                  color: Colors.lime,
                  width: double.infinity,
                  height: 140,
                  child: Text(study.items[i].e_k == false ? study.items[i].english : study.items[i].korean,
                  style: TextStyle(fontSize: 30),),
                ),

                onTap: () {
                  setState(() {
                    study.items[i].e_k = !study.items[i].e_k;
                  });
                },
              ),
              SizedBox(height: 10,),
            ],
          ))
    );
  }
}
```

변규리

```dart
import 'package:flutter/cupertino.dart';
import 'package:flutter/material.dart';

void main() {
  return runApp(MaterialApp(
      home: Scaffold(
    appBar: AppBar(
      title: Text('flash card'),
    ),
    body: FlashCardPage(),
  )));
}

class FlashCardPage extends StatefulWidget {
  _FlashCardState createState() => _FlashCardState();
}

class _FlashCardState extends State<FlashCardPage> {
  int i = 1;
  List<String> dicE = ['apple', 'banana', 'kiwi', 'strawberry'];
  List<String> dicK = ['사과', '바나나', '키위', '딸기'];
  String text = 'adf';
/*
  void chg_card(n)
  {
    return setState(() {
      i = (i + 1) % 2;
      if(i == 1)
      {
        Text('$i');
      }
      else {
        Text('$i');
      }
    });
  }
*/
  Padding mk_card(int n) {
    text = dicE[n];
    return Padding(
      padding: const EdgeInsets.all(8.0),
      child: FlatButton(
        height: 100,
        child: Text(
          text,
          style: TextStyle(
            fontSize: 18,
            fontWeight: FontWeight.bold,
            color: Colors.white,
          ),
        ),
        color: Colors.black38,
        onPressed: () {
          setState(() {
            text = dicK[n];
            print(text);
          });
        },
      ),
    );
  }

  @override
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
        ),
      ),
    );
  }
}

```
