# D'CENT 콘텐츠 마케팅 팀

Claude Code 기반의 블로그 콘텐츠 자동 생성 시스템입니다. AI 에이전트가 리서치부터 글 작성, 이미지 생성, Shopify HTML 변환까지 전 과정을 자동화합니다.

## 주요 기능

| 기능 | 설명 |
|------|------|
| 🎯 콘텐츠 기획 | SEO 키워드 전략, 콘텐츠 구조 설계 |
| ✍️ 블로그 작성 | 브랜드 톤에 맞는 다국어(EN/JP/KO) 콘텐츠 |
| 🎨 이미지 생성 | Dzine AI로 썸네일, 섹션 이미지, 카드뉴스 |
| 🖼️ 썸네일 자동화 | Figma 템플릿 기반 썸네일 자동 생성 |
| 📦 HTML 변환 | Shopify 블로그용 HTML 자동 생성 |
| ✅ 품질 검수 | 팩트체크, SEO 점검, 브랜드 가이드 준수 확인 |

---

## 빠른 시작 (Quick Start)

> 🆕 **처음이신가요?** 개발 경험이 없다면 [비개발자용 가이드](docs/ONBOARDING.md)를 먼저 읽어보세요!

### 1단계: 사전 요구사항

| 항목 | 필수 | 설명 |
|------|------|------|
| Claude Code | ✅ | [설치 가이드](https://docs.anthropic.com/en/docs/claude-code) |
| Anthropic 계정 | ✅ | Pro/Max 구독 또는 API 키 |
| Node.js | ✅ | v18 이상 |
| Dzine API 키 | ⬜ | 이미지 생성용 - [발급하기](https://www.dzine.ai/api/) |
| Figma 데스크톱 | ⬜ | 썸네일 자동화용 |

### 2단계: 설치

```bash
# 1. 저장소 클론
git clone https://github.com/dcent-mkt/content-multiagent.git
cd content-multiagent

# 2. Dzine MCP 서버 설치
cd dzine-mcp && npm install && cd ..

# 3. 썸네일 서버 설치 (선택사항)
cd thumbnail-server && npm install && cd ..

# 4. MCP 설정 파일 생성
cp .claude/settings.example.json .claude/settings.json
```

### 3단계: API 키 설정

`.claude/settings.json` 파일을 열어 경로와 API 키를 수정하세요:

```json
{
  "mcpServers": {
    "dzine": {
      "command": "node",
      "args": ["/YOUR/PATH/TO/content-marketing-team/dzine-mcp/index.js"],
      "env": {
        "DZINE_API_KEY": "YOUR_DZINE_API_KEY_HERE"
      }
    }
  }
}
```

> ⚠️ **중요**: `settings.json`은 `.gitignore`에 포함되어 Git에 업로드되지 않습니다.

### 4단계: 실행

```bash
# Claude Code 실행
claude

# 콘텐츠 제작 시작
@planner
```

---

## 프로젝트 구조

```
content-marketing-team/
├── CLAUDE.md                  # Claude Code 프로젝트 설정
├── .claude/
│   ├── agents/                # AI 에이전트 정의
│   │   ├── planner.md         # 🎯 콘텐츠 기획 (메인)
│   │   ├── blog.md            # ✍️ 블로그 작성
│   │   ├── newsletter.md      # 📧 뉴스레터 작성
│   │   ├── reviewer.md        # ✅ 품질 검수
│   │   └── help.md            # ❓ 도움말
│   ├── skills/                # 스킬 정의
│   │   ├── figma-thumbnail.md # 🖼️ Figma 썸네일 생성
│   │   ├── section-images.md  # 🎨 섹션 이미지 생성
│   │   ├── card-news.md       # 📱 카드뉴스 생성
│   │   └── shopify-html.md    # 📦 Shopify HTML 변환
│   └── settings.example.json  # MCP 설정 템플릿
├── dzine-mcp/                 # Dzine AI MCP 서버
├── thumbnail-server/          # Figma 썸네일 WebSocket 서버
├── figma-plugin/              # Figma 플러그인
├── guide/                     # 콘텐츠 가이드
│   ├── Brand_Tone_Rules.md    # 브랜드 톤 & 보이스
│   ├── SEO_Playbook_2026.md   # SEO 가이드
│   ├── Image_Style_Guide.md   # 이미지 스타일 가이드
│   └── Feedback_Log.md        # 피드백 기록
├── resource/                  # 참고 자료
└── output/                    # 생성된 콘텐츠 출력
```

---

## 사용법

### 기본 명령어

```bash
# Claude Code 실행 후:

@planner              # 콘텐츠 제작 시작 (권장)
@help                 # 도움말 보기

# 자연어로도 가능:
"콘텐츠 만들어보자"
"블로그 쓰자"
```

### 워크플로우

```
1. @planner        → 주제 선정, 키워드 전략, 브리프 작성
2. @blog           → 블로그 콘텐츠 작성 (EN/JP/KO)
3. /section-images → 섹션별 이미지 생성
4. /figma-thumbnail → 썸네일 자동 생성
5. /shopify-html   → Shopify HTML 변환
6. @reviewer       → 품질 검수 및 최종 확인
```

### 입력 양식 (간소화)

```
목적: (교육 / 비교&분석 / 제품소개&구매제안)
목표: (교육 / 판매 / 브랜딩 / 리드)
독자 레벨: (초급 / 중급 / 고급)
톤&매너: (교육적이고 친절한 / 간결하고 실용적 / 등)
주제: [콘텐츠 주제]
제작 언어: (EN+JP / EN만 / JP만 / 번역 없음)
```

---

## 선택 기능 설정

### Dzine AI (이미지 생성)

Dzine MCP가 제공하는 도구:

| 도구 | 설명 |
|------|------|
| `dzine_generate_image` | 텍스트 → 이미지 생성 |
| `dzine_edit_image` | 기존 이미지 스타일 변환 |
| `dzine_get_styles` | 사용 가능한 스타일 목록 |
| `dzine_upscale` | 이미지 해상도 업스케일 |
| `dzine_get_balance` | 토큰 잔액 확인 |

### Figma 썸네일 자동화

Figma 템플릿 기반으로 썸네일을 자동 생성합니다.

#### 설정 방법

**1. 썸네일 서버 실행**
```bash
cd thumbnail-server
npm install  # 최초 1회
node server.js
# → http://localhost:3847 에서 실행
```

**2. Figma 플러그인 설치**
1. Figma 데스크톱 앱 열기
2. Plugins → Development → Import plugin from manifest...
3. `figma-plugin/manifest.json` 선택
4. 플러그인 실행: Plugins → Development → D'CENT Thumbnail Generator
5. 플러그인 UI에서 "서버 연결됨" (녹색) 확인

**3. 사용**
```bash
# Claude Code에서:
/figma-thumbnail
- 블로그 제목: [제목]
- 핵심 메시지: [한 줄 요약]
```

#### 서버 엔드포인트

| 엔드포인트 | 메서드 | 설명 |
|-----------|--------|------|
| `/thumbnail` | POST | 썸네일 생성 요청 |
| `/status` | GET | 서버 상태 확인 |
| `/clients` | GET | 연결된 플러그인 수 |

---

## 가이드 문서

| 문서 | 설명 |
|------|------|
| [Brand_Tone_Rules.md](guide/Brand_Tone_Rules.md) | 브랜드 톤, 금지/권장 표현 |
| [SEO_Playbook_2026.md](guide/SEO_Playbook_2026.md) | SEO 구조, FAQ 설계, E-E-A-T |
| [Image_Style_Guide.md](guide/Image_Style_Guide.md) | 이미지 스타일, 프롬프트 가이드 |
| [Feedback_Log.md](guide/Feedback_Log.md) | 누적 피드백 및 적용 규칙 |

---

## 트러블슈팅

### Claude Code 관련

| 문제 | 해결 방법 |
|------|----------|
| MCP 도구가 안 보임 | `settings.json` 경로 확인, Claude Code 재시작 |
| 에이전트 호출 실패 | `.claude/agents/` 폴더 존재 확인 |

### Dzine MCP 관련

| 문제 | 해결 방법 |
|------|----------|
| API 키 오류 | `settings.json`의 `DZINE_API_KEY` 확인 |
| 이미지 생성 실패 | `dzine_get_balance`로 토큰 잔액 확인 |

### 썸네일 서버 관련

| 문제 | 해결 방법 |
|------|----------|
| `ECONNREFUSED` | `node server.js`로 서버 실행 |
| `No Figma Plugin connected` | Figma에서 플러그인 열기 |
| `Request timeout` | 플러그인 재시작 |

---

## 커스터마이징

### 브랜드 가이드 수정

`guide/Brand_Tone_Rules.md` 파일을 수정하여 브랜드 톤과 금지/권장 표현을 변경할 수 있습니다.

### 에이전트/스킬 추가

`.claude/agents/` 또는 `.claude/skills/` 폴더에 마크다운 파일을 추가하면 새로운 에이전트/스킬을 만들 수 있습니다.

### 출력 구조 변경

`planner.md`의 "파일 네이밍 규칙" 섹션을 수정하여 출력 폴더 구조를 변경할 수 있습니다.

---

## 보안 주의사항

- ⚠️ `settings.json`에 API 키가 포함되므로 **절대 Git에 커밋하지 마세요**
- ⚠️ `.gitignore`가 설정되어 있지만, 커밋 전 항상 확인하세요
- ⚠️ 민감한 정보가 포함된 `output/` 폴더는 필요시 `.gitignore`에 추가하세요

---

## 라이선스

이 프로젝트는 내부 사용 목적으로 제작되었습니다.

---

## 기여 및 피드백

피드백이 있으면 Claude Code에서 다음과 같이 말씀해주세요:

```
"아래 피드백을 앞으로 반영해줘"
[피드백 내용]
```

피드백은 `guide/Feedback_Log.md`에 자동으로 기록되고 이후 콘텐츠 제작에 반영됩니다.
