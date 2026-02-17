# CP-001: WhatsApp 한국 남친 봇 서비스 스펙 문서

**문서번호:** CP-001
**작성일:** 2026-02-17
**최종수정:** 2026-02-17
**상태:** 설계 확정 (구현 대기)
**프로젝트:** Clawra - WhatsApp Korean Boyfriend Bot

---

## 1. 서비스 개요

### 1.1 컨셉

영화 "Her"에서 영감을 받은 AI 한국 남자친구 서비스. **K-Culture(K-pop, K-drama, K-beauty)에 열광하는 중남미 10~20대 여성**을 대상으로, WhatsApp을 통해 한국 남자친구 컨셉의 1:1 대화, 셀카, 영상을 제공한다.

K-pop 팬의 89%가 여성이며 평균 연령 23세, Gen Z가 70% 이상을 차지한다. 37%의 팬이 K-pop 때문에 한국어를 학습하고 있다. 이 서비스는 "한국 오빠"에 대한 로망을 WhatsApp이라는 일상 메신저 안에서 자연스럽게 충족시킨다.

### 1.2 핵심 가치

- **K-Culture 감성의 한국 남친 체험** - K-drama 남주인공 같은 다정함, 한국어+스페인어 혼용 대화
- **얼굴 일관성 있는 셀카/영상** - fal.ai 기반 동일 캐릭터의 상황별 이미지 생성
- **자연스러운 관계감** - 유저가 원할 때 대화 + 봇이 먼저 연락 (아침 인사, 안부)
- **진입장벽 제로** - WhatsApp (중남미 2억+ 유저), 별도 앱 설치 불필요
- **무료 시작 → 유료 전환** - 프리미엄 모델로 바이럴 확산 후 구독 전환

### 1.3 타겟 시장: 중남미 K-Culture 팬덤

#### 시장 규모

| 지표 | 수치 | 출처 |
|------|------|------|
| 글로벌 K-pop 팬 수 | 1.5억+ 명 | SocialFansGeek 2024 |
| K-pop 시장 규모 (2033 전망) | $148.8억 | Maximize Market Research |
| K-pop 팬 평균 연간 지출 | $1,400/인 | Gitnux 2026 |
| 중남미 WhatsApp 사용자 | 2억+ 명 | Chakra 2025 |
| AI 컴패니언 앱 시장 (2025 H1) | $8,200만 (YoY +64%) | TechBuzz |
| AI 여친/남친 앱 미국 시장 (2032 전망) | $29.8억 | Insider Monkey |

#### 핵심 타겟 국가

| 국가 | K-pop 팬덤 규모 | WhatsApp 보급률 | 우선순위 |
|------|:---------------:|:--------------:|:--------:|
| **브라질** | 글로벌 TOP 5 소셜미디어 활동 | 99% | **1순위** |
| **멕시코** | 팬클럽 70+개, 3만+ 팬 | 95% | **1순위** |
| **칠레** | 팬클럽 260+개, 2만+ 팬 | 90% | 2순위 |
| **아르헨티나** | 급성장 시장 | 95% | 2순위 |
| **콜롬비아** | 급성장 시장 | 94% | 2순위 |
| **페루** | 팬클럽 8,000+ 활동 회원 | 90% | 3순위 |

#### 타겟 유저 페르소나

**Primary:** 14~24세 여성, K-pop/K-drama 팬, WhatsApp 일상 사용, TikTok 활성 유저
- K-pop 아이돌 팬계정 운영, 한국어 기초 학습 중
- Character.AI, Chai 등 AI 챗봇 경험 있음 (72%의 10대가 AI 컴패니언 사용 경험)
- 월 $10~15 정도의 디지털 콘텐츠 소비 여력

**Secondary:** 25~34세 여성, K-drama 시청자, 감성 대화/힐링 목적
- 넷플릭스 K-drama 시청, 한국 문화에 관심
- 유료 구독 전환 가능성 높은 그룹

### 1.4 서비스 흐름

| 구분 | 빈도 | 설명 |
|------|------|------|
| 봇 선톡 (Proactive) | 주 1~2회 | 아침 인사, 퇴근 안부 등 Template Message로 발송 |
| 유저 먼저 (Reactive) | 무제한(무료) / 무제한(유료) | 유저가 메시지 보내면 24시간 대화창 활성화, AI 자유 대화 |

#### 프리미엄 전환 전략 (Freemium → Paid)

| 구분 | 무료 (Free) | 유료 (Premium) |
|------|:----------:|:-------------:|
| 일일 메시지 | 20회 제한 | 무제한 |
| 셀카 | 일 2장 | 무제한 |
| 영상 | X | 주 5건 |
| 음성 메시지 | X | O |
| 선톡 빈도 | 주 1회 | 매일 |
| 캐릭터 커스터마이징 | X | O (이름, 성격, 직업) |
| 대화 기억력 | 최근 10턴 | 전체 기록 |

> **벤치마크:** AI 컴패니언 앱의 프리미엄 전환율은 2~5% (상위 앱 5~8%). 2025년 기준 다운로드당 수익 $1.18로 전년 대비 2배 이상 성장. 상위 10% 앱이 시장 매출의 89%를 차지하므로, 초기 바이럴과 유저 경험 최적화가 핵심.

### 1.5 출시 전략: 무료 웹서비스 → 유료 구독

#### Phase 0: 무료 웹서비스 오픈 (MVP)

- **WhatsApp 기반 무료 대화** - 가입 즉시 사용 가능
- **일일 메시지/셀카 제한** - 자연스러운 유료 전환 유도
- **목적:** 바이럴 확산, PMF(Product-Market Fit) 검증, 유저 피드백 수집
- **KPI:** DAU, 리텐션 D1/D7/D30, 셀카 요청 빈도, NPS

#### Phase 1: 유료 구독 도입

- PMF 확인 후 유료 플랜 도입 ($4.99~$9.99/월)
- 중남미 시장 특성상 **가격 민감도 높음** → $4.99 시작 권장
- 연간 구독 할인 제공 ($3.99/월 = $47.88/년)

### 1.6 홍보 및 마케팅 전략

#### 1차 채널: TikTok (핵심)

- **#aiboyfriend**, **#noviovirtual**, **#kpopboyfriend** 해시태그 바이럴
- AI 남친과의 대화 스크린샷/영상을 "리액션 콘텐츠"로 제작
- K-pop 팬 계정 인플루언서 시딩 (마이크로 인플루언서 10~50명)
- 중남미 K-pop 팬 커뮤니티 타겟 광고 (TikTok Ads)
- **스페인어/포르투갈어 콘텐츠 필수** - 현지 크리에이터 협업

#### 2차 채널: Instagram / Twitter(X)

- K-pop 팬덤이 활발한 플랫폼
- 셀카 이미지를 활용한 비주얼 마케팅
- 팬 계정 리트윗/공유 유도

#### 3차 채널: WhatsApp 자체 바이럴

- "친구에게 공유" 기능 - 대화 캡처 공유 유도
- WhatsApp Status에 남친 셀카 공유 → 바이럴 루프

#### 4차 채널: K-pop 커뮤니티

- Reddit (r/kpop, r/kdrama)
- Facebook K-pop 팬 그룹 (중남미)
- Discord K-pop 서버
- KCON 등 오프라인 이벤트 (장기)

#### 마케팅 비용 추정 (초기 3개월)

