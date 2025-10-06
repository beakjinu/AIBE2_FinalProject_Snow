## 브랜치 전략

우리의 브랜치 전략입니다.

### 메인 브랜치
- **`main`** - 프로덕션 배포용
- **`develop`** - 개발 통합 브랜치

### 작업 브랜치

모든 새로운 작업은 `develop`에서 브랜치를 만들어 시작합니다.

## 브랜치 네이밍 규칙

작업 브랜치는 반드시 아래 형식을 따라야 합니다:

### 형식
```
<타입>/<간단한-설명>
```

### 타입 종류

| 타입 | 용도 | 예시 |
|------|------|------|
| `feature/` | 새로운 기능 개발 | `feature/user-login` |
| `fix/` | 버그 수정 | `fix/navbar-responsive` |
| `hotfix/` | 긴급 수정 (main에서 분기) | `hotfix/payment-error` |
| `refactor/` | 코드 리팩토링 | `refactor/api-structure` |
| `docs/` | 문서 작업 | `docs/update-readme` |
| `test/` | 테스트 코드 추가 | `test/login-validation` |

### 네이밍 규칙
- 소문자 사용
- 단어 구분은 하이픈(`-`) 사용
- 간결하고 명확하게 작성
- 영어 사용 권장

## 작업 플로우

### 1. 새 작업 시작
```bash
# develop 최신 상태로 업데이트
git checkout develop
git pull origin develop

# 새 작업 브랜치 생성
git checkout -b feature/새기능명
```

### 2. 작업 및 커밋
```bash
# 작업 후 스테이징
git add .

# 의미있는 커밋 메시지 작성
git commit -m "feat: 사용자 로그인 기능 추가"
```

### 3. GitHub에 푸시
```bash
git push -u origin feature/새기능명
```

### 4. Pull Request 생성
1. GitHub 저장소로 이동
2. "Compare & pull request" 버튼 클릭
3. **Base:** `develop` / **Compare:** `feature/새기능명`
4. PR 제목과 설명 작성
5. 팀원에게 리뷰 요청

### 5. 코드 리뷰 및 병합
- 최소 1명의 승인 필요
- 리뷰어의 피드백 반영
- 승인 후 "Squash and merge" 클릭

### 6. 브랜치 정리
```bash
# 병합 후 로컬 브랜치 삭제
git checkout develop
git pull origin develop
git branch -d feature/새기능명
```

## 커밋 메시지 규칙

### 형식
```
<타입>: <제목>

<본문> (선택사항)
```

### 타입
- `feat`: 새로운 기능
- `fix`: 버그 수정
- `docs`: 문서 수정
- `style`: 코드 포맷팅 (기능 변경 없음)
- `refactor`: 코드 리팩토링
- `test`: 테스트 코드
- `chore`: 빌드, 설정 파일 수정

### 예시
```
feat: 사용자 회원가입 API 구현

- 이메일 유효성 검증 추가
- 비밀번호 암호화 처리
- 중복 가입 방지 로직 구현
```

## 배포 프로세스

### develop → main 병합 (배포)
```bash
# 로컬에서
git checkout main
git pull origin main
git merge develop
git push origin main

# 또는 GitHub에서 PR 생성
develop → main Pull Request 생성
```

## 주의사항

⚠️ **develop 브랜치에 직접 푸시 금지!**
- 모든 변경사항은 Pull Request를 통해서만 병합됩니다.
- 브랜치 보호 규칙이 설정되어 있습니다.

⚠️ **main 브랜치는 배포용**
- 검증된 코드만 병합
- 긴급 수정을 제외하고 develop을 거쳐서만 병합

## 질문이나 문제가 있다면?

- 팀원과 논의
- Issue 생성
- Pull Request에 코멘트

---

**Happy Coding! 🚀**