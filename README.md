# ICML 2026 Mathematical Optimization Meetup — Website Source

ICML 2026 기간 중 서울 COEX 인근에서 진행하는 **수학적 최적화 연구자 커피챗 + 저녁 식사**용 정적 웹페이지입니다.

- 외부 프레임워크·폰트·이미지 의존성 없음
- 반응형 데스크톱/모바일 레이아웃
- 영어/한국어 전환
- `.ics` 캘린더 파일 생성
- 접근성 기본 요소와 `prefers-reduced-motion` 대응
- ICML 공식 행사로 오인되지 않도록 독립 행사 고지 포함

## 1. 가장 먼저 수정할 파일

`event-config.js`만 열어 아래 항목을 바꾸면 됩니다.

```js
window.EVENT_CONFIG = Object.freeze({
  startISO: "2026-07-10T18:00:00+09:00",
  endISO: "2026-07-10T21:30:00+09:00",
  rsvpUrl: "https://forms.gle/여기에-신청폼-주소",
  organizerEmail: "organizer@your-domain.org"
});
```

특히 다음 네 항목을 실제 정보로 교체하세요.

1. `startISO`, `endISO`: 실제 시작·종료 시각
2. `dateLabel`: 화면에 표시할 날짜 문구(영문/국문)
3. `rsvpUrl`: Google Forms, Tally, Luma, Partiful 등의 신청 링크
4. `organizerEmail`: 문의 이메일

카페와 식당이 확정되면 `coffeeVenue`, `dinnerVenue`, `locationLabel`, `mapUrl`도 수정하세요.

## 2. 로컬 실행

파일을 직접 열어도 동작하지만, 브라우저 보안 정책 차이를 피하려면 간단한 로컬 서버를 권장합니다.

```bash
cd icml2026-optimization-meetup
python3 -m http.server 8080
```

그다음 브라우저에서 `http://localhost:8080`을 엽니다.

## 3. 배포

정적 파일이므로 다음 서비스에 그대로 배포할 수 있습니다.

- GitHub Pages
- Netlify
- Vercel
- Cloudflare Pages
- 사내 정적 호스팅/S3

루트 디렉터리에 `index.html`이 오도록 업로드하면 됩니다.

## 4. 문구·디자인 수정

- 본문: `index.html`
- 색상·레이아웃: `styles.css` 상단의 CSS 변수
- 언어 전환·카운트다운·캘린더: `script.js`
- 행사 정보: `event-config.js`

주요 색상:

```css
--bg: #08110f;
--accent: #b7f34a;
--accent-2: #5ce1c6;
--paper: #f1f4ec;
```

## 5. 운영 체크리스트

- 신청 폼에 연구 키워드, 논의하고 싶은 질문, 식이 요구사항을 포함
- 실제 일정 확정 후 `dateStatus`를 “Confirmed / 확정”으로 변경
- 확정 참가자에게 카페·식당 상세 주소 발송
- 신청 마감 시 `rsvpUrl`을 대기 명단 폼으로 교체
- 행사 종료 후 카운트다운 및 참가 신청 버튼 정리

## 참고

페이지에 기재된 2026년 7월 10일 일정은 예시용 임시 일정입니다. 공개된 ICML 공식 소셜 시간대(7월 6·8·9일 저녁)와의 직접 충돌을 피하도록 잡았지만, 최신 컨퍼런스 플래너를 확인한 뒤 최종 확정하세요.
