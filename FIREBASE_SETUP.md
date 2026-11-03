# 두 휴대폰 연동 설정 (시연용)

GitHub Pages는 정적 파일만 배포합니다. 신청·승인 내역을 두 휴대폰에서 공유하려면 Firebase Realtime Database가 필요합니다.

1. [Firebase Console](https://console.firebase.google.com/)에서 프로젝트를 만들고 웹 앱을 추가합니다.
2. **Authentication → Sign-in method**에서 **이메일/비밀번호**를 사용 설정합니다. **Users**에서 앱의 교사 1명과 학생 4명의 이메일을 추가하고, 비밀번호를 모두 `1234567!`로 지정합니다. (앱의 이메일 목록은 `index.html`의 `demoAccounts`를 참고하세요.)
3. **Realtime Database**를 만들고 데이터베이스 URL을 확인합니다. 공개 테스트 모드 대신 아래 규칙을 붙여 넣습니다.
4. Firebase의 웹 앱 설정 값(`apiKey`, `authDomain`, `databaseURL`, `projectId`, `appId`)을 `firebase-config.js`의 `null` 대신 객체로 입력합니다. 예: `window.DADAE_FIREBASE_CONFIG = { apiKey: '...', authDomain: '...', databaseURL: '...', projectId: '...', appId: '...' };`
5. 수정한 파일을 GitHub 저장소의 `main` 브랜치에 올린 뒤, Pages 배포가 끝나면 두 휴대폰에서 같은 주소를 새로고침합니다. 각 폰에서 학생/교사 계정으로 로그인하세요.

시연용 Realtime Database 규칙:

```json
{
  "rules": {
    "demoState": {
      ".read": "auth != null && (auth.token.email == 'hangidong.te@dadae.hs.kr' || auth.token.email == 'parknabin.st@dadae.hs.kr' || auth.token.email == 'seoyeona.st@dadae.hs.kr' || auth.token.email == 'jeonggiyeong.st@dadae.hs.kr' || auth.token.email == 'josoyeong.st@dadae.hs.kr')",
      ".write": "auth != null && (auth.token.email == 'hangidong.te@dadae.hs.kr' || auth.token.email == 'parknabin.st@dadae.hs.kr' || auth.token.email == 'seoyeona.st@dadae.hs.kr' || auth.token.email == 'jeonggiyeong.st@dadae.hs.kr' || auth.token.email == 'josoyeong.st@dadae.hs.kr')"
    }
  }
}
```

이 규칙은 시연용입니다. 다섯 계정 모두 하나의 공유 데이터에 쓸 수 있어, 실제 학생 개인정보나 실서비스에 사용하면 안 됩니다. 활동 사진도 같은 데이터베이스에 저장됩니다. 실제 서비스는 서버 측 권한 분리, 안전한 파일 저장소, 사진 보관·삭제 정책이 필요합니다.
