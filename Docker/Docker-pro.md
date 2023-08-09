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
  - docker images [OPTIONS]REPOSITORY[:TAG]]
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
