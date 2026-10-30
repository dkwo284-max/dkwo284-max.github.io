# My Hub

https://dkwo284-max.github.io/ — 나의 앱 모음 입구.

- 앱 추가: `index.html` 의 `APPS` 에 한 줄 (이름·아이콘·주소·설명·업데이트 시각을 읽을 데이터 파일)
- 각 앱은 자기 저장소(예: News_Summary, Whale_Radar)에서 따로 배포되고, 이 페이지는 링크와 상태만 보여줍니다.
- 이 저장소 이름이 `dkwo284-max.github.io` 여야 루트 주소로 열립니다. Settings → Pages → Source: Deploy from a branch → main / (root).

## 공용 AI 예산 (budget.json)

세 앱(Daily Brief · 웨일 레이더 · 로봇 레이더)이 같은 Gemini 키의 하루 몫을 나눠 씁니다.

- `budget.json` 의 `apps.*.guaranteed` = 앱별 보장량(다른 앱이 못 뺏음), `reserve` = 공유 예비분, `total` = 합계(보장량 합 + 예비분).
- **하루 = 오클랜드(Pacific/Auckland) 00시 리셋.**
- 각 앱은 실행 전에 이 파일과 다른 앱의 `ai-usage.json` 을 읽어 "내 남은 보장량 + 남은 예비분"만큼만 Gemini 를 호출합니다(`scripts/budget.py`, 세 저장소에 같은 파일).
  이 파일이나 다른 앱 기록을 읽지 못하면 안전하게 내 보장량만 씁니다.
- 숫자를 바꾸면 다음 실행부터 모든 앱에 적용됩니다. 합계가 맞는지 확인하세요: `total == reserve + Σ guaranteed`.
- 현재 배분: Daily Brief 7 · 웨일 레이더 3 · 로봇 레이더 3 · 예비 3 = 16회/일.
