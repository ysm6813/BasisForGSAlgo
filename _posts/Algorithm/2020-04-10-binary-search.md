---
layout : post
title : 2.Binary search
author : JaeyunK
categories: algorithm
tags: [binary search]
---


앞에서 이상한? 복잡도니 컴퓨터니를 얘기해놓고 뭔 이상한 영어인가 싶겠지만...

`Binary search`는 중요하고 심지어 이미 사용해본 적이 있을 것이다.

`Binary search`를 번역하면 `이분 탐색`이 되는데, 이 이분 탐색은 정렬된 데이터에서(단조성을 띄고 있을때) 아주 많이 유용하게 쓰인다.

그냥 얘기를 하자면, **중요하다**.


### Problems

#### 1-1

길이가 n인 정수형 일차원 배열에 값들이 저장되어 있다. 주어진 값을 가지는 원소의 위치를 알아내는 방법을 생각해보자.


#### 1-2

만약 값들이 정렬되어 있다면 어떤 방법으로 원소를 찾을 수 있을까?

----

#### 2-1

재윤이는 영민이와 up-down게임을 한다 (1~n까지 숫자 사이에 답이 있다). 

정보선생님은 공평한 게임을 위해서 ans를 1~n까지 임의의 숫자중에 램덤하게 정하고, 답을 확인하기 위한 함수를 만들었다.

``` c++
int check(int c){
    if(ans < c) return 0;
    else if(ans == c) return 1;
    else return 2;
}
```

둘 줄에서 답을 확인하기 위한 함수 `check()`를 적게 사용한 사람이 이기게 된다.

게임을 푸는 코드를 작성하라.


#### 2-2

다음은 재윤이가 작성한 코드이다.


``` c++
int func(){
    int res = 1;
    while(check(res) == 1) 
        res++;
    return res;
}
```


다음은 영민이가 작성한 코드이다.

```c++
int func(){
    int l = 1; r = n;
    while(l <= r){
        int m = (l+r)/2;
        int chk = check(m);
        
        if(chk == 0) r = m-1;
        else if(chk == 1) return m;
        else l = m+1;
        
    }
    return -1; //이잉?
}
```

둘 중에 누가 이길지 예측하고, 시간복잡도, 공간복잡도를 분석해보자.

## 마무리 하면서

추가로 이분탐색을 연습할 수 있는 문제들이다.