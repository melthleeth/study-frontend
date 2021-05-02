# Async Await

- await는 await 구문이 complete되고 value값을 가져올때까지 함수 실행을 멈춰준다. 즉, 코드를 synchronous적으로 보이게 할 수 있다.

- error handling은 try catch 구문으로 할 수 있다.

- 단점은 만약 await 수가 상당히 많아진다면 각 `await`들은 이전 await가 끝날때 까지 기다려야 해서 코드가 느려질 수 있다는 점이다.

([공식문서](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Async_await) 참고하여 더 수정 필요)

```javascript
// promise code
fetch("https://jsonplaceholder.typicode.com/users")
  .then((response) => response.json())
  .then((users) => {
    const firstUser = users[0];
    console.log("firstUser", firstUser);
    return fetch(
      `https://jsonplaceholder.typicode.com/posts?userId=${firstUser.id}`
    );
  })
  .then((response) => response.json())
  .then((posts) => console.log("posts", posts))
  .catch((error) => console.log(error));


//async await
const myAsyncFunction = async () => {
  try {
    const usersResponse = await fetch(
      "https://jsonplaceholder.typicode.com/users"
    );
    const users = await usersResponse.json();
    const secondUser = users[1];
    console.log("secondUser", secondUser);
    const postsResponse = await fetch(
      `https://jsonplaceholder.typicode.com/posts?userId=${secondUser.id}`
    );
    const posts = await postsResponse.json();
    console.log("posts", posts);
  } catch (error) {
    console.log("There was an error.");
  }
};
```