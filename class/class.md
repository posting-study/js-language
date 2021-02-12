# JS에서 Class 다루기

JS로 게임을 만들다가 파일과 코드 분리에 어려움이 생겨 class 도입에 대한 필요성을 느꼈다. 공부한 것을 바탕으로 JS식 객체지향 프로그래밍에 대한 정리를 해보려고 한다.

정리의 끝에는 'JS의 class는 프로토타입을 베이스로 한다' 라는 말을 조금이나마 와닿게 하려 한다.

---

## 생성자

생성자는 **객체를 생성하는 함수**이며, 'new'를 사용해 호출한다.
다른 함수와 구분하기 위해 대문자로 시작하는 것이 규칙이다.

```JS
function Person(name, age, gender){
    this.name = name;
    this.age = age;
    this.gender = gender;
    this.sayHi = () =>{
        console.log('Hi!');
    }
}

let a = new Person('A','20','Female')
 // {name:A, age:20, gender:Female}인 Person 객체를 만듬
a.sayHi(); // Hi!
```

## 프로토타입

위에서 처럼 생성자 안에서 메소드를 정의하게 된다면, 생성자로 인스턴스를 생성하는 만큼 메소드를 생성하기 때문에 메모리를 낭비하게 되는 문제가 발생한다.
이러한 문제를 해결하기 위해, 프로토타입 객체에 메소드를 정의한다.

JS에서는 함수도 객체이기 때문에 기본적으로 prototype이라는 프로퍼티를 가지고 있다.
위에서 작성한 생성자 안의 메소드를 프로토타입 객체 안에 넣어주었다.

```JS
function Person(name, age, gender){
    this.name = name;
    this.age = age;
    this.gender = gender;
}
Person.prototype.sayHi = () =>{
    console.log('Hi!');
}
```

프로토타입 객체 안에는 메소드 뿐만 아니라 다른 속성도 넣을 수 있다.
이때 주의해야할 점은 프로토타입 객체의 프로퍼티는 읽기만 가능하고 수정은 불가능하다는 것이다.

## Class

Class는 객체를 생성하기 위한 또 다른 함수라고 생각할 수 있다.
단 일반적인 함수와는 다르게 호이스팅이 되지 않는다는 점을 인지하고 있어야 한다.
앞에서 생성한 Person 객체를 Class로 생성해 보겠다.

```JS
class Person{
    constructor(name, age, gender){
        this.name = name;
        this.age = age;
        this.gender = gender;
    }
    sayHi = () =>{
        console.log('Hi!');
    }
}

let a = new Person('A','20','Female')
```

위에서 객체를 생성한 방법과 비교해보자.
먼저, class의 constructor 메소드는 객체를 생성 및 초기화 하는 역할을 하며 클래스 안에 한 개만 존재할 수 있다.
프로토타입 객체 안에 넣었던 메소드는 생성자 바깥에 작성하면 된다.

---

결국, 'JS의 class는 프로토타입을 베이스로 한다' 는 것은,
기존 함수에서 프로토타입을 이용해 객체를 생성한 방식을 class 문법으로 넘긴 것이라고 쉽게 이해해 보려 한다.
