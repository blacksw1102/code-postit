# group by 없이 순위 매기는 방법

## 중복 순위의 다음 순위 기준

`RANK()`의 경우 중복 순위 개수만큼 다음 순위의 값을 증가시켜 순위를 매기나, `DENSE_RANK()`의 경우 중복 순위 개수에 상관없이 다음 순위 값은 +1만 증가시켜서 순위를 매긴다.

```sql
SELECT ENAME
     , SAL
     , RANK() OVER(ORDER BY SAL DESC) RANK
     , DENSE_RANK() OVER(ORDER BY SAL DESC) DENSE_RANK
  FROM EMP
 ORDER BY SAL DESC

```

## 중복 순위 값 없애기

`OVER` 함수 내부의 `ORDER BY 컬럼`을 추가해서 세부적으로 순위를 매기도록 한다.

```sql
SELECT ENAME
     , SAL
     , COMM
     , RANK() OVER(ORDER BY SAL DESC, COMM DESC) RANK
  FROM EMP
 ORDER BY SAL DESC, COMM DESC
```

## 그룹별 순위 정하기

`PARTITION BY` 절을 추가하면 해당 컬럼을 기준으로 그룹핑 해서, 그룹별 순위를 매길 수 있다.

```sql
SELECT DEPT
     , ENAME
     , SAL
     , COMM
     , RANK() OVER(PARTITION BY DEPT ORDER BY SAL DESC, COMM DESC) RANK
  FROM EMP
 ORDER BY DEPT, SAL DESC, COMM DESC
```

## 그룹별 최소값, 최대값 구하기

`FIRST, LAST`를 이용하면 `DENSE_RANK ORDER BY 컬럼` 으로 정렬된 레코드들 중에서 첫번째 순위 또는 마지막 순위의 레코드들을 추려낼 수 있다. 근데 만약에 추려낸 레코드가 2개 이상이라면 `MIN(컬럼), MAX(컬럼)`을 통해서 특정 컬럼을 기준으로 한번더 걸러내어 최종적인 최소값 최대값을 구할 수가 있다.

```sql
SELECT DEPT
     , ENAME
     , SAL
     , MIN(SAL) KEEP(DENSE_RANK FIRST ORDER BY SAL) OVER(PARTITION BY DEPT) SAL_MIN
     , MAX(SAL) KEEP(DENSE_RANK LAST ORDER BY SAL) OVER(PARTITION BY DEPT) SAL_MAX
  FROM EMP
 ORDER BY DEPT, SAL DESC
```

## 키워드 정리

- RANK
- DENSE_RANK
- OVER
- ORDER BY
- PARTITION BY
- MIN
- MAX
- KEEP
- FIRST
- LAST
