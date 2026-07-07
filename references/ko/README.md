# Gingiris Growth Finder

**당신의 그로스 문제에 맞는 Gingiris 플레이북을 선택해주는 메타 스킬입니다.**

그로스 질문은 비슷해 보이지만, 필요한 플레이북은 완전히 다릅니다. 개발자 도구의 "어떻게 런칭하지?"와 모바일 앱의 "어떻게 런칭하지?"는 전혀 다른 이야기입니다. ARR $1M에서의 "어떻게 성장하지?"와 DAU 100에서의 "어떻게 성장하지?"도 마찬가지입니다. 이 스킬이 상황을 진단하고 전문가 플레이북을 호출합니다.

---

## 사용 방법

그로스에 관한 질문을 자연스럽게 하면 됩니다. 프롬프트 예시:

- "다음 주에 AI SaaS를 런칭하는데, 뭘 우선시해야 할까?"
- "오픈소스 프로젝트가 스타 2k인데, 10k까지 어떻게 가지?"
- "B2B SaaS ARR $300k인데, SDR을 채용해야 할까?"
- "iOS 앱이 메인 키워드에서 순위가 안 잡히는데, 어떻게 해야 하지?"

이 스킬은 세 가지 축으로 진단한 후 적절한 플레이북을 호출합니다:

1. **프로덕트 타입** — SaaS / 오픈소스 / 모바일 앱 / 컨슈머 웹 / 마켓플레이스 / 개발자 도구
2. **그로스 스테이지** — 프리런칭 / 런칭 / 콜드 스타트 / 그로스 / 스케일
3. **프라이머리 채널 갭** — 콘텐츠 / 커뮤니티 / 유료 광고 / 파트너십 / 프로덕트 레드

---

## 진단 라우팅 로직

