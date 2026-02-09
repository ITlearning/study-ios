# swift-quiz - Swift/iOS 퀴즈

적응형 퀴즈와 코딩 연습을 위한 스킬.

## Instructions

Swift/iOS 퀴즈를 출제한다. 난이도는 학습자 수준에 맞게 자동 조절한다.

### Step 0: Language Selection

스킬 시작 시 AskUserQuestion으로 언어를 선택한다:

```
questions:
  - question: "Which language do you prefer? / 어떤 언어로 진행할까요?"
    header: "Language"
    options:
      - label: "한국어"
        description: "한국어로 퀴즈를 풉니다"
      - label: "English"
        description: "Take the quiz in English"
    multiSelect: false
```

선택한 언어로 이후 모든 소통을 진행한다. 코드와 Swift 키워드는 어떤 언어를 선택하든 영어 그대로 유지한다.

### Step 1: 퀴즈 주제 선택

**한국어 선택 시:**
"어떤 주제로 퀴즈를 풀까요? 주제를 알려주세요. 뭘 할지 모르겠으면 '추천해줘'라고 해주세요."

**English 선택 시:**
"What topic should the quiz cover? Tell me a topic, or say 'recommend' if you're not sure."

- **유저가 주제를 입력한 경우**: 해당 주제로 바로 퀴즈 시작
- **"추천해줘"라고 한 경우**: 학습 이력(memory의 SwiftLearningProgress)을 참고하여 최근 학습한 주제 중심으로 3-4개 추천. AskUserQuestion으로 선택지 제시.

### Step 2: 퀴즈 진행 (5문제)

총 5문제를 출제한다. 내부적으로 난이도를 1~5로 추적한다 (시작: 3).
- 정답 -> 난이도 +1
- 오답 -> 난이도 -1

### 문제 유형

각 문제는 아래 유형 중 하나로 출제. **서술형을 기본으로 하되, 적절히 섞는다.**

#### Type A: 코드 결과 예측 (서술형)
```
다음 코드의 출력 결과는? 답과 이유를 함께 적어주세요.

var nums = [1, 2, 3]
var copy = nums
copy.append(4)
print(nums.count)
```
유저가 직접 답을 타이핑한다.

#### Type B: 에러 찾기 (서술형)
```
다음 코드에서 문제가 되는 부분은? 왜 에러가 나는지 설명해주세요.

let name: String = "Swift"
name = "SwiftUI"
print(name)
```
유저가 직접 답을 타이핑한다.

#### Type C: 개념 질문 (객관식 허용)
```
Swift에서 struct 인스턴스의 프로퍼티를 메서드 안에서 변경하려면 어떤 키워드가 필요할까요?
```
AskUserQuestion으로 4지선다 제시. 개념 확인용 문제는 객관식도 괜찮다.

#### Type D: 코드 작성 (난이도 4 이상)
```
다음 조건을 만족하는 함수를 작성하세요:
- 함수명: isEven
- Int를 받아서 Bool을 반환
- 짝수면 true, 홀수면 false
```
사용자가 코드를 작성하면 Task 도구로 서브에이전트를 활용하여 Swift 컴파일러로 검증한다.
서브에이전트 사용 시 `subagent_type: "Bash"`를 사용하고, swift 명령어로 코드를 실행하여 결과를 확인한다.

### 피드백 규칙

**정답일 때:**
```
정답입니다!

핵심 포인트: Array는 값 타입(Value Type)이라서 copy는 독립적인 복사본입니다.
따라서 nums.count는 여전히 3입니다.
```

**오답일 때:**
간결한 텍스트 해설을 제공한다. ASCII 다이어그램은 메모리 구조 등 텍스트만으로 설명하기 어려운 경우에만 사용한다.
```
아쉽지만 틀렸습니다. 정답은 "3"입니다.

Array는 struct(값 타입)이므로 `var copy = nums`는 독립적인 복사본을 만듭니다.
copy에 append해도 원본 nums에는 영향이 없습니다.
```

### Step 3: 결과 요약

5문제 완료 후 결과 요약:

```
퀴즈 결과
- 주제: 기본 문법
- 정답: 3/5
- 최종 난이도: 4/5
- 강점: 옵셔널 처리, 타입 시스템
- 보완 필요: 값 타입 vs 참조 타입
- 추천: /swift-study로 "값 타입 vs 참조 타입" 복습하기
```

### 규칙

1. **선택한 언어로 소통** - Step 0에서 선택한 언어를 사용. 코드와 키워드만 영어
2. **한 번에 한 문제만** - 다음 문제는 현재 문제 해결 후
3. **서술형 중심** - 유저가 직접 생각하고 답을 써야 학습이 됨. 개념 확인용은 객관식 가능
4. **ASCII 다이어그램은 필요할 때만** - 기본은 텍스트 해설
5. **난이도 적응** - 학습자 수준에 맞게 자동 조절
6. **격려하는 톤** - 틀려도 배움의 기회로
7. **이모지 사용 금지** - 깔끔한 텍스트만 사용
