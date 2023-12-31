# SQL (+ C언어와 같은 프로그래밍 언어와 어떤 차이가 있는지)

SQL(Structured Query Language)은 데이터베이스에서 데이터를 조작하고 관리하기 위해 사용되는 언어입니다. SQL은 관계형 데이터베이스 관리 시스템(RDBMS)과 함께 사용되며, 데이터의 삽입, 조회, 수정, 삭제 등 다양한 작업을 수행할 수 있습니다. SQL은 선언형 언어로서, 어떤 결과를 원하는지를 명시하는 방식으로 동작합니다. 반면에 C언어와 같은 프로그래밍 언어는 절차적 언어로서, 데이터 처리를 순차적으로 기술하는 방식으로 동작합니다.

# 개발자가 작성한 SQL이 실행되는 과정

1. SQL 문장 작성: 개발자가 SQL 문장을 작성합니다. 이 문장은 데이터베이스에서 수행하고자 하는 작업을 정의합니다.

2. 파싱: 데이터베이스 관리 시스템은 작성된 SQL 문장을 파싱하여 문법적으로 올바른지 확인합니다.

3. 컴파일: 파싱된 SQL 문장은 실행 계획으로 변환됩니다. 데이터베이스 엔진은 적절한 인덱스나 조인 방법 등을 고려하여 최적의 실행 계획을 수립합니다.

4. 최적화: 실행 계획이 최적화되고, 데이터베이스 엔진은 데이터 액세스 경로를 결정합니다.

5. 실행: 최적화된 실행 계획을 바탕으로 SQL 문장이 실행됩니다. 데이터베이스에서 요청한 작업을 수행하고 결과를 반환합니다.

# DML

DML(Data Manipulation Language)은 데이터베이스에서 데이터를 조작하는 역할을 담당하는 SQL의 하위 언어입니다.

- 주요 DML 구문
  - SELECT: 데이터베이스에서 데이터를 조회하는데 사용됩니다.
  - INSERT: 새로운 데이터를 테이블에 삽입하는데 사용됩니다.
  - UPDATE: 테이블에 있는 기존 데이터를 수정하는데 사용됩니다.
  - DELETE: 테이블에서 데이터를 삭제하는데 사용됩니다.

# DDL

DDL(Data Definition Language)은 데이터베이스의 구조를 정의하고 관리하는 역할을 담당하는 SQL의 하위 언어입니다.

- 주요 DDL 구문

  - CREATE: 테이블, 인덱스, 뷰 등의 데이터베이스 객체를 생성하는데 사용됩니다.
  - ALTER: 테이블이나 데이터베이스 객체의 구조를 변경하는데 사용됩니다.
  - DROP: 테이블이나 데이터베이스 객체를 삭제하는데 사용됩니다.
  - TRUNCATE: 테이블의 모든 데이터를 삭제하는데 사용됩니다.

# DCL

DCL(Data Control Language)은 데이터베이스에 대한 접근 권한을 제어하는 역할을 담당하는 SQL의 하위 언어입니다.

- 주요 DCL 구문
  - GRANT: 데이터베이스 사용자에게 특정 작업에 대한 권한을 부여하는데 사용됩니다.
  - REVOKE: 데이터베이스 사용자에게 부여된 권한을 취소하는데 사용됩니다.

# CASCADE 설정

CASCADE는 테이블을 수정하거나 삭제할 때, 해당 테이블과 관련된 다른 테이블들에도 동일한 수정 또는 삭제 작업을 전파시키는 옵션입니다. CASCADE 설정을 적용하면, 부모 테이블의 행이 수정되거나 삭제될 때 자식 테이블의 관련 행들도 동일하게 수정 또는 삭제됩니다. 이를 통해 데이터베이스의 무결성을 유지하고 관련된 데이터들이 일관성 있게 유지될 수 있습니다.

# VIEW

VIEW는 하나 이상의 테이블로부터 유도된 가상 테이블입니다. 실제로 데이터를 저장하는 것이 아니라, SQL 쿼리의 결과를 가상으로 나타내는 역할을 합니다. VIEW는 데이터베이스 사용자가 복잡한 쿼리를 단순화하고, 데이터에 접근하는 권한을 제어하기 위해 사용됩니다. VIEW를 사용하면 사용자는 특정 데이터만을 선택적으로 조회하거나 수정할 수 있습니다.

# SELECT 절의 처리순서

SELECT 절은 SQL 쿼리에서 데이터를 조회하는데 사용되는 부분입니다.

- SELECT 절의 처리 순서

1. FROM: 데이터를 조회할 테이블을 지정합니다.
2. WHERE: 조회할 데이터의 조건을 지정합니다. (선택적)
3. GROUP BY: 데이터를 그룹화하는 기준을 지정합니다. (선택적)
4. HAVING: 그룹화된 데이터에 대한 조건을 지정합니다. (선택적)
5. SELECT: 조회할 열들을 선택합니다.
6. ORDER BY: 조회된 데이터의 정렬 기준을 지정합니다. (선택적)

# SELECT ~ FOR UPDATE 구문

SELECT ~ FOR UPDATE 구문은 특정 데이터를 조회할 때 해당 데이터에 대한 잠금을 걸어 다른 트랜잭션들이 해당 데이터를 수정하지 못하도록 하는 역할을 합니다. 이 구문을 사용하면 데이터를 조회하는 시점에 해당 데이터에 대한 쓰기 잠금이 설정되며, 다른 트랜잭션들은 해당 데이터를 조회할 수 있지만, 수정은 할 수 없습니다. 이를 통해 데이터의 일관성을 유지하고 동시성 문제를 방지할 수 있습니다.

# GROUP BY절

GROUP BY절은 데이터를 특정 기준으로 그룹화하는데 사용됩니다. GROUP BY절을 사용하면 결과 집합이 특정 열의 고유한 값으로 그룹화되며, 이 그룹들에 대한 집계 함수를 적용할 수 있습니다. GROUP BY절과 함께 사용되는 집계 함수로는 COUNT, SUM, AVG, MAX, MIN 등이 있습니다. 이를 통해 특정 조건에 따른 데이터의 통계를 얻을 수 있습니다.

# ORDER BY절

ORDER BY절은 조회된 데이터의 정렬 순서를 지정하는데 사용됩니다. ORDER BY절을 사용하면 특정 열의 값을 기준으로 오름차순(ASC) 또는 내림차순(DESC)으로 정렬할 수 있습니다. ORDER BY절은 주로 조회된 데이터를 사용자에게 편리하게 보여주기 위해 사용되며, 특정 기준으로 정렬된 결과를 얻을 수 있습니다.

# INNER JOIN과 OUTER JOIN의 차이점

INNER JOIN과 OUTER JOIN은 테이블 간의 관계를 이용하여 데이터를 결합하는데 사용되는 JOIN의 종류입니다.

- INNER JOIN: INNER JOIN은 두 테이블 간에 공통된 값을 가지고 있는 행들만을 반환합니다. 즉, 두 테이블의 조인 조건을 만족하는 데이터만 조회됩니다.

- OUTER JOIN: OUTER JOIN은 두 테이블 간에 조인 조건을 만족하지 않는 행들까지도 모두 반환합니다. 즉, 조인 조건을 만족하지 않더라도 한 쪽

테이블의 데이터를 모두 포함하여 결과를 반환합니다.

# LEFT OUTER JOIN, RIGHT OUTER JOIN

- LEFT OUTER JOIN: LEFT OUTER JOIN은 왼쪽(첫 번째) 테이블을 기준으로 조인을 수행하며, 조인 조건을 만족하는 오른쪽(두 번째) 테이블의 데이터를 모두 포함하여 결과를 반환합니다. 조인 조건을 만족하지 않는 경우에는 오른쪽 테이블의 데이터는 NULL로 채워집니다.

- RIGHT OUTER JOIN: RIGHT OUTER JOIN은 오른쪽(두 번째) 테이블을 기준으로 조인을 수행하며, 조인 조건을 만족하는 왼쪽(첫 번째) 테이블의 데이터를 모두 포함하여 결과를 반환합니다. 조인 조건을 만족하지 않는 경우에는 왼쪽 테이블의 데이터는 NULL로 채워집니다.

# CROSS JOIN

CROSS JOIN은 두 개 이상의 테이블들을 조합하여 가능한 모든 조합을 생성하는데 사용되는 JOIN의 종류입니다. CROSS JOIN은 각 테이블의 모든 행들과 다른 테이블들의 모든 행들을 조합하여 결과를 반환합니다. 따라서 CROSS JOIN은 결과 집합의 크기가 각 테이블의 행 수를 곱한 만큼 커질 수 있으므로 사용시 주의가 필요합니다.

# 서브쿼리

서브쿼리(Subquery)는 다른 쿼리 내에 포함된 중첩된 쿼리를 의미합니다. 서브쿼리는 주로 WHERE, FROM, SELECT, HAVING 등의 절에서 사용됩니다. 서브쿼리는 먼저 실행되어 결과를 반환한 후, 외부 쿼리와 결합되어 최종 결과를 생성합니다. 서브쿼리는 주로 복잡한 조건을 작성하거나 한정된 결과를 필요로 할 때 사용됩니다.

# DROP, TRUNCATE, DELETE

- DROP: DROP은 데이터베이스 객체(테이블, 뷰 등)를 삭제하는데 사용됩니다. DROP 명령을 실행하면 해당 객체와 관련된 데이터와 구조가 완전히 삭제됩니다.

- TRUNCATE: TRUNCATE는 테이블에 있는 모든 데이터를 삭제하는데 사용됩니다. TRUNCATE는 DELETE보다 더 빠르게 데이터를 삭제하지만, 롤백(복구)이 불가능하고 테이블 구조는 유지됩니다.

- DELETE: DELETE는 테이블에서 특정 행 또는 조건에 맞는 데이터를 삭제하는데 사용됩니다. DELETE 명령을 실행하면 해당 행들의 데이터만 삭제되고 테이블 구조는 유지됩니다. DELETE는 롤백(복구) 가능합니다.

# DISTINCT

DISTINCT는 중복되는 데이터를 제거하여 유니크한 값만을 반환하는데 사용됩니다. SELECT 문에서 DISTINCT 키워드를 사용하면 중복된 데이터가 있는 경우 하나의 데이터만을 결과로 반환합니다. 예를 들어, "SELECT DISTINCT column_name FROM table_name;"과 같이 사용할 수 있습니다. DISTINCT를 사용하는 경우, 데이터베이스가 모든 행을 검사하여 중복 값을 제거하므로 성능에 영향을 미칠 수 있습니다.

# SQL Injection 공격

SQL Injection은 악의적인 사용자가 웹 응용 프로그램에 악의적인 SQL 코드를 삽입하여 데이터베이스를 공격하는 기법입니다. 이를 통해 데이터베이스의 정보를 불법적으로 조회하거나 조작할 수 있습니다. 예를 들어, 사용자 입력에 대해 검증이 제대로 이루어지지 않고 직접 SQL 쿼리에 삽입되는 경우, 악의적인 사용자는 해당 쿼리를 조작하여 보안에 취약한 상태로 만들 수 있습니다.

- SQL Injection을 예방

* Prepared Statement 사용: Prepared Statement를 사용하면 사용자 입력을 파라미터로 전달하여 쿼리를 실행하므로, 악의적인 코드를 삽입하는 것을 방지할 수 있습니다.

* 입력 값 검증: 사용자로부터 입력받은 값을 검증하여 쿼리 실행 전에 올바른 형식과 범위의 값인지 확인해야 합니다.

* Stored Procedure 사용: 저장 프로시저를 사용하여 SQL 쿼리를 미리 정의하고, 사용자 입력을 전달하는 방식으로 데이터베이스를 접근하면 보안 취약점을 줄일 수 있습니다.

* 권한 제한: 데이터베이스 사용자에게 최소한의 권한만 부여하여 필요한 작업만 수행하도록 제한해야 합니다.

# SQL 안티패턴

SQL 안티패턴은 비효율적인 쿼리 작성이나 부적절한 데이터베이스 구조로 인해 발생하는 문제를 의미합니다. 몇 가지 대표적인 SQL 안티패턴은 다음과 같습니다:

- SELECT _ 사용: 모든 열을 조회하는 SELECT _ 문은 필요하지 않은 데이터까지 조회하여 성능 저하를 가져올 수 있습니다. 필요한 열만 명시하여 조회하는 것이 좋습니다.

- 중복 데이터 저장: 데이터베이스에서 동일한 정보를 중복해서 저장하는 것은 데이터 일관성을 해치고 저장 공간을 낭비할 수 있습니다. 정규화를 통해 중복 데이터를 최소화하는 것이 바람직합니다.

- 너무 많은 인덱스 사용: 인덱스는 검색 성능을 향상시키지만, 너무 많이 사용하면 데이터 삽입, 수정, 삭제에 영향을 미칠 수 있습니다. 필요한 인덱스만 생성하는 것이 좋습니다.

# 페이지네이션을 구현 시 쿼리 작성

페이지네이션은 데이터베이스에서 대량의 데이터를 한 번에 로드하지 않고, 필요한 페이지만을 나누어 조회하는 기법입니다. 페이지네이션을 구현하기 위해서는 LIMIT 절과 OFFSET 절을 사용하는 것이 일반적입니다. 데이터베이스마다 문법이 다를 수 있으므로 몇 가지 예시를 보겠습니다:

1. MySQL, PostgreSQL:

```
SELECT * FROM table_name LIMIT page_size OFFSET (page_number - 1) * page_size;
```

2. Oracle:

```
SELECT * FROM (SELECT rownum as rn, t.* FROM table_name t) WHERE rn >= ((page_number - 1) * page_size) AND rn <= (page_number * page_size);
```

위의 쿼리에서 `page_size`는 한 페이지에 표시할 항목의 개수를, `page_number`는 조회할 페이지 번호를 나타냅니다. 페이지네이션을 구현할 때는 쿼리 성능과 데이터 정렬에 주의하여 효율적으로 작성하는 것이 중요합니다.
