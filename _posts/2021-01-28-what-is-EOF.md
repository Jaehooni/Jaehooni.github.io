---
title: "[Q 11718]EOF 활용"
date: 2021-01-28 14:25:00 -0400
categories: algorithm
---
11718번 문제에서는 입력받은 그대로(개행, 공백 포함)을 출력해야 한다.

그렇다면 입력이 끝나는 순간의 조건문을 어떻게 작성해야 할 것인가?


```cpp
#include <iostream>
	using namespace std;
	char c;
int main(){
  while(scanf("%c",&c) != EOF)
    printf("%c",c);

  return 0;
}
```
먼저 필자의 코드이다. 보면 scanf를 이용하고 있고 조건문으로 EOF라는 애랑 비교하는 것을 작성해놓았다

EOF란 End Of File의 약자로서 명시되어있지는 않지만 모든 파일(입력)의 끝에 존재하는 녀석이다.

따라서 EOF와 비교하여 scanf의 반환값이 EOF가 같지 않다면 입력이 아직 끝나지 않았다는 뜻이 된다.

근데 왜 여기서는 cin을 이용하지 않고 scanf를 이용하였을까?

바로 cin은 공백 및 개행 문자를 무시하기 때문이다.

그렇다면 cin을 활용하여 풀 수는 없는 것일까?


아니, 있다.


cin.unsetf(ios::skipws)를 추가해주면 된다.

해당 구문을 추가하게 되면 개행, 공백을 무시하지 않는다.

저 구문을 활용하면 이런 코드도 나올 수 있다.

```cpp
#include <iostream>
	using namespace std;
	char c;

int main(){
  cin.unsetf(ios::skipws);
  cin >> c;
  while(cin){
    cout << c;
    cin >> c;
  }
  return 0;
}
```

아니면 cin.get()을 활용하여 flag 변경 없이 할 수도 있다.

```cpp
#include <iostream>
using namespace std;
char c;

int main(){
    while(cin.get(c))
        cout << c;

    return 0;
}
```
