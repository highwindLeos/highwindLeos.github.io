---
layout: single
title:  "React Hook 정리"
categories : Coding
tag : [JavaScript, React]
toc : true 
author_profile : true 
search : true 
---

# React Hook 정리

## Hook 이란?
리액트 컴포넌트에는 **Class Component** 와 **Funtion Component** 가 존재함
두가지 컴포넌트의 특징은 아래와 같다.
![Hook]({{url}}/images/2022-06-28/Hook.jpg "Hook")

해당 Hook 함수들은 정해진 시점에 원하는 기능을 수행하게끔 약속되어진 함수로
생명주기 함수 및 React State 관련 제어 함수, 최적화 관련 함수들이 이에 속한다.
특징은 **use** 라는 앞머리가 달린 함수들이 많이 존재한다.

### 주요 Hook 함수

#### useState()

이 함수를 이용해 State의 값을 할당하고 수정도 해당 함수로 선언된 변수를 수정하는 함수로 사용되어야
페이지가 **Rerendering** 된다.

```javascript
    const [변수명, set함수명] = useState();
```
*****
#### useEffect()

이 함수를 이용해 Side Effect 를 이용하여 실행하게 되는 Hook 임. 해당 함수 하나로 생명주기 함수와 같은 효과를 줄수 있음.
페이지가 **Rerendering** 될때나 업데이트 될 때 .

```javascript
    useEffect(이벤트 함수, 의존성 배열); // 기본형식
    useEffect(이벤트 함수, []); // mount 와 unmount 시 한번씩만 실행됨
    useEffect(이벤트 함수); // 의존성배열 생략시에는 컴포넌트가 업테이트 될때 마다 실행됨.
```

Example
```javascript
    import React, {useState, useEffect } from "react";

    function Counter (prors) {
        const [count, setCount] = useState(0);

        // componentDidMount, componentDidUpdate 와 비슷하게 작동합니다.
        useEffect(()=>{
            // 브라우저 API 를 이용해서 docment의 title 을 업데이트 합니다.
            docment.title = `you cilced ${count} times`; 
        });

        return (
            <div>
                <p>총 {count}번 클릭했습니다.</p>
                <button onClick={()=> setCount(count + 1)}>
                    클릭
                </button>  
            </div>
        );
    }
```

[Oracle Express Edition](https://www.oracle.com/kr/database/technologies/xe-downloads.html){: .btn .btn--danger target="_blank"}