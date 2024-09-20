# LISA HACKATHON

## 언어 선택

[English](README.md) | [한국어](README_KR.md)

<br><br>

## 파일 구조

```
Source_code/
├── Data_Collected/
│   └── Sensing Dataset-00001 ~ 00056.txt
│ 
├── code/
│   ├── PCANBasic.py
│   ├── CAN 데이터 검출 및 분석.ipynb
│   ├── CAN 데이터 수집.ipynb
│   └── 제공된 CAN 데이터 검출 및 분석.ipynb

```

<br><br>

## DATA 출처
2023 LISA 해커톤에서 주어진 해커톤 비정상 이벤트 - `CCAN.txt` 파일을 활용함.

<br><br>

## DATA의 규모

- (2872262, 15)총 2872262개의 데이터로 구성되어있고, 15개의 칼럼으로 이루어져있음.

```python
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 2872262 entries, 0 to 2872261
Data columns (total 15 columns):
 #   Column       Dtype  
---  ------       -----  
 0   No           object 
 1   Time_Offset  float64
 2   Type         int64  
 3   ID           object 
 4   Data_Length  int64  
 5   One          object 
 6   Two          object 
 7   Three        object 
 8   Four         object 
 9   Five         object 
 10  Six          object 
 11  Seven        object 
 12  Eight        object 
 13  Unnamed: 13  float64
 14  Unnamed: 14  float64
dtypes: float64(3), int64(2), object(10)
memory usage: 328.7+ MB

```

<br><br>

## 세부사항 및 분석 결과

이 데이터는 CAN 메시지 통신으로 얻은 데이터로, 총 15개의 칼럼으로 구성됨:
- **0번째 칼럼**: 데이터 넘버
- **1번째 칼럼**: 타임 오프셋
- **2번째 칼럼**: 데이터 타입
- **3번째 칼럼**: CAN-ID
- **4번째 칼럼**: 데이터 길이
- **5~14번째 칼럼**: 데이터 필드

이 데이터를 통해 차량에서 보내는 데이터를 분석하여, 이벤트들을 확인하고 비정상적인 이벤트를 검출할 수 있음.

<br><br>

## 기대효과

- CAN 데이터를 통해 차량 내부 시스템 간 통신을 개선하고, 차량 제어 시스템을 최적화할 수 있음.
- 차량의 상태를 모니터링하여 문제를 조기에 감지하고, 유지보수 및 수리 작업을 효율적으로 수행할 수 있음.
- CAN 데이터를 활용하여 안전 기능을 개선하고, 다양한 시스템을 구현 가능.
- 데이터 분석을 통해 운전 습관 및 도로 상황에 대한 인사이트를 얻어 차량 및 운전자의 안전성을 높일 수 있음.

<br><br>

## 기타 산출물 및 설명

### 데이터 분석 (설명)
1. 데이터 분석을 통해 비정상 이벤트를 검출(2점), 분석(2점)하여 총 4점으로 평가함.
2. **검출**이란, 비정상 이벤트를 생성하는 CAN ID 조합을 검출하고, 위치 및 지속 시간 패턴을 설명할 수 있음을 의미함.
3. 모든 검출된 이벤트에 대한 분석 점수는 데이터 분석의 총점으로 계산됨.

<br>

### SW 개발 (설명)
1. 데이터 분석을 통해 비정상 이벤트를 검출(4점), 분석(4점)하여 총 8점으로 평가함.
2. 비정상 이벤트를 만드는 CAN ID 조합을 검출하고, 그 위치 및 지속 시간 패턴을 설명할 수 있어야 함.

<br><br>

## 평가 기준 및 시상 기준
1. **보고서**: 참가자들이 비정상 이벤트를 탐지하는 과정에 대한 내용을 다룸.
2. **발표**: 참가자들이 비정상 이벤트 탐지에 대한 내용을 설명함.

<br><br>

## 보고서 순서
- 머신러닝 활용
- SW 개발
- 이벤트 목록
- 이벤트 검출 및 분석

<br><br>

## 머신러닝 활용

정상 이벤트만 포함된 데이터를 바탕으로 비정상 이벤트의 패턴과 시점을 예측할 수 있는 머신러닝 모델 개발.  
비지도 학습 모델인 `OneSVM`을 사용했으며, 아래는 해당 코드 및 출력 값임.

<br>

![image](https://github.com/user-attachments/assets/fe390267-31f8-4d0e-b404-73c679d46858)

<br>

![image](https://github.com/user-attachments/assets/581325ee-6173-4249-927a-a934e2f8a599)


<br><br>

## SW 개발

### CAN 데이터 실시간 수집

- `PCANBasic` 라이브러리의 예제 코드를 참조하여 CAN 데이터를 수집.
- 비정상 이벤트 검출 및 분석을 위한 알고리즘 적용.
- 실시간으로 수집된 데이터가 100개가 될 때마다 `Dataset` 디렉토리에 지정된 파일명으로 저장됨.
- 비정상 이벤트 검출 및 분석 알고리즘을 별도의 파일로 함수화하여, 실시간 검출이 가능하게 설정함.

<br>

![image](https://github.com/user-attachments/assets/d0208049-de66-46b5-aaf7-5e27d87fd2b6)

<br>

![image](https://github.com/user-attachments/assets/17de31d5-dfb6-40d4-aa29-93b43a21888c)



<br><br>

## 이벤트 목록

다음을 토대로 비정상 이벤트를 검출 및 분석하였음

![image](https://github.com/user-attachments/assets/4b5172e7-919c-42e4-9cd2-1f61220a08db)


이벤트 목록은 다음과 같음:
- **0316 & 043F**: P기어일 때 RPM이 올라가는 경우
- **0316 & 0440**: RPM이 높은데 속도가 0인 경우
- **0316 & 043F**: N기어일 때 RPM이 올라가는 경우
- **0316 & 0440**: N기어일 때 속도가 올라가는 경우
- **0018 & 043F**: 운전자석 문이 열려 있을 때 D 기어일 경우
- **0018 & 043F**: 운전자석 문이 열려 있을 때 R 기어일 경우
- **0018**: One 시트벨트가 off일 때 Eight 시트벨트가 on일 경우
- **0018 & 043F**: 벨트 off일 때 D 기어일 경우
- **0018 & 043F**: 벨트 off일 때 R 기어일 경우
- **0018 & 0440**: 벨트 off일 때 속도가 올라가는 경우

<br><br>

## 이벤트 검출 및 분석

모든 이벤트 검출 및 분석 과정은 비정상 이벤트를 그래프로 표현하고, 해당 이벤트가 실제로 일어나는지를 육안으로 확인함.  
`time_offset`을 활용해 해당 이벤트의 발생 시점을 출력하며, 알아보기 쉽게 주요 데이터를 추림.

- **0316 & 043F**: P기어일 때 RPM이 올라가는 경우
  - 16진수를 10진수로 변환한 그래프를 통해 파란 점(P기어)에서 RPM이 상승하는 경우를 확인할 수 있음.

<br>

![image](https://github.com/user-attachments/assets/c3705ada-7670-4fcd-80a5-615e64c5e8dd)


- 데이터를 통해 P기어일 경우 RPM이 상승하는 모든 경우를 추출하여 아래와 같이 데이터 전체 정보를 출력함.

<br>

![image](https://github.com/user-attachments/assets/13e817ec-361e-4809-a4dd-d54ebc1369d0)


- 필요한 데이터를 선별하여 추림.

<br>

![image](https://github.com/user-attachments/assets/be080fe4-4e14-46e3-b0de-74193061f550)


- 신뢰성을 높이기 위해 start_time과 end_time을 변수로 사용하여 그래프를 그려냄.

<br>

![image](https://github.com/user-attachments/assets/60c0e3fe-8ed8-4651-ab42-48725d6f696a)


다른 이벤트도 동일한 방식으로 검출 및 분석됨.
