### 레코드 검색

Select 문

### 1.1. 테이블의 모든 행과 열 검색

```SQL
select *
  from [TABLE_NAME]
```

* 별표 문자는 지정한 테이블의 모든 열이 반환됨. Where(조건) 을 지정하지 않았으므로 모든 행이 반환됨.
* 대체 모든 각 열을 개별적으로 나열하는 것

```SQL
select empno, ename,job,sal,hiredate,comm,deptno
  from emp
```

(*) 을 사용하는 것이 더 편하나, 각 열을 개별적으로 지정하는 것이 더 좋음.
성능은 비슷하지만 쿼리에서 어떤 열을 반환하는 지 정확하게 알 수 있고 다른 사용자가 이해하기 더 쉽다.


### 1.2 테이블에서 행의 하위 집합 검색하기

테이블에서 특정 조건을 충족하는 행만 보려고 합니다.

```SQL
select *
  from emp
  where deptno = 10
```

Where 절을 사용하면 원하는 조건의 행만 검색할 수 있음.
Where 절의 식이 해당행에 대해 참이면 해당 행이 반환 됨.(= , < , > , <= , >=, ! , <> 와 같은 일반 연산자 지원)

### 여러 조건을 충족하는 행 찾기

여러 조건을 충족하는 행을 반환하려고 합니다.

OR , AND 절과 함께 Where 절을 사용함.

```SQL
select *
  from emp
  where deptno = 10
  or comm is not null
  or sal <= 2000 and deptno = 20
```

AND, OR과 괄호를 조합하여 여러 조건을 만족하는 행을 반환 가능함.
괄호가 있으면 괄호 안의 조건을 함꼐 평가함.
