# react-router-dom

## parameter 전달하기

- component간 이동시 parameter를 전달하고자 할 때 주소에 보이게 할 수도 있고 숨겨서 보낼 수도 있다.

### 링크에 보이게 전달하기

- `Route`에서 path를 정의할 때 `링크/:{전달할 변수}`를 달아주면 된다.

- 변수는 여러 개 넣을 수 있다.

```javascript
<Route path="/user/payment/:employeeNum">
  <PaymentDetailPage />
</Route>
```

```javascript
<Route path="//payment/:employeeNum/:userId" component={PaymentDetailPage}>
```

### 숨겨서 전달하기

- `useHistory` hook을 사용할 때 `state`를 이용하여 component에 실어 보낼 수 있다.

- detail page로 넘어갈 때 path에 티는 내고 싶지만 개인 정보인 userId는 숨기고 싶어서 아래와 같은 방식으로 구성했다.

```javascript
history.push({
  pathname: `/user/list/${props.employeeNum}`,
  state: { userName: `${props.userName}`, userId: `${props.userId}` },
});
```

- component에서 가져올 때 `useLocation` hook을 사용하여 가져올 수 있다.

```javascript
const location = useLocation();
const { userId } = location.state;
```
