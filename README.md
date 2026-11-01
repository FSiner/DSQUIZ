# 수업 퀴즈

고등학교 교실용 실시간 퀴즈 · 판서 도구. 서버 없이 `index.html` 한 파일로 동작합니다.

- 선생님: 퀴즈 제작·분류 관리, 수업 중 정답/해설/힌트 공개, 판서, 학생 응답 실시간 확인
- 학생: 이름 입력 → 퀴즈 풀이 → 자동 결과 화면 → 오답 복습·오답만 재풀이
- 판서(선생님 화면 전용): 볼펜·만년필·형광펜, 획/부분 지우개, 올가미, 도형 자동 보정, 종이 서식, PNG·PDF 저장
- 키보드: `1~4` 보기 강조, `Space` 정답·해설 공개, `←` `→` 문제 이동

## 파일 구성

| 파일 | 용도 |
|---|---|
| `index.html` | 앱 전체 (이 파일만 있으면 됩니다) |
| `database.rules.json` | Firebase Realtime Database 보안 규칙 |
| `firebase.json` | Firebase Hosting / 규칙 배포 설정 (선택) |
| `netlify.toml` | Netlify 배포 설정 (선택) |
| `.github/workflows/pages.yml` | GitHub Pages 자동 배포 (선택) |
| `docs/DEPLOY.md` | 배포 단계별 안내 |
| `docs/FIREBASE.md` | Firebase 연결 안내 |
| `docs/CHECKLIST.md` | 수업 전 점검표 |

## 빠른 시작

1. 이 폴더를 GitHub 저장소에 올리거나 Netlify에 끌어다 놓습니다. → [docs/DEPLOY.md](docs/DEPLOY.md)
2. 배포된 주소에서 선생님으로 입장합니다. 기본 비밀번호는 `1234`이며 **바로 변경**하세요. 설정 화면에서 바꿉니다.
3. 여러 기기를 쓰려면 Firebase를 연결합니다. → [docs/FIREBASE.md](docs/FIREBASE.md)

## 데이터 보관

- Firebase 미연결: 같은 브라우저 안에서만 저장됩니다(`localStorage`). 학생 기기와 공유되지 않습니다.
- 퀴즈는 정기적으로 **내보내기(JSON)** 로 백업하세요.

## 주의

- 선생님 비밀번호는 브라우저에서 확인하는 방식입니다. 시험처럼 보안이 중요한 용도에는 맞지 않습니다.
- Firebase 설정 값은 웹 앱에서 공개되는 값이지만, **보안 규칙은 꼭 확인**하세요.
- 외부 서비스: Tailwind CDN, Firebase SDK(gstatic), QR 라이브러리. 학교 망에서 막히면 동작하지 않을 수 있습니다.

## 라이선스

MIT