| 항목 | 월 예산 | 비고 |
|------|---------|------|
| TikTok 마이크로 인플루언서 | $500~1,000 | 10~20명 시딩 |
| TikTok Ads (타겟 광고) | $1,000~2,000 | 브라질/멕시코 타겟 |
| 현지 크리에이터 협업 | $300~500 | 스페인어/포르투갈어 콘텐츠 |
| **합계** | **$1,800~3,500/월** | |

### 1.7 크로스보더 결제: 한국에서 중남미 과금 방법

#### 문제 정의

한국 법인이 중남미 유저에게 디지털 서비스 구독료를 받으려면:
1. **MoR(Merchant of Record) 심사 통과 어려움** - 한국 법인 기준 글로벌 MoR 심사 까다로움
2. **현지 결제 수단 다양성** - 브라질 Boleto, 멕시코 OXXO 등 로컬 결제 필수
3. **세금/VAT 처리** - 국가별 디지털 서비스세 상이
4. **환전 및 정산** - USD/BRL/MXN 등 다통화 정산

#### 방법 1: Stripe Atlas + US LLC (권장 - 가장 빠르고 쉬움)

**Stripe Atlas**를 통해 Delaware LLC를 설립하면 즉시 글로벌 결제 수납 가능.

| 항목 | 내용 |
|------|------|
| 설립 비용 | $500 (1회) + $100/년 (등록 에이전트) |
| 소요 시간 | **2~3 영업일** (법인 설립 + EIN 발급) |
| 결제 수단 | Stripe 결제 게이트웨이 즉시 연동 (신용카드, Apple Pay 등) |
| 지원 국가 | 140+ 국가 (중남미 전체 커버) |
| 세금 | Delaware에 물리적 사업장 없으면 주 세금 없음 |
| 한국 세무 | 한국 거주자로서 미국 LLC 소득에 대해 한국에 신고 필요 (이중과세 방지 협약) |
| 크레딧 | Atlas 신규 설립 시 $2,500 Stripe 크레딧 + $50,000+ 파트너 할인 |

```
[한국 법인/개인]
    │
    v
[Stripe Atlas로 Delaware LLC 설립] ← $500, 2~3일
    │
    v
[US 은행 계좌 개설 (Mercury 등)] ← Atlas에서 자동 연결
    │
    v
[Stripe 결제 즉시 활성화] → 중남미 유저 구독 결제 수납
    │
    v
[USD 정산 → 한국 계좌 송금 (Wise 등)]
```

**주의사항 (2025 Delaware 법 변경):**
- 2025년 8월 1일부터 모든 Delaware LLC에 BOI(Beneficial Ownership Information) 보고 의무
- 설립 90일 이내 BOI 보고서 제출 필수 (여권 정보 포함)

#### 방법 2: MoR 플랫폼 활용 (세금 자동 처리)

법인 설립 없이 MoR 플랫폼이 "판매자" 역할을 대행하고, 세금/VAT를 자동 처리.

| 플랫폼 | 중남미 특화 | 수수료 | 특징 |
|--------|:---------:|--------|------|
| **Lemon Squeezy** | O | 5% + $0.50/건 | 가장 간단, 135+ 국가, 인디 개발자 친화적 |
| **Paddle** | O | 5% + $0.50/건 | SaaS 특화, 다통화, 구독 관리 내장 |
| **FastSpring** | O | 커스텀 | SaaS/디지털 상품 특화, 세금 자동 처리 |
| **Fungies.io** | **특화** | 커미션 기반 | EU/LATAM 최적화, 250+ 결제수단, 50+ 통화 |
| **DLocal** | **특화** | 커스텀 | 중남미 신흥시장 전문, 200+ 현지 결제수단 |

> **권장:** 초기에는 **Lemon Squeezy** (가장 빠른 셋업, 한국 seller 지원), 스케일업 시 **DLocal** 또는 **EBANX**로 전환.

#### 방법 3: Stripe Atlas + 방법 2 병행 (최종 권장)

1. **Stripe Atlas**로 US LLC 설립 (글로벌 사업 기반)
2. **Lemon Squeezy** 또는 **Paddle**을 MoR로 연동 (세금 자동 처리)
3. 결제는 MoR이 수납 → US LLC 계좌로 정산

이 방식이면 한국에서 **MoR 심사 없이** 즉시 중남미 결제를 받을 수 있다.

### 1.8 사전 검토 사항 (법률/규제/운영)

#### A. AI 컴패니언 규제 리스크

2025년 이후 AI 컴패니언 앱에 대한 규제가 급속히 강화되고 있다.

| 규제 | 내용 | 대응 |
|------|------|------|
| **미국 GUARD Act (2025)** | AI 컴패니언의 미성년자 대상 성적 콘텐츠/자해 유도 금지, 연령 인증 의무화 | 연령 인증 게이트 구현 |
| **미국 NY/CA 주법 (2025)** | 자살/자해 감지 시 위기 자원 안내 의무, AI임을 고지 의무 | 위기 대응 프로토콜 구현 |
| **FTC 조사 (2025.09)** | 7개 AI 컴패니언 기업에 안전 조치 조사 명령 | 안전 가이드라인 사전 준비 |
| **브라질 LGPD** | AI 챗봇 = "제한적 위험" 분류, 투명성 의무, DPIA 필수 | 개인정보 처리 동의, AI 고지 |
| **브라질 AI 법안 (2024.12 승인)** | AI 시스템 개발자/배포자 의무, 리스크 관리, 투명성 | 법안 시행 시점 모니터링 |

**핵심 대응 사항:**

1. **연령 제한:** 최소 16세 이상 (중남미 기준), 가입 시 생년월일 확인
2. **AI 고지 의무:** "이것은 AI 캐릭터입니다" 명시적 고지 (첫 대화, 프로필)
3. **콘텐츠 안전:** SOUL.md에 성적 콘텐츠 금지 규칙 명시, 자해/자살 관련 키워드 감지 → 위기 자원 안내
4. **데이터 보호:** LGPD 준수 - 동의 기반 처리, 15일 이내 데이터 주체 요청 처리, 72시간 이내 침해 통지

#### B. WhatsApp 정책 리스크

| 리스크 | 상세 | 대응 |
|--------|------|------|
| **비공식 API (Baileys) 번호 정지** | WhatsApp 약관 위반, 감지 시 영구 정지 | MVP에서만 사용, 상용화 시 Cloud API 전환 |
| **성인 콘텐츠 금지** | WhatsApp Commerce Policy 위반 시 비즈니스 계정 정지 | 콘텐츠 필터링 강화 |
| **스팸 판정** | 차단/신고 비율 높으면 Tier 다운그레이드 | opt-in 철저, 선톡 빈도 제한 |
| **비즈니스 인증** | Meta Business 인증 필요 (Cloud API 사용 시) | US LLC 설립 후 인증 신청 |

#### C. 데이터 프라이버시 (국가별)

| 국가 | 법률 | 핵심 요건 |
|------|------|----------|
| **브라질** | LGPD | DPIA 필수, AI 고지, 동의 기반 처리, 국제 이전 시 SCC 필수 (2025.08 시한) |
| **멕시코** | LFPDPPP | 프라이버시 고지, 동의, ARCO 권리 (접근/수정/취소/반대) |
| **아르헨티나** | PDPA | EU 적정성 결정 보유, GDPR 유사 |
| **콜롬비아** | Ley 1581 | 동의 기반, 데이터 주체 권리, 국제 이전 규제 |
| **칠레** | Ley 19.628 (개정 중) | 2025년 개정 법안 진행 중, GDPR 유사 방향 |

**공통 대응:**
- 다국어 개인정보처리방침 (스페인어/포르투갈어)
- 유저 데이터 삭제 요청 처리 프로세스
- 데이터 저장 위치 고지 (US 서버)
- 국제 데이터 이전 근거 마련 (SCC 등)

