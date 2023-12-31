## DB 트랜잭션, 회복

### DB 세션

DB 세션은 사용자나 응용 프로그램이 데이터베이스와의 연결을 말합니다. 세션은 데이터베이스에 대한 작업을 수행하는 단위이며, 세션 간에 데이터는 공유되지 않습니다.

### Commit과 Rollback

- **Commit:** 트랜잭션 내에서 수행한 모든 작업이 성공적으로 끝났고, 데이터베이스가 변경 사항을 영구적으로 저장하도록 하는 작업입니다. Commit 후에는 해당 트랜잭션이 완료된 것으로 간주됩니다.

- **Rollback:** 트랜잭션 도중에 오류가 발생하거나 롤백 명령을 내린 경우, 해당 트랜잭션의 모든 변경 사항을 취소하고 이전 상태로 되돌리는 작업입니다.

### 트랜잭션

트랜잭션은 데이터베이스에서 논리적인 작업 단위를 말합니다. 하나의 트랜잭션 내에서 여러 개의 데이터 조작 작업(INSERT, UPDATE, DELETE 등)이 실행되며, 이들은 모두 한꺼번에 성공하거나 실패합니다.

### 트랜잭션의 성질 ACID

ACID는 트랜잭션이 가져야 할 네 가지 중요한 성질을 나타냅니다.

- **원자성(Atomicity):** 트랜잭션의 모든 작업은 원자적으로 실행되어야 하며, 트랜잭션 전체가 성공하거나 전혀 수행되지 않아야 합니다.
- **일관성(Consistency):** 트랜잭션이 수행되기 전과 수행된 후에 데이터베이스는 일관된 상태를 유지해야 합니다.
- **고립성(Isolation):** 여러 개의 트랜잭션이 동시에 실행되더라도, 각 트랜잭션은 서로에게 영향을 주지 않는 것처럼 동작해야 합니다.
- **지속성(Durability):** 트랜잭션이 성공적으로 완료되면, 그 결과는 영구적으로 저장되어야 합니다.

### 트랜잭션 고립 수준(Isolation Level)

트랜잭션 고립 수준은 여러 개의 트랜잭션이 동시에 실행될 때 각 트랜잭션 간의 격리 정도를 나타냅니다. READ UNCOMMITTED, READ COMMITTED, REPEATABLE READ, SERIALIZABLE 등의 고립 수준이 있습니다.

### DB 락(Lock)

락은 트랜잭션이나 쿼리가 데이터에 접근할 때 다른 트랜잭션과의 충돌을 방지하기 위해 사용되는 메커니즘입니다. 락은 데이터의 일관성을 보장하고 동시성 문제를 해결하는 데 도움을 줍니다.

### DB 갱신 손실 문제

DB 갱신 손실 문제란 여러 개의 트랜잭션이 동시에 같은 데이터를 수정할 때 발생할 수 있는 문제를 의미합니다. 이로 인해 특정 트랜잭션의 결과가 다른 트랜잭션에 덮어씌워질 수 있습니다.

### DB 동시성 제어

동시성 제어는 여러 개의 트랜잭션이 동시에 실행될 때, 데이터의 일관성을 유지하면서 동시성을 보장하는 메커니즘입니다. 락과 트랜잭션 고립 수준을 이용하여 동시성 문제를 관리합니다.

### DB 데드락(Deadlock)

데드락은 두 개 이상의 트랜잭션이 서로의 락을 대기하는 상태로 교착되는 현상을 말합니다. 이러한 상황에서는 트랜잭션들이 무한히 진행하지 못하고 대기 상태에 머무를 수 있습니다.

### DB 회복(Recovery)

DB 회복은 데이터베이스 시스템이 비정상적으로 종료되거나 데이터가 손실되었을 때, 데이터를 이전 상태로 복원하는 작업을 의미합니다.

### REDO와 UNDO

- **REDO:** 트랜잭션의 커밋이 발생했을 때, 해당 트

랜잭션의 변경 사항을 로그에 기록하는 작업입니다. 이 로그 정보를 사용하여 시스템이 비정상적으로 종료되었을 때 변경 사항을 복구할 수 있습니다.

- **UNDO:** 트랜잭션이 롤백되거나 실패했을 때, 해당 트랜잭션의 변경 사항을 취소하고 이전 상태로 돌리는 작업입니다.

### 체크포인트 회복 기법

체크포인트 회복 기법은 데이터베이스의 상태를 주기적으로 체크포인트로 지정하여 로그를 통해 이전 상태로 복구할 수 있는 방법입니다. 이를 통해 회복 작업의 범위와 시간을 줄일 수 있습니다.

### MySQL InnoDB의 기본 트랜잭션 고립 수준

MySQL InnoDB의 기본 트랜잭션 고립 수준은 REPEATABLE READ입니다. 이로 인해 같은 트랜잭션 내에서 같은 쿼리를 여러 번 실행해도 결과가 일관성 있게 유지됩니다.
