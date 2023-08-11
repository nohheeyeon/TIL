# Docker

    [도커 공식 홈페이지] https://docs.docker.com/get-started/overview/

### Docker

- open platform
- 어플리케이션을 인프라에서 분리
- 신속
- 인프라를 어플리케이션을 관리하는 것 처럼 관리 가능
- 코드 배포에 용이
- **컨테이너 기반 가상화 도구**
  - 리눅스 컨테이너 기술인 LXC(Linux Containers) 기반
- **애플리케이션을 컨테이너라는 단위로 격리하여 실행하고 배포하는 기술**
- 다양한 운영체제에서 사용할 수 있으며, 컨테이너화된 애플리케이션을 손쉽게 빌드, 배포, 관리할 수 있는 다양한 기능을 제공
- 애플리케이션을 빠르게 개발하고, 효율적으로 배포, 관리할 수 있음

### Container

- 컨테이너는 가상화 기술 중 하나
- 호스트 운영체제 위에 여러 개의 격리된 환경을 생성
- 각각의 컨테이너 안에서 애플리케이션을 실행

#### Container 기반 특징

- 리눅스 커널의 기능을 사용하여 만들어짐
  - chroot: 파일 시스템을 격리
  - namespace: 프로세스 격리
  - cgroup: 하드웨어 자원 격리
- 프로세스 단위의 격리 환경

### 가상화 (Virtualization) 기술

- 하나의 물리적인 컴퓨터 자원(CPU, 메모리, 저장장치 등)을 가상적으로 분할하여 여러개의 가상 컴퓨터 환경을 만들어내는 기술
  -> 물리적인 컴퓨터 자원을 더욱 효율적으로 사용 가능
  -> 서버나 애플리케이션 등을 운영하는데 있어 유연성과 안정성을 제공
  _ 하이퍼바이저 (Hypervisor)
  _ 가상 머신(Virtual Machine, VM)을 생성하고 구동하는 소프트웨어
  _ OS에 자원을 할당 및 조율
  _ OS들의 요청을 번역하여 하드웨어에 전달

### Docker Architecture

- 도커 데몬 ( Docker daemon = dockerd )
  - 도커 엔진의 핵심 구성 요소
  - 도커 호스트에서 컨테이너를 관리하고 실행하는 역할
  - 컨테이너를 생성, 시작, 중지, 삭제하는 등의 작업을 수행
  - 컨테이너 이미지를 관리
  - 외부에서 이미지를 다운로드하고 빌드하는 작업을 수행
- 도커 클라이언트 ( Docker Client )
  - Docker와 상호작용
  - docker 명령어를 사용하면 Docker daemon으로 보내어 실행
- 도커 오브젝트 ( Docker Object )
  - 도커 이미지 ( Docker Image )
    - 도커 컨테이너를 만들기 위한 읽기 전용 템플릿
  - 도커 컨테이너 ( Docker Container )
    - 한 도커 이미지의 실행 가능한 인스턴스
    - 애플리케이션을 실행하기 위한 모든 파일과 설정 정보를 포함하는 패키지

* 도커 레지스트리 ( Docker Registries )
  - 도커 이미지 ( Docker Image )를 관리하고 저장하는 곳
    - Docker hub: 디폴트 레지스트리, 누구나 접근 가능한 공개형 저장소

### Docker CLI

- Download an image from registry
  - docker pull [OPTINS]NAME:[:TAG|@DIGEST]
- List images
  - docker images [OPTIONS] [REPOSITORY [:TAG]]
- Create and run a new container from an image
  - docker run [OPTIONS]IMAGE[COMMAND][ARG...]
- Stop one or more running containers
  - docker stop [OPTINOS]CONTAINER[CONTAINER...]
- Fetch the logs of a container
  - docker logs [OPTIONS] CONTAINER
- Remove one or more containers
  - docker rm [OPTIONS]CONTAINER[CONTAINER...]
- Remove one or more images
  - docker rmi [OPTIONS]IMAGE[IMAGE...]

### 도커 이미지 빌드하기

    Dockerfile syntax
    https://docs.docker.com/build/guide/intro/

