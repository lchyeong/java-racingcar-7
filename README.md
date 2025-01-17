## **자동차 경주**

**작성자 :** 이찬형  
**프로젝트** : 우아한 테크코스 프리코스 7기 - 2주차 과제
&nbsp;

## 📋 목차

- [📌 프로젝트 소개](#-프로젝트-소개)
- [📂 프로젝트 구조](#-프로젝트-구조)
- [🚀 기능](#-기능)
- [🖥️ 입출력 예시](#-입출력-예시)
    - [입력](#입력)
    - [출력](#출력)
    - [실행 결과 예시](#실행-결과-예시)
- [🚨 예외 사항](#-예외-사항)
    - [자동차 이름 입력 오류](#자동차-이름-입력-오류)
    - [시도 횟수 입력 오류](#시도-횟수-입력-오류)
- [⭐ 사전 요구 사항](#-사전-요구-사항)
    - [과제 진행 요구 사항](#과제-진행-요구-사항)
    - [프로그래밍 요구 사항1](#프로그래밍-요구-사항-1)
    - [프로그래밍 요구 사항2](#프로그래밍-요구-사항-2)
- [📦 라이브러리 사용 안내](#-라이브러리-사용-안내)
- [🤔 회고](#-회고)

## 📌 **프로젝트 소개**

**자동차들이 경주를 하여 우승자를 가리는 게임 프로젝트입니다.**

![Java Version](https://img.shields.io/badge/Java-21-blue?style=for-the-badge)  
![Gradle](https://img.shields.io/badge/build%20with-Gradle-green?style=for-the-badge)  
&nbsp;

## 📂 **프로젝트 구조**

⚠️ 아래 구조는 지속적으로 수정/보완될 예정입니다!

```
└── src
    ├── main
    │   └── java
    │       └── racingcar
    │           ├── Application.java             # 애플리케이션 진입점
    │           ├── controller
    │           │   └── RacingCarController.java # 사용자 입력 처리 및 게임 흐름제어
    │           ├── exception
    │           │   ├── CustomException.java     # 커스텀 예외 정의(IlligarArgumentException)
    │           │   └── ErrorMessage.java        # 예외 메시지 통합 관리
    │           ├── service
    │           │   └── RacingCarService.java    # 레이싱에 관한 비즈니스 로직
    │           ├── validator
    │           │   ├── CarNamesValidator.java   # 자동차 이름 검증
    │           │   └── TryNumberValidator.java  # 시도 횟수 검증
    │           └── viewer
    │               └── RacingCarViewer.java     # 입력 프롬프트 및 출력 화면 관리
    └── test
        └── java
            └── racingcar
                ├── ApplicationTest.java             # 메인 애플리케이션 테스트
                ├── service
                │   └── RacingCarServiceTest.java    # 서비스 로직 테스트
                ├── validator
                │   ├── CarNamesValidatorTest.java   # 자동차 이름 검증 테스트
                │   └── TryNumberValidatorTest.java  # 시도 횟수 검증 테스트
                └── viewer
                    └── RacingCarViewerTest.java     # 입출력 테스트
├──README.md
├──build.gradle
```

&nbsp;

## 🚀 **기능**

### 입력 처리 및 검증

- **자동차 이름 입력**: 사용자로부터 경주에 참가할 자동차 이름을 입력받습니다.
- **시도 횟수 입력**: 경주를 몇 번 시도할지에 대한 횟수를 입력받습니다.
- **입력값 검증**: 입력된 자동차 이름과 시도 횟수가 유효한지 검증합니다. 잘못된 입력값이 들어오면 오류 메시지를 출력하고 애플리케이션이 종료됩니다.

### 경주 준비

- **자동차 위치 초기화**: 입력받은 자동차 이름을 사용하여 각 자동차의 초기 위치를 초기화 합니다.

### 자동차 이동

- **이동 여부 결정**: 랜덤 숫자를 생성하여 각 자동차가 이동할 수 있는지 여부를 결정합니다. 랜덤 숫자가 4이상일 경우 자동차가 전진합니다.
- **자동차 위치 업데이트**: 이동한 자동차의 위치를 업데이트합니다.

### 라운드 실행

- **라운드별 경주 실행**: 입력된 시도 횟수에 따라 경주를 반복하여 실행합니다. 자동차의 전진 거리는 누적됩니다.
- **라운드 결과 출력**: 각 라운드가 끝날 때마다 각 자동차의 현재 위치를 출력하여 사용자에게 진행 상황을 보여줍니다.

### 우승자 결정

- **최대 이동 거리 계산**: 모든 라운드가 끝난 후, 가장 멀리 이동한 자동차의 이동 거리를 계산합니다.
- **우승자 판별**: 최대 이동 거리와 일치하는 자동차들을 찾아 우승자로 선정합니다.

### 경주 결과 출력

- **경주 결과 출력**: 최종 우승자의 이름을 화면에 출력합니다. 공동 우승자가 있을 경우 모두 출력됩니다.

&nbsp;

## 🖥️ **입출력 예시**

### **입력**

- 경주할 자동차 이름(이름은 쉼표(,) 기준으로 구분)

```
pobi,woni,jun
```

- 시도할 횟수

```
5
```

### **출력**

- 차수별 시행 결과

```
pobi :--
woni :----
jun :---
```

- 단독 우승자 안내 문구

```
최종 우승자 :pobi
```

- 공동 우승자 안내 문구

```
최종 우승자 :pobi,jun
```

### **실행 결과 예시**

```
경주할 자동차 이름을 입력하세요.(이름은 쉼표(,) 기준으로 구분)
pobi,woni,jun
시도할 횟수는 몇 회인가요?
5

실행 결과
pobi :-
woni :
jun :-

pobi :--
woni :-
jun :--

pobi :---
woni :--
jun :---

pobi :----
woni :---
jun :----

pobi :-----
woni :----
jun :-----

최종 우승자 :pobi,jun
```

&nbsp;

## 🚨 **예외 사항**

프로젝트에서 다음과 같은 경우 **예외**가 발생할 수 있습니다. 이 경우, 프로그램은 `IllegalArgumentException`을 발생시키며 종료됩니다.

### **자동차 이름 입력 오류**

- 자동차 이름이 **공백**으로만 이루어진 경우.
- 자동차 이름이 **5자를 초과**한 경우.
- 자동차 이름이 **쉼표**(,)로 구분되지 않은 경우.
- 입력된 자동차 이름이 **중복된** 경우.

### **시도 횟수 입력 오류**

- 시도 횟수가 **0**인 경우.
- 시도 횟수가 **음수**인 경우.
- 시도 횟수가 **공백**인 경우.
- **숫자가 아닌 값**을 입력한 경우.

예외 발생 시, 해당 오류 메시지를 출력하고 프로그램을 종료합니다. 이를 통해 사용자가 잘못된 입력을 수정할 수 있도록 돕습니다.

### 다음 상황은 예외가 아닙니다.

- 경주 차량이 **1**인 경우.
- 자동차 이름에 **공백** 및 **문자가 아닌 값**이 포함 경우.

&nbsp;

## ⭐ **사전 요구 사항**

- [x] **JDK 21**이 설치되어 있어야 합니다. [JDK 21 설치 가이드](https://openjdk.org/projects/jdk/21/)를 참고하세요.
- [x] **Git**이 설치되어 있어야 합니다. [Git 설치 가이드](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)를 참고하세요.
- [x] **Gradle**을 설치하거나, 프로젝트에 포함된 **Gradle Wrapper**를 사용할 수 있어야 합니다.
- [x] 명령어를 실행할 수 있는 **터미널 또는 명령 프롬프트**가 필요합니다.  
  &nbsp;

### **과제 진행 요구 사항**

- [x] 미션은 자동차 경주 저장소를 **포크하고 클론**하는 것으로 시작한다.
- [x] 기능을 구현하기 전 **README.md**에 구현할 기능 목록을 정리해 추가한다.
- [ ] ~~Git의 커밋 단위는 앞 단계에서 README.md에 정리한 기능 목록 단위로 추가한다.~~
- [x] [AngularJS Git Commit Message Conventions](https://gist.github.com/stephenparish/9941e89d80e2bc58a153)을 참고해 커밋
  메시지를 작성한다.
- [x] 자세한 과제 진행 방법은 프리코스 진행 가이드 문서를 참고한다.  
  &nbsp;

### **프로그래밍 요구 사항 1**

- [x] **JDK 21** 버전에서 실행 가능해야 한다.
- [x] 프로그램 실행의 시작점은 `Application`의 `main()`이다.
- [x] `build.gradle` 파일은 변경할 수 없으며, 제공된 라이브러리 이외의 **외부 라이브러리**는 사용하지 않는다.
- [x] 프로그램 종료 시 **`System.exit()`**를 호출하지 않는다.
- [x] 프로그래밍 요구 사항에서 달리 명시하지 않는 한 **파일, 패키지** 등의 이름을 바꾸거나 이동하지 않는다.
- [x] **자바 코드 컨벤션**을 지키면서 프로그래밍한다.
    - 기본적으로 [Java Style Guide](https://google.github.io/styleguide/javaguide.html)를 원칙으로 한다.  
      &nbsp;

### **프로그래밍 요구 사항 2**

- [x] `indent`(인덴트, 들여쓰기) depth를 **3이 넘지 않도록** 구현한다. 2까지만 허용한다.
    - 예를 들어 **`while`문** 안에 **`if`문**이 있으면 들여쓰기는 2이다.
    - 힌트: `indent`(인덴트, 들여쓰기) depth를 줄이는 좋은 방법은 **함수(또는 메서드)를 분리**하면 된다.
- [x] **3항 연산자**를 쓰지 않는다.
- [ ] ~~함수(또는 메서드)가 **한 가지 일만** 하도록 최대한 작게 만들어라.~~
- [x] **JUnit 5**와 **AssertJ**를 이용하여 정리한 기능 목록이 정상적으로 작동하는지 **테스트 코드**로 확인한다.

&nbsp;

## 📦 **라이브러리 사용 안내**

- [x] `camp.nextstep.edu.missionutils`에서 제공하는 `Randoms` 및 `Console` API를 사용하여 구현해야 한다.
    - [x] **Random 값 추출**: `camp.nextstep.edu.missionutils.Randoms`의 `pickNumberInRange()`를 활용한다.
    - [x] **사용자가 입력하는 값**: `camp.nextstep.edu.missionutils.Console`의 `readLine()`을 활용한다.

## 🤔 **회고**

### 프로젝트 회고

이번 프로젝트에서는 디렉토리 구조를 나누고 `exception`과 `validator`를 분리하여 책임을 분리하려 했습니다.
도메인(Car,Dto...)을 별도로 분리해야 할지에 대해 많이 고민했지만 이번 프로젝트에서 현재 구조를 유지하기로 결정했습니다.

- `과제 진행 요구사항`과 `프로그래밍 요구사항 2`에서 언급했던 `기능 단위 커밋`과 `함수가 한 가지 일만`에 대한 요구사항을 잘 지키지 못한 것 같습니다. 기획과 설계 단계에서 미처 생각지 못한 부분들이 너무
  많이 나와 수정이 빈번하게 이루어졌기 때문입니다.


- 이번 프로젝트에서는 모든 메서드를 검증하기보다는 중요한 메서드에 대한 검증에 집중하여 진행했습니다. 또한 다양한 예외케이스와 사용자 입장에서 궁금할 만한 내용에 대해 다양하게 생각을 했습니다.(자동차 이름에
  공백이 들어가도 되는지 등.)


- Map,Set 자료구조에 대해 좀 더 깊은 이해를 할 수 있었던 시간이었습니다. 랜덤한 숫자는 어떻게 검증을 하는지, void 타입은 어떻게 검증을 하는지에 대한 부분도 생각해 볼 수 있었던 시간이었습니다.


- 지난 번 프로젝트와 가장 크게 달라진 점은 문서 작성인 것 같습니다. 문서의 중요성에 대해 깨닫고 많은 시간을 투자하고 구상했습니다. 프리코스 기간동안 저만의 틀을 만들어가고자 합니다.

&nbsp;

### 프리코스 2주차 회고

#### 지원서에 작성한 목표를 얼마나 달성하고 있다고 생각하나요? 그 이유는 무엇인가요?

- 목표는 약 80% 정도 달성하고 있다고 생각합니다. 기초에 충실하고 습관을 유지하는 부분에서는 잘 진행하고 있으나, 프리코스를 진행하면서 몰입을 위한 기초가 부족하다는 점을 많이 느끼고 있습니다. 객체지향적인
  설계와 기능을 분리하는 것에 대해 특히 많은 부족함을 느끼고 있습니다. 20%를 채우는 것도 목표지만 80%를 잘 유지할 수 있도록 노력할 예정입니다.

&nbsp;

#### 지원서에 작성한 목표를 변경해야 한다고 생각하시나요? 그렇다면 그 이유와 어떤 목표로 변경하고 싶으신가요?

- 큰 방향성에 대한 변경은 없습니다. 다만 세부적인 목표를 조금 더 자세히 세울 수 있을 것 같습니다. 프리코스에서 제시하고 있는 클린코드, 협업을 위한 컨벤션들, 기초적인 공통 사항들, 테스트 주도 개발, 책임의
  분리 등 기초적인 부분들을 진행 기간 동안 반복해 익히고 자바에 대한 이해를 높이는 데 집중하고자 합니다.

&nbsp;

#### 프리코스를 진행하면서 눈에 띄는 변화나 깨달은 점이 있나요?

- 정말 많이 변했습니다. 같은 문제를 다양한 시각으로 바라보는 과정을 통해 시야가 한층 넓어졌고, 개발에 열정이 있는 사람들과 생각과 의견을 활발히 교류하는 과정이 너무 재밌고 설레는 일이라는 것을 느꼈습니다.
  부족하지만 역설적이게도 자신감이 생겼습니다. '이렇게 하면 되겠구나', '이렇게 하면 성장할 수 있겠구나'라는 생각을 정말 많이 했습니다. 가야 할 길이 훨씬 더 또렷해졌습니다.
  무엇보다 요구사항을 정확히 파악하고 정리하는 것의 중요성을 깨달았습니다. 개발 중간에 미처 파악하지 못한 요구사항을 발견하게 되면 많은 수정 작업이 필요하다는 점을 직접 느꼈습니다. 요구사항에 대한 분석과 기록의
  중요성을 많이 깨달았던 시간이 되고 있지 않나 생각합니다.