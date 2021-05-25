# Modern JavaScript

## TOC

[ES6 Arrow Functions](#es6-arrow-functions)

[Exports & Imports](#exports--imports)

[Spread & Rest Operator](#spread--rest-operator)

[Destructuring](#destructuring)

## ES6 Arrow Functions

- 함수를 정의하는 또 다른 방법

- 짧아진 syntax로 간편하지만 기존 함수와 몇 가지 차이점과 한계가 있다.

  - `this`나 `super`로의 binding이 존재하지 않으며 `method`로 사용되어선 안된다.
    _methods란?_

    ```javascript
    const obj = {
      foo() {
        return "bar";
      },
    };

    console.log(obj.foo());
    // expected output: "bar"
    ```

  - `argument`나 `new.target` 키워드가 없다.

  - `scope` 생성에 의존하는 `call`, `apply`, `bind` method에 적합하지 않다.

  - 생성자 (constructor)로 사용되면 안된다.

  - body 안에서 `yield`를 사용하면 안된다.

### Arrow Function으로 바꾸는 과정

```javascript
function getLength(material) {
  return material.length;
}
```

```javascript
const getLength: function(material) {
  return material.length;
}
```

```javascript
const getLength = (material) => {
  material.length;
};
```

- 만약 하나의 `argument`만 있다면 괄호를 생략할 수 있다.

- 단순하게 값을 리턴하면 중괄호와 세미콜론을 생략할 수 있다.

```javascript
const getLength = (material) => material.length;
```

- 전달할 `argument`가 없다면 빈 괄호를 두면 된다.

```javascript
const print = () => console.log("result");
```

### 예제

```javascript
const materials = ["Hydrogen", "Helium", "Lithium", "Beryllium"];

console.log(materials.map((material) => material.length));
// expected output: Array [8, 6, 7, 9]
```

## Exports & Imports

- 프로젝트 내 코드를 여러 개의 JS file로 쪼개서 관리할 수 있는데 이를 `module`이라고 부른다.

- 다른 파일에서 접근하도록 위해 `export`가 필요하며 접근하기 위해 `import` statement가 필요하다.

- `export`에는 두 가지 타입이 있다.

### default

- `export default ...;`

- **default**로 내보낼 시 아무 이름으로 `import`가 가능하다.
  i.e. `import upToMe from './someFile.js';`

- default는 하나밖에 가질 수 없다.

### named

- `export const someFunction = ...;`

- **named export**는 무조건 이름으로 가져와야 한다.
  i.e. `import { someFunction } from './someFile.js';`

- named는 무제한이다.

- 모든 named를 가져올 땐 \* 선택자를 사용하면 된다.

## Spread & Rest Operator

- `...` 를 통해 기존 array에 원소를 합칠 수 있다.

- Array 뿐만 아니라 object도 가능하다.

```javascript
const oldArray = [1, 2, 3];
const newArray = [...oldArray, 4, 5];
```

```javascript
const oldObj = {
  name: "Meredith",
};

const newObj = {
  ...oldObj,
  color: "blue",
};
```

## Destructuring

- Array나 object의 값에 접근하여 변수에 바로 값을 할당할 수 있다.

```javascript
const array = [1, 2, 3];
const [a, b] = array; // a = 1, b = 2

const payment = {
  product: "apple watch",
  price: 329,
  date: "2021.04.12",
};

const { product } = payment;
console.log(name); // 'apple watch'
```

```javascript
const printName = ({ name }) => {
  console.log(name);
};
printName({ name: "Max", age: 28 }); // 'Max'
```