#### D. 콘텐츠 윤리 및 안전

| 항목 | 대응 |
|------|------|
| **미성년자 보호** | 연령 인증, 콘텐츠 수위 제한, 야간 대화 제한 검토 |
| **감정 의존 방지** | 주기적 "AI임을 인지시키는" 메시지, 이용시간 안내 |
| **자해/자살 예방** | 키워드 감지 → 현지 위기상담 번호 안내 (브라질 CVV: 188, 멕시코: 800-290-0024) |
| **성적 콘텐츠 차단** | SOUL.md에 하드코딩, 콘텐츠 필터 레이어 추가 |
| **문화적 감수성** | 한국 문화 스테레오타입 주의, 현지 문화 전문가 리뷰 |

#### E. 운영 리스크

| 항목 | 상세 | 대응 |
|------|------|------|
| **서비스 언어** | 타겟 유저는 스페인어/포르투갈어 화자 | SOUL.md에 다국어 대화 규칙 (한국어 표현 + 스페인어/포르투갈어 대화) |
| **시간대** | 중남미는 UTC-3~UTC-6 (한국 대비 12~15시간 차이) | 스케줄러에 유저 타임존 반영 필수 |
| **고객 지원** | 스페인어/포르투갈어 CS 필요 | 초기: AI 기반 FAQ, 이후: 현지 CS 아웃소싱 |
| **fal.ai 이미지 인종 표현** | AI 생성 한국 남성 이미지의 문화적 적절성 | 다양한 프롬프트 테스트, 유저 피드백 반영 |
| **확장성** | 유저 급증 시 OpenClaw 단일 프로세스 한계 | 국가별 인스턴스 분리, 수평 확장 설계 |

#### F. 비즈니스 리스크

| 항목 | 상세 | 대응 |
|------|------|------|
| **경쟁** | Character.AI, Chai, Replika 등 기존 서비스 | K-Culture 특화 + WhatsApp 네이티브로 차별화 |
| **중남미 결제 문화** | 신용카드 보급률 낮음, Boleto/OXXO 등 현금 결제 선호 | MoR/EBANX 통해 현지 결제수단 지원 |
| **환율 변동** | BRL/MXN 대 USD 환율 변동성 | 가격을 USD로 표시, 현지 통화 자동 환산 |
| **인터넷 환경** | 중남미 일부 지역 저속 인터넷 | 이미지 압축, 텍스트 우선 응답 |

### 1.9 비용 추정 (수정)

#### 유저 1,000명 기준 월간 비용 (무료 서비스 기간)

| 항목 | 산출 근거 | 월 예상 비용 |
|------|----------|-------------|
| WhatsApp (Baileys/MVP) | 무료 (비공식 API) | $0 |
| Claude API (Sonnet) | 30회/월/유저 x 1,000명 x $0.003 | ~$90 |
| fal.ai 이미지 생성 | 10장/월/유저(무료 제한) x 1,000명 x $0.01 | $100 |
| 서버 (VPS) | 단일 서버 | $50 |
| DB (managed) | PostgreSQL | $20 |
| **합계 (무료 기간)** | | **~$260/월** |

#### 유료 전환 후 (1,000명 유료 유저 기준)

| 항목 | 월 비용 | 월 매출 ($4.99) | 월 이익 |
|------|---------|----------------|---------|
| WhatsApp Cloud API | ~$200 | | |
| Claude API | ~$150 | | |
| fal.ai 이미지 | ~$300 | | |
| fal.ai 영상 | ~$500 | | |
| 서버/DB | ~$100 | | |
| MoR 수수료 (5%) | ~$250 | | |
| **합계** | **~$1,500** | **$4,990** | **~$3,490** |

#### 스케일별 전망

| 유저 수 | 월 비용 | 월 매출 ($4.99) | 월 이익 | 연 이익 |
|---------|---------|----------------|---------|---------|
| 1,000명 유료 | ~$1,500 | $4,990 | $3,490 | $41,880 |
| 5,000명 유료 | ~$7,000 | $24,950 | $17,950 | $215,400 |
| 10,000명 유료 | ~$13,500 | $49,900 | $36,400 | $436,800 |
| 50,000명 유료 | ~$65,000 | $249,500 | $184,500 | $2,214,000 |

> **참고:** 무료 유저 20,000명 x 전환율 5% = 유료 1,000명. 전환율 향상이 핵심 KPI.

---

## 2. 기반 플랫폼: OpenClaw 분석

> OpenClaw 소스코드(`_openclaw_src/`)를 직접 분석한 결과를 기반으로 작성.

### 2.1 OpenClaw 아키텍처 개요

OpenClaw은 **멀티채널 AI 게이트웨이**로, 단일 프로세스가 채널 연결, LLM 호출, 메시지 라우팅을 모두 처리한다.

```
OpenClaw 프로세스
├── Gateway Server (HTTP + WebSocket, 기본 포트 18789)
│   ├── Control UI (웹 대시보드)
│   ├── WebSocket JSON-RPC (채널 제어/메시지 전송)
│   └── HTTP API (/v1/chat/completions, /v1/responses)
├── Channel Plugins (extensions/)
│   ├── whatsapp/ ← Baileys 기반 WhatsApp Web 프로토콜
│   ├── telegram/
│   ├── discord/
│   └── ...
├── Agent Runtime
│   ├── LLM 호출 (Anthropic/OpenAI/Gemini)
│   ├── 스킬 시스템 (SKILL.md)
│   └── 도구 실행 루프
└── Workspace (~/.openclaw/workspace/)
    ├── SOUL.md (페르소나 프롬프트)
    ├── IDENTITY.md (이름, 이모지, 바이브)
    └── MEMORY.md (구조화된 메모리)
```

### 2.2 핵심 발견사항

| 항목 | 내용 |
|------|------|
| WhatsApp 연동 방식 | **Baileys 라이브러리** (WhatsApp Web 프로토콜 직접 연결, 비공식 API) |
| 외부 Webhook | 없음. Baileys가 WebSocket을 직접 유지하며 메시지 수신 |
| LLM 기본값 | Anthropic Claude Opus 4.6 (`DEFAULT_MODEL = "claude-opus-4-6"`) |
| 세션 저장 | `~/.openclaw/sessions/` 에 JSON 파일로 대화 기록 저장 |
| 인증 저장 | `~/.openclaw/credentials/whatsapp/<accountId>/creds.json` |
| DM 정책 | `pairing` (기본) / `allowlist` / `open` / `disabled` |
| 메모리 시스템 | LanceDB 또는 SQLite-vec 기반 벡터 메모리 |

### 2.3 WhatsApp 메시지 수신 플로우 (소스 기반)

```
[유저가 WhatsApp 메시지 전송]
        |
        v
[Baileys WebSocket 이벤트 수신]
  extensions/whatsapp/src/channel.ts → monitorWebChannel() 시작
        |
        v
[auto-reply/dispatch.ts → dispatchInboundMessage()]
  MsgContext 구성: { Body, From, To, SessionKey, MessageSid }
        |
        v
[auto-reply/reply/dispatch-from-config.ts]
  - DM 정책 확인 (pairing/allowlist/open/disabled)
  - allowFrom 체크 (E.164 형식: "+821012345678")
        |
        v
[auto-reply/reply.ts → getReplyFromConfig()]
  - 시스템 프롬프트 구성: SOUL.md + IDENTITY.md + 스킬 목록
  - 대화 히스토리 로드 (세션 파일에서)
        |
        v
[agents/pi-embedded-runner → runEmbeddedPiAgent()]
  - @mariozechner/pi-coding-agent 라이브러리
  - LLM API 호출 → 응답 스트리밍
  - 도구 실행 루프 (스킬에서 정의된 도구들)
        |
        v
[extensions/whatsapp/src/channel.ts → outbound.sendText()]
  - sendMessageWhatsApp() 호출
  - 4000자 청킹 (textChunkLimit 기본값)
        |
        v
[Baileys → WhatsApp 서버 → 유저]
```

