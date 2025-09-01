AccessToken과 RefreshToken
==

AccessToken
--
- 짧은 만료 시간(예: 30분)으로 발급됨

- 클라이언트(브라우저, 앱 등)가 서버에 요청을 보낼 때 Authorization 헤더에 담아 인증에 사용

- 서버는 매번 AccessToken을 검증하여 사용자가 누구인지, 권한이 있는지를 확인

RefreshToken
--
- 긴 만료 시간(예: 7일, 2주 등)으로 발급

- AccessToken이 만료되었을 때, 새 AccessToken을 발급받을 수 있는 재발급용 토큰

- 클라이언트는 AccessToken이 만료되면 RefreshToken을 가지고 /auth/refresh 같은 엔드포인트에 요청 → 서버에서 검증 후 새로운 AccessToken 발급

RefreshToken만 DB에 저장하는 이유
--
1. AccessToken은 짧게 쓰고 금방 만료되므로 서버에서 굳이 저장할 필요가 없음
2. RefreshToken은 재발급 관리가 필요하기 때문에 DB에 저장
    - DB의 RefreshToken과 클라이언트의 RefreshToken을 비교 검증하여 새로운 AccessToken을 발급

클라이언트 측에서의 AccessToken과 RefreshToken 관리
--
accessToken, refreshToken을 클라이언트에서 HttpOnly 쿠키 같은 곳에 넣어 저장하며 관리한다.

그 후 서버에서 요청 시 Authorization: Bearer &lt;accessToken&gt; 헤더에 넣어 보내주는 것

accessToken이 만료되면 refreshToken을 Authorization: Bearer &lt;accessToken&gt; 헤더에 넣어 보내준다.

accessToken의 만료 판단은 요청 보낼 때 그냥 Authorization 헤더에 accessToken 넣고 보내고, 만료됐다면 서버가 401 Unauthorized 반환 → 클라이언트가 RefreshToken 써서 새 AccessToken 발급하는 방식이 많이 쓰인다.