## 기계학습기초
기계학습 기초 수업 내용 정리 복습

### 개인 프로젝트 빌표 : 자전거 수요 예측
#### - 사용 데이터 : 캐글, Bike Sharing Demand
> Capital Bikeshare 프로그램의 자전거 대여 수요 예측

#### - 평가척도  : RMSLE
> MSLE에 루트를 취한 것으로 root*log function 의 특성에 의해 에러율이 9이하인 경우에는 MSLE보다 값이 크게 나오고, 그보다 큰 경우 작게 나옴.   <br>
> 작을수록 회귀 성능이 좋은 것.

#### 데이터 사전
datetime - hourly date + timestamp (날짜와 시간) <br>
season - 1 = spring, 2 = summer, 3 = fall, 4 = winter (계절) <br>
holiday - whether the day is considered a holiday (휴일) <br>
workingday - whether the day is neither a weekend nor holiday (평일) <br>
weather  <br>
Clear, Few clouds, Partly cloudy, Partly cloudy (맑은 날씨) <br>
Mist + Cloudy, Mist + Broken clouds, Mist + Few clouds, Mist (안개) <br>
Light Snow, Light Rain + Thunderstorm + Scattered clouds, Light Rain + Scattered clouds (가벼운 눈, 비) <br>
Heavy Rain + Ice Pallets + Thunderstorm + Mist, Snow + Fog (폭설, 폭우) <br>
 <br>
temp - temperature in Celsius (온도) <br>
atemp - “feels like” temperature in Celsius (체감 온도) <br>
humidity - relative humidity (상대 습도) <br>
windspeed - wind speed (풍속) <br>
casual - number of non-registered user rentals initiated (비회원 대여량) <br>
registered - number of registered user rentals initiated (회원 대여량) <br>
count - number of total rentals (총 대여량) <br>
 <br>

 #### 데이터 탐색
- 계절에 따른 시간별 대여량 확인 <br>

<img width="547" height="227" alt="image" src="https://github.com/user-attachments/assets/979363ef-5697-47c8-b972-e09130248720" />

1.출퇴근 시간으로 예상되는 8시, 17시, 18시에 대여량이 가장 높음. <br>
2.봄(Spring)의 대여량이 다른 계절에 비해 상대적으로 낮게 나옴. <br>
3.봄보다 겨울 대여량이 많은 것이 신기해 계절을 어떻게 나눴는지 확인. <br>
> 1, 2, 3월 봄/  4, 5, 6월 여름/ 7, 8, 9월 가을/ 10, 11, 12월 겨울 <br>

<img width="412" height="160" alt="image" src="https://github.com/user-attachments/assets/9988acaa-8822-4aa8-bb8f-4acfa5d20575" />
 <br>
- 데이터 상관관계 확인 <br>
1.온도, 습도, 풍속은 거의 연관관계가 없음. <br>
2.대여량과 가장 연관이 높은 건 registered 로 등록 된 대여자가 많지만, test 데이터에는 이 값이 없음. <br>
3.atemp와 temp는 0.98로 상관관계가 높지만 온도와 체감온도를 둘 다 피처로 사용하기에 적합하지 않음. 둘의 상관관계가 높음. <br>
<img width="395" height="322" alt="image" src="https://github.com/user-attachments/assets/8db51368-95a1-4b5a-8988-1dd977462b1b" />

- Count(대여량) 데이터 분포도 파악 <br>
1.종속변수 count 가 오른쪽으로 치우쳐진 것을 확인할 수 있음. <br>
2.대부분의 기계학습은 종속변수가 normal 이어야 하기 때문에 정규분포를 갖는 것이 바람직함. <br>
<img width="487" height="217" alt="image" src="https://github.com/user-attachments/assets/cf389fb4-8903-4d8d-ba8e-d87594ccb323" />

#### 예측모델 : 랜덤포레스트
( LinearRegression,  Lasso,  Ridge, RandomforestRegressor 비교)

### 결과
<img width="896" height="227" alt="image" src="https://github.com/user-attachments/assets/a8a22352-fe89-422a-b121-a5492daf656a" />






