# WheelGo
개요 : '휠'은 바퀴를, '고'는 가다의 의미로, 자전거와 킥보드를 대여할 수 있는 시스템

# WheelGo 서버 구조도

![image](https://github.com/user-attachments/assets/292408d5-1298-4b90-985a-a101ef284ec9)


# 개발 환경:

언어: Java
백엔드 프레임워크: Spring Boot
프론트엔드 프레임워크: Vue
데이터베이스: MariaDB (MySQL 대신)
서버: Google Cloud Platform (GCP)


# 개발 워크플로우:

1. 개발자가 코드를 작성하고 GitHub에 푸시합니다.
  GitHub 웹훅이 Jenkins에 변경 사항을 알립니다.


2. CI/CD 파이프라인 (Jenkins):
  Jenkins가 코드를 가져와 테스트하고 빌드합니다.
  빌드 성공 시 Docker 이미지를 생성합니다.
  SSH를 통해 GCP 서버에 접속하여 Docker 컨테이너를 배포합니다.

3. 서버 구성:
  GCP에 여러 개의 가상 머신(VM)을 생성하여 Docker 컨테이너를 실행합니다.
  각 VM에는 Spring Boot 애플리케이션이 Docker 컨테이너로 실행됩니다.


4. 로드 밸런싱:
  NGINX를 사용하여 여러 Spring Boot 애플리케이션 인스턴스 간 로드 밸런싱을 수행합니다.


5. 데이터베이스:
  MariaDB를 주 데이터베이스로 사용하며, 필요시 복제 구성을 할 수 있습니다.


6. 캐싱 및 세션 관리:
  
  Redis를 사용하여 세션 서버와 캐시 서버로 활용할 수 있습니다.


7. 보안:
  HashiCorp Vault를 사용하여 비밀번호, 토큰 등 중요 정보를 안전하게 관리합니다.


8. 사용자 접근:
  사용자는 NGINX를 통해 애플리케이션에 접근합니다.
