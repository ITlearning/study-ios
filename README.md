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

#### `/swift-study` - 마스터리 기반 학습

한 주제를 깊게 다룹니다. 먼저 코드를 보고 예측한 뒤, 왜 그런지 설명하고 다시 본인 말로 정리합니다.

- Mystery Hook으로 시작해서 현재 이해 수준을 빠르게 진단
- Core Loop(PREDICT -> REVEAL -> RESTATE) 반복
- 모호한 답변은 gate를 통과하지 못하고, 근거를 요구
- 세션 끝에 Anchor 규칙 3개를 직접 작성
- 실행 모드 선택 가능: Swift 컴파일러 실행 또는 설명 모드

#### `/swift-quiz` - 적응형 퀴즈

총 5문제입니다. 정답 여부뿐 아니라 근거 설명까지 보고 난이도를 조정합니다.

- 출력 예측, 버그 찾기, 개념 질문, 코드 작성 문제 포함
- 정답만 맞추면 부분 점수 처리, 이유까지 설명하면 full credit
- 최근 학습 이력의 misconception을 우선적으로 점검
- 결과에 Gap Analysis와 다음 학습 추천 제공

#### `/study-summary` - 학습 노트 저장

세션 내용을 `notes/`에 Markdown 파일로 저장합니다.

- Anchor에서 작성한 규칙과 헷갈린 포인트를 그대로 보존
- Core Loop에서 사용한 seed 코드를 복습용으로 정리
- 학습 진도와 취약 지점을 다음 세션에서 다시 활용 가능하도록 기록

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

#### `/swift-study` - Mastery-based study

This skill goes deep on one topic at a time. You predict first, then explain why, then restate in your own words.

- Starts with a Mystery Hook to quickly diagnose your level
- Repeats a Core Loop: PREDICT -> REVEAL -> RESTATE
- Uses a gate so vague answers do not pass
- Ends with 3 Anchor rules written by the learner
- Supports run mode selection: real Swift execution or explanation mode

#### `/swift-quiz` - Adaptive quiz

Five questions per session. Difficulty changes based on both correctness and reasoning quality.

- Includes output prediction, bug finding, concept checks, and coding tasks
- Correct answer without reasoning gets partial credit
- Prioritizes recent misconceptions from study history
- Returns a concrete gap analysis and next-study suggestion

#### `/study-summary` - Save learning notes

This skill saves the session as a Markdown note in `notes/`.

- Preserves learner-written Anchor rules and confusion points
- Stores Core Loop seed code for later review
- Records progress so future sessions can target weak areas

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

### License

MIT
