## flutter packages

[pub.dartlang.org](http://pub.dartlang.org) 

main.dart 위에 imort 'package 주소'

yaml파일 dependency 마지막 부분에 

package name : ^version표시

```dart
import 'package:english_words/english_words.dart';

main() {
  nouns.take(50).forEach(print);
}
```

```yaml
dependencies:
  flutter:
    sdk: flutter

  cupertino_icons: ^0.1.2
  english_words: ^3.1.5
#꺽쇠의 의미는 major version이 3이면 걍 다운 받아 써라.. 첫 넘버가 바뀌면 사용 불가
```

### audioplayers

```yaml
child: FlatButton(onPressed: () {
	final player = AudioCache();
	player.play('note1.wav'); 
	// audio file의 경우, folder/file이라고 하지 않고, asset폴더 밑에 있을 경우에는 그냥 이름으로 사용가능
},
```

## Functions

return type 조심

```yaml
buildkey(color : Colors.red, n : 1); //function call

//function 
void buildkey({Color color, int n}) { }// {}있어야 functioncall 저렇게 가능.
```