---
layout: single
title:  "Oracle Function 정리"
categories : Coding
tag : [Oracle, SQL]
toc : true 
author_profile : true 
search : true 
---

# Oracle 함수 모음

**[Notice]** [Oracle Korea](hhttps://www.oracle.com/kr/index.html){: target="_blank" }
{: .notice--danger }

## 단일 행 함수
- 함수가 정의된 SQL문이 실행될 때 각각의 ROW에 대해 수행되며 ROW 당 하나의 결과를 리턴 해줍니다.
- 인수로는 상수, 변수, 표현식들이 사용 될 수 있습니다.
- SELECT, WHERE, ORDER BY 절에 사용 할 수 있습니다.

### 문자함수

|구분|함수|내용|
|:---:|:---:|:---|
|문자함수|LOWER|모든 문자를 소문자로|
||UPPER|모든 문자를 대문자로|
||INITCAP|첫 글자는 대문자,나머지는 소문자로|
||CANCAT|첫 번째 문자와 두 번째 문자를 연결|
||LENGTH|문자의 길이를 리턴할 때|
||LENGTHB|문자열의 실제 길이를 변환할 때|
||NVL|널값을 다른 값으로 대체할 때|
||NVL2|조건에 의해 널값을 다른 값으로 대체할 때|
||SUBSTR|특정 문자의 문자열중 필요 부분만 선별하여 사용|
||RTRIM|서브 스트림의 정확한 위치와 길이를 요구(오른쪽)|
||LTRIM|서브 스트림의 정확한 위치와 길이를 요구(왼쪽)|
||RPAD|문자열을 제외한 공간에 지정한 문자열로 대체(오른쪽)|
||LPAD|문자열을 제외한 공간에 지정한 문자열로 대체(왼쪽)|
||TRANSLATE|첫 문자는 탐색집합의 첫 문자로 대체(2번째도 동일)|
||REPLACE|특정 문자열을 다른 문자열로 대체|
||SOUNDX|같은 단어 또는 유사한 사운드 단어를 음성학적으로|
||INTSTR|문자열 내의 특정 스트림의 위치 반환|
||NULLIF|조건이 같으면 NULL,다르면 지정된 값을 리턴할 때|
||COALESCE|조건에 따라 여러 가지 값을 리턴할 때|
|시스템 함수|USER|현재 DB 사용자|
||USERID|현재 DB 사용자에게 할당되는 사용자번호|

#### 문자함수의 예제   
   
-2개의 문자값을 결합합니다.
```sql
      SELECT CONCAT(CONCAT(ENAME,  ' is a '),JOB) FROM EMP;
```
```bash
      SMITH is a CLERK
      ALLEN is a SALESMAN
```
*****

-정의된 문장 단어의 첫 번째 문자를 대문자로 변환
```sql
      SELECT INITCAP('the soap') FROM DUAL;
```
```bash
      The Soap
```
*****

-정의된 문장의 왼쪽 나머지 공간을 지정한 문자로 채웁니다.
```sql
      SELECT LPAD( 'Page 1' , 15 , '*.') FROM DUAL;
```
```bash
     *.*.*.*.*Page 1
```
*****

-정의된 문장의 왼쪽부터 지정된 단어가 발견되면 제거합니다.
```sql
      SELECT LTRIM( 'xyxXxyLAST WORD','xy') FROM DUAL;
```
```bash
     XxyLAST WORD
```
*****
 
-정의된 문장에서 해당 문자가 발견되면 지정된 문자로 변경합니다.
```sql
      SELECT REPLACE( 'JACK and JUE' , 'J' , 'BL') FROM DUAL;
```
```bash
     BLACK and BLUE
```
*****

-정의된 문자의 오른쪽 나머지 공간을 지정한 문자로 채웁니다.
```sql
    SELECT RPAD(ename, 11 ,'ab' ) 
    FROM emp 
    WHERE ename = 'TURNER';
```
```bash
     TURNERababa
```
*****

-정의된 문자의 오른쪽부터 지정된 단어가 발견되면 제거합니다.
```sql
    SELECT RTRIM( 'TURNERyxXxy' , 'xy') FROM DUAL;
```
```bash
    TURNERyxX
```
*****

-정의된 문장의 지정된 위치부터 해당 길이 만큼만 추출합니다.
```sql
    SELECT SUBSTR( 'ABCDEFG' , 3 , 2 ) FROM DUAL;
```
```bash
    CD
```
*****

-정의된 문장의 뒤에서부터 지정된 위치의 해당 길이 만큼만 추출합니다.
```sql
    SELECT SUBSTR ( 'ABCDEFG' , -3 , 2 ) FROM DUAL;
```
```bash
    EF
```
*****

-문자 'Q'를 ASCII 코드로 변환합니다.
```sql
   SELECT ASCII ( 'Q' ) FROM DUAL;
```
```bash
   81
```
*****
 
-정의된 문장에서 지정된 위치에 존재하는 문자의 위치 값을 찾아 줍니다.
```sql
   SELECT INSTR ('CORPORATE FLOOR', 'OR', 3, 2) FROM DUAL;
```
```bash
   14
```
*****
 
-정의된 문장의 길이를 변환합니다.
```sql
   SELECT LENGTHB ('가나다라마바사') FROM DUAL;
```
```bash
   14
```
*****

-정의된 단어 중에 가장 높은 값을 찾아줍니다.
```sql
   SELECT GREATEST ('HARRY', 'HARIOT', 'HALORD') FROM DUAL;
```
```bash
  HARRY
```
*****

-정의한 컬럼이 NULL이면 지정한 값으로 대체합니다.

```sql
    SELECT NVL(sal, 0), NVL(ename, '*'), NVL(hiredate , '01-JAN-02') 
    FROM EMP;
```
```bash
  800 SMITH 80/12/17
```
*****

#### 시스템 함수 예제
   
-어떤사용자로 데이터베이스에 접속하였는지 알 수 있습니다.
```sql
   SELECT USER FROM dual;
```
```bash
   USER
   -------
   SCOTT
```
*****

### 숫자함수 / 날짜함수

|구분|함수|내용|
|:---:|:---:|:---|
|숫자함수|ROUND|해당 소수점 자리에서 반올림할 때|
||TRUNC|해당 소수점 자리에서 절삭할 때|
||MOD(m/n)|m을 n으로 나누고 남은 나머지를 리턴할 때|
||ABS|숫자 값을 절대값으로 바꾼다|
||SIGN|숫자가 양수:+1, 음수:-1, 0:0|
||FLOOR|실수값을 정수값으로|
||CEIL|그 수보다 가장 크거나 작은값을 리턴|
||POWER|해당 수에 대한 지수값을 표현|
||LOG|로그값으로 변환|
||SIN|SIN 값|
||COS|COSIN 값|
||TAN|TANGENT 값|
|날짜함수|SYSDATE|현재 시스템 날짜를 보여줄 때|
||ADD_MONTHS|지정한 날짜에 몇 월을 추가한 결과의 월을 계산할 때|
||LAST_DAY|해당 월의 마지막 날짜를 알고자 할 때|
||NEW_TIME|해당 표준시로 시간을 변환할 때|
||NEXT_DAY|해당 날짜의 다음 지정한 날짜로 반환 할 때|
||NONTH_BETWEEN|지정된 월 간의 월수를 알고자 할 때|

#### 숫자함수 예제
-정의된 값을 절대값으로 변환 합니다
```sql
    SELECT ABS(-15) FROM DUAL;
```
```bash
    ABS(-15)
    -----------
    15
```
*****

-정의된 값의 올림된 값으로 변환합니다
```sql
    SELECT CEIL(15.7) FROM DUAL;
```
```bash
    CEIL(15.7)
    -------------
    16
```
*****

-정의된 값의 내림된 값으로 변환합니다
```sql
    SELECT FLOOR(15.7) FROM DUAL;
```
```bash
    FLOOR(15.7)
    ---------------
    15
```
*****

-정의된 산술식의 COSINE 값으로 변환합니다
```sql
    SELECT COS(180 * 3.14 / 180) FROM DUAL;
```
```bash
    COS(180*3.14/180)
    --------------------
    -.99999873
```
*****

-정의된 숫자의 지수승값을 계산합니다
```sql
    SELECT EXP(4) FROM DUAL;
```
```bash
    EXP(4)
    ---------
    54.59815
```
*****

-뒤에 정의된 수로 앞에 정의된 수를 나눈 나머지 값을 반환합니다
```sql
    SELECT MOD(11, 4) FROM DUAL;
```
```bash
    MOD(11,4)
    ------------
    3
```
*****

-정의된 수를 지정한 자리 수에서 반올림합니다
```sql
    SELECT ROUND(15.193, 1) FROM DUAL;
```
```bash
    ROUND(15.193 , 1)
    -------------------
    15.2
```
*****

-정의된 값이 음수이면 -1 , 0 이면 0, 양수이면 1을 리턴합니다
```sql
    SELECT SIGN(-15) FROM DUAL;
```
```bash
    SIGN(-15)
    ------------
    -1
```
*****

-정의된 수를 지정한 자리 수 에서 절삭합니다
```sql
    SELECT TRUNC(15.97 , 1) FROM DUAL;
```
```bash
    TRUNC(15.79 , 1)
    -----------------
    15.7
```
*****
 
#### 날짜 함수 예제

-현재 시스템 날짜를 제공합니다
```sql
    SELECT SYSDATE FROM DUAL;
```
```bash
    SYSDATE
    -----------
    06/11/13
```
*****

-해당 날짜에 지정한 달 수만큼 더합니다
```sql
    SELECT HIREDATE , ADD_MONTHS(HIREDATE , 1)
    FROM EMP 
    WHERE EMPNO = 7782;
```
```bash
    HIREDATE     ADD_MONT
    --------------------------
    81/06/09     81/07/09
```
*****

-정의된 날짜의 달에서 마지막 일이 몇 일인지 알 수 있습니다
```sql
    SELECT HIREDATE , LAST_DAY(HIREDATE)
    FROM EMP 
    WHERE EMPNO = 7782;
```
```bash
    HIREDATE     LAST_DAY
    --------------------------
    81/06/09     81/06/30
```
*****
 
-정의된 두 날짜간의 차이 값을 알 수 있습니다
```sql
    SELECT HIREDATE , MONTHS_BETWEEN(SYSDATE , HIREDATE)
    FROM EMP 
    WHERE EMPNO = 7782;
```
```bash
    HIREDATE          MONTHS_BETWEEN(SYSDATE , HIREDATE)
    ----------------------------------------------------
    81/06/09          252.930883
```
*****


-정의된 날짜를 녀도 값을 기준으로 반올림 합니다
```sql
    SELECT ROUND(TO_DATE('27-OCT-98', 'DD-MON-YY'), 'YEAT') 
    FROM DUAL;
```
```bash
    99/01/01
```
*****

[Oracle Express Edition](https://www.oracle.com/kr/database/technologies/xe-downloads.html){: .btn .btn--danger target="_blank"}