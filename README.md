# Spring Boot Multi Module Template

이 프로젝트는 **Spring Boot** 기반 멀티 모듈 프로젝트를 구성하고, 모듈 간 의존성을 체계적으로 관리하는 방법을 다룹니다.  
**코드 재사용성**과 **유지보수성**을 높이고, 확장 가능한 프로젝트 구조를 제공합니다.

---

## 개요

- **멀티 모듈(Multi Module)**:  
  하나의 프로젝트를 **기능별** 또는 **관심사별**로 나누어 관리하여 코드 중복을 줄이고 협업을 효율적으로 개선.
- **적용 효과**:  
  - 코드 재사용성 증가  
  - 유지보수성 향상  
  - MSA 확장 용이

---

## 기술 스펙

- **프레임워크**: Spring Boot 3.4.1
- **Java 버전**: Java 17
- **빌드 도구**: Gradle (Groovy DSL)
- **프로젝트 구조**: Multi Module

---

## 모듈 디렉토리 구조

```plaintext
spring-multi-module-example/
├── module-common/            # 공통 유틸, 상수, DTO 등
├── module-api/               # API 요청 처리, Controller & Service
├── module-storage/           # 외부 저장소(JPA 등) 관련 로직
│   ├── db-jpa/               # JPA 관련 하위 모듈
├── module-infra/             # 외부 서비스(S3, MQ 등) 관련 로직
│   ├── s3/                   # S3 연동 하위 모듈
└── build.gradle
```
- **module-common**
  - 역할
    - 공통적으로 사용되는 유틸리티 클래스, 공통 상수, 예외 처리, DTO
    - 모든 모듈에서 참조 가능
  - example
    - 공통 Response 개체 (ApiResponse 클래스)
    - Custom Exception 클래스 (BizException 클래스)
    - Logging 및 Validation 관련 유틸리티
- **module-api**
  - 역할
    - API 요청을 처리하고, Controller 및 Service 계층을 포함
    - 주로 클라이언트와 직접적으로 소통하는 역할
  - example
    - Rest API Controller
    - API 요청/응답을 위한 DTO
    - Service 계층과의 인터페이스
- **module-storage**
  - 역할
    - 외부 시스템과의 통합 및 인프라 관련 로직을 관리
    - 파일 스토리지, 메시지 큐, 외부 API 호출 등 기술적인 구현 세부 사항 포함
  - example
    - AWS S3 또는 Azure Blob과 같은 스토리지 연동 코드
    - Kafka, RabbitMQ등의 메시지 브로커 설정
    - 외부 API 통신 (예: HTTP Client)

## 상세 설명 블로그
- <https://devk-jung.github.io/posts/multiModule-1/>