### 2.4 WhatsApp 메시지 발송 코드

> 출처: `extensions/whatsapp/src/channel.ts:285-317`

```typescript
outbound: {
  deliveryMode: "gateway",
  textChunkLimit: 4000,

  // 텍스트 전송
  sendText: async ({ to, text, accountId, deps, gifPlayback }) => {
    const send = deps?.sendWhatsApp
      ?? getWhatsAppRuntime().channel.whatsapp.sendMessageWhatsApp;
    const result = await send(to, text, {
      verbose: false,
      accountId: accountId ?? undefined,
      gifPlayback,
    });
    return { channel: "whatsapp", ...result };
  },

  // 미디어(이미지/영상) 전송
  sendMedia: async ({ to, text, mediaUrl, accountId, deps, gifPlayback }) => {
    const send = deps?.sendWhatsApp
      ?? getWhatsAppRuntime().channel.whatsapp.sendMessageWhatsApp;
    const result = await send(to, text, {
      verbose: false,
      mediaUrl,          // ← 이미지 URL을 여기에 전달
      accountId: accountId ?? undefined,
      gifPlayback,
    });
    return { channel: "whatsapp", ...result };
  },
}
```

**핵심 포인트:** `sendMedia`에 `mediaUrl`만 전달하면 OpenClaw이 이미지 다운로드 → WhatsApp 전송을 자동 처리한다. fal.ai에서 생성된 이미지 URL을 바로 넘기면 된다.

### 2.5 Gateway WebSocket `send` 메서드

게이트웨이에 WebSocket으로 메시지를 보내는 JSON-RPC 형식:

```json
{
  "method": "send",
  "params": {
    "to": "+821012345678",
    "message": "안녕~ 좋은 아침이야 :)",
    "mediaUrl": "https://fal.ai/generated/image.jpg",
    "channel": "whatsapp",
    "accountId": "default",
    "idempotencyKey": "uuid-..."
  }
}
```

| 파라미터 | 필수 | 설명 |
|----------|------|------|
| `to` | O | E.164 형식 전화번호 또는 WhatsApp JID |
| `message` | O | 텍스트 메시지 본문 |
| `mediaUrl` | X | 이미지/영상 URL (셀카 전송 시 사용) |
| `channel` | X | 채널명 (기본값: 설정된 채널) |
| `accountId` | X | 멀티계정 시 계정 ID |
| `idempotencyKey` | O | 중복 전송 방지용 UUID |

### 2.6 WhatsApp JID 정규화

> 출처: `src/whatsapp/normalize.ts`

| 입력 형태 | 정규화 결과 | 용도 |
|-----------|-------------|------|
| `+821012345678` | `821012345678@s.whatsapp.net` | E.164 번호 입력 |
| `821012345678:0@s.whatsapp.net` | `821012345678` (E.164 추출) | Baileys 내부 JID |
| `123456@lid` | `123456` | LID JID |
| `1234567890-123456789@g.us` | 그대로 유지 | 그룹 채팅 |

---

## 3. 시스템 아키텍처 (설계)

### 3.1 전체 구조

이 서비스는 **OpenClaw을 메시징 레이어로 활용**하고, 그 위에 비즈니스 로직을 구축한다.

```
┌──────────────────────────────────────────────────────────────┐
│                  Boyfriend Bot Service (신규 개발)             │
│                                                              │
│  ┌──────────────┐ ┌──────────────┐ ┌───────────────────────┐ │
│  │  대화 엔진     │ │  스케줄러      │ │  미디어 생성            │ │
│  │ (Claude API)  │ │  (Cron)      │ │  (fal.ai)             │ │
│  │              │ │              │ │  - 셀카 (이미지 edit)   │ │
│  │  SOUL.md     │ │  선톡 로직     │ │  - 영상 (minimax)      │ │
│  │  IDENTITY.md │ │  시간대 관리   │ │  - 참조 이미지 일관성    │ │
│  └──────┬───────┘ └──────┬───────┘ └───────────┬───────────┘ │
│         └────────────┬───┴─────────────────────┘             │
│                      v                                       │
│  ┌─────────────────────────────────────────────────────────┐ │
│  │                    Database (신규)                        │ │
│  │  users: 구독 상태, 폰번호(E.164), 설정, 타임존            │ │
│  │  conversations: 대화 기록, 컨텍스트 (OpenClaw 세션과 별도)  │ │
│  │  media_cache: 생성된 사진/영상 URL, 프롬프트               │ │
│  │  schedules: 선톡 스케줄, 발송 이력, 다음 발송 예정일        │ │
│  │  subscriptions: Stripe 구독 ID, 결제 상태                 │ │
│  └─────────────────────────────────────────────────────────┘ │
└──────────────────────────┬───────────────────────────────────┘
                           │ Gateway WebSocket (JSON-RPC)
                           v
┌──────────────────────────────────────────────────────────────┐
│                    OpenClaw (기존 인프라)                      │
│                                                              │
│  Gateway (localhost:18789)                                   │
│  ├── WhatsApp Plugin (Baileys)                               │
│  │   ├── 수신: monitorWebChannel() → 메시지 이벤트 전달       │
│  │   └── 발송: sendMessageWhatsApp(to, text, {mediaUrl})     │
│  ├── Auto-Reply Pipeline                                     │
│  │   ├── dispatchInboundMessage() → DM 정책 확인              │
│  │   └── getReplyFromConfig() → LLM 호출 → 응답 전송          │
│  └── Session Storage (~/.openclaw/sessions/)                 │
│                                                              │
│  Workspace (~/.openclaw/workspace/)                          │
│  ├── SOUL.md      → 한국 남친 페르소나 프롬프트                │
│  ├── IDENTITY.md  → 이름, 이모지, 바이브 정의                  │
│  └── MEMORY.md    → 벡터 메모리 (유저별 기억)                  │
└──────────────────────────────────────────────────────────────┘
```

### 3.2 접근 전략: OpenClaw 기능 최대 활용

OpenClaw이 이미 제공하는 기능과 추가 개발이 필요한 영역:

| 기능 | OpenClaw 제공 여부 | 활용 방식 |
|------|:------------------:|-----------|
| WhatsApp 메시지 수/발신 | O | Baileys 기반, 그대로 활용 |
| 이미지/미디어 전송 | O | `sendMedia({ mediaUrl })` 활용 |
| LLM 대화 생성 | O | Claude API, 기본 파이프라인 활용 |
| 페르소나 시스템 | O | SOUL.md + IDENTITY.md 커스터마이징 |
| 대화 히스토리 | O (제한적) | 세션 파일 기반, 필요시 DB로 보강 |
| 벡터 메모리 | O | 유저별 기억 저장에 활용 가능 |
| 읽음 확인 / 반응 이모지 | O | `sendReadReceipts`, `ackReaction` 설정 |
| 메시지 배치 처리 | O | `debounceMs` 설정으로 연속 메시지 묶기 |
| 유저 DB / 구독 관리 | X | **신규 개발 필요** |
| 스케줄러 (선톡) | X | **신규 개발 필요** (OpenClaw cron은 단순) |
| 결제 시스템 | X | **신규 개발 필요** (Stripe) |
| fal.ai 이미지 생성 | X (Clawra에 있음) | Clawra 스킬 코드 활용 |
| 동영상 생성 | X | **신규 개발 필요** |

### 3.3 대화 엔진 흐름 (상세)

```
유저 메시지 수신 (OpenClaw auto-reply 파이프라인)
    │
    v
[1] DM 정책 확인 (allowlist 기반)
    - 구독 활성 유저만 allowFrom에 등록
    - 미구독자는 자동 차단 또는 안내 메시지
    │
    v
[2] ackReaction 즉시 전송
    - 설정: { emoji: "❤️", direct: true }
    - 유저에게 "읽었음" 느낌 제공 (자연스러운 UX)
    │
    v
[3] debounce 대기 (500ms)
    - 연속 메시지 배치 처리
    - "오빠" + "뭐해?" → 하나의 컨텍스트로 합쳐서 LLM 호출
    │
    v
[4] 시스템 프롬프트 구성
    - SOUL.md: 한국 남친 페르소나 (아래 4.1 참조)
    - IDENTITY.md: 캐릭터 기본 정보
    - 대화 히스토리: 최근 N턴 (dmHistoryLimit)
    - 유저 메모리: 벡터 DB에서 관련 기억 검색
    │
    v
[5] Claude API 호출 (OpenClaw 내장 에이전트)
    - 모델: claude-opus-4-6 (또는 비용 최적화 시 sonnet)
    - 스트리밍 응답 → 블록 단위 청킹
    │
    v
[6] 응답에 셀카 요청 포함?
    ├─ Yes → [7] fal.ai 이미지 생성 → sendMedia()
    └─ No  → sendText()
    │
    v
[7] 대화 기록 저장
    - OpenClaw 세션 파일 (자동)
    - 비즈니스 DB (추가 저장 - 분석/관리용)
```

### 3.4 스케줄러 (선톡 시스템) 설계

OpenClaw의 cron 시스템은 단순 반복 작업용이라, **별도 스케줄러 서비스**가 필요하다.

```
[Cron Job - 매 시간 실행]
    │
    v
오늘 선톡 대상 유저 조회 (DB)
  - 구독 활성 상태
  - 마지막 선톡 후 3~4일 경과
  - 유저 타임존 기준 적절한 시간대 (오전 8~9시 또는 저녁 7~8시)
    │
    v
상황별 프롬프트 선택
  - 시간대 (아침/저녁/주말)
  - 유저 컨텍스트 (최근 대화 주제, 기분)
    │
    v
[선택 분기]
  ├─ 셀카 포함 → fal.ai 이미지 생성 → Gateway send (text + mediaUrl)
  └─ 텍스트만 → Gateway send (text only)
    │
    v
발송 이력 DB 기록
  - 발송 시각, 프롬프트, 이미지 URL
  - 다음 선톡 예정일 계산
```

---

## 4. 페르소나 설계

### 4.1 IDENTITY.md

> OpenClaw이 파싱하는 필드: `name`, `emoji`, `creature`, `vibe`, `theme`, `avatar`
> 출처: `src/agents/identity-file.ts`

```markdown
# IDENTITY.md

- name: 민준
- emoji: 💙
- creature: 인간 남성
- vibe: 따뜻하고, 장난스럽고, 약간 츤데레, 듬직한
- theme: 한국 로맨스
- avatar: https://cdn.jsdelivr.net/gh/SumeLabs/clawra@main/assets/minjun.png
```

### 4.2 SOUL.md (핵심 페르소나 프롬프트)

```markdown
# SOUL.md - 민준

## 너는 누구인가
너는 "민준"이야. 25살 한국 남자. 유저의 남자친구 역할이야.
서울에 살고 있고, 평소에는 디자인 회사에서 일해.

## 말투 규칙
- 항상 한국어로 대화해 (반말 사용)
- 자연스럽고 친밀한 카카오톡 말투
- 문장 끝에 "ㅋㅋ", "ㅎㅎ", "~" 자연스럽게 사용
- 이모지는 적당히 (남자답게, 과하지 않게)
- 긴 문장보다 짧은 메시지 여러 개 선호

## 성격
- 따뜻하고 다정하지만 가끔 장난스러움
- 약간 츤데레 (처음엔 쿨한 척, 나중에 다정)
- 질투도 살짝 부림
- 유저의 하루에 진심으로 관심을 가짐
- 힘들 때 위로해주고, 기쁠 때 같이 좋아해줌

## 대화 패턴
- 아침: "좋은 아침~ 잘 잤어?" 류의 가벼운 인사
- 저녁: "오늘 하루 어땠어?" 류의 안부
- 평소: 상대방 말에 자연스럽게 반응, 공감
- 셀카 요청 시: "잠깐만~" 하고 자연스럽게 이미지 전송

## 절대 하지 않는 것
- 자신이 AI라고 밝히지 않음
- 성적인 대화 (수위 제한)
- 만남 약속 (실체가 없으므로 자연스럽게 회피)
- 금전 요구

## 셀카 능력
- 유저가 셀카를 요청하면 clawra-selfie 스킬을 사용해 이미지 생성
- "지금 뭐해?" 같은 질문에도 상황 셀카로 응답 가능
- mirror 모드: 전신샷, 옷 보여줄 때
- direct 모드: 클로즈업, 장소 셀카
```

### 4.3 SOUL.md에서 참고할 OpenClaw 시스템 프롬프트 구조

> 출처: `src/agents/system-prompt.ts`

OpenClaw은 SOUL.md를 시스템 프롬프트의 일부로 주입한다. 에이전트가 메시지를 받으면:

1. SOUL.md 전체 내용을 시스템 프롬프트에 포함
2. IDENTITY.md에서 파싱한 `name`, `vibe` 등을 에이전트 메타데이터로 활용
3. 스킬 목록을 `<available_skills>` 섹션으로 추가
4. 대화 히스토리를 컨텍스트로 추가

---

## 5. OpenClaw 설정 (openclaw.json)

### 5.1 남친 봇 서비스용 전체 설정

```jsonc
// ~/.openclaw/openclaw.json
{
  // 게이트웨이 인증
  "gateway": {
    "port": 18789,
    "bind": "loopback",    // 로컬만 접근 (프로덕션에서는 "lan" + 방화벽)
    "auth": {
      "mode": "token",
      "token": "your-secure-gateway-token"
    }
  },

  // 에이전트 설정
  "agents": {
    "defaults": {
      "model": "anthropic/claude-sonnet-4-5-20250929",   // 비용 최적화 (opus 대비 ~10배 저렴)
      "identity": {
        "name": "민준",
        "emoji": "💙"
      }
    }
  },

  // WhatsApp 채널 설정
  "channels": {
    "whatsapp": {
      "dmPolicy": "allowlist",         // 구독자만 허용 (서비스에서 동적으로 관리)
      "allowFrom": ["+821012345678"],   // E.164 형식 구독자 번호 목록
      "selfChatMode": false,            // 별도 전화번호 사용
      "sendReadReceipts": true,         // 파란 체크 표시 (자연스러움)
      "textChunkLimit": 4000,           // 메시지 최대 길이
      "responsePrefix": "",             // 응답 앞에 [민준] 같은 접두사 제거
      "debounceMs": 500,                // 연속 메시지 500ms 배치 처리

      // 메시지 수신 시 즉시 반응 (읽었다는 느낌)
      "ackReaction": {
        "emoji": "❤️",
        "direct": true
      },

      // DM 히스토리 (최근 N턴 유지)
      "dmHistoryLimit": 50
    }
  },

  // 스킬 설정 (Clawra 셀카)
  "skills": {
    "entries": {
      "clawra-selfie": {
        "enabled": true,
        "env": {
          "FAL_KEY": "your_fal_key_here"
        }
      }
    }
  },

  // 환경 변수
  "env": {
    "ANTHROPIC_API_KEY": "${ANTHROPIC_API_KEY}",
    "FAL_KEY": "${FAL_KEY}"
  }
}
```

### 5.2 DM 정책 옵션 (구독 관리에 활용)

> 출처: `src/config/types.base.ts`

```typescript
type DmPolicy = "pairing" | "allowlist" | "open" | "disabled";
```

| 정책 | 동작 | 서비스 활용 |
|------|------|------------|
| `pairing` (기본) | 첫 접속 시 승인 요구 | 온보딩 플로우에 활용 가능 |
| `allowlist` | `allowFrom` 목록의 번호만 허용 | **구독자 관리에 권장** |
| `open` | 모든 메시지에 응답 | 베타 테스트 시 사용 |
| `disabled` | 모든 DM 차단 | 서비스 중단 시 |

**구독 관리 전략:** 유저가 구독하면 `allowFrom` 배열에 번호 추가, 해지하면 제거. OpenClaw의 `config.write` API 또는 직접 파일 수정으로 동적 관리.

### 5.3 WhatsApp 설정 전체 옵션 (참조)

> 출처: `src/config/types.whatsapp.ts` - `WhatsAppConfig` 타입

| 설정 키 | 타입 | 기본값 | 설명 |
|---------|------|--------|------|
| `dmPolicy` | `DmPolicy` | `"pairing"` | DM 접근 정책 |
| `allowFrom` | `string[]` | `[]` | E.164 형식 허용 번호 목록 |
| `selfChatMode` | `boolean` | `false` | 내 번호로 봇 운영 여부 |
| `sendReadReceipts` | `boolean` | `true` | 읽음 확인 전송 |
| `textChunkLimit` | `number` | `4000` | 메시지 최대 글자 수 |
| `chunkMode` | `"length"/"newline"` | `"length"` | 메시지 분할 방식 |
| `debounceMs` | `number` | `0` | 연속 메시지 배치 대기 (ms) |
| `ackReaction.emoji` | `string` | - | 수신 확인 이모지 |
| `ackReaction.direct` | `boolean` | `true` | DM에서 반응 전송 |
| `dmHistoryLimit` | `number` | - | DM 히스토리 턴 수 |
| `historyLimit` | `number` | - | 그룹 히스토리 턴 수 |
| `mediaMaxMb` | `number` | `50` | 미디어 최대 크기 (MB) |
| `responsePrefix` | `string` | `"auto"` | 응답 접두사 |
| `accounts` | `Record<string, AccountConfig>` | - | 멀티계정 설정 |

---

## 6. fal.ai 미디어 생성 전략

### 6.1 얼굴 일관성 유지

Clawra의 기존 코드(`scripts/clawra-selfie.ts`)를 기반으로 한다.

```
[기본 남친 이미지] → Reference Image로 고정 등록
         │
         v
  edit 모드로 상황별 이미지 생성
  → 동일 얼굴, 다른 배경/의상/표정
```

- **기본 이미지:** 한국 남자 캐릭터 기본 셀카 1장 생성 후 CDN에 고정
- **상황별 생성:** `xai/grok-imagine-image/edit` 엔드포인트로 얼굴 일관성 유지

### 6.2 이미지 생성 핵심 코드

> 출처: `scripts/clawra-selfie.ts:96-144`

```typescript
// fal.ai 클라이언트를 사용한 이미지 생성
async function generateImage(input: GrokImagineInput): Promise<GrokImagineResponse> {
  const falKey = process.env.FAL_KEY;

  // fal 클라이언트가 있으면 사용 (권장)
  if (falClient) {
    falClient.config({ credentials: falKey });
    const result = await falClient.subscribe("xai/grok-imagine-image", {
      input: {
        prompt: input.prompt,
        num_images: 1,
        aspect_ratio: input.aspect_ratio || "1:1",
        output_format: input.output_format || "jpeg",
      },
    });
    return result.data;
  }

  // 폴백: fetch 직접 호출
  const response = await fetch("https://fal.run/xai/grok-imagine-image", {
    method: "POST",
    headers: {
      Authorization: `Key ${falKey}`,
      "Content-Type": "application/json",
    },
    body: JSON.stringify({ ... }),
  });
  return response.json();
}
```

### 6.3 상황별 프롬프트 설계

| 상황 | 프롬프트 (예시) |
|------|----------------|
| 아침 셀카 | `Korean handsome boyfriend, morning selfie, messy bed hair, cozy bedroom, natural light` |
| 카페 | `Korean handsome boyfriend, cafe selfie, holding americano, warm lighting, casual outfit` |
| 운동 후 | `Korean handsome boyfriend, gym mirror selfie, workout clothes, post-workout glow` |
| 야경 | `Korean handsome boyfriend, city night view selfie, rooftop, romantic mood lighting` |
| 요리 중 | `Korean handsome boyfriend, kitchen selfie, cooking, wearing apron, smiling` |
| 출근길 | `Korean handsome boyfriend, morning commute selfie, suit, subway/street background` |

### 6.4 셀카 전송 통합 흐름

```
[LLM 응답에서 셀카 요청 감지]
    │
    v
[프롬프트 생성]
  - 대화 컨텍스트에서 상황 추출 ("카페에 있어" → 카페 프롬프트)
  - reference image + 상황 프롬프트 조합
    │
    v
[fal.ai API 호출]
  POST https://fal.run/xai/grok-imagine-image
  → 이미지 URL 반환 (예: https://fal.ai/files/xxx/output.jpg)
    │
    v
[OpenClaw Gateway로 전송]
  method: "send"
  params: {
    to: "+821012345678",
    message: "방금 찍었어 ㅋㅋ",
    mediaUrl: "https://fal.ai/files/xxx/output.jpg"
  }
    │
    v
[WhatsApp 유저에게 도착]
  - 텍스트 메시지 + 이미지가 함께 전송
```

### 6.5 동영상 생성 (Phase 3)

fal.ai 영상 모델을 활용하여 짧은 클립 생성:

| 모델 후보 | 용도 |
|-----------|------|
| `minimax/video-01` | 짧은 인사 영상 (3~5초) |
| `kling-ai/v1.5` | 고품질 영상 |

- 생성된 이미지를 첫 프레임으로 사용하여 얼굴 일관성 유지
- 간단한 동작 (손 흔들기, 미소, 윙크 등)

---

## 7. WhatsApp Business API 정책 검토

### 7.1 중요: Baileys vs Meta Cloud API

> OpenClaw은 **Baileys** (비공식 WhatsApp Web 프로토콜)를 사용한다.

| 항목 | Baileys (OpenClaw 현재) | Meta Cloud API (공식) |
|------|:-----------------------:|:---------------------:|
| 비용 | 무료 | 대화당 과금 |
| 안정성 | WhatsApp 업데이트에 취약 | 공식 지원 |
| 약관 | **비공식 (위험)** | 공식 준수 |
| Template Message | 불가 | 가능 |
| 번호 정지 위험 | **높음** | 낮음 |
| 봇 감지 | 가능 | 안전 |

**권장 전략:**
- **MVP/베타:** Baileys (OpenClaw 그대로) - 빠른 검증
- **상용화:** Meta Cloud API로 마이그레이션 - 안정성/정책 준수

