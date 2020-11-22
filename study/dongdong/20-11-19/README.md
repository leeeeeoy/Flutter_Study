# 11/16 내용정리

## 새로 알게된 내용

classs - define a blueprint for objects
import material에서 -> BuildContext 나옴 (구성하는 재료를 갖고온다고 생각)
constructor - class를 사용하고자 하는 arguments를 쓸 수 있도록 구조화? 뭐라해야하지 음 암튼 할 줄 알면 되니 패스

class Name with @@@@ 은 포괄적이다. -> can have several parents
class Name extends @@@@@ 은 보다 더 밀접하다. -> have only one parent

list.where((prod) => prod.id == productId) 라 하면 prod.id가 ProductId와 긑은 것들을 골라주는 편리한 기능을 가지고있다.
import '../providers/cart.dart' show cart;
ㄴ> 앞에 ../providers/cart.dart에서 cart클래스만을 받아오겠다는 것을 의미한다. 성능이 좋아진다.

## 궁금한 내용

## 같이 공유하고 싶은 내용

## 기타 자유롭게 적고싶은 내용
