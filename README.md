# AI톡톡 (iux-aitalk) — 작업 안내서

## 한 줄 요약
책을 정해 AI와 독서 토론(대화)을 하는 앱. 사용자가 자기 AI API 키(Claude·OpenAI·Gemini)를 넣어서 쓴다.

## 주의: 이 저장소의 index.html은 "묶음(번들) 파일"
- `index.html`(약 8.8MB)은 화면 코드와 자원을 압축해 한 파일로 묶은 결과물(`<title>Bundled Page`)이다. 안의 코드는 gzip+base64로 들어 있어 **직접 고치기 어렵다.**
- 고치려면 원본 소스(아티팩트/프로젝트 파일)에서 수정한 뒤 다시 묶어서 올려야 한다. 원본 소스를 찾으면 `src/`로 이 저장소에 함께 올려 둘 것.

## 확정된 결정
| 항목 | 결정 |
|---|---|
| AI 키 | 사용자가 직접 입력, 브라우저(localStorage `aitoktok_creds`)에만 저장. 저장소·코드에 키를 넣지 않음 |
| 호출 | 브라우저에서 Anthropic / OpenAI / Gemini API로 직접 |
| 연관 | KoreaTalk(ktalk)과 같은 "AI 대화 + 학습" 계열 |

---

## 공통 작업 원칙 (IUX 프로젝트 전체)
- **언어:** 화면 문구·문서·커밋 메시지는 한국어. 쉬운 말, 기술 용어 최소화.
- **퍼블리싱 시안:** 순수 HTML/CSS + 간단한 스크립트만 넣는다. 서버·DB 연동 코드는 개발 단계에서 따로 붙인다.
- **아이콘:** Lucide. 디자인 시스템을 따로 정하지 않았으면 스포티파이 스타일(다크/화이트 + 포인트 컬러)을 기본으로 쓴다.
- **배포:** GitHub `main` → Vercel 자동 배포. 도메인은 가비아 `iux.kr`의 서브도메인(`*.iux.kr` CNAME → Vercel)을 쓴다.
- **DB:** Supabase 무료 플랜은 활성 프로젝트 2개까지라, 새 프로젝트를 만들지 말고 기존 `iux-cloud`(studio) 프로젝트에 테이블을 얹는 것을 먼저 검토한다.
- **비밀값:** 공개 저장소다. 서비스 키·AI 키·비밀번호는 절대 커밋하지 않는다. 키는 Vercel 환경 변수나 Supabase secrets에 둔다. Supabase anon(public) 키만 코드에 넣을 수 있다.
- **확인:** 고친 뒤에는 브라우저 콘솔 오류 0개, 모바일(390px)과 PC 화면을 눈으로 확인하고 나서 완료라고 한다.
- **브랜치:** `main`은 배포 중인 상태. 큰 작업이나 검증 전 작업은 브랜치(`wip/…`, `claude/…`)에 올리고, `main`을 강제 푸시(-f)로 덮어쓰지 않는다.
- **전체 프로젝트 목록:** https://github.com/handgoldking1234/iux-app/blob/main/docs/PROJECTS.md
