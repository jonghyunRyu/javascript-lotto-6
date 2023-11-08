# 💬 미션 - 로또
로또 게임 기능을 구현한다. 로또 게임은 아래와 같은 규칙으로 진행된다.
```
- 로또 번호의 숫자 범위는 1~45까지이다.
- 1개의 로또를 발행할 때 중복되지 않는 6개의 숫자를 뽑는다.
- 당첨 번호 추첨 시 중복되지 않는 숫자 6개와 보너스 번호 1개를 뽑는다.
- 당첨은 1등부터 5등까지 있다. 당첨 기준과 금액은 아래와 같다.
    - 1등: 6개 번호 일치 / 2,000,000,000원
    - 2등: 5개 번호 + 보너스 번호 일치 / 30,000,000원
    - 3등: 5개 번호 일치 / 1,500,000원
    - 4등: 4개 번호 일치 / 50,000원
    - 5등: 3개 번호 일치 / 5,000원
```
## 📋 미션을 하며 신경 쓴 부분
- 함수에 대한 이해하기 (async, await 등)
- 함수가 기능을 한 가지일만 하도록 하기
- jest에 대해 이해하고 test case 만들기

## 🚀 구현한 함수 목록

**Buy.js**

- 로또를 구입할 금액을 입력 받음 예외는 Exception 클래스를 참조
- 예외 발생 시 에러 메세지를 출력 후 구입할 금액을 다시 입력 받음

```
예외 케이스 에러 메세지 출력 예시

1. 숫자가 아닌 값을 입력했을 때
[ERROR] : 숫자를 입력해 주세요.
2. 천 원 단위로 입력하지 않았을 때
[ERROR] : 천 원 단위로 입력해 주세요.
3. 입력을 하지 않았을 때
[ERROR] : 구입할 금액을 입력해 주세요.
```
- 입력 받은 금액을 천 원 단위로 나눈 갯수만큼 랜덤하게 로또를 발행
- 로또 갯수를 lottoEach, 발행된 모든 로또를 lottoAll 배열에 저장

<br>

**Winning.js**

- 당첨 번호를 입력 받은 뒤 보너스 번호를 입력 받음
- 당첨 번호 예외는 주어진 Lotto클래스를 참조하고 보너스 번호는 Exception 클래스를 참조
- 각각 예외 발생 시 에러 메세지를 출력 후 재입력 받음
```
당첨 번호 예외 에러 메세지 출력 예시

1. 로또 번호를 6개 입력하지 않은 경우
[ERROR] : 로또 번호는 6개여야 합니다.
2. 로또 번호에 숫자가 아닌 값을 입력했을 때
[ERROR] : 숫자를 입력해 주세요.
3. 로또 번호를 중복되게 입력했을 때
[ERROR] : 로또 번호는 중복되지 않아야 됩니다.
``` 
```
보너스 번호 예외 에러 메세지 출력 예시

1. 보너스 번호를 당첨 번호와 중복되게 입력한 경우
[ERROR] : 당첨 번호와 중복된 번호입니다.
2. 숫자가 아닌 값을 입력했을 때
[ERROR] : 숫자를 입력해 주세요.
3. 보너스 번호를 입력하지 않았을 때
[ERROR] : 보너스 번호를 입력해 주세요.
```
- 당첨 번호와 발행한 로또를 비교하여 로또 등수에 맞춰 배열에 저장

<br>

**View.js**

- 구매한 로또 갯수를 출력한 뒤 발행한 모든 로또를 출력
- 당첨 통계를 출력
- 총 수익률을 출력

<br>

**Rate.js**

- 당첨 통계와 발행한 로또 갯수를 입력 받아 총 수익률을 계산하는 함수

<br>

**Exception.js**

- 구입 금액 입력 예외 처리, 보너스 번호 입력 예외 처리하는 함수

<br>

**Constants.js**

- 문자열과 숫자 상수로 만듦

<br>

**Lotto.js**

- 당첨 로또 번호 입력 받을 때 예외 처리하는 함수

<br>

**App.js**

- Buy, View, Winning, Rate 객체를 생성하고 로또를 실행함
- 로또 프로그램이 돌아갈 수 있게 함수들을 호출

## ⏱ 실행 결과 예시
```
구입금액을 입력해 주세요.
10000

10개를 구매했습니다.
[8, 29, 34, 43, 44, 45]
[2, 17, 21, 23, 25, 43]
[12, 14, 19, 25, 26, 40]
[6, 8, 9, 10, 13, 38]
[8, 9, 15, 25, 38, 42]
[7, 15, 17, 22, 24, 30]
[2, 3, 28, 38, 39, 43]
[4, 14, 17, 19, 37, 42]
[6, 7, 11, 26, 27, 40]
[5, 8, 17, 29, 38, 39]

당첨 번호를 입력해 주세요.
1,2,3,4,5,6

보너스 번호를 입력해 주세요.
7

당첨 통계
---
3개 일치 (5,000원) - 0개
4개 일치 (50,000원) - 0개
5개 일치 (1,500,000원) - 0개
5개 일치, 보너스 볼 일치 (30,000,000원) - 0개
6개 일치 (2,000,000,000원) - 0개
총 수익률은 0%입니다.
```
