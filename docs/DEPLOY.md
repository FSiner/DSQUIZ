# 배포 안내

GitHub만 가능한 것이 아닙니다. 정적 파일을 HTTPS로 제공하는 곳이면 어디든 됩니다. 아래 세 가지 중 하나를 고르세요.

| 방법 | 난이도 | 특징 |
|---|---|---|
| A. Netlify Drop | 가장 쉬움 | 폴더를 끌어다 놓으면 끝. 계정만 있으면 됨 |
| B. GitHub Pages | 쉬움 | 수정·이력 관리가 편함. 저장소가 공개일 수 있음 |
| C. Firebase Hosting | 보통 | Firebase를 이미 쓴다면 호스팅·규칙을 한곳에서 관리 |

## A. Netlify Drop
1. 이 폴더(또는 `index.html`만 담은 폴더)를 준비합니다. 파일 이름은 `index.html` 이어야 합니다.
2. netlify.com 에 로그인 후 사이트 추가 → 폴더를 끌어다 놓습니다(Drop).
3. 나온 `https://○○.netlify.app` 주소를 확인하고, Site settings → Change site name 에서 이름을 바꿉니다.
4. 수정할 때는 같은 사이트의 Deploys 탭에 폴더를 다시 끌어다 놓습니다.

## B. GitHub Pages

### 방법 1: 설정만으로 (가장 간단)
1. GitHub에서 새 저장소를 만듭니다. 이 폴더의 파일을 모두 올립니다(Add file → Upload files).
2. Settings → Pages → Build and deployment → Source: **Deploy from a branch**, Branch: `main`, Folder: `/ (root)` → Save.
3. 1~2분 뒤 `https://계정명.github.io/저장소명/` 에서 열립니다.

### 방법 2: 자동 배포(Actions)
1. 저장소 Settings → Pages → Source 를 **GitHub Actions** 로 선택합니다.
2. `main` 에 push 하면 `.github/workflows/pages.yml` 이 자동 배포합니다. Actions 탭에서 진행 상황을 봅니다.

### 터미널로 올리기
```bash
git init
git add .
git commit -m "수업 퀴즈 첫 배포"
git branch -M main
git remote add origin https://github.com/계정명/저장소명.git
git push -u origin main
```

> 무료 계정에서 Pages는 저장소가 공개(Public)여야 할 수 있습니다. 공개 저장소에는 개인정보나 비밀번호를 넣지 마세요. 퀴즈 데이터는 저장소에 들어 있지 않고 각자의 브라우저와 Firebase에 있습니다.

## C. Firebase Hosting
```bash
npm i -g firebase-tools
firebase login
firebase init        # Hosting 과 Database 선택, 기존 database.rules.json / firebase.json 은 덮어쓰지 않음
firebase deploy
```
`firebase.json` 은 이미 이 폴더 기준으로 작성되어 있습니다. 호스팅과 규칙이 함께 배포됩니다.

## 배포 후 확인
1. 주소에 접속 → 선생님 입장 → 비밀번호 변경
2. (선택) Firebase 연결 → [FIREBASE.md](FIREBASE.md)
3. 예시 퀴즈 공개 → 폰에서 학생으로 접속
4. QR 버튼으로 학생 입장 화면 열기
5. [CHECKLIST.md](CHECKLIST.md) 로 점검
