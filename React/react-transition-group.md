# react-transition-group

- [공식문서](https://reactcommunity.org/react-transition-group/)

- 설치
  `npm install react-transition-group --save `

- CSS만으로는 rendering의 한계가 있어 고안되었다.

- 사용법: 해당 component에 import한다.

- Transition과 CSSTransition이 있다.

## Transition

`import Transition from "react-transition-group/Transition";`

- `state`로 감싸야 한다.
  `{state => (<div> ... </div>)}`

## CSSTranstion

`import CSSTransition from "react-transition-group/CSSTransition";`

- function형태로 쓰지 않는다. 대신 이름처럼 CSS class를 지정할 수 있다.

- 그냥 Transition보다 간단하며 custom화 할 수 있다.

- 단일 element에 대해 사용할 수 있으며 list와 같은 group 객체에 사용하고 싶다면 TransitionGroup과 같이 사용해야 한다.

### ❗️ style 줄 때 주의점

- `.module.css`로 모듈화된 css는 적용되지 않는다!
  `classNames={classes.fade}` 이렇게 하면 적용되지 않는다.

- `.css`로 classNames를 pure하게 호출해야 한다.
  `classNames="fade"`

```javascript
<CSSTransition
  mountOnEnter
  unmountOnExit
  in={props.show}
  timeout={300}
  classNames="alert"
>
  <div className={classes.Modal}>
    <span onClick={props.closed} className={classes.closeBtn}>
      ✕
    </span>
    {children}
  </div>
</CSSTransition>
```

## Alternative Packages

- react-motion

- react-move

- react-router-transition
