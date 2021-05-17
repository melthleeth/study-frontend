# Recharts

- [공홈](https://recharts.org/en-US)

- chart library

- 다양한 example이 있어 사용하기 좋다.

- data를 props로 넘기기만 하면 되서 다른 차트 라이브러리에 비해 편했다.

- 각 예제마다 code sandbox로 넘어가기 링크가 있어 미리 원하는대로 스타일이나 데이터를 바꿔본 후 프로젝트에 적용할 수 있어서 좋다.

## 사용법

- component로 분리하여 사용하기 위해 파일을 하나 생성한다.
  i.e. `SimpleAreaChart.js`

- 제공되는 샘플 코드를 복사해온다. 이때 code sandbox 예제를 가져오는게 편했다.

- data 값을 `props.data`로 바꿔주고 함수형 component인 경우 parameter에 `props`를 추가한다.

- `API`탭을 눌러보면 커스터마이징 할 수 있는 가이드가 나온다.
  AreaChart같은 경우 그라데이션을 넣을 수도 있다. [예제](https://recharts.org/en-US/api/AreaChart)

- 이제 이 차트가 필요한 파일에 component를 import하고 props로 data를 넘겨주면 된다.

- data의 경우 백엔드 api를 호출하여 받아주면 더욱 좋겠다.

### 샘플 코드

#### SimpleAreaChart.js

```javascript
import {
  AreaChart,
  Area,
  XAxis,
  YAxis,
  CartesianGrid,
  Tooltip,
  Legend,
} from "recharts";

import Card from "../../components/UI/Card/Card";

import "./Chart.css";

const SimpleAreaChart = (props) => {
  return (
    <Card unset>
      <AreaChart
        width={700}
        height={250}
        data={props.data}
        margin={{
          top: 10,
          right: 30,
          left: 0,
          bottom: 0,
        }}
      >
        <defs>
          <linearGradient id="colorUsed" x1="0" y1="0" x2="0" y2="1">
            <stop offset="5%" stopColor="#32499A" stopOpacity={0.8} />
            <stop offset="95%" stopColor="#7986FF" stopOpacity={0} />
          </linearGradient>
          <linearGradient id="colorPayback" x1="0" y1="0" x2="0" y2="1">
            <stop offset="5%" stopColor="#7986FF" stopOpacity={0.8} />
            <stop offset="95%" stopColor="#D3DEFF" stopOpacity={0} />
          </linearGradient>
        </defs>
        <CartesianGrid strokeDasharray="3 3" />
        <XAxis dataKey="name" interval={0} />
        <YAxis />
        <Tooltip />
        <Legend />
        <Area
          type="monotone"
          dataKey="사용된 금액"
          stroke="#32499A"
          fill="url(#colorUsed)"
          fillOpacity={0.2}
        />
        <Area
          type="monotone"
          dataKey="정산된 금액"
          stroke="#7986FF"
          fill="url(#colorPayback)"
          fillOpacity={0.3}
        />
      </AreaChart>
    </Card>
  );
};

export default SimpleAreaChart;
```

#### 적용할 Component

```javascript
const data_monthlyConsumed = [
  {
    name: "1",
    "정산된 금액": 4000,
    "사용된 금액": 2400,
    amt: 2400,
  },
  {
    name: "5",
    "정산된 금액": 3000,
    "사용된 금액": 1398,
    amt: 2210,
  },
  {
    name: "10",
    "정산된 금액": 2000,
    "사용된 금액": 9800,
    amt: 2290,
  },
  {
    name: "15",
    "정산된 금액": 2780,
    "사용된 금액": 3908,
    amt: 2000,
  },
  {
    name: "20",
    "정산된 금액": 1890,
    "사용된 금액": 4800,
    amt: 2181,
  },
  {
    name: "25",
    "정산된 금액": 2390,
    "사용된 금액": 3800,
    amt: 2500,
  },
  {
    name: "31",
    "정산된 금액": 3490,
    "사용된 금액": 4300,
    amt: 2100,
  },
];

<SimpleAreaChart data={data_monthlyConsumed} />;
```

#### 결과

![AreaChart](https://user-images.githubusercontent.com/22411481/118508555-44958c80-b76a-11eb-9642-bf45ae6345b1.png)