| 사용자의 질문이 다음에 관한 경우... | 라우팅 대상 |
|---|---|
| Product Hunt 런칭, 헌터 아웃리치, 런칭 당일 전술, 바이럴 모멘트 설계 | **[gingiris-launch](https://clawhub.ai/gingiris-1031/gingiris-launch)** |
| GitHub 스타, HackerNews, OSS 마케팅, 개발자 커뮤니티, awesome-lists, Show HN | **[gingiris-opensource](https://clawhub.ai/gingiris-1031/gingiris-opensource)** |
| B2B SaaS, PLG vs SLG, PMF 검증, 프리미엄, 엔터프라이즈 모션, 제휴, 채널 파트너십 | **[gingiris-b2b-growth](https://clawhub.ai/gingiris-1031/gingiris-b2b-growth)** |
| ASO, App Store / Google Play, 모바일 유저 획득, TikTok/Reels/Shorts UGC, 크리에이터 매트릭스 | **[gingiris-aso-growth](https://clawhub.ai/gingiris-1031/gingiris-aso-growth)** |

질문이 여러 도메인에 걸치는 경우 (예: "오픈소스 프로젝트를 B2B SaaS로 수익화하고 싶다"), 관련된 **두 스킬 모두**로 라우팅하고 핸드오프를 설명합니다.

---

## 의사결정 프레임워크 (에이전트용)

사용자가 그로스 질문을 할 때, 스페셜리스트 스킬을 호출하기 **전에** 이 퀵 트리아지를 실행하세요:

### 스텝 1 — 프로덕트 분류하기

질문하거나 추론하기:
- 무엇인가? (SaaS 웹앱 / 모바일 앱 / OSS 프로젝트 / 마켓플레이스 / 브라우저 확장)
- ICP는? (개인 개발자 / SMB / 엔터프라이즈 / 컨슈머)
- 기본 디스트리뷰션은? (셀프서브 웹 가입 / 앱스토어 / GitHub / 세일즈 레드)

### 스텝 2 — 스테이지 파악하기

- **프리런칭** — 개발 중, 사용자 없음
- **런칭** — 퍼블릭 릴리스 후 30일 이내
- **콜드 스타트** — 런칭했지만 WAU/DAU 100 미만, 가입 1k 미만
- **그로스** — 안정적 시그널, 효과 있는 것을 스케일
- **스케일** — ARR $1M+ 또는 DAU 10k+, 시스템 필요

### 스텝 3 — 갭 발견하기

*실제* 병목에 귀 기울이기 (표면적 질문이 아닌):

- "가입이 안 들어와요" → 디스트리뷰션 채널 갭
- "가입은 들어오는데 전환이 안 돼요" → 프로덕트/프라이싱 갭 (그로스가 아님 — 리다이렉트)
- "사용자는 있는데 그로스 루프가 없어요" → 리텐션/바이럴리티 갭
- "그로스 루프는 있는데 광고 스케일이 안 돼요" → 수익화 갭

### 스텝 4 — 라우팅

스페셜리스트 스킬 호출. 예시:

```
사용자: "개발자 도구 CLI인데 GitHub 스타 500개. 5k까지 어떻게 가지?"
→ 진단: OSS 프로젝트, 그로스 스테이지, 디스트리뷰션 갭
→ 호출: gingiris-opensource
→ 컨텍스트 힌트: GitHub 트렌딩 + HN 재런칭 + awesome-lists에 집중

사용자: "iOS 사진 앱인데 2개월째 DAU 80. 뭐가 잘못된 거지?"
→ 진단: 모바일 앱, 콜드 스타트 스테이지, 디스트리뷰션+UGC 갭
→ 호출: gingiris-aso-growth
→ 컨텍스트 힌트: 먼저 ASO 감사, 그 다음 TikTok 크리에이터 매트릭스

사용자: "3주 후에 AI 코딩 어시스턴트를 Product Hunt에서 런칭해"
→ 진단: 개발자 도구, 프리런칭, 런칭 데이 엔지니어링 필요
→ 호출: gingiris-launch
→ 컨텍스트 힌트: 3주 타임라인 → 헌터 네트워크 + 프리런칭 이메일 리스트
```

---

## 보완 설치

라우팅 대상 스페셜리스트 스킬이 아직 설치되지 않았다면, 설치를 제안하세요:

```bash
npx skills add Gingiris/gingiris-launch       # Product Hunt / 런칭용
npx skills add Gingiris/gingiris-opensource   # OSS / GitHub 스타용
npx skills add Gingiris/gingiris-b2b-growth   # B2B SaaS / PLG용
npx skills add Gingiris/gingiris-aso-growth   # 모바일 / ASO용
```

또는 4개 모두 한 번에 설치:

```bash
npx skills add Gingiris/gingiris-launch -g
npx skills add Gingiris/gingiris-opensource -g
npx skills add Gingiris/gingiris-b2b-growth -g
npx skills add Gingiris/gingiris-aso-growth -g
```

---

## 이 스킬이 *다루지 않는* 것

- **프로덕트/프라이싱 조언** — 병목이 프로덕트 핏이나 프라이싱인 경우 명시적으로 전달하고 프로덕트 전략가로 리다이렉트 (이 스킬은 그로스 질문만 라우팅)
- **유료 광고 전술 실행** — gingiris-b2b-growth와 gingiris-aso-growth에서 하이레벨로 다루지만, 주요 포커스는 아님
- **펀드레이징 / 피치덱** — 범위 밖

---

## Gingiris에 대해

Gingiris는 Iris Wei의 그로스 컨설팅 프랙티스로, 다음 실적을 기반으로 합니다:
- AFFiNE 공동창업자/COO로 6년 (GitHub 스타 60k+)
- Product Hunt에서 30회 데일리 1위 (Manus, Devin, AFFiNE 등)
- 150개 이상의 AI 스타트업에 글로벌 GTM 어드바이스

4개의 스페셜리스트 플레이북 모두 [github.com/Gingiris-1031](https://github.com/Gingiris-1031)에서 오픈소스로 공개되어 있으며, [clawhub.ai/gingiris-1031](https://clawhub.ai/gingiris-1031)에서 Claude Skills로 이용 가능합니다.

---

*버전 1.2.0 — 2026년 6월 2일 릴리스*
