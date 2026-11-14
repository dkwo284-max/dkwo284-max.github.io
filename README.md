# My Hub

https://dkwo284-max.github.io/ — 나의 앱 모음 입구.

- 앱 추가: `index.html` 의 `APPS` 에 한 줄 (이름·아이콘·주소·설명·업데이트 시각을 읽을 데이터 파일)
- 각 앱은 자기 저장소(예: News_Summary, Whale_Radar)에서 따로 배포되고, 이 페이지는 링크와 상태만 보여줍니다.
- 이 저장소 이름이 `dkwo284-max.github.io` 여야 루트 주소로 열립니다. Settings → Pages → Source: Deploy from a branch → main / (root).

## 앱별 AI 한도 (budget.json)

세 앱(Daily Brief · 웨일 레이더 · 로봇 레이더)은 각자 자기 Google 프로젝트의 Gemini 키를 씁니다(2026-11-14부터). 한도도 앱별로 따로이고 공유 예비분은 없습니다.

- `budget.json` 의 `apps.*.guaranteed` = 그 앱의 하루 한도, `reserve` = 0, `total` = 한도 합계.
- **하루 = 오클랜드(Pacific/Auckland) 00시 리셋.**
- 각 앱은 실행 전에 이 파일을 읽어 "내 남은 한도"만큼만 Gemini 를 호출합니다(`scripts/budget.py`, 세 저장소에 같은 파일). 이 파일을 읽지 못하면 각 저장소 설정의 안전값을 씁니다.
- 숫자를 바꾸면 다음 실행부터 적용됩니다. 합계 확인: `total == reserve + Σ guaranteed`.
- 현재 한도: Daily Brief 12 · 웨일 레이더 6 · 로봇 레이더 6 = 24회/일. (무료 등급 Flash 는 프로젝트당 하루 20회라 그 아래로 둡니다.)
