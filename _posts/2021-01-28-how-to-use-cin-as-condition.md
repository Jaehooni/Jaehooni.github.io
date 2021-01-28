---
title: "cin을 조건문으로 이용할 수 있다."
date: 2021-01-28 14:10:45 -0400
categories: algorithm
---
cin은 값을 받는 행위 자체에 boolean type의 return 값을 가질 수 있다.

10951번 문제를 예를 들어 설명해보자.

10951번 문제는 입력으로 주어진 두 수가 더 이상 없을때까지 두 수의 합을 반환해서 출력하도록 하는 문제이다.

그렇다면 반복문의 조건문을 어떤식으로 작성하면 입력을 받을 숫자가 더 이상 남아있지 않을때 끝날 수 있을 것인가?
```cpp
#include <iostream>
using namespace std;
int a,b;

int main(){
  while(cin >> a >> b){
    cout << a + b << '\n';
  }

  return 0;
}
```
저런식으로 while 문 안에 cin >> a >> b라는 조건식을 넣어주면 성립이 된다.

해당 조건식의 과정을 살펴보면 먼저 cin >> a 가 실행이 되고 cin이 반환이 된다.

그리고 다시 cin >> b가 실행이 되고 그 후 cin이 반환이 되는 과정을 반복하면서 대입이 이루어지는 것이다.

이때 cin 객체가 조건문으로 사용이 될시 내부 operator에 의해 boolean으로 형 변환이 일어남.

그에 따라 cin >> a 또는 cin >> b가 실행이 되는 과정에서 정상적으로 대입이 이루어지지 않으면, 즉 더 이상 대입받을 수가 없는 상황에서

반환된 cin 객체는 false를 반환하므로 조건문으로 사용이 가능하다.

그래서 아래에 나와있는 코드처럼 작성을 해도 정상적으로 작동이 된다.

```cpp
#include <iostream>
	using namespace std;
	int a,b;

int main(){
  cin >> a >> b;
  while(cin){
    cout << a + b << '\n';
    cin >> a >> b;
  }

  return 0;
}
```
