## 🚀깃허브 액션을 활용한 CI/CD🚀
<br>

  ### 📋 프로젝트 개요

  - 목표: GitHub Actions를 사용한 CI/CD 파이프라인 구축
  - 프로젝트: HTML/CSS 정적 웹사이트
  - 배포 환경: AWS S3 버킷

  ### ⚙️ CI 워크플로우 (코드 품질 검사)

  📄 파일: .github/workflows/ci.yml

  - 도구: Super-Linter v6
  - 트리거: main, deploy 브랜치 push & main으로의 PR
  - 검사 항목: HTML, CSS 외 다양한 코드 품질 검사
  - 보안: 최소 권한 원칙 적용
  - 성능 최적화: 변경된 파일만 검사

  ### 🔧 주요 설정

  VALIDATE_ALL_CODEBASE: false  # 성능 최적화
  VALIDATE_CSS: false          # CSS 린터 비활성화
  DISABLE_STATUS_API: true     # 권한 최소화

  ### 🚀 CD 워크플로우 (자동 배포)

  📄 파일: .github/workflows/cd.yml

  - 배포 대상: AWS S3 버킷 (ta2025-cicd-testuser)
  - 트리거: CI 성공 후 자동 실행
  - 배포 파일: HTML, CSS만 선별 업로드
  - 기능: 정적 웹사이트 호스팅 자동 설정

  ### 🔑 AWS 설정

  - IAM 사용자: S3 Access 권한
  - Secrets 설정:
    - AWS_ACCESS_KEY_ID
    - AWS_SECRET_ACCESS_KEY
  - S3 버킷: 퍼블릭 액세스 허용, 정적 웹사이트 호스팅 활성화


  ## ✅ 완성된 기능들

  1. 자동 코드 품질 검사: 푸시할 때마다 코드 린팅
  2. 자동 배포: CI 성공 시 S3에 자동 배포
  3. 배포 검증: 업로드된 파일 확인 및 웹사이트 상태 체크
  4. 보안 강화: 최소 권한 원칙, IAM 사용자 활용

  ### 🌐 최종 결과

  - 웹사이트 URL: http://ta2025-cicd-testuser.s3-website.ap-northeast-2.amazonaws.com
  - 배포 프로세스: 코드 푸시 → CI 검사 → 자동 배포 → 웹사이트 업데이트
