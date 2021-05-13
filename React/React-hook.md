## useState

- 기존에는 class component 안의 constructor에서 state를 정의 후 `this.setState()`로 상태 변화를 줬었다면

- hook을 호출해서 할 수 있다.

- hook 사용시 this keyword를 사용하지 않아도 된다.

### React.Component

```javascript
state = {
    modalIsOpen: false,
    showBlock: false,
  };

...

showModal = () => this.setState({ modalIsOpen: true });
closeModal = () => this.setState({ modalIsOpen: false });
```

### function call

```javascript
import { setState } from "React";

[modalIsOpen, setModalIsOpen] = setState(false);

const showModal = () => setModalIsOpen(true);
const closeModal = () => setModalIsOpen(false);
```