- FROM: 베이스 이미지 선정
- WORKDIR: work directory 선정
- COPY: 복사할 파일 선정 (예: 작업한 서비스 파일들)
- RUN: 실행할 명령어
- ENTRYPOINT: 컨테이너가 시작할 때 실행할 명령어 (예: 서버 실행)

### 도커 이미지를 도커 허브에 올리기

도커 이미지 만들기

- 이미지 태그 설정
  - Docker Hub에 이미지를 등록하려면 아래와 같은 규칙을 준수해야한다:
    - [Docker Hub 사용자명]/이미지명:[태그명]
  - 태그 방법
    - build 시: docker build -t my-httpd .
    - build 후: docker image tag [image name]

### 도커 네트워크

네트워크 드라이버

- Network Drivers [https://docs.docker.com/network/drivers/]
  - bridge: 기본 네트워크 드라이버, 동일한 도커 호스트에서 컨테이너 간의 통신을 도와줌
  - host: 호스트의 네트워크를 직접 사용
  - overlay: 서로 다른 도커 호스트의 컨테이너 간 통신을 도와줌

### 도커 컴포즈

https://docs.docker.com/compose/compose-file/

- 도커 컨테이너를 일괄적으로 정의하고 제어하는 도구
- 설정 파일을 도커 CLI로 번역하는 역할

##### 도커 컴포즈 파일 구성

- version
- services
  - 실행하려는 컨테이너들을 정의하는 역할
  - 이름, 이미지, 포트 매핑, 환경 변수, 볼륨 등을 포함
  - 해당 정보를 가지고 컨테이너를 생성하고 관리
    - image: 컨테이너를 생성할 때 쓰일 이미지 지정
    - build: 정의된 도커파일에서 이미지를 빌드해 서비스의 컨테이너를 생성하도록 설정
    - environment: 환경 변수 설정, docker run 명령어의 --env, -e 옵션과 동일
    - command: 컨테이너가 실행될 때 수행할 명령어, docker run 명령어의 마지막에 붙는 커맨드와 동일
    - depends_on: 컨테이너 간의 의존성 주입, 명시된 컨테이너가 먼저 생성되고 실행
    - ports: 개방할 포트 지정, docker run 명령어의 -p와 동일
    - expose: 링크로 연계된 컨테이너에게만 공개할 포트 설정
    - volumes: 컨테이너에 볼륨을 마운트함
    - restart: 컨테인어가 종료될 때 재시작 정책
      - no: 재시작되지않음
      - always: 외부에 영향에 의해 종료되었을 때 항상 재시작 ( 수동으로 끄기 전까지)
      - on-failure: 오류가 있을 시에 재시작

##### 도커 컴포트 명령어

- docker-compose vs docker compose
  -> docker-compose 명령어가 docker compose로 흡수되었음
  -> 이전에는 Docker에서는 docker-compose 명령어가 별도로 설치되어야 했지만, Docker 1.13 이후로는 docker-compose 명령어가 Docker CLI에 통합됨

* docker-compose -f local-infra.yml up -d
  - up: 도커 컴포즈 파일로, 컨테이너를 생성하기
  - -f: 도커 컴포즈 파일 지정하기
  - -d: 백그라운드에서 실행하기

##### 도커 CLI로 여러개 컨테이너 관리하기

- 도커 네트워크 리스트 조회
  - docker network ls
    - bridge: 도커 엔진에 의해 자동으로 생성되는 가상 네트워크. 컨테이너끼리 연결되는 기본 네트워크
    - host: 호스트 컴퓨터의 네트워크 인터페이스를 그대로 사용하는 네트워크
    - none: 네트워크를 사용하지 않는 컨테이너
- 도커 네트워크 생성
  - docker network create wordpress_net
    -> 도커 네트워크를 생성하는 명령어 (네트워크의 이름을 지정)
- 도커 컴포즈로 여러개 컨테이너 관리하기
  - docker-compose -f docker-compose.yml up --build

### 컨테이너 오케스트레이션의 기능

- 컨테이너 클러스터링(Clustering)

  - 여러 대의 노드(node)를 하나의 클러스터(cluster)로 묶어, 애플리케이션을 분산하여 실행하고, 자원을 효율적으로 활용하는 기능
  - 여러 대의 물리적인 또는 가상의 서버를 하나의 시스템처럼 동작하게 하는 기술
  - 컨테이너를 실행하는 호스트의 자원을 효율적으로 분배, 컨테이너가 안정적으로 실행되도록 함
  - 여러 대의 컨테이너를 묶어 하나의 서버처럼 사용할 수 있도록 지원

- 서비스 디스커버리(Service Discovery)

  - 컨테이너를 자동으로 발견하고, 서비스 이름과 IP 주소 등을 관리하여, 애플리케이션 간의 연결을 관리하는 기능
  - 클라우드 환경에서의 컨테이너 생성, 배치, 이동에 따른 IP, Port 정보 업데이트 및 관리

- 자동 스케일링(Autoscaling)

  - 애플리케이션의 트래픽 양에 따라 자동으로 컨테이너 수를 조절하여, 자원 사용량을 최적화하고, 가용성을 보장하는 기능

- 로드 밸런싱(Load Balancing)

  - 여러 대의 노드에서 실행 중인 컨테이너들을 조절하여, 트래픽을 균등하게 분배하여, 애플리케이션의 성능을 최적화하는 기능

- 롤아웃과 롤백(Rollout and Rollback)

  - 새로운 버전의 애플리케이션을 롤아웃하고, 이전 버전을 롤백하는 기능

- 자동 복구(Automatic Recovery)

  - 컨테이너나 노드의 장애 시 자동으로 복구하는 기능

- 모니터링과 로깅(Monitoring and Logging)

  - 컨테이너나 노드의 상태를 모니터링하고, 로그를 수집하여, 애플리케이션의 성능과 문제점을 분석하는 기능

- 보안과 네트워크 관리(Security and Network Management)
  - 컨테이너와 노드의 보안을 관리하고, 네트워크 설정을 관리하는 기능

### 대표적인 컨테이너 오케스트레이션 툴/서비스

1. 도커 스윔

- Docker Inc.이 개발한 도커 컨테이너 오케스트레이션 도구
- Docker Swarm은 2015년 Docker 1.12 버전에서 처음 발표됨
- 이전에는 Docker Swarm Classic이라는 이름으로, Swarm 모드가 추가되지 전에 도커 엔진에 통합되지 전에 독립적으로 배포
- Docker Swarm은 쿠버네티스가 등장하기 전까지 가장 ㄷ중적인 컨테이너 오케스트레이션 도구 중 하나
- 간단하게 작동하고 설정이 쉬움

2. Kubernetes

https://kubernetes.io/ko/docs/home/

- 배경
  - Gmail, Youtube, 검색 등 다양한 웹 서비스가 있고, 대용량 트래픽을 감당해야함
  - 이를 감당하기위해, Kubernetes 프로젝트를 시작, 실제 서비스에 적용함
- 오픈 소스 기반
- 구글에서 설계, 현재 리눅스 재단에 의해 관리
- 쿠버네티스 v1.0은 2015년 7월 21일에 출시
- 대규모에 적합
  - 스케일링 기능 강화 ( Replication Controller: 컨테이너 수를 동적으로 조절)
  - 서비스 디스커버리 기능 강화 (DNS 기반)
- 가장 기능이 풍부하고 널리 사용되는 컨테이너 오케스트레이션 프레임워크
- 베어 메탈, VM환경, 퍼블릿 클라우드 등의 다양한 환경에서 작동하도록 설계되어 있음

3. GKE(Google Kubernetes Engine)

- Google Cloud Platform(GCP)에서 제공하는 Kubernetes 기반의 관리형 컨테이너 오케스트레이션 서비스
- 따라서 GKE는 Kubernetes를 기반으로 하고, Kubernetes의 기능을 모두 제공

4. EKS (Amazon Elastic Kubernetes Service)

- AWS 제공하는 관리형 Kubernetes 서비스
- EKS는 Kubernetes 기반으로 구축되어 있음
- 사용자는 Kubernetes API를 사용하여 EKS 클러스터를 관리할 수 있음

5. ECS (Amazon Elastic Container Service)
   https://docs.aws.amazon.com/ko_kr/ecs/index.html

- AWS에서 제공하는 관리형 컨테이너 오케스트레이션 서비스
- Docker 컨테이너를 실행하기 위한 기능을 제공
- 사용자는 ECS를 사용하여 컨테이너를 배포, 관리, 스케일링
- ECS 서비스 종류 유형
  - 1. EC2
    - 컨테이너가 운영되는 자원이 AWS EC2
    - 용량공급자(Capacity Providers)를 통해 EC2 Auto-ScalingGroup을 연결
    - ECS에서 제공하는 관리형 지표 "CapacityProviderReservation"에 따라 EC2 용량을 추가/제거 할 수 있으며, 컨테이너의 숫자의 증가/축소에 따라 EC2도 함께 증가/축소하게 됩니다
    - EC2 유형 비용: 호스트로 사용하는 EC2 요금만 과금
  - 2. Fargate
    - 서버리스 유형으로, EC2를 배포하거나 관리할 필요없이 그냥 서비스만 운영
    - 컨테이너가 어디서 운영되는 지 관리할 필요 없음
    - Fargate 유형 비용: 시간 당 vCPU, Storage 용량 비용이 부과
  - 3. External
    - AWS 인프라가 아닌 호스트에서 ECS에서 정의한 서비스
    - 호스트&컨테이너 등 실제 서비스는 물리적으로 AWS 밖에서 동작
    - AWS 콘솔에서 관리
- ECS 구성 요소
  - Task Definition
    - ECS에서 컨테이너를 실행하기 위한 "블루프린트" 또는 "레시피"
      - 어플리케이션이 어떻게 실행될 지에 대한 세부 사항을 포함
        - 도커 이미지, 필요한 CPU와 메모리, 사용되는 환경 변수, 포트 매핑 등을 지정
  - Task
    - Task Definition에 기반하여 실행되는 컨테이너 인스턴스
      - Task Definition은 레시피나 설계도라면, Task는 그 설계도를 기반으로 만들어진 '제품' 또는 '실행 인스턴스' 라고 볼 수 있음
        -> 예를 들어, 하나의 Task Definition으로부터 동시에 여러 Task를 실행할 수 있따
      - 각 테스크는 독립적으로 실행되며, 각자의 상태 및 라이프사이클을 가지게 됨
  - Service
    - 특정 작업 정의에 기반한 작업 집합을 실행하고 유지 관리하는 역할
      - 특정 작업의 인스턴스를 지정된 수로 유지하거나, 부하 분산, 서비스 발견, 롤링 업데이트 등과 같은 추가 기능을 제공
    - Service (주요 기능 및 목적)
      - Desired Count
        - 사용자가 지정한 수의 작업 인스턴스를 지속적으로 실행하도록 보장
        - 만약 작업 인스턴스가 실패하거나 중지되면 ECS는 자동으로 새 작업을 시작하여 원하는 수의 작업을 유지
      - Load Balancing
        - Application Load Balancer, Network Load Balancer 또는 Classic Load Balance와 통합될 수 있음
        - 트래픽이 ECS 작업에 균일하게 분산될 수 있도록 함
      - Service Discovery
        - 동적 IP 주소를 사용하여 서비스를 검색하고 연결
      - Rolling Updates
        - 애플리케이션 업데이트
        - 작업 정의를 업데이트하면서 서비스를 지속적으로 실행할 수 있도록 함
      - Scaling
        - 요구 사항 / 정책에 따라 자동으로 확장 및 축소 시킴
      - ECS cluster
        - 컨테이너화된 애플리케이션을 실행하기 위한 논리적인 그룹핑 또는 환경을 의미
          - 하나 이상의 인스턴스와 함께 실행되는 서비스 및 Task로 구성됨

### IAM 권한 설정

- 기존 정책 연결
  - AmazonECS FullAccess
  - AmazonECS2ContainerRegistryFullAccess

##### Task와 Service의 차이

- Task
  - 하나의 작업
- Service
  - 여러 개의 Task를 관리
  - 다양한 설정을 할 수 있음 (ELB / Auto Scaling)
