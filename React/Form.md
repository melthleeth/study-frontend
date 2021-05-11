# Input

## checkbox

- `select` 태그와 달리 props에서 값을 가져와 value를 설정하면 check 속성이 바뀌지 않는다.

- 이때 `defaultChecked` 속성에 값을 넣어주면 된다.

```javascript
 let days = [
    { id: 1, value: "월", checked: false },
    { id: 2, value: "화", checked: false },
    { id: 3, value: "수", checked: false },
    { id: 4, value: "목", checked: false },
    { id: 5, value: "금", checked: false },
    { id: 6, value: "토", checked: false },
    { id: 7, value: "일", checked: false },
  ];
  let modifiedDays = [];
  for (let i = 1; i <= 7; i++) {
    if (props.days.charAt(i - 1) === "1") {
      modifiedDays.push(i.toString());
      days[i - 1].checked = true;
    }
  }

...

<div className={classes.control}>
    {days.map((day, index) => (
        <label
        className={`${classes.label} ${classes.checkbox}`}
        key={day.id}
        >
        <input
            className={`${classes.checkboxStyles}`}
            type="checkbox"
            // id="day"
            name="day"
            value={day.id}
            defaultChecked={days[index].checked}
            onChange={changeHandler}
        />
        <span>{day.value}</span>
        </label>
    ))}
</div>
```
