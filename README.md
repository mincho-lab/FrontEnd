# 🧭 Git & Coding Convention Guide

팀 프로젝트에서 **일관성 있는 협업**을 위해 아래 규칙을 따릅니다.

---

## 🌱 Branch 규칙

### 1️⃣ 브랜치 이름 규칙

> 형식
> 

```
요구사항ID-기능대제목

```

- 요구사항 ID를 반드시 포함합니다.
- 기능의 핵심이 드러나도록 간결하게 작성합니다.

📌 **예시**

```
SEC_64_로그인

```

---

### 2️⃣ 브랜치 워크플로우 (Fork 방식)

- 기본 브랜치: `main`
- 개인 작업은 Fork 후 진행합니다.

📖 **참고 자료**

- https://poalim.tistory.com/46

---

## 🔀 Pull Request(PR) 규칙

### 📄 PR 템플릿

```markdown
## 📄 PR 한 줄 요약
PR 내용을 한 문장으로 요약해주세요.

## 🧑‍💻 PR 세부 내용
- 수정/추가한 내용을 상세히 작성해주세요.

## 📎 Issue 번호
<!-- closed #이슈번호 -->

```

- PR 제목만 보고도 **무엇을 했는지 알 수 있게** 작성합니다.
- Issue 연동은 필수입니다.

---

## 📝 Commit Convention

### 📌 커밋 타입(Type)

| Type | 사용 시점 |
| --- | --- |
| CREATE | 프로젝트 초기 세팅 |
| Add | 새로운 파일 추가 |
| Delete | 파일 삭제 |
| Feat | 새로운 기능 추가 / 기능 수정 |
| Fix | 버그 수정 |
| Build | 빌드 관련 설정 수정 |
| Chore | 기타 설정 수정 (.gitignore 등) |
| Docs | 문서 및 주석 수정 |
| Style | 코드 스타일 / 포맷 수정 |
| Refactor | 기능 변경 없는 리팩토링 |
| Test | 테스트 코드 추가/수정 |
| Release | 버전 릴리즈 |
| Rename | 파일/폴더 이름 변경 |
| Readme | README 수정 |
| Comment | 주석 관련 작업 |

---

### ✏️ 커밋 메시지 규칙

### 📐 기본 형식

```
Type: 요구사항ID 대제목

- 상세 설명 1
- 상세 설명 2
- 상세 설명 3

```

> 💡 설명은 반드시 줄바꿈하여 상세히 작성합니다.
> 

---

### ✅ 커밋 메시지 예시

```bash
git commit -m "Feat: SEC_64 실시간 데이터 반영" -m "- MongoDB 연결 완료
- 잔고 조회 시 실시간 시세 반영
- 주식 과거 데이터 저장 및 API 구축
- KIS WebSocket 연결 로직 개선"

```

- 커밋 제목은 **간결**
- 본문은 **왜 / 무엇을 / 어떻게** 했는지 중심으로 작성

---

## 🧑‍💻 Code Convention

### 🔤 네이밍 규칙

- 대소문자를 **엄격히 구분**합니다.
- 변수명 / 함수명은 **lowerCamelCase**를 사용합니다.

```java
getReady()
colorOfCar

```

---

### 📦 변수 & 함수

- **변수명**: 명사 사용

```java
count, number, userName

```

- **함수명**: 동사 또는 동사구

```java
findCamera()
getUserInfo()

```

- **상수명**: 대문자 + 언더스코어

```java
MAX_COUNT
PI

```

- **이벤트 핸들러**: `on`으로 시작

```java
onClick()
onSubmit()

```

---

### 🧠 네이밍 원칙

- 축약어 사용 ❌
- **의미가 명확하게 드러나도록 작성 ⭕**

```java
// ❌
cnt, tmp

// ⭕
totalCount, temporaryValue

```

---

## 💬 주석 컨벤션 (Comment Convention)

### 1️⃣ 공통 원칙

- **Why 위주로 작성** (코드 설명 ❌, 의도 설명 ⭕)
- 주석은 **코드 상단에 작성**
- 불필요하거나 중복되는 주석 금지
- TODO / FIXME 명확히 구분

```java
// TODO: 예외 처리 고도화 필요
// FIXME: null 가능성 있음

```

---

### 2️⃣ Backend (Spring / Java)

### 📌 Javadoc 규칙

- `public class`, `public method` → **Javadoc 필수**
- 내부(private) 메서드는 필요 시 작성

```java
/**
 * 사용자 정보를 조회하는 서비스
 */
@Service
public class UserService {

    /**
     * 사용자 ID로 사용자 조회
     *
     * @param userId 사용자 ID
     * @return 사용자 엔티티
     */
    public User findById(Long userId) {
        return userRepository.findById(userId);
    }
}

```

---

### 📌 일반 주석 규칙

- 복잡한 로직, 비즈니스 규칙 설명 시 사용
- 한 줄 주석 `//` 우선 사용

```java
// 관리자만 접근 가능하도록 권한 검증
validateAdmin(user);

```

---

### 📌 금지 사항

```java
i++; // i 증가 ❌

```

---

### 3️⃣ Frontend (React)

### 📌 컴포넌트 주석

- 컴포넌트 역할을 상단에 간단히 명시

```jsx
// 사용자 프로필을 표시하는 컴포넌트
function UserProfile() {
  return <div />;
}

```

---

### 📌 함수 / 이벤트 핸들러 주석

- 비즈니스 로직, 상태 변경 의도만 설명

```jsx
// 로그인 성공 시 토큰 저장 및 메인 페이지 이동
const handleLogin = () => {
  saveToken();
  navigate('/');
};

```

---

### 📌 JSX 내부 주석

```jsx
{/* 에러 발생 시 안내 메시지 */}
{error && <ErrorMessage />}

```

---

### 📌 금지 사항

```jsx
setCount(count + 1); // count 증가 ❌

```

---

### 4️⃣ 주석 작성 기준 요약

| 구분 | 작성 대상 |
| --- | --- |
| Backend | public class / method |
| Frontend | 컴포넌트 역할, 핵심 로직 |
| 공통 | Why 설명, TODO / FIXME |

---
