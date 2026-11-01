# Firebase 연결 (여러 기기 실시간 동기화)

연결하지 않으면 데이터가 한 브라우저 안에만 저장되어 학생 기기와 공유되지 않습니다.

## 1. 프로젝트와 데이터베이스 만들기
1. console.firebase.google.com → 프로젝트 추가
2. 빌드 → **Realtime Database** → 데이터베이스 만들기 (위치는 가까운 곳, 예: 싱가포르)
3. 처음에는 "잠금 모드"로 시작해도 됩니다. 다음 단계에서 규칙을 바꿉니다.

## 2. 보안 규칙 적용
Realtime Database → 규칙 탭에 `database.rules.json` 내용을 붙여 넣고 게시합니다.

이 앱이 쓰는 경로는 `quizzes`, `hints`, `students`, `responses` 네 가지뿐입니다. 규칙은 이 네 경로만 열고 나머지는 막습니다.

> 이 규칙은 인증 없이 읽고 쓰게 열어 둡니다(학생이 로그인 없이 참여하기 위해). 주소를 아는 사람이 데이터를 바꿀 수 있으니, 수업이 끝나면 `responses` 를 삭제하거나 필요할 때만 데이터베이스를 쓰세요. 더 강한 보호가 필요하면 Firebase 인증 도입이 필요합니다.

## 3. 웹 앱 설정 값 복사
1. 프로젝트 설정(톱니바퀴) → 일반 → 내 앱 → 웹 앱(`</>`) 추가
2. 나온 `firebaseConfig` 객체를 복사합니다. 반드시 `databaseURL` 이 들어 있어야 합니다.
   (없으면 Realtime Database 화면 상단의 주소 `https://○○-default-rtdb.○○.firebasedatabase.app` 를 추가)

## 4. 앱에 넣기
1. 배포된 주소에서 선생님으로 입장 → 설정 → Firebase 항목
2. 복사한 객체를 붙여 넣고 저장 (페이지가 다시 불러와집니다)
3. 학생 기기에서 접속해 응답이 선생님 화면에 실시간으로 올라오는지 확인합니다.

## 문제 해결
| 증상 | 확인할 것 |
|---|---|
| 학생 응답이 안 올라옴 | `databaseURL` 오타, 규칙 게시 여부 |
| `permission_denied` | 규칙이 네 경로를 열고 있는지 |
| 학교에서만 안 됨 | `firebaseio.com`, `firebasedatabase.app`, `gstatic.com` 차단 여부 |