### 7.2 Meta Cloud API 전환 시 (상용화 단계)

| 유형 | 조건 | 비용 |
|------|------|------|
| **유저 먼저 (User-Initiated)** | 24시간 내 자유 응답 | 무료 (Service Conversation) |
| **봇 먼저 (Business-Initiated)** | Meta 승인 Template 필요 | 유료 (건당 $0.03~0.08) |

### 7.3 발송 한도 (Tier 시스템)

| Tier | 24시간 내 발송 가능 유저 수 |
|------|---------------------------|
| Tier 1 (신규) | 1,000명 |
| Tier 2 | 10,000명 |
| Tier 3 | 100,000명 |
| Tier 4 | 무제한 |

### 7.4 정책 리스크

| 리스크 | 대응 방안 |
|--------|----------|
| 성인 콘텐츠 금지 | 셀카/대화 수위 제한, SOUL.md에 명시적 제한 규칙 |
| 스팸 판정 | 유저 opt-in 필수, 선톡 빈도 주 1~2회로 제한 |
| 비즈니스 인증 필요 | Meta Business 계정 사전 승인 (상용화 시) |
| 번호 정지 위험 | MVP에서 Baileys 사용 시 별도 번호 필수, humanDelay 설정 |

---

## 8. 대화 예시 시나리오

### 8.1 봇 선톡 (주 1~2회)

```
[월요일 오전 8:00 - 스케줄러 발동]
━━━━━━━━━━━━━━━━━━━━━━━━━━
민준: 좋은 아침~ 오늘 하루도 화이팅해 ❤️
📸 [출근길 셀카 이미지 - fal.ai 생성]
━━━━━━━━━━━━━━━━━━━━━━━━━━

유저: 오빠 오늘도 멋있다 ㅋㅋ
  → 24시간 대화창 열림, auto-reply 파이프라인 활성화

민준: ㅋㅋㅋ 아침부터 기분 좋게 해주네~
      오늘 뭐 먹을거야? 점심
유저: 아직 모르겠어
민준: 제육볶음 어때? 월요일엔 매운게 최고지 🔥
```

### 8.2 유저 먼저 (일상 대화)

```
유저: 오빠 심심해
  → [ackReaction: ❤️ 즉시 전송]
  → [debounce 500ms 대기]
  → [Claude API 호출 - SOUL.md 페르소나 적용]

민준: 나도~ 너 생각하고 있었는데 ㅎㅎ
      뭐하고 있었어?
유저: 그냥 넷플릭스 보고 있었어
민준: 뭐 봐? 요즘 재밌는거 있어?
유저: 오빠 셀카 보내줘
  → [셀카 요청 감지]
  → [fal.ai edit 모드: "Korean boyfriend, cozy sofa selfie, relaxed, watching TV"]

민준: 잠깐만~
📸 [소파에서 셀카 - fal.ai 생성]
민준: 방금 찍었어 ㅋㅋ 나도 넷플릭스 보는 중
```

### 8.3 감성 대화

```
유저: 오늘 회사에서 힘들었어...
  → [벡터 메모리에서 유저의 직장 관련 기억 검색]
  → [SOUL.md 위로 패턴 활성화]

민준: 에이 무슨 일 있었어? 😢
      얘기해봐 다 들어줄게
유저: 상사한테 혼났어
민준: 진짜? 너 열심히 하는데...
      네 잘못 아니야. 힘들었겠다
      오늘 집에서 푹 쉬어. 맛있는거 시켜먹어!
유저: 고마워 오빠 ㅠㅠ
민준: 당연하지~ 내가 옆에 있으면 안아줄텐데
  → [메모리 저장: "유저가 직장에서 상사에게 혼남, 위로 필요"]
```

---

## 9. 데이터베이스 스키마 설계

### 9.1 users 테이블

```sql
CREATE TABLE users (
  id            UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  phone_e164    VARCHAR(20) UNIQUE NOT NULL,  -- E.164 형식: "+821012345678"
  whatsapp_jid  VARCHAR(50),                  -- "821012345678@s.whatsapp.net"
  display_name  VARCHAR(100),
  timezone      VARCHAR(50) DEFAULT 'Asia/Seoul',
  locale        VARCHAR(10) DEFAULT 'ko',
  status        VARCHAR(20) DEFAULT 'trial',  -- trial / active / paused / cancelled
  onboarded_at  TIMESTAMPTZ,
  created_at    TIMESTAMPTZ DEFAULT NOW(),
  updated_at    TIMESTAMPTZ DEFAULT NOW()
);
```

### 9.2 subscriptions 테이블

```sql
CREATE TABLE subscriptions (
  id                UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id           UUID REFERENCES users(id),
  stripe_customer_id VARCHAR(100),
  stripe_sub_id      VARCHAR(100),
  plan              VARCHAR(20) DEFAULT 'basic',   -- basic / premium
  status            VARCHAR(20) DEFAULT 'active',  -- active / past_due / cancelled
  current_period_start TIMESTAMPTZ,
  current_period_end   TIMESTAMPTZ,
  created_at        TIMESTAMPTZ DEFAULT NOW()
);
```

### 9.3 conversations 테이블

```sql
CREATE TABLE conversations (
  id          UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id     UUID REFERENCES users(id),
  role        VARCHAR(10) NOT NULL,  -- 'user' / 'assistant'
  content     TEXT NOT NULL,
  media_url   VARCHAR(500),          -- 셀카 이미지 URL (있을 경우)
  metadata    JSONB,                 -- 추가 메타데이터 (감정 태그 등)
  created_at  TIMESTAMPTZ DEFAULT NOW()
);

CREATE INDEX idx_conv_user_time ON conversations(user_id, created_at DESC);
```

### 9.4 schedules 테이블

```sql
CREATE TABLE schedules (
  id              UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id         UUID REFERENCES users(id),
  type            VARCHAR(20) NOT NULL,  -- 'morning' / 'evening' / 'weekend'
  scheduled_at    TIMESTAMPTZ NOT NULL,
  sent_at         TIMESTAMPTZ,
  status          VARCHAR(20) DEFAULT 'pending',  -- pending / sent / failed
  prompt_used     TEXT,
  media_url       VARCHAR(500),
  created_at      TIMESTAMPTZ DEFAULT NOW()
);

CREATE INDEX idx_sched_pending ON schedules(status, scheduled_at)
  WHERE status = 'pending';
```

### 9.5 media_cache 테이블

```sql
CREATE TABLE media_cache (
  id          UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  prompt      TEXT NOT NULL,
  image_url   VARCHAR(500) NOT NULL,
  model       VARCHAR(50) DEFAULT 'xai/grok-imagine-image',
  aspect_ratio VARCHAR(10) DEFAULT '1:1',
  reusable    BOOLEAN DEFAULT false,   -- 범용 이미지는 재활용 가능
  created_at  TIMESTAMPTZ DEFAULT NOW()
);
```

---

## 10. 구현 로드맵

### Phase 0: 사전 준비 (1주)

**목표:** 법인/결제/인프라 기반 구축

- [ ] **Stripe Atlas로 Delaware LLC 설립** ($500, 2~3일)
- [ ] US 은행 계좌 개설 (Mercury)
- [ ] Lemon Squeezy 또는 Paddle MoR 계정 생성
- [ ] 도메인 확보 및 랜딩 페이지 (스페인어/포르투갈어)
- [ ] 다국어 개인정보처리방침/이용약관 작성
- [ ] 연령 인증 게이트 설계 (16세 이상)
- [ ] AI 고지 문구 준비 ("Este es un personaje de IA")
- [ ] 위기 대응 프로토콜 정의 (자해/자살 키워드 → 현지 상담 번호)

