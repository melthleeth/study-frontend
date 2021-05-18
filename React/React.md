# Rendering

- Vue에선 `v-if`와 `v-else`로 component를 보여지거나 숨기게 했다면

- React에선 여러가지 방법이 있겠지만 변수 상태에 따라 통째로 렌더링 여부를 결정한다.

- 가장 쉬운 방법은 변수 하나를 두고 해당 변수 값이 true/false에 따라 보여지게 하는 것이다.

```javascript
const [toggle, setToggle] = useState(false);

...

{toggle && <button>Click to Close</button>}
{!toggle && <button>Click to Open</button>}
```

- 이런식으로 button 문구가 다르게 나타낼 수 있다.

- 혹은 로그인 된 상태에 따라 Navigation Bar를 보이거나 숨길 수 있다.

- Route 안에서 Navigation Guard로써의 역할도 한다.

```javascript
<Route exact path="/">
  {!authCtx.isLoggedIn && <AuthPage />}
  {authCtx.isLoggedIn && <DashBoardPage />}
</Route>
```
