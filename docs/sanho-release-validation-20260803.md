# Sanho release validation 2026-08-03

이 문서는 Sanho release candidate `588d5e4`의 실제 세 저장소 양방향 동기화와
애플리케이션 main 선행 게시를 검증하기 위해 추가했다.

- 실행 환경: 격리 `sanhod`, 격리 server/client/docs clone
- 검증 범위: docs push/pull, dirty layer 보존, main publication, alias 및 직접 URL 차단
- 검증 방식: fast-forward only, force push 없음
- 역방향 검증: sanho-client에서 canonical docs로 정상 게시
