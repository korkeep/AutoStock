# AutoStock
## Project Goal
주식 종목 추천 & 자동 매수, 매도 프로그램 개발

## To-Do List
- **Acquisition**: 데이터 수집 & 전처리
- **Analysis**: API 형식으로 데이터 변환
- **Visualization**: 웹 / GUI 프로그래밍

## Description
### 1. 종목 분석: 하루 누적 거래량 패턴 분석
- 당일 기준 A일 이전까지의 데이터 호출
- 전일 거래량 / 당일 거래량 B배 이상 종목 필터링
- 시가 / 종가 비율 C% 이상, 이하 종목 필터링
- A, B, C은 사용자의 입력값 Ex) A, B, C : 20일, 2.5배 이상, 5.0% 이상
- 필터링된 종목 다음날 자동매수 설정
### API Format
| Content | Description |
| --- | --- |
| date | 날짜 |
| start | 시가 |
| end | 종가 |
| volume | 거래량 |

### 2. 자동 매수: 분 단위 거래량 패턴 분석
- <종목 분석>에서 필터링된 종목에 대한 모니터링
- A분봉 직전 / 현재 거래량 B배 이상 종목 필터링
- A분봉 직전 / 현재 가격 비율 C% 이상 종목 필터링
- 필터링된 종목 D원만큼 현재가로 매수 주문
- A, B, C, D는 사용자의 입력값 Ex) A, B, C, D : 10분, 3.0배 이상, 0.5% 이상, 50000원
### API Format
| Content | Description |
| --- | --- |
| time | 시간 |
| price | 가격 |
| volume | 거래량 |

### 3. 자동 매도: 분 단위 거래량 패턴 분석
- 현재 보유하고 있는 모든 종목에 대한 모니터링
- A분봉 직전 / 현재 거래량 B배 이상 종목 필터링
- A분봉 직전 / 현재 가격 비율 C% 이하 종목 필터링
- 필터링된 종목 현재가로 전량 매도 주문
- A, B, C, D는 사용자의 입력값 Ex) A, B, C, D : 15분, 2.0배 이상, 0.2% 이하
### API Format
| Content | Description |
| --- | --- |
| time | 시간 |
| price | 가격 |
| volume | 거래량 |

## How to Use?
**Step1**: [python3 설치](https://www.python.org/downloads/)  
**Step2**: PyQT5, pandas 설치  
```
pip install pandas
pip install pyqt5-tools
```
**Step3**: [키움증권 OpenAPI+ 설치](https://www3.kiwoom.com/nkw.templateFrameSet.do?m=m1408010600)  
**Step4**: pytrader.py 실행  
```
python3 pytrader.py
```