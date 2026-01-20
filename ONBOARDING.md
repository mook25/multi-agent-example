# 🚀 처음 시작하기 (비개발자용 가이드)

개발 경험이 없어도 괜찮습니다!

---

## ⚡ 원클릭 설치 (권장)

### 준비물
| 항목 | 확인 | 어디서 받나요? |
|------|:----:|--------------|
| Mac 컴퓨터 | ☐ | - |
| Claude Pro/Max 구독 | ☐ | [claude.ai](https://claude.ai) 결제 |
| Dzine API 키 | ☐ | 관리자에게 요청 |

### 설치 방법

**1단계**: 아래 링크에서 설치 파일 다운로드
- 👉 [install.command 다운로드](https://github.com/dcent-mkt/content-multiagent/raw/main/install.command)

**2단계**: 다운로드된 `install.command` 파일 **더블클릭**

> ⚠️ "확인되지 않은 개발자" 경고가 나오면:
> - `Control + 클릭` → "열기" 선택
> - 또는: 시스템 설정 → 개인정보 보호 및 보안 → "확인 없이 열기" 클릭

**3단계**: 화면 안내에 따라 진행
- Node.js 없으면 → 자동으로 다운로드 페이지 열림
- API 키 입력 요청 → 붙여넣기
- 완료!

**4단계**: VSCode에서 Claude Code 확장 설치
1. VSCode 실행
2. 왼쪽 **확장 프로그램** 아이콘 클릭 (`Cmd + Shift + X`)
3. **"Claude Code"** 검색 → **Install**

**5단계**: 사용 시작
1. 왼쪽 **Claude 아이콘** 클릭
2. 로그인 후 채팅창에 `@planner` 입력

끝! 🎉

---

## 📝 매일 사용법

1. **VSCode 실행**
2. **File → Open Recent → content-multiagent**
3. **왼쪽 Claude 아이콘** 클릭
4. **채팅창에 입력**: `@planner`

---

## 🔄 업데이트 받기

관리자가 기능을 업데이트하면:

1. VSCode 왼쪽에서 **소스 제어** 아이콘 클릭 (가지 모양)
2. 상단 `...` 메뉴 → **Pull** 클릭

---

## ❓ 문제 해결

### "확인되지 않은 개발자" 경고

`Control + 클릭` → "열기" 선택

### "Node.js가 설치되어 있지 않습니다"

1. https://nodejs.org 접속
2. **LTS** 버전 다운로드 및 설치
3. `install.command` 다시 실행

### "git: command not found"

팝업이 뜨면 "설치" 클릭 후, `install.command` 다시 실행

### Claude Code 확장이 안 보여요

1. VSCode 확장에서 "Claude Code" 검색
2. **Anthropic** 개발자인지 확인 후 설치
3. VSCode 재시작

### MCP 도구가 안 보여요 (Dzine 등)

1. `.claude/settings.json` 파일 열기
2. API 키가 제대로 들어갔는지 확인
3. VSCode 재시작

---

## 🆘 그래도 안 되면?

관리자에게 **화면 캡처**와 함께 연락하세요!

---

## 📖 수동 설치 (참고용)

원클릭 설치가 안 되는 경우에만 참고하세요.

<details>
<summary>수동 설치 방법 보기</summary>

### 1. 필수 프로그램 설치

**VSCode 설치:**
1. https://code.visualstudio.com/ 접속
2. **Download for Mac** 클릭
3. 응용 프로그램 폴더로 드래그

**Node.js 설치:**
1. https://nodejs.org 접속
2. **LTS** 버전 다운로드 및 설치

### 2. 프로젝트 다운로드

VSCode 터미널에서 (`Ctrl + \``):

```bash
cd ~/Desktop
git clone https://github.com/dcent-mkt/content-multiagent.git
cd content-multiagent/dzine-mcp && npm install && cd ..
```

### 3. API 키 설정

```bash
cp .claude/settings.example.json .claude/settings.json
```

`.claude/settings.json` 파일 열어서:
- `/YOUR/PATH/TO/...` → `/Users/본인사용자명/Desktop/content-multiagent/dzine-mcp/index.js`
- `YOUR_DZINE_API_KEY_HERE` → 실제 API 키

### 4. Claude Code 확장 설치

VSCode → 확장 → "Claude Code" 검색 → Install

</details>

---

*마지막 업데이트: 2025-01*
