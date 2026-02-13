# Swift Study Skills

[한국어](#한국어) | [English](#english) | [제작의도](https://velog.io/@kirri1124/Swift-%EB%A9%98%ED%86%A0%EB%A5%BC-Skill%EB%A1%9C-%EB%A7%8C%EB%93%A4%EC%96%B4%EB%B2%84%EB%A6%AC%EA%B8%B0-with-Claude-Code)

---

## 한국어

Swift/iOS를 공부할 때 쓸 수 있는 AI CLI 스킬 3개입니다. Claude Code, Codex CLI, Gemini CLI에서 사용할 수 있습니다. 답을 알려주는 대신 질문을 던져서 스스로 생각하게 만들고, 퀴즈로 복습하고, 공부한 내용을 노트로 정리해줍니다.

### 스킬 목록

#### `/swift-study` - 마스터리 기반 Swift 학습

주제를 말하면 도발적인 코드 스니펫으로 시작합니다. 먼저 예측하고, 맞든 틀리든 그 이유를 파고듭니다. 이해가 검증될 때까지 다음으로 넘어가지 않습니다.

- Mystery Hook: 호기심을 유발하는 코드로 시작, 사전 지식 수준 자동 진단
- Core Loop: 예측(PREDICT) -> 검증(REVEAL) -> 정리(RESTATE) 사이클을 난이도를 올리며 반복
- Gate 시스템: 모호한 답변은 통과시키지 않고, 구체적 메커니즘을 요구
- Anchor: 세션 마지막에 학습자가 직접 규칙 3개를 작성
- 코드 실행 모드: Swift 컴파일러로 실제 실행하거나 AI 설명 중 선택

#### `/swift-quiz` - 적응형 퀴즈 (추론 필수)

5문제짜리 퀴즈. 맞추면 난이도가 올라가고, 틀리면 내려갑니다. 모든 문제에서 "왜?"를 물어봅니다.

- 코드 결과 예측, 에러 찾기, 개념 질문, 코드 작성 등 4가지 유형
- 정답만으로는 부분 점수 -- 근거까지 설명해야 full credit
- 학습 이력에서 misconception을 읽어서 약점 우선 출제
- 결과에 구체적 Gap Analysis + 다음 학습 추천 포함

#### `/study-summary` - 학습 노트 생성

대화에서 공부한 내용을 마크다운 노트로 정리해줍니다.

- 학습자가 직접 쓴 규칙(Anchor)과 실수한 부분을 그대로 포함
- Core Loop의 Seed 코드를 복습용으로 모두 기록
- Memory에 misconception과 gate 통과 여부를 기록해서 다음 세션에 연동
- `notes/` 폴더에 날짜별로 자동 저장

### 설치 방법


#### 방법 3: Skills (전체)(권장)

```bash
npx skills add https://github.com/itlearning/study-ios
```

이후 원하는 스킬 스페이스바로 선택, 설치할 수 있습니다.

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

# 스킬 파일을 프로젝트에 복사
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

설치하면 `/swift-study-skills:swift-study`, `/swift-study-skills:swift-quiz`, `/swift-study-skills:study-summary` 로 사용할 수 있습니다.

### 사용법

AI CLI에서 슬래시 커맨드로 실행하면 됩니다:

```
/swift-study          # 새로운 주제 학습 시작
/swift-quiz           # 퀴즈로 복습
/study-summary        # 오늘 배운 내용 정리
```

### 학습 흐름

```
/swift-study로 새 주제 학습
        |
        v
/swift-quiz로 복습 퀴즈
        |
        v
/study-summary로 노트 정리 및 진도 기록
        |
        v
다음 세션에서 이력 기반 추천으로 이어서 학습
```

### 지원 CLI

| CLI | 스킬 위치 | 프로젝트 지침 |
|-----|----------|-------------|
| [Claude Code](https://claude.ai/claude-code) | `.claude/skills/` | `CLAUDE.md` |
| [Codex CLI](https://github.com/openai/codex) | `.agents/skills/` | `AGENTS.md` |
| [Gemini CLI](https://github.com/google-gemini/gemini-cli) | `.gemini/skills/` | `.gemini/GEMINI.md` |

### 요구 사항

- 위 CLI 중 하나 이상
- Swift 컴파일러 (`swift` 명령어) - 퀴즈의 코드 작성 문제 검증에 사용

### 라이선스

MIT

---

## English

Three AI CLI skills for studying Swift/iOS. Works with Claude Code, Codex CLI, and Gemini CLI. Instead of giving you answers, they ask questions so you work things out yourself. There's also a quiz and a note-taking tool.

### Skills

#### `/swift-study` - Mastery-based Swift learning

Tell it what you want to learn. It starts with a provocative code snippet. You predict first, then dig into why. It won't advance until your understanding is verified.

- Mystery Hook: starts with curiosity-inducing code, auto-diagnoses your level
- Core Loop: PREDICT -> REVEAL -> RESTATE cycle, difficulty increases each round
- Gate system: vague answers don't pass -- you must explain the mechanism
- Anchor: you write 3 rules in your own words at the end of each session
- Code execution mode: run code with Swift compiler or get AI explanations

#### `/swift-quiz` - Adaptive quiz (reasoning required)

5 questions. Get one right, difficulty goes up. Get one wrong, it goes down. Every question asks WHY.

- Predict output, find bugs, answer concept questions, or write code
- Correct answer alone is partial credit -- explain your reasoning for full credit
- Reads your study history to prioritize weak spots (misconception-driven)
- Results include specific gap analysis + next study recommendation

#### `/study-summary` - Learning notes

Turns your study conversation into a markdown note.

- Includes your own Anchor rules and mistakes exactly as you wrote them
- Records all Seed codes from Core Loop cycles for later review
- Tracks misconceptions and gate results in Memory for cross-session continuity
- Auto-saved to `notes/` folder by date

### Installation


#### Option 1: Skills (ALL)(Recommend)

```bash
npx skills add https://github.com/itlearning/study-ios
```

After that, you can select and install the desired skill using the spacebar.

#### Option 2: Plugin marketplace (Claude Code)

```bash
# Add the marketplace in Claude Code
/plugin marketplace add itlearning/study-ios

# Install the plugin
/plugin install swift-study-skills@study-ios
```

#### Option 3: Manual copy

```bash
# Clone the repo
git clone https://github.com/itlearning/study-ios.git

# Copy skill files to your project
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

After that, skills are available as `/swift-study-skills:swift-study`, `/swift-study-skills:swift-quiz`, `/swift-study-skills:study-summary`.

### Usage

Run slash commands in your AI CLI:

```
/swift-study          # Start learning a new topic
/swift-quiz           # Review with a quiz
/study-summary        # Save today's learning notes
```

### Study flow

```
Learn a new topic with /swift-study
        |
        v
Review with /swift-quiz
        |
        v
Save notes with /study-summary
        |
        v
Next session picks up with history-based recommendations
```

### Supported CLIs

| CLI | Skills location | Project instructions |
|-----|----------------|---------------------|
| [Claude Code](https://claude.ai/claude-code) | `.claude/skills/` | `CLAUDE.md` |
| [Codex CLI](https://github.com/openai/codex) | `.agents/skills/` | `AGENTS.md` |
| [Gemini CLI](https://github.com/google-gemini/gemini-cli) | `.gemini/skills/` | `.gemini/GEMINI.md` |

### Requirements

- One or more of the CLIs above
- Swift compiler (`swift` command) -- the quiz uses it to check your code

### License

MIT
