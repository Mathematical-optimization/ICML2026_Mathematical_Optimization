# ICML 2026 Mathematical Optimization Meetup — Website Source

ICML 2026 참가자 중 **수학적 최적화(Mathematical Optimization) 연구에 관심 있는 사람들**을 위한 오프라인 티타임 및 저녁 모임용 정적 웹페이지입니다.

## 확정 반영된 행사 정보

- 대상: 수학적 최적화 연구에 관심 있는 ICML 2026 참가자
- 시작: 2026년 7월 7일(화) 16:00 KST
- 티타임: 카페 언더라인
- 진행: 인사, 아이스브레이킹 및 친목 중심의 티타임 후 저녁 식사
- 저녁 대화: AI 연구와 관련된 다양한 주제
- 참여 비용: 1인 15,000원
- 최종 안내: 7월 6일 참석 확정자에게 세부 집결 위치, 시간 안내 및 식사 장소 전달

종료 시각은 제공된 정보에 없으므로 화면에 임의로 표시하지 않았고, 생성되는 `.ics` 파일에도 `DTEND`를 넣지 않았습니다. 종료 시각이 확정되면 `event-config.js`의 `endISO`를 설정하면 됩니다.

## 주요 기능

- 외부 프레임워크·폰트·이미지 의존성 없음
- 반응형 데스크톱/모바일 레이아웃
- 한국어 기본 표시 및 영어 전환
- `.ics` 캘린더 파일 생성
- 접근성 기본 요소와 `prefers-reduced-motion` 대응
- ICML 공식 행사로 오인되지 않도록 독립 행사 고지 포함

## 1. 가장 먼저 수정할 파일

`event-config.js`에서 신청 링크와 주최자 이메일을 실제 값으로 교체하세요.

```js
window.EVENT_CONFIG = Object.freeze({
  startISO: "2026-07-07T16:00:00+09:00",
  endISO: "", // 종료 시각 확정 후 예: "2026-07-07T20:30:00+09:00"
  rsvpUrl: "https://forms.gle/여기에-신청폼-주소",
  organizerEmail: "organizer@your-domain.org"
});
```

식당이나 세부 집결 위치가 확정되면 다음 항목도 갱신하세요.

- `locationLabel`
- `coffeeVenue`
- `dinnerVenue`
- `calendarLocation`
- `calendarDescription`

## 2. 로컬 실행

파일을 직접 열어도 동작하지만, 브라우저 보안 정책 차이를 피하려면 간단한 로컬 서버를 권장합니다.

```bash
cd icml2026-optimization-meetup
python3 -m http.server 8080
```

브라우저에서 `http://localhost:8080`을 엽니다.

## 3. 배포

정적 파일이므로 다음 서비스에 그대로 배포할 수 있습니다.

- GitHub Pages
- Netlify
- Vercel
- Cloudflare Pages
- 사내 정적 호스팅 또는 S3

루트 디렉터리에 `index.html`이 오도록 업로드하면 됩니다.

## 4. 파일별 역할

- 본문 및 문구: `index.html`
- 색상·레이아웃: `styles.css`
- 언어 전환·카운트다운·캘린더: `script.js`
- 행사별 설정: `event-config.js`

## 5. 배포 전 체크리스트

- `rsvpUrl`에 실제 참가 신청 링크 입력
- `organizerEmail`에 실제 문의 이메일 입력
- 7월 6일 최종 안내 후 식당명과 세부 장소 반영
- 종료 시각 확정 시 `endISO` 입력
- 신청 폼에 참여 비용 15,000원과 안내 일정을 명확히 표기
- 행사 종료 후 카운트다운 및 신청 버튼 정리
