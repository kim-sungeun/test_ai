# [2021 Spring Class] Ajou AI by JBR
1. **대회목표**: 알파고를 이겨라!

2. **세부 프로토콜**

   데이터셋: 바둑 데이터셋
   
   네트워크 파라미터: 자유

   아키텍쳐: 자유

   학습알고리즘: 자유

   딥러닝 프레임워크: PyTorch 권장, TensorFlow등 다른 프레임워크도 사용 가능

   외부데이터: 사용 가능

3. **순위산정:** 바둑 데이터셋의 Top-1 Accuracy

4. **팀 구성**: 5인 구성된 팀

5. **시상**: 최종 성적에 N% 반영

6. **대회진행**

   |     날짜      |      일정       |
   | :-----------: | :-------------: |
   |     시작      | 2021년 3월 19일 |
   |     중간      | 2021년 4월 22일 |
   |     기말      | 2021년 6월 15일 |
   | 최종결과 발표 | 2021년 6월 22일 |

7. **최종 결과 산출 방법:** 중간, 기말 시점의 정확도를 일정 비율로 합쳐서 최종 결과에 반영


## 퍼블릭 랭킹

  
- Total Score가 아직 업데이트되지 않았습니다. 
 - 다음 업데이트 일정은 중간 점수 집계(2021-04-22) 입니다.
  
**현재 랭킹 1위는 team1 입니다. 평균 accuracy는 16.64% 입니다.**
|Ranking|Name|Penalty|Accuracy(%)|Last Submission|Total Submission Count|Total Score(%)|
| :---: | :---: | :---: | :---: | :---: | :---: | :---: |
|1|team1|0|18.0855|2021-03-19 16:31:50.008196+09:00|3|0.0|
|2|team5|0|17.34201|2021-03-19 13:43:10.533568+09:00|1|0.0|
|3|team3|0|16.82156|2021-03-19 13:43:10.533568+09:00|1|0.0|
|4|team8|0|16.80297|2021-03-19 13:43:10.533568+09:00|1|0.0|
|5|team6|0|16.74721|2021-03-19 13:43:10.533568+09:00|1|0.0|
|6|team4|0|16.59851|2021-03-19 13:43:10.533568+09:00|1|0.0|
|7|team9|0|16.48699|2021-03-19 13:43:10.533568+09:00|1|0.0|
|8|team12|0|16.26394|2021-03-19 13:43:10.533568+09:00|1|0.0|
|9|team2|0|16.26394|2021-03-19 13:43:10.533568+09:00|1|0.0|
|10|team11|0|16.20818|2021-03-19 13:43:10.533568+09:00|1|0.0|
|11|team10|0|16.171|2021-03-19 13:43:10.533568+09:00|1|0.0|
|12|team7|0|15.85502|2021-03-19 13:43:10.533568+09:00|1|0.0|


**정확도는 소숫점 5자리 까지 출력됩니다.**
**Time zone is seoul,korea (UTC+9:00)**
## 퍼블릭 랭킹 제출 방법

본인이름의 폴더 안에 테스트 데이터 셋을 예측한 결과값을 암호화해서 제출하면 됨.

Example) 

1. 예측 파일 만들기. 다음과 같은 예측 파일이 있다고 가정 `ans.txt`=(Test Label1 예측값), `ans2.txt`=(Test Label2 예측값)

   `ans.txt` 예시

   ```tex
   1 9
   2 8
   3 10
   4 99
   5 98
   6 70
   7 18
   8 33
   ```

   

   `ans2.txt` 예시

   ```
   1 9d
   2 2k
   3 2k
   4 4k
   ```

   

2. 예측 파일(`ans.txt`, `ans2.txt`)과 본인의 키를 `Encrypt` 폴더에 넣고 `Encrypt.py`를 실행 시켜서 암호화한 예측 파일(`ans.json` `ans2.json`)을 만들어 낸 다. 생성한 파일을 본인의 이름으로 된 폴더안(`submission/hankyul`)에 넣고 커밋 후 푸쉬하면 됨.

   ```python
   # 1.이메일을 통해서 전달 받은 키 파일의 경로 입력
   key_path = "key.pem"
   # 2. 예측한 결과를 텍스트 파일로 저장했을 경우 리스트로 다시 불러오기
   # 본인이 원하는 방식으로 리스트 형태로 예측 값을 불러오기만 하면 됨(순서를 지킬것)
   raw_ans_path = ['ans', 'ans2']
   for path in raw_ans_path:
   	ans = read_txt(path+'.txt')
   	# 3. 암호화된 파일을 저장할 위치
   	encrypt_ans_path = path+".json"
       # 4. 암호화!(pycrytodome 설치)
       encrypt_data(key_path, ans, encrypt_ans_path)
   ```

   이 때 꼭 로컬에서 이 스크립트를 실행해서 제출해야 되는건 아님. 그냥 코랩에서 편하게 pycryptodomex 라이브러리 설치하고 코랩에서 스크립트 실행시켜서 정답 파일 만든 뒤에 제출해도 됩니다. 파이팅 입니다!



## 퍼블릭 랭킹 평가 방법

Test Label 1 + Test Label 2 의 Top 1 acc 를 더해서 평균 낸 것으로 한다.

ex) `ans.txt`=(Test Label1 예측값), `ans2.txt`=(Test Label2 예측값)

1. `ans1.txt` top 1 acc = 98%

   ```tex
   1 0
   2 1
   3 -1
   4 1
   ```

2. `ans2.txt` top 1 acc = 100% (k=급, d=단) 

   ```tex
   1 9d
   2 2k
   3 2k
   4 4k
   ```

3. ACC = 99%

