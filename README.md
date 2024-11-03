---

# 티켓 예매 자동화 프로그램

뮤지컬 티켓 예매 과정을 자동화하여, 사용자가 원하는 시간에 원하는 좌석을 빠르게 예약할 수 있도록 돕는 프로그램입니다. 자동화 도구가 티켓 예매 사이트에 접속해 로그인 후, 사용자 정의 기준에 따라 좌석을 예약하며, 예매 대기 시간 및 높은 수요 상황에서도 안정적으로 동작하도록 오류 처리가 포함되어 있습니다.

## 1. 개요

이 티켓 예매 자동화 프로그램은 사용자가 설정한 시간에 맞춰 예매 사이트에 접속해 좌석을 빠르게 확보할 수 있도록 설계되었습니다. 주요 기능은 다음과 같습니다:
- 예약 시간에 맞춘 예매 실행
- 사용자 선호 조건에 따른 좌석 선택
- 높은 수요나 대기 상황에서도 안정적인 예매 진행

이를 통해 사용자는 수작업 부담을 줄이고, 경쟁이 치열한 예약 상황에서도 원하는 티켓을 성공적으로 확보할 가능성을 높일 수 있습니다.

## 2. 사용 기술 스택 및 주요 기능

### Python
Python은 주 언어로 사용되었으며, 풍부한 라이브러리와 자동화 기능을 통해 웹 스크래핑, 시간 제어, UI 통합 등을 지원합니다.

### Selenium
Selenium을 사용하여 크롬 브라우저를 제어하며, 다음과 같은 기능을 구현했습니다:
- **브라우저 자동화 및 사용자 로그인**: 티켓 예매 사이트에 자동으로 접근해 로그인하며, 크롬 브라우저의 `detach` 옵션을 사용해 브라우저가 닫히지 않도록 하여 실시간 모니터링과 디버깅을 지원합니다.
- **지정 시간에 맞춘 티켓팅**: `WebDriverWait`을 통해 사용자가 설정한 시간에 맞춰 정확히 클릭과 작업이 이루어지도록 하여 예매 시간을 놓치지 않게 했습니다.
- **조건부 좌석 선택**: 사용자 선호 조건에 맞춰 좌석을 필터링하고 자동으로 선택하는 로직을 구현했습니다. 극장마다 좌석 배열과 조건이 다르기 때문에, 블루스퀘어 및 디큐브아트센터 등의 특정 조건에 맞춰 iframe 내 요소를 조작하여 좌석을 선택하도록 설정했습니다.

### Tkinter
Tkinter를 통해 사용자 입력을 위한 GUI를 구성하였습니다. 사용자로부터 아이디, 비밀번호, 뮤지컬명, 티켓팅 시간 등의 정보를 입력받아, 프로그램 실행 전에 필요한 데이터를 수집할 수 있습니다.

### ChromeDriver
ChromeDriver는 Selenium과 함께 브라우저 제어에 사용되어, 웹페이지 요소 탐색 및 반응 속도가 최적화되도록 했습니다.

## 3. 효율적 실행과 최적화

- **탐색 시간 최소화**: `implicitly_wait`와 `WebDriverWait`을 조합하여 로딩 시간을 줄여 불필요한 대기를 방지하고, 설정된 시간에 정확히 예매가 진행되도록 했습니다.
- **프레임 탐색**: 특정 좌석 선택 시 iframe 내 요소를 탐색하여 특정 영역의 좌석을 자동으로 클릭하도록 설정하여 예매 과정을 효율적으로 진행했습니다.
- **다중 좌석 조건 처리**: 사용자가 선호하는 좌석 조건을 극장별로 구분하여 필터링 로직을 구현했습니다. 각 극장의 좌석 특성에 맞게 연석 등을 고려하여 좌석을 선택하도록 했습니다.

## 4. 사용 방법

### 사전 준비
- Python 및 Selenium 설치 (`pip install selenium`)
- ChromeDriver 다운로드 (Chrome 버전과 일치하는지 확인)

### 프로그램 실행
1. 터미널에서 프로그램을 실행합니다:
   ```bash
   python ticket_reservation.py
   ```
2. GUI에서 요구하는 정보를 입력합니다 (ID, 비밀번호, 뮤지컬명, 티켓팅 시간, 극장 이름).
3. 프로그램이 로그인부터 좌석 선택, 예매까지 자동으로 진행합니다.

### 예시
```plaintext
Enter ID: your_id
Enter Password: your_password
Enter Musical Name: 프랑켄슈타인
Enter Ticketing Time: 11:00
Enter Theater Name: 블루스퀘어
```

## 5. 오류 처리

프로그램은 다음과 같은 오류 처리를 통해:
- 높은 수요 상황에서도 안정적으로 작동
- 예기치 않은 장애나 재로그인 방지
- 특정 요소가 즉시 접근되지 않을 경우에도 프로그램이 원활히 진행될 수 있도록 구성했습니다.