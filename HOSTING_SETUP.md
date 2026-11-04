# 2ryeon이 보이지 않는 앱 주소 만들기

이 저장소는 Firebase Hosting의 `dadaeon` 사이트에 바로 배포할 수 있도록 `firebase.json`과 `.firebaserc`가 준비되어 있습니다. 배포 후 주소는 `https://dadaeon.web.app/`입니다. 실제 배포 전에는 열리지 않습니다.

Windows 컴퓨터에서 한 번 배포하는 순서:

1. [Node.js LTS](https://nodejs.org/)를 설치합니다.
2. [GitHub 저장소](https://github.com/2ryeon/dadaeon-app)에서 **Code → Download ZIP**을 눌러 내려받고, ZIP을 압축 해제합니다.
3. 압축을 푼 `dadaeon-app-main` 폴더를 열고, 파일 탐색기 주소창에 `powershell`을 입력한 다음 Enter를 누릅니다.
4. 열린 창에서 `npx firebase-tools login`을 실행합니다. Firebase 프로젝트를 만든 Google 계정으로 로그인합니다.
5. 같은 창에서 `npx firebase-tools deploy --only hosting --project dadaeon-demo-2728f`를 실행합니다.
6. 끝에 표시되는 Hosting URL(`https://dadaeon.web.app/`)을 열어 앱 로그인과 실시간 알림을 시험합니다. 확인 후 새 주소로 QR 코드를 다시 만듭니다.

프로젝트 파일을 나중에 수정하면 다시 내려받아 3~5단계를 반복해야 Firebase Hosting에도 반영됩니다. 기존 GitHub Pages 주소는 별도로 남아 있습니다. 관리자 계정 비밀번호나 Firebase 서비스 계정 비공개 키를 채팅이나 저장소에 올리지 마세요.
