# 음성 챗봇

## 개요
* 음성으로 사용자의 말을 입력받아 음성으로 출력하는 음성 챗봇
* 음성을 텍스트 형태로 변환하고, 해당 텍스트를 학습된 트랜스포머 모델에 입력해 응답을 출력한 뒤 출력된 텍스트를 음성으로 변환
* 학습은 코랩 환경에서, 결과 확인(음성 인식 및 출력)은 아나콘다 환경에서 진행
## 학습 데이터
* ai 허브의 '공감형 대화'를 사용했다.
* Training과 Validation의 데이터를 합친 약 40만 개의 데이터를 학습에 사용하였다.
## 트랜스포머 학습 및 추론
* 아래 참고 사이트의 코드를 거의 그대로 사용하였는데, 토크나이저는 단어 집합을 저장할 수 있는 것을 찾아 sentencepiece를 사용하게 되었다.
  * 단어 집합의 크기는 2만 개로 설정하였다.
* 임의로 몇 가지 문장을 넣어 확인한 결과는 다음과 같다.
  <pre><code>Input: 모든 게 잘 될 거야
  Output: 고마워 . 그렇게 말해줘서 . 고마워

  Input: 너무 힘들어요
  Output: 왜 그런 말씀을 하시는지 모르겠지만 , 무슨 일 있으세요 ?

  Input: 고마워요
  Output: 나도 항상 우리 곁에 있어 줘서 고마워요 .

  Input: 괜찮겠죠?
  Output: 그럼 , 당연하지 . 그리고 지금 당장은 너무 힘들겠지만 , 분명 시간이 지나면 괜찮아질 거야 . 너무 걱정하지 말고 , 힘내 !

  Input: 이제 가 봐야 겠다.
  Output: 응 . 오늘 하루도 고생 많았어 .
  </code></pre>
## STT와 TTS
* stt는 speech_recognition, tts는 pyttsx3 라이브러리를 사용하여 구현하였다.
* 코랩에서는 음성 인식이 안 되는 듯하여 음성 인식 후 출력하는 부분은 아나콘다 환경에서 진행하였다. 가상 환경을 생성한 후 아래의 라이브러리들을 설치해주었다.
  <pre><code>pip install SpeechRecognition pyttsx3 pyaudio tensorflow==2.12.0 pandas sentencepiece
  </code></pre>
## 파일
* data.ipynb: 데이터 중 대화 부분만 추출하여 csv 형태로 저장
* transformer.ipynb: 트랜스포머 학습
* transformer_voice_chatbot.ipynb: stt와 tts 적용하여 음성 챗봇 만들고 결과 확인
## 참고 목록
* 트랜스포머: https://wikidocs.net/31379