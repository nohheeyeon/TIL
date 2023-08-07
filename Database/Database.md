# 파일시스템과 데이터베이스의 차이

- 파일시스템은 운영체제에서 파일과 폴더를 저장하고 관리하는 시스템으로, 데이터를 일반적인 텍스트나 바이너리 형태로 저장합니다. 반면에 데이터베이스는 구조화된 방식으로 데이터를 저장하며, 관계형 데이터베이스는 테이블 형태로 데이터를 정리하여 저장합니다.
- 데이터베이스는 데이터에 대한 일관성, 무결성, 보안 등을 보장하고 여러 사용자가 동시에 접근할 수 있는 동시성 제어 기능을 제공합니다. 또한 데이터베이스는 쿼리 기능을 제공하여 데이터를 검색하고 조작하는 데 유용합니다.

# 데이터베이스의 특징

- 데이터의 중복 최소화: 데이터베이스는 중복된 데이터를 허용하지 않고, 정규화를 통해 데이터를 최적화하여 저장합니다.
- 데이터 무결성: 데이터베이스는 정의된 규칙에 따라 유효한 데이터만 저장하여 데이터의 무결성을 보장합니다.
- 동시성 제어: 여러 사용자가 동시에 데이터에 접근하는 상황에서도 데이터의 일관성을 유지하기 위해 동시성 제어 기능을 제공합니다.
- 보안: 데이터베이스는 권한 관리를 통해 데이터에 대한 접근을 제어하고 보안을 유지합니다.

# DBMS (Database Management System)에 대한 설명:

- DBMS는 데이터베이스를 생성, 수정, 관리하고 데이터를 검색하고 조작하는 소프트웨어입니다.
- DBMS는 데이터베이스의 구조를 정의하고 데이터를 효율적으로 저장하며, 데이터베이스를 사용하는 응용 프로그램과 데이터베이스 사이의 상호 작용을 조정합니다.

- 일반적으로 DBMS는 SQL(Structured Query Language)을 사용하여 데이터를 조작합니다.

# 스키마와 3단계 데이터베이스 구조:

- 스키마는 데이터베이스의 구조를 정의한 것으로, 데이터베이스의 테이블, 속성, 관계 등을 기술합니다.
- 3단계 데이터베이스 구조는 외부 스키마, 개념 스키마, 내부 스키마로 나누어지며, 사용자, 응용 프로그램, 데이터베이스 관리자 간의 관점을 반영합니다.

# 데이터 독립성:

- 데이터 독립성은 데이터베이스의 논리적 구조와 물리적 구조를 분리하여 변경이나 수정에 유연성을 제공하는 개념입니다.
- 논리적 독립성은 외부 스키마가 변경되어도 개념 스키마와 내부 스키마에 영향을 주지 않는 것을 의미하며, 물리적 독립성은 내부 스키마가 변경되어도 개념 스키마에 영향을 주지 않는 것을 의미합니다.

# RDBMS (관계형 데이터베이스 관리시스템)

- RDBMS는 관계형 데이터베이스를 생성, 관리, 조작하는 DBMS의 한 유형입니다.
- 데이터는 테이블로 구성되며, 테이블 간에 관계를 정의하여 데이터를 구조화합니다.
- SQL을 사용하여 데이터를 쿼리하고 조작합니다.

# 릴레이션 스키마와 릴레이션 인스턴스:

- 릴레이션 스키마는 테이블의 구조를 정의한 것으로, 속성의 이름과 타입을 기술합니다.
- 릴레이션 인스턴스는 릴레이션 스키마에 따라 구체적인 데이터를 포함한 테이블의 한 행을 나타냅니다.

# 릴레이션의 차수와 카디널리티

- 릴레이션의 차수는 테이블의 열(속성)의 개수를 의미합니다.
- 릴레이션의 카디널리티는 테이블의 행(인스턴스)의 개수를 의미합니다.

# 키(Key)에 대한 설명

- 키는 데이터베이스에서 특정 레코드를 고유하게 식별하는 데 사용되는 속성입니다.
- 슈퍼키, 후보키, 기본키, 대체키, 외래키 등 다양한 종류의 키가 있으며, 각각의 키는 특정 목적과 제약에 따라 사용됩니다.

# 무결성 제약조건

- 데이터베이스에서 데이터의 무결성을 보장하기 위해 정의된 제약조건입니다.
- 도메인 무결성, 개체 무결성, 참조 무결성은 데이터의 유효성과 일관성을 유지하는 데 도움을 줍니다.