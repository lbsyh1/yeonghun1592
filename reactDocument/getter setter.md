접근자 프로퍼티의 본질은 함수인데, 이 함수는 값을 획득(get)하고 설정(set)하는 역할을 담당합니다.

```

let obj = {
  get propName() {
    // getter, obj.propName을 실행할 때 실행되는 코드
  },

  set propName(value) {
    // setter, obj.propName = value를 실행할 때 실행되는 코드
  }
};

```

getter 메서드는 obj.propName을 사용해 프로퍼티를 읽으려고 할 때 실행되고, setter 메서드는 obj.propName = value으로 프로퍼티에 값을 할당하려 할 때 실행됩니다.

```

let user = {
  name: "John",
  surname: "Smith"
};

```

이 객체에 fullName 이라는 프로퍼티를 추가해 fullName이 'John Smith'가 되도록 해봅시다. 기존 값을 복사-붙여넣기 하지 않고 fullName이 'John Smith'가 되도록 하려면 접근자 프로퍼티를 구현하면 됩니다.

```

let user = {
  name: "John",
  surname: "Smith",

  get fullName() {
    return `${this.name} ${this.surname}`;
  }
};

alert(user.fullName); // John Smith

```

한편, 위 예시의 fullName은 getter 메서드만 가지고 있기 때문에 user.fullName=을 사용해 값을 할당하려고 하면 에러가 발생합니다.

```

let user = {
  get fullName() {
    return `...`;
  }
};

user.fullName = "Test"; // Error (프로퍼티에 getter 메서드만 있어서 에러가 발생합니다.)

```

user.fullName에 setter 메서드를 추가해 에러가 발생하지 않도록 고쳐봅시다.

```

let user = {
  name: "John",
  surname: "Smith",

  get fullName() {
    return `${this.name} ${this.surname}`;
  },

  set fullName(value) {
    [this.name, this.surname] = value.split(" ");
  }
};

// 주어진 값을 사용해 set fullName이 실행됩니다.
user.fullName = "Alice Cooper";

```

이렇게 getter와 setter 메서드를 구현하면 객체엔 fullName이라는 '가상’의 프로퍼티가 생깁니다. 가상의 프로퍼티는 읽고 쓸 순 있지만 실제로는 존재하지 않습니다.

접근자 프로퍼티 설명자
데이터 프로퍼티의 설명자와 접근자 프로퍼티의 설명자는 다릅니다.

접근자 프로퍼티엔 설명자 value와 writable가 없는 대신에 get과 set이라는 함수가 있습니다.

따라서 접근자 프로퍼티는 다음과 같은 설명자를 갖습니다.

get – 인수가 없는 함수로, 프로퍼티를 읽을 때 동작함
set – 인수가 하나인 함수로, 프로퍼티에 값을 쓸 때 호출됨
enumerable – 데이터 프로퍼티와 동일함
configurable – 데이터 프로퍼티와 동일함

프로퍼티는 접근자 프로퍼티(get/set 메서드를 가짐)나 데이터 프로퍼티(value를 가짐) 중 한 종류에만 속하고 둘 다에 속할 수 없다는 점을 항상 유의하시기 바랍니다.

