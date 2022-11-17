# 미션 - java-bridge

## 기능 목록
### class : BridgeGame
/* 다리 건너기 게임을 관리하는 클래스 */
  - package 변경 가능 
  - 필드(인스턴스 변수) 추가가능
  - 메서드의 시그니처(인자, 이름)와 반환타입 변경 가능
  - 메서드 추가 가능

#### move()
/* 사용자가 칸을 이동할 때 사용하는 메서드 */
- [InputView.java - readMoving()]에서 받아온 값과 makeBridge n번째 값이 일치할 경우 이동
    
#### retry()
/* 사용자가 게임을 다시 시도할 때 사용하는 메서드 */
- [InputView.java - readGameCommand()]에서 받아온 값이 R이면 재시작, Q이면 종료
- Q일 경우 최종 게임 결과와 게임 성공 여부 및 횟수 출력

### class : BridgeMarker
/* 다리의 길이를 입력 받아서 다리를 생성해주는 역할을 한다. */
  - 필드(인스턴스 변수) 변경 불가능
  - 메서드의 시그니처(인자, 이름)와 반환타입 변경 불가능
#### makeBridge()
    public List<String> makeBridge(int size) {
    return null;
    }
    /* return : 입력받은 길이에 해당하는 다리 모양. 위 칸이면 "U", 아래 칸이면 "D"로 표현해야 한다. */
- [InputView.java - readBridgeSize()]에서 받아온 size 값만큼 Bridgemaker로 생성
- bridgeNumberGenerator의 값이 1인 경우 U를 List에 저장, 0인경우 D를 List에 저장
- BridgeMaker 생성자로 BridgeNumberGenerator을 이용해 1 or 0의 값을 무작위로 저장
  - 한 칸의 다리 생성시 사용
  - makeBridge에서 생성 후 값 추출 후 끝날 메서드이기 때문에 변수로 받을 필요가 없어보임

### interface : BridgeNumberGenerator
### class : BridgeRandomNumberGenerator
  - 코드 변경 불가능
  - int number = bridgeNumberGenerator.generate(); 이렇게 추출

### class : InputView
/* 사용자로부터 입력을 받는 역할을 한다. */
  - package 변경 가능
  - 메서드의 시그니처(인자, 이름)와 반환타입 변경 가능
  - 메서드 추가 가능

#### readBridgeSize()
/* 다리의 길이를 입력받는다. */
- 3 이상 20 이하의 숫자 입력 가능 -> 예외처리
    
#### readMoving()
/* 사용자가 이동할 칸을 입력받는다. */
- U or D로 입력 가능 -> 예외처리

#### readGameCommand()
/* 사용자가 게임을 다시 시도할지 종료할지 여부를 입력받는다. */
- R or Q로 입력 가능 -> 예외처리

### class : OutputView
/* 사용자에게 게임 진행 상황과 결과를 출력하는 역할을 한다. */
  - package 변경 가능
  - 메서드의 시그니처(인자, 이름)와 반환타입 변경 가능
  - 메서드 추가 가능

#### printMap()
/* 현재까지 이동한 다리의 상태를 정해진 형식에 맞춰 출력한다. */
#### printResult()
/* 게임의 최종 결과를 정해진 형식에 맞춰 출력한다. */ 

### 구현
- [] 다리 사이즈 input
  - () 예외처리
- [] 다리 생성
- [] 이동 칸 input
  - () 예외처리
  - [] 게임 시도 횟수 저장
  - [] 선택 칸과 다리 값 비교
  - [] O or X로 출력
  - [] X일 경우 게임 진행 input
    - () 예외처리
    - R : 재시작
    - Q : 종료
      - [] 최종 결과 출력