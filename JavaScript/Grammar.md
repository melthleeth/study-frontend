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
