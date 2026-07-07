---
name: wbl-design
description: |
  wbL(더블유비엘) 주얼리 브랜드의 디자인 시스템/스타일가이드를
  실제 결과물에 적용한다. 세이지 그린·아이보리·차콜 기반의
  에디토리얼 미니멀 톤, Figma "wbL Primitives / Semantic"을
  단일 원천으로 하는 토큰·컴포넌트·아이콘·카피 규칙을 담는다.
  다음 요청에 사용: "wbL 스타일로 만들어줘", "wbL 디자인 시스템 적용",
  "wbL 랜딩/상세페이지", "이거 wbL 톤으로 바꿔줘", "wbL 컴포넌트로",
  "wbL 색상·폰트 적용", "wbL 배너/이메일/카드 만들어줘".
  라이브 가이드: https://w-island.github.io/wbl-styleguide/
  NOT: 비브아(VIVOIR)나 다른 브랜드 작업, W-ISLAND 사내 툴 디자인.
argument-hint: "[만들거나 수정할 대상] (예: 상세페이지 히어로 섹션)"
allowed-tools: Read, Write, Edit, Bash, Glob, Grep
---

# wbL Design System 적용 스킬

wbL 브랜드의 화면/문서/그래픽에 디자인 시스템을 **일관되게** 입힌다.
라이브 가이드: **https://w-island.github.io/wbl-styleguide/**
원본 소스: `w-island/wbl-styleguide` 레포의 `index.html` (Figma "wbL Primitives / Semantic"이 단일 원천)

## 핵심 원칙 (먼저 읽기)

1. **HEX 직접 쓰지 말 것.** 항상 토큰(CSS 변수)으로 운용한다. 색을 바꿔야 하면 토큰 값을 바꾼다.
2. **에디토리얼 미니멀** — 여백을 넉넉히, 요소는 적게. 주얼리 브랜드답게 콘텐츠가 숨 쉬게 둔다.
3. **한 화면 = 하나의 강조.** CTA는 화면당 하나만 차콜로 강조한다.
4. **다크 모드 자동 대응.** 색은 반드시 시맨틱 토큰(`--text-title`, `--bg-default` 등)으로 써서 `[data-theme="dark"]`에서 자동 반전되게 한다.
5. **금지:** 별·마법·우주·운세, 의료 차트, 키치, 과한 이모지/느낌표, "~보다 낫다"식 비교·경쟁 카피, 할인·최저가 중심 언어, 모델·제품의 AI 생성 이미지.

## 적용 워크플로

1. 무엇을 만들/고칠지 확인한다(랜딩, 상세, 배너, 이메일, 카드 등).
2. `tokens.css`(이 폴더)를 프로젝트에 넣거나 `<style>`에 붙인다 — **토큰이 항상 먼저**.
3. 아래 컴포넌트 패턴/클래스를 재사용한다. 새 컴포넌트도 토큰·radius·타이포 스케일 위에서 만든다.
4. 카피는 "보이스 & 카피" 규칙으로 다듬는다.
5. 다크 모드에서 한 번 확인한다(색이 하드코딩이면 반드시 토큰으로 교체).
6. 렌더 확인이 필요하면 `sharp`로 PNG를 뽑아 시각 검증한다(브라우저 스크린샷 툴이 불안정할 때).

## 디자인 토큰

### 색상 — Primitives (테마 불문 고정)
- **Green (브랜드 코어)**: 50 `#eef1ea` · 100 `#dce4d6` · 200 `#c8d3be` · 300 `#b6c3a8` · **400 `#a5b398` = CORE** · 500 `#8c9b7e` · 600 `#6e7e5f` · **700 `#515e45` = STRONG** · 800 `#39432f` · 900 `#20271a`
- **Gray/차콜**: white `#fff` · 50 `#f7f7f7` · 100 `#f0f0f0` · 200 `#d9d9d9` · 300 `#d7d7d7` · 400 `#bcbcbc` · 500 `#9e9e9e` · 600 `#7c7c7c` · 700 `#565656` · 800 `#363636` · 900 `#252525`
- **Blue(서브 액센트)** 50 `#eff3f6` … 400 `#8b9dab` … 900 `#131a20` / **Pink(서브)** 50 `#fbeef2` … 400 `#c691a3` … 900 `#24121b`
- **브랜드 네임드**: green `#a5b398` · ivory `#e4e0d5` · charcoal `#454342` · blue `#cad3da` · pink `#c691a3`
- **State**: sale `#c0392b` · success `#515e45` · error `#c0392b`

### 색상 — Semantic 토큰 (실무에서 이걸 쓴다)
| 토큰 | Light | 용도 |
|---|---|---|
| `--text-title` | #363636 | 대제목·핵심 텍스트 |
| `--text-primary` | #3e3948 | 기본 본문 |
| `--text-secondary` | #7c7c7c | 설명·캡션 |
| `--text-disabled` | #bcbcbc | 비활성 |
| `--bg-default` | #ffffff | 기본 페이지 배경 |
| `--bg-subtle` | #e4e0d5 | 섹션·카드 베이스(아이보리) |
| `--bg-surface` | #f7f7f7 | 보조 면·입력 배경 |
| `--border` | #d7d7d7 | 형태 구분 라인 |
| `--brand-default` | #a5b398 | 브랜드 강조·포인트 |
| `--brand-strong` | #515e45 | 흰 글씨 올라가는 강조 버튼 |
| `--action-default` | #454342 | 주 행동 CTA(차콜) |
| `--action-hover` | #2e2c2b | CTA hover |
| `--price` | #363636 | 가격 텍스트 |
| `--state-sale` | #c0392b | 세일가·할인율 |

