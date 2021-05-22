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
