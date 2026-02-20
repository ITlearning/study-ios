# Swift Study Skills

[한국어](#한국어) | [English](#english) | [제작의도](https://velog.io/@kirri1124/Swift-%EB%A9%98%ED%86%A0%EB%A5%BC-Skill%EB%A1%9C-%EB%A7%8C%EB%93%A4%EC%96%B4%EB%B2%84%EB%A6%AC%EA%B8%B0-with-Claude-Code)

---

## 한국어

Swift/iOS 공부할 때 바로 가져다 쓸 수 있는 CLI 스킬 3개입니다.
Claude Code, Codex CLI, Gemini CLI에서 같은 흐름으로 사용할 수 있습니다.

핵심은 단순합니다.
- 바로 답을 주기보다 먼저 생각하게 만들고
- 퀴즈로 확인하고
- 마지막에 노트로 남겨서 다음 학습으로 이어갑니다

### 스킬 목록

#### `/swift-study` - Classic + Mastery 학습

학습 스타일을 고를 수 있습니다.

- Classic: 설명을 먼저 듣고 질문으로 이해를 확인하는 방식 (처음 배우는 주제에 추천)
- Mastery: 예측 -> 검증 -> 재진술 루프를 반복하는 훈련 방식 (실전 대비에 추천)
- 모드 선택 문구에 각 모드의 용도와 난이도를 함께 안내
- 용어는 한국어 우선으로 설명하고, 필요할 때 영어를 괄호로 병기
- `격리 경계(isolation boundary)`처럼 낯선 표현은 바로 한 줄 설명을 붙여 이해를 돕는 방식
- 실행 모드 선택 가능: Swift 컴파일러 실행 또는 설명 모드

#### `/swift-quiz` - 적응형 퀴즈

Classic/Mastery 모드를 선택해서 퀴즈를 진행합니다.

- Classic: 빠른 점검 중심, 근거 설명은 권장
- Mastery: 정답 + 이유(WHY) 검증, 근거 품질까지 반영
- 출력 예측, 버그 찾기, 개념 질문, 코드 작성 문제 포함
- 최근 학습 이력의 오해 포인트를 우선적으로 점검
- 결과에 보완 포인트 분석과 다음 학습 추천 제공
- 해설에서도 기술 용어를 처음 쓸 때 짧은 쉬운 설명을 함께 제공

#### `/study-summary` - 학습 노트 저장

세션 내용을 `notes/`에 Markdown 파일로 저장합니다.

- Classic: 핵심 개념 위주로 간결하게 정리
- Mastery: 규칙/혼동 포인트/seed 코드까지 상세 기록
- 학습 진도와 취약 지점을 다음 세션에서 다시 활용 가능하도록 기록
- 노트 안에서도 용어를 한국어 우선으로 쓰고, 필요한 영어 용어는 괄호로 병기

### 설치 방법

#### 방법 1: Skills로 설치 (권장)

```bash
npx skills add https://github.com/itlearning/study-ios
```

설치 후 원하는 스킬을 선택해서 추가하면 됩니다.

#### 방법 2: Plugin Marketplace (Claude Code)

```bash
# Claude Code에서 마켓플레이스 추가
/plugin marketplace add itlearning/study-ios

# 플러그인 설치
/plugin install swift-study-skills@study-ios
```

#### 방법 3: 직접 복사

```bash
# 저장소 클론
git clone https://github.com/itlearning/study-ios.git

# Claude Code
cp -r study-ios/.agents/skills/swift-study YOUR_PROJECT/.claude/skills/
cp -r study-ios/.agents/skills/swift-quiz YOUR_PROJECT/.claude/skills/
cp -r study-ios/.agents/skills/study-summary YOUR_PROJECT/.claude/skills/

# Codex CLI
cp -r study-ios/.agents/skills/swift-study YOUR_PROJECT/.agents/skills/
cp -r study-ios/.agents/skills/swift-quiz YOUR_PROJECT/.agents/skills/
cp -r study-ios/.agents/skills/study-summary YOUR_PROJECT/.agents/skills/

# Gemini CLI
cp -r study-ios/.agents/skills/swift-study YOUR_PROJECT/.gemini/skills/
cp -r study-ios/.agents/skills/swift-quiz YOUR_PROJECT/.gemini/skills/
cp -r study-ios/.agents/skills/study-summary YOUR_PROJECT/.gemini/skills/
```

설치 후 다음 명령으로 실행할 수 있습니다.

- `/swift-study-skills:swift-study`
- `/swift-study-skills:swift-quiz`
- `/swift-study-skills:study-summary`

### 사용법

AI CLI에서 슬래시 커맨드로 실행합니다.

```bash
/swift-study          # 새로운 주제 학습 시작
/swift-quiz           # 퀴즈로 복습
/study-summary        # 오늘 배운 내용 정리
```

### 권장 학습 흐름

```text
/swift-study로 학습
        |
        v
/swift-quiz로 점검
        |
        v
/study-summary로 정리
        |
        v
다음 세션에서 이전 기록 기반으로 이어서 학습
```

### 지원 CLI

| CLI | 스킬 위치 | 프로젝트 지침 |
|-----|-----------|---------------|
| [Claude Code](https://claude.ai/claude-code) | `.claude/skills/` | `CLAUDE.md` |
| [Codex CLI](https://github.com/openai/codex) | `.agents/skills/` | `AGENTS.md` |
| [Gemini CLI](https://github.com/google-gemini/gemini-cli) | `.gemini/skills/` | `.gemini/GEMINI.md` |

### 요구 사항

- 위 CLI 중 하나 이상
- Swift 컴파일러 (`swift` 명령)

### 라이선스

MIT

---

## English

Three CLI skills for studying Swift and iOS.
They work with Claude Code, Codex CLI, and Gemini CLI.

The workflow is straightforward.
- Think first instead of getting instant answers
- Check understanding with a quiz
- Save what you learned so the next session starts with context

### Skills

#### `/swift-study` - Classic + Mastery study

You can choose the learning style per session.

- Classic: explanation-first flow with question checks (recommended for new topics)
- Mastery: prediction -> reveal -> restate loop with gate checks (recommended for practice)
- Mode prompts include plain-language guidance on who each mode is for
- Learner-facing wording uses plain terms first, with technical terms in parentheses when helpful
- New technical terms are followed by a short one-line explanation
- Supports run mode selection: real Swift execution or explanation mode

#### `/swift-quiz` - Adaptive quiz

You can run the quiz in Classic or Mastery mode.

- Classic: fast review, lighter reasoning requirements
- Mastery: verifies both answer and WHY, and uses reasoning quality in scoring
- Includes output prediction, bug finding, concept checks, and coding tasks
- Correct answer without reasoning gets partial credit
- Prioritizes recent weak points from study history
- Returns a concrete gap analysis and next-study suggestion
- Explanations include short plain-language glosses for unfamiliar technical terms

#### `/study-summary` - Save learning notes

This skill saves the session as a Markdown note in `notes/`.

- Classic: concise recap focused on core points
- Mastery: detailed notes with rules, confusion points, and seed code history
- Records progress so future sessions can target weak areas
- Notes use plain wording first and add technical terms only when helpful

### Installation

#### Option 1: Install with Skills (recommended)

```bash
npx skills add https://github.com/itlearning/study-ios
```

Then choose and install the skills you want.

#### Option 2: Plugin Marketplace (Claude Code)

```bash
# Add the marketplace in Claude Code
/plugin marketplace add itlearning/study-ios

# Install the plugin
/plugin install swift-study-skills@study-ios
```

#### Option 3: Manual copy

```bash
# Clone the repository
git clone https://github.com/itlearning/study-ios.git

# Claude Code
cp -r study-ios/.agents/skills/swift-study YOUR_PROJECT/.claude/skills/
cp -r study-ios/.agents/skills/swift-quiz YOUR_PROJECT/.claude/skills/
cp -r study-ios/.agents/skills/study-summary YOUR_PROJECT/.claude/skills/

# Codex CLI
cp -r study-ios/.agents/skills/swift-study YOUR_PROJECT/.agents/skills/
cp -r study-ios/.agents/skills/swift-quiz YOUR_PROJECT/.agents/skills/
cp -r study-ios/.agents/skills/study-summary YOUR_PROJECT/.agents/skills/

# Gemini CLI
cp -r study-ios/.agents/skills/swift-study YOUR_PROJECT/.gemini/skills/
cp -r study-ios/.agents/skills/swift-quiz YOUR_PROJECT/.gemini/skills/
cp -r study-ios/.agents/skills/study-summary YOUR_PROJECT/.gemini/skills/
```

After installation, you can run:

- `/swift-study-skills:swift-study`
- `/swift-study-skills:swift-quiz`
- `/swift-study-skills:study-summary`

### Usage

Run slash commands in your AI CLI.

```bash
/swift-study          # Start a new topic
/swift-quiz           # Review with a quiz
/study-summary        # Save learning notes
```

### Suggested flow

```text
Learn with /swift-study
        |
        v
Review with /swift-quiz
        |
        v
Save notes with /study-summary
        |
        v
Continue next time with history-based context
```

### Supported CLIs

| CLI | Skills location | Project instructions |
|-----|-----------------|----------------------|
| [Claude Code](https://claude.ai/claude-code) | `.claude/skills/` | `CLAUDE.md` |
| [Codex CLI](https://github.com/openai/codex) | `.agents/skills/` | `AGENTS.md` |
| [Gemini CLI](https://github.com/google-gemini/gemini-cli) | `.gemini/skills/` | `.gemini/GEMINI.md` |

### Requirements

- One or more CLIs above
- Swift compiler (`swift` command)

## 기여하기 (Contributing)

이 프로젝트에 대한 기여를 환영합니다! 버그 리포트, 기능 제안, Pull Request 모두 환영합니다.

Contributions are welcome! Feel free to submit bug reports, feature requests, or pull requests.

### License

MIT
