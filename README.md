# 📦 POS Common Module

`pos-common`은 POS(Order/Inventory) 마이크로서비스 프로젝트에서 공통적으로 사용하는  
DTO, 응답 포맷, 예외 처리 객체 등을 모아놓은 **공통 모듈 (Shared Library)** 입니다.

이 모듈은 다른 서비스(`pos-order-service`, `pos-inventory-service` 등)에서  
의존성으로 참조하여, 일관된 응답 구조 및 코드 중복 제거를 돕습니다.

---

## ✅ Features

- ✅ `ApiResponse<T>`: 표준 응답 래핑 객체
- ✅ `BaseException`: 공통 예외 핸들링 구조
- ✅ `ErrorResponse`: API 에러 포맷 통일
- ✅ `ResultCode`: 성공/실패 코드 관리
- ✅ Maven 로컬 배포 및 재사용 가능

---

## 🧱 Tech Stack

- Java 17
- Gradle 8.x
- Spring Boot 3.3 compatible
- Maven Publish Plugin

---

## 📁 구조

```
pos-common/
├── src/main/java/com/pos/common/
│   ├── dto/
│   │   └── ApiResponse.java
│   ├── exception/
│   │   ├── BaseException.java
│   │   └── ErrorResponse.java
│   └── code/
│       └── ResultCode.java
├── build.gradle
├── settings.gradle
└── README.md
```

---

## 🚀 사용 방법

### 1. Maven Local로 배포

```bash
./gradlew clean publishToMavenLocal
```

> 배포 후, `~/.m2/repository/com/pos/common/0.0.1-SNAPSHOT/` 경로에 JAR이 생성됩니다.

### 2. 다른 서비스에서 참조

예: `pos-order-service/build.gradle`

```groovy
repositories {
    mavenLocal()
    mavenCentral()
}

dependencies {
    implementation 'com.pos:common:0.0.1-SNAPSHOT'
}
```

---

## ✨ 클래스 예시

### `ApiResponse<T>`

```java
public class ApiResponse<T> {
    private T data;
    private String code;
}
```

### `BaseException`

```java
public class BaseException extends RuntimeException {
    private final String code;
}
```

---

## 🔜 향후 확장 예정

- 공통 Validation 유틸
- 국제화 메시지 지원
- 공통 로그 포맷 / 트레이싱

---

## 👤 Author

- **grshin**
- [GitHub](https://github.com/grshin)

---

## 📦 함께 쓰면 좋은 리포지토리

| 서비스                                                                   | 설명                          |
| ------------------------------------------------------------------------ | ----------------------------- |
| [pos-order-service](https://github.com/grshin/pos-order-service)         | 주문 처리 마이크로서비스      |
| [pos-inventory-service](https://github.com/grshin/pos-inventory-service) | 재고 처리 마이크로서비스      |
| [pos-api-gateway](https://github.com/grshin/pos-api-gateway)             | API 라우팅 및 통합 게이트웨이 |
