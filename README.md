# Swift Study Skills for Claude Code

[한국어](#한국어) | [English](#english) | [제작의도](https://velog.io/@kirri1124/Swift-%EB%A9%98%ED%86%A0%EB%A5%BC-Skill%EB%A1%9C-%EB%A7%8C%EB%93%A4%EC%96%B4%EB%B2%84%EB%A6%AC%EA%B8%B0-with-Claude-Code)

---

## 한국어

Swift/iOS를 공부할 때 쓸 수 있는 Claude Code 스킬 3개입니다. 답을 알려주는 대신 질문을 던져서 스스로 생각하게 만들고, 퀴즈로 복습하고, 공부한 내용을 노트로 정리해줍니다.

### 스킬 목록

#### `/swift-study` - 대화형 Swift 학습

주제를 말하면 핵심 개념을 하나씩 짚어가며 가르칩니다. 답을 바로 알려주는 게 아니라 질문을 던져서 스스로 생각하게 만드는 방식입니다.

- 주제를 직접 입력하거나 학습 이력 기반 추천을 받을 수 있음
- 개념 설명 후 서술형 질문으로 이해도 확인
- 틀리면 힌트를 주고 다시 생각하게 유도
- 맞으면 바로 심화 내용으로 연결

#### `/swift-quiz` - 적응형 퀴즈

5문제짜리 퀴즈를 풀 수 있습니다. 맞추면 난이도가 올라가고, 틀리면 내려갑니다.

- 코드 결과 예측, 에러 찾기, 개념 질문, 코드 작성 등 4가지 유형
- 서술형 중심이라 직접 생각하고 답을 써야 함
- 코드 작성 문제는 Swift 컴파일러로 실제 검증
- 끝나면 강점/약점 분석과 다음 학습 추천

#### `/study-summary` - 학습 노트 생성

대화에서 공부한 내용을 마크다운 노트로 정리해줍니다.

- 핵심 개념, 코드 예제, 복습 질문을 포함한 구조화된 노트
- `notes/` 폴더에 날짜별로 자동 저장
- 학습 진도를 메모리에 기록해서 다음 세션에 이어서 공부 가능

### 설치 방법

#### 방법 1: 직접 복사

```bash
# 저장소 클론
git clone https://github.com/YOUR_USERNAME/study-ios.git

# 스킬 파일을 프로젝트의 .claude/skills/ 에 복사
cp -r study-ios/skills/swift-study YOUR_PROJECT/.claude/skills/
cp -r study-ios/skills/swift-quiz YOUR_PROJECT/.claude/skills/
cp -r study-ios/skills/study-summary YOUR_PROJECT/.claude/skills/
```

#### 방법 2: Plugin Marketplace (권장)

```bash
# Claude Code에서 마켓플레이스 추가
/plugin marketplace add YOUR_USERNAME/study-ios

# 플러그인 설치
/plugin install swift-study-skills@study-ios
```

설치하면 `/swift-study-skills:swift-study`, `/swift-study-skills:swift-quiz`, `/swift-study-skills:study-summary` 로 사용할 수 있습니다.

### 방법 3: Skills 

```bash
npx skills add https://github.com/itlearning/study-ios 
```

이후 원하는 스킬 스페이스바로 선택, 설치할 수 있습니다.

### 사용법

Claude Code에서 슬래시 커맨드로 실행하면 됩니다:

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

### 요구 사항

- [Claude Code](https://claude.ai/claude-code) CLI
- Swift 컴파일러 (`swift` 명령어) - 퀴즈의 코드 작성 문제 검증에 사용

### 라이선스

MIT

---

## English

Three Claude Code skills for studying Swift/iOS. Instead of giving you answers, they ask questions so you work things out yourself. There's also a quiz and a note-taking tool.

### Skills

#### `/swift-study` - Interactive Swift learning

Tell it what you want to learn. It walks you through concepts one at a time, asking questions instead of lecturing.

- Enter a topic directly or get recommendations based on your study history
- After each explanation, you answer open-ended questions to check understanding
- Wrong answers get hints, not immediate corrections
- Right answers lead straight into deeper material

#### `/swift-quiz` - Adaptive quiz

5 questions. Get one right, difficulty goes up. Get one wrong, it goes down.

- Predict output, find bugs, answer concept questions, or write code
- Mostly open-ended -- you have to think through your answers
- Code-writing questions get verified by the actual Swift compiler
- Results tell you what you're good at and what to review next

#### `/study-summary` - Learning notes

Turns your study conversation into a markdown note.

- Key concepts, code examples, and review questions in one file
- Auto-saved to `notes/` folder by date
- Tracks your progress in memory so you can pick up where you left off

### Installation

#### Option 1: Manual copy

```bash
# Clone the repo
git clone https://github.com/YOUR_USERNAME/study-ios.git

# Copy skill files to your project's .claude/skills/
cp -r study-ios/skills/swift-study YOUR_PROJECT/.claude/skills/
cp -r study-ios/skills/swift-quiz YOUR_PROJECT/.claude/skills/
cp -r study-ios/skills/study-summary YOUR_PROJECT/.claude/skills/
```

#### Option 2: Plugin marketplace (recommended)

```bash
# Add the marketplace in Claude Code
/plugin marketplace add YOUR_USERNAME/study-ios

# Install the plugin
/plugin install swift-study-skills@study-ios
```

After that, skills are available as `/swift-study-skills:swift-study`, `/swift-study-skills:swift-quiz`, `/swift-study-skills:study-summary`.

### Option 2: Skills 

```bash
npx skills add https://github.com/itlearning/study-ios 
```

After that, you can select and install the desired skill using the spacebar.

### Usage

Run slash commands in Claude Code:

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

### Requirements

- [Claude Code](https://claude.ai/claude-code) CLI
- Swift compiler (`swift` command) -- the quiz uses it to check your code

### License

MIT
