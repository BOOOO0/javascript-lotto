# 🎰 로또

## 기능 목록

1. 사용자에게 로또를 구매할 금액을 입력받는다.
2. 구매할 금액이 올바르게 입력되었다면 금액을 1000으로 나눠서 로또를 몇 게임 구매 가능한지 구한다.
3. 중복이 없는 6개의 숫자를 가진 로또 게임을 반환하는 함수를 생성한다.
4. 몇 게임 구매 가능한지 구했다면 3의 함수를 이용해서 그 수 만큼의 로또 게임을 생성한다.
5. 생성된 자동 로또 게임들을 모두 출력한다.
6. 사용자에게 당첨 번호를 입력받는다.
7. 문자열로 입력된 당첨 번호를 (,)를 기준으로 나눠서 배열로 만들고 동시에 원소들을 정수형으로 바꾼다.
8. 사용자에게 보너스 번호를 입력받는다.

## Programming Plan

이번 미션에서 추가된 요구 사항 중 else를 지양한다는 부분을 충족시키기 위해서 값을 다루는 함수들이 return으로 종료될 수 있게 만들어야 겠다고 생각을 했다.
이번에는 값을 객체의 프로퍼티로 가지고 있으면서 그것을 다루기보다 값을 반환하게 하고 콜백함수를 인자로 받아서 수행하는 방식으로 할 계획이다.  
그리고 이 방식이 도메인 로직에 대한 테스트 코드 작성에 더 용이할 것이라고 생각한다.  
그리고 UI로직과 도메인 로직을 나누는 데에도 더 용이할 것이라고 생각한다.

### 예시

```javascript
const MissionUtils = require("@woowacourse/mission-utils");

const getInput = (getNumber, returnArray, printArray) => {
  MissionUtils.Console.readLine("얼마", (budget) => {
    printArray(returnArray(getNumber(budget)));
  });
};

const getNumber = (budget) => {
  return Math.floor(budget / 1000);
};

const returnArray = (number) => {
  const array = [];
  for (let i = 0; i < number; i++) {
    array.push(MissionUtils.Random.pickUniqueNumbersInRange(1, 45, 6));
  }
  return array;
};

const printArray = (array) => {
  array.forEach((elm) => {
    MissionUtils.Console.print(elm);
  });
};

getInput(getNumber, returnArray, printArray);
```