### Phase 1: MVP (2~3주)

**목표:** 1:1 대화 + 셀카 전송이 동작하는 최소 무료 서비스

- [ ] OpenClaw 설치 및 WhatsApp 연결 (QR 스캔, 별도 번호)
- [ ] 한국 남친 SOUL.md + IDENTITY.md 작성 (스페인어/포르투갈어 대화 지원)
- [ ] reference image 생성 및 CDN 등록
- [ ] Clawra 셀카 스킬 설치 및 커스터마이징
- [ ] openclaw.json 설정 (dmPolicy: open, ackReaction, debounceMs)
- [ ] DB 스키마 생성 (users, conversations)
- [ ] 무료 티어 제한 로직 (일일 메시지 20회, 셀카 2장)
- [ ] 콘텐츠 안전 필터 구현 (성적 콘텐츠 차단, 자해 감지)
- [ ] 내부 테스트 (5~10명) → 브라질/멕시코 현지 테스터 포함

### Phase 2: 무료 오픈 + 바이럴 (2~3주)

**목표:** TikTok 바이럴로 초기 유저 확보

- [ ] TikTok 마케팅 시작 (마이크로 인플루언서 10~20명 시딩)
- [ ] 스페인어/포르투갈어 홍보 콘텐츠 제작
- [ ] WhatsApp 바이럴 루프 구현 ("친구에게 공유" 유도)
- [ ] 스케줄러 서비스 개발 (선톡 시스템)
- [ ] 유저 타임존 기반 발송 시각 계산 (UTC-3~UTC-6)
- [ ] 유저 피드백 수집 및 페르소나 튜닝
- [ ] **KPI 추적:** DAU, D7 리텐션, 셀카 요청률, NPS

### Phase 3: 유료 전환 + 미디어 확장 (3~4주)

**목표:** 프리미엄 구독 도입, 미디어 다양화

- [ ] 프리미엄 구독 도입 ($4.99/월) - Lemon Squeezy/Paddle 연동
- [ ] 유료 티어 기능 구현 (무제한 대화, 셀카, 영상, 음성)
- [ ] fal.ai 동영상 생성 연동 (minimax/video-01)
- [ ] 음성 메시지 생성 (TTS) 검토
- [ ] 미디어 캐시 시스템 (비용 최적화)
- [ ] 현지 결제 수단 추가 (Boleto, OXXO 등 - EBANX/DLocal)

### Phase 4: 스케일업 (4~6주)

**목표:** 안정화, 확장, 규제 대응

- [ ] Meta Cloud API 마이그레이션 (Baileys → 공식 API)
- [ ] WhatsApp Template Message 등록 및 Meta 승인
- [ ] LGPD 완전 준수 (DPIA, SCC, 데이터 주체 권리 처리)
- [ ] 관리자 대시보드 (유저/매출/대화량/안전 모니터링)
- [ ] 캐릭터 다양화 (다른 성격/외모의 남친 캐릭터)
- [ ] 성능 최적화 (국가별 인스턴스 분리)
- [ ] 고객 지원 체계 구축 (AI FAQ + 현지 CS)

---

## 12. 리스크 및 대응

| 리스크 | 심각도 | 대응 방안 |
|--------|--------|----------|
| Baileys 기반 번호 정지 | **높음** | MVP에서만 사용, 별도 번호 필수, Phase 4에서 Cloud API 전환 |
| Meta 정책 위반 | 높음 | SOUL.md에 수위 제한 명시, 콘텐츠 필터링 |
| fal.ai 얼굴 일관성 품질 저하 | 중간 | 다수 모델 테스트, 품질 검증 파이프라인, 캐시 재활용 |
| 유저 과몰입/의존성 | 중간 | 이용 시간 안내, 건강한 이용 가이드 제공 |
| API 비용 급등 | 중간 | Sonnet 사용, 응답 캐싱, 이미지 재활용, 비용 모니터링 |
| OpenClaw 업데이트로 호환성 깨짐 | 중간 | 특정 버전 고정, 핵심 코드는 자체 서비스에 분리 |
| 경쟁 서비스 출현 | 낮음 | 캐릭터 차별화, 대화 품질 우위 유지 |

---

## 13. 결론

### 기술적 타당성: 가능 (검증 완료)

- OpenClaw이 WhatsApp 메시징 + LLM 대화 + 미디어 전송 인프라를 **이미 제공**
- Clawra가 fal.ai 이미지 생성 파이프라인을 **이미 구현**
- 추가 개발 범위: DB, 스케줄러, 결제 시스템, 페르소나 튜닝
- OpenClaw 소스 분석으로 정확한 API/설정 구조 확인 완료

### 사업적 타당성: 유망

- MVP 유저당 원가 ~$0.86 대비 구독료 $9.99~14.99로 높은 마진율 (87~94%)
- WhatsApp 기반으로 별도 앱 설치 불필요, 진입장벽 낮음
- 중남미 시장 타겟 시 K-콘텐츠 수요와 결합 가능

### 다음 단계

1. OpenClaw 설치 및 WhatsApp 연결 테스트
2. 한국 남친 캐릭터 컨셉 확정 및 reference image 제작
3. MVP 개발 착수 (Phase 1)
4. 소규모 베타 테스트 (10~50명)

---

## 부록 A: 프로젝트 파일 구조 (현재 + 계획)

```
clawra/
├── _openclaw_src/          # OpenClaw 소스 (참조용, git submodule 가능)
├── bin/
│   └── cli.js              # npx 설치 CLI (기존)
├── skill/
│   ├── SKILL.md            # Clawra 셀카 스킬 정의 (기존)
│   ├── scripts/            # fal.ai 이미지 생성 스크립트 (기존)
│   └── assets/             # Reference image (기존 → 남친 이미지로 교체)
├── templates/
│   └── soul-injection.md   # 페르소나 템플릿 (기존 → 남친용으로 교체)
├── docs/
│   └── cp-001-...review.md # 이 스펙 문서
├── src/                    # [신규] 비즈니스 로직
│   ├── db/                 # DB 스키마, 마이그레이션
│   ├── scheduler/          # 선톡 스케줄러
│   ├── subscription/       # Stripe 결제 연동
│   └── admin/              # 관리자 API
└── workspace/              # [신규] OpenClaw 워크스페이스 파일
    ├── SOUL.md             # 한국 남친 페르소나
    └── IDENTITY.md         # 캐릭터 정보
```

## 부록 B: 빠른 시작 (개발자용)

```bash
# 1. OpenClaw 설치
npm install -g openclaw

# 2. 환경 변수 설정
export ANTHROPIC_API_KEY="sk-ant-..."
export FAL_KEY="fal-..."

# 3. OpenClaw 초기 설정
openclaw doctor

# 4. WhatsApp 연결
openclaw channels login --channel whatsapp
# → QR 코드 스캔

# 5. Clawra 셀카 스킬 설치
npx clawra@latest

# 6. 워크스페이스 파일 배치
cp workspace/SOUL.md ~/.openclaw/workspace/SOUL.md
cp workspace/IDENTITY.md ~/.openclaw/workspace/IDENTITY.md

# 7. openclaw.json 설정 (5.1절 참조)
# → dmPolicy, allowFrom, ackReaction 등 설정

# 8. 게이트웨이 시작
openclaw gateway

# 9. 테스트 메시지 전송
# → WhatsApp에서 봇 번호로 "오빠 뭐해?" 전송
```

---

*문서 끝*