> 다크 모드에서는 위 토큰이 자동 반전(bg #252525, 텍스트는 화이트 알파). **HEX 대신 토큰만 쓰면 공짜로 다크 대응.**

### 타이포그래피 (Pretendard)
| 스타일 | 크기/굵기/자간 | 예시 |
|---|---|---|
| Display | 48 / 700 / -2% | 빛을 입은 일상 |
| Heading 1 | 36 / 700 / -2% | 26 Summer Edition |
| Heading 2 | 28 / 600 / -1% | 이혈테라피 주얼패치 |
| Heading 3 | 22 / 600 / -1% | 진주 드롭 컬렉션 |
| Subtitle | 18 / 500 | 예뻐지는데 단 3초 |
| Body | 16 / 400 | 기본 본문 |
| Body Small | 14 / 400 | 보조 본문 |
| Caption | 13 / 500 | * 주문 제작 안내 |
| Price | 18 / 700 · tnum | 39,000원 |

폰트: `Pretendard`(CDN: `https://cdn.jsdelivr.net/gh/orioncactus/pretendard@v1.3.9/dist/web/static/pretendard.min.css`), fallback `system-ui, sans-serif`. 본문 line-height 1.6.

### 스페이싱 · Radius · Elevation
- **Spacing (4px 베이스)**: 4 · 8 · 12 · 16 · 20 · 24 · 32 · 40 · 48 · 64. 여백은 넉넉하게.
- **Radius**: `--r-sm 8px` · `--r-md 12px` · `--r-lg 16px` · `--r-xl 20px` · `--r-pill 999px`
- **Elevation**: sm `0 1px 3px rgba(69,67,66,.07)` · md `0 6px 18px rgba(69,67,66,.09)` · lg `0 16px 40px rgba(69,67,66,.12)`. 그림자는 절제 — 떠 있는 느낌만.
- **Easing**: `cubic-bezier(.2,.8,.2,1)`, transition 0.15~0.18s.

## 컴포넌트 패턴 (index.html 클래스 재사용)

- **버튼** `.btn` + 변형:
  - `.btn-cta` 차콜 배경/흰 글씨 = 주 CTA(구매·결제) — 화면당 1개
  - `.btn-brand` 세이지 강조(green-700) = 보조 강조
  - `.btn-secondary` 아이보리 / `.btn-outline` 아웃라인 / `.btn-ghost` 고스트 = 보조 행동
  - 크기 `.sm` / (기본) / `.lg`, 전체폭 `.block`
- **배지** `.badge` (+`.pill`): `-best`(차콜) `-new`(세이지) `-sale`(세일 레드) `-celeb` `-gold` `-soldout`
- **폼** `.field`>`label`+`.input`(`.err`), 도움말 `.help`, 수량 `.qty`, 검색 `.search`
- **탭/칩** `.tabs`>`.tab`(`.active`), `.chip`(`.on`)
- **알림/토스트** `.alert`(`-info -ok -warn -err`), `.toast`(`.show`)
- **카드** `.card` (bg-default + border + r-md + padding 24)
- **컨셉/필러** `.concept-lead`, `.pillars`>`.pillar`
- **Do/Don't** `.dodont`>`.dd.do` / `.dd.dont`

### 아이콘 (Iconography 섹션)
얇은 라인 · 부드러운 곡선. **1.4~2px 라인, 끝 둥글게.** 차콜 라인 + 은은한 세이지 면 힌트.
- SVG viewBox `0 0 32 32`, `stroke:var(--text-title); stroke-width:1.4; fill:none; stroke-linecap:round; stroke-linejoin:round`
- 면 힌트 클래스: `.isf`(fill `--green-100`) · `.isd`(fill `--green-600`) · `.icf`(fill `--text-title`)
- 세트: 귀 라인/부착 가이드, 패치 원형, 글로우, 밸런스 라인, 지속력(시계), 방수(물방울), 지압볼(과녁), 주얼(별), 선물, 귀 위치
- 새 아이콘은 이 라인 두께·둥근 끝·32그리드 규칙 위에서 그린다. 별/마법/의료차트/키치 금지.

## 보이스 & 카피

**컨셉:** Daily Luxury Wellness Jewelry — "몇 초 만에 더하는 자신감 / Confidence in Seconds."
스킨케어·메이크업·운동을 대체하지 않고, 모든 좋은 선택 **곁에 더하는** 동행의 언어.

**5개 축:** #더한다(Add) · #시작된다(Begin) · #몇초의변화(In Seconds) · #완성된다(Finish) · #함께한다(Together)

- 이렇게: 순간·즉각성 강조("몇 초", "지금", "바로"), 다른 루틴 존중, 절제된 럭셔리(담백·단정).
- 피함: 효능·건강효과 단정, 할인·최저가 세일 언어, 과한 이모지/느낌표, 비교·경쟁("~보다 낫다").

## 참고 파일
- `tokens.css` (이 SKILL.md와 같은 폴더) — 프로젝트에 바로 넣는 드롭인 토큰 + 다크 테마
- 전체 컴포넌트 마크업/CSS 원본: `w-island/wbl-styleguide` 레포의 `index.html` (또는 라이브 가이드 소스 보기)
- 라이브 가이드에서 스와치를 누르면 HEX가 복사된다.
