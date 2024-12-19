# 14주차 개별 프로젝트 진행상황

# 1. 프로젝트 개요 및 목표
목표: 스마트 온도 조절기는 사용자가 설정한 온도에 맞게 실내 환경을 자동으로 조절하며, 에너지 효율을 높이고 편안한 실내 환경을 유지하는 시스템입니다. 라즈베리파이와 다양한 센서 및 액추에이터를 활용하여 실내 온도와 습도를 모니터링하고, 난방 및 냉방 장치를 제어합니다.
# 2. 기술 스택 및 하드웨어 구성
하드웨어:
라즈베리파이 4: 메인 컨트롤러로서 데이터 수집, 처리, 제어 신호 전송을 담당.
온도/습도 센서 (DHT22): 실내 온도와 습도를 측정하고 이를 라즈베리파이에 전달.
릴레이 모듈: 난방 및 냉방 장치(예: 히터, 에어컨) 제어용.
소프트웨어 및 기술:
Python: 라즈베리파이에서 실행되는 주요 프로그래밍 언어로, 센서 데이터를 읽고 액추에이터를 제어하는 데 사용.
Flask 또는 Django: 모바일 또는 웹 애플리케이션을 통해 원격으로 온도를 제어하는 시스템 구축.
AI (머신러닝): 사용자의 생활 패턴을 분석하여 자동으로 온도를 조정하는 알고리즘을 개발.
# 3. 하드웨어 설치 및 구성
라즈베리파이 설정:

라즈베리파이 4 모델 B를 설정하고 Raspbian OS를 설치하여 프로젝트에 필요한 소프트웨어 환경을 준비합니다.
GPIO 핀을 통해 DHT22 센서와 릴레이 모듈을 연결합니다.
센서 연결:

DHT22 온도/습도 센서는 라즈베리파이의 GPIO 핀에 연결하여 실시간으로 온도와 습도 데이터를 읽어올 수 있습니다.
센서와 라즈베리파이 간의 데이터 송수신을 위한 Python 라이브러리(DHT 라이브러리)를 설치하여 센서 데이터를 쉽게 처리합니다.
릴레이 모듈 연결:

릴레이 모듈을 라즈베리파이와 연결하여 난방 및 냉방 장치의 전원을 제어합니다.
릴레이를 통해 온도 조절 장치를 켜거나 끄는 신호를 전송합니다.
# 4. 소프트웨어 개발
센서 데이터 수집:

Python을 사용하여 DHT22 센서에서 실시간 온도 및 습도 데이터를 읽어오는 코드를 작성합니다.
데이터는 일정 간격으로 읽혀지고, 이를 라즈베리파이에서 처리하여 온도 조절을 위한 기준을 설정합니다.
온도 자동 조절 시스템:

사용자가 설정한 목표 온도에 맞춰 난방 및 냉방 장치를 제어하는 기능을 구현합니다.
기본적으로 사용자가 설정한 목표 온도보다 온도가 높으면 냉방 장치를 작동시키고, 온도가 낮으면 난방 장치를 작동시킵니다.
웹/모바일 애플리케이션:

Flask 또는 Django를 사용하여 웹 애플리케이션을 개발하고, 사용자가 원격으로 온도를 조절할 수 있도록 합니다.
모바일 애플리케이션에서는 사용자가 실시간으로 온도 및 습도를 확인하고 제어할 수 있는 기능을 구현합니다.
AI 기반 자동 온도 조절:

사용자의 생활 패턴을 분석하여 온도 설정을 자동으로 조정하는 기능을 개발합니다. 예를 들어, 사용자가 자주 집에 있는 시간대에는 온도를 적절하게 조정하고, 외출하는 시간대에는 에너지를 절약하기 위해 온도를 낮추는 방식입니다.
머신러닝 알고리즘을 통해 사용자의 행동 패턴을 학습하고, 이를 바탕으로 온도 조절을 최적화합니다.
# 5. 에너지 사용량 모니터링 및 보고서
에너지 사용량 추적:
온도 조절 시스템이 난방 및 냉방 장치를 제어함에 따라 발생하는 에너지 사용량을 모니터링하는 시스템을 개발합니다.
전력 소비 측정: 전력 소비를 모니터링하는 장치를 추가하여 사용자가 에너지 소비량을 실시간으로 확인할 수 있도록 합니다.
사용자 보고서:
에너지 사용량 및 온도 조절 결과를 주간 또는 월간 보고서 형식으로 제공하여 사용자가 시스템의 효율성을 확인할 수 있게 합니다.
# 6. 테스트 및 최적화
시스템 테스트:

각 구성 요소가 정상적으로 작동하는지 테스트합니다.
센서에서 실시간 데이터를 읽고, 난방 및 냉방 장치를 제어하는 동작이 의도대로 이루어지는지 확인합니다.
AI 알고리즘 최적화:

사용자의 생활 패턴 분석을 위한 AI 모델을 지속적으로 학습시키고, 예측 정확도를 높이기 위해 알고리즘을 개선합니다.
에너지 효율성 최적화:

에너지 사용량을 최소화하면서도 실내 온도를 최적화할 수 있는 방법을 찾고, 시스템을 조정합니다.
# 7. 완성 및 사용자 피드백
사용자 피드백:
프로젝트가 완료된 후, 사용자가 실제로 시스템을 사용하며 겪은 경험을 수집하고, 필요한 개선 사항을 반영합니다.
추가 기능 개발:
사용자 피드백을 바탕으로 더 발전시킬 수 있는 기능을 추가합니다. 예를 들어, 음성 인식 기능을 추가하여 음성 명령으로 온도를 제어하는 기능 등을 고려할 수 있습니다.

# 1. DHT22 센서 데이터 읽기
먼저, 라즈베리파이에서 DHT22 센서를 통해 온도와 습도를 읽어오는 코드입니다.

필요 라이브러리 설치

pip install Adafruit-DHT

코드 

import Adafruit_DHT
import time

sensor = Adafruit_DHT.DHT22
pin = 4

def read_temperature_humidity():
    humidity, temperature = Adafruit_DHT.read_retry(sensor, pin)
    if humidity is not None and temperature is not None:
        print(f"Temperature: {temperature:.1f}C")
        print(f"Humidity: {humidity:.1f}%")
        return temperature, humidity
    else:
        print("Failed to retrieve data from sensor")
        return None, None

while True:
    temperature, humidity = read_temperature_humidity()
    time.sleep(5)

# 온도 조절 시스템 (난방/냉방 제어)
위에서 얻은 온도 값을 바탕으로 난방/냉방 장치를 제어하는 코드입니다. 릴레이 모듈을 사용해 난방기나 에어컨을 제어합니다.

import RPi.GPIO as GPIO

relay_pin_heat = 17
relay_pin_cool = 27

GPIO.setmode(GPIO.BCM)
GPIO.setup(relay_pin_heat, GPIO.OUT)
GPIO.setup(relay_pin_cool, GPIO.OUT)

def control_temperature(temperature, target_temperature):
    if temperature < target_temperature - 1:
        GPIO.output(relay_pin_heat, GPIO.HIGH)
        GPIO.output(relay_pin_cool, GPIO.LOW)
    elif temperature > target_temperature + 1:
        GPIO.output(relay_pin_heat, GPIO.LOW)
        GPIO.output(relay_pin_cool, GPIO.HIGH)
    else:
        GPIO.output(relay_pin_heat, GPIO.LOW)
        GPIO.output(relay_pin_cool, GPIO.LOW)

target_temperature = 22

while True:
    temperature, humidity = read_temperature_humidity()
    if temperature:
        control_temperature(temperature, target_temperature)
    time.sleep(5)


# 웹 애플리케이션을 통한 원격 제어

Flask를 이용해 웹 애플리케이션을 만들어 원격으로 온도를 제어하는 기능을 구현합니다.

from flask import Flask, render_template, request
import Adafruit_DHT
import RPi.GPIO as GPIO
import time

app = Flask(__name__)

sensor = Adafruit_DHT.DHT22
pin = 4

relay_pin_heat = 17
relay_pin_cool = 27
GPIO.setmode(GPIO.BCM)
GPIO.setup(relay_pin_heat, GPIO.OUT)
GPIO.setup(relay_pin_cool, GPIO.OUT)

def read_temperature_humidity():
    humidity, temperature = Adafruit_DHT.read_retry(sensor, pin)
    if humidity is not None and temperature is not None:
        return temperature, humidity
    else:
        return None, None

def control_temperature(temperature, target_temperature):
    if temperature < target_temperature - 1:
        GPIO.output(relay_pin_heat, GPIO.HIGH)
        GPIO.output(relay_pin_cool, GPIO.LOW)
    elif temperature > target_temperature + 1:
        GPIO.output(relay_pin_heat, GPIO.LOW)
        GPIO.output(relay_pin_cool, GPIO.HIGH)
    else:
        GPIO.output(relay_pin_heat, GPIO.LOW)
        GPIO.output(relay_pin_cool, GPIO.LOW)

@app.route("/", methods=["GET", "POST"])
def index():
    temperature, humidity = read_temperature_humidity()

    if request.method == "POST":
        target_temperature = int(request.form["target_temperature"])
        control_temperature(temperature, target_temperature)

    return render_template("index.html", temperature=temperature, humidity=humidity)

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)




# AI 기반 온도 조절 (생활 패턴 분석)

이 부분은 간단한 머신러닝 알고리즘을 사용하여 사용자의 생활 패턴을 학습하고 자동으로 온도를 조절하는 부분입니다. 예시로, 사용자가 특정 시간대에 온도를 선호한다면, 이를 학습하고 다음에 비슷한 시간대에 자동으로 온도를 조절할 수 있습니다. 이를 위해 Scikit-learn 라이브러리와 같은 머신러닝 라이브러리를 사용할 수 있습니다.

import numpy as np
from sklearn.linear_model import LinearRegression
import time

X = np.array([[8], [12], [18], [22]])
y = np.array([20, 22, 24, 21])

model = LinearRegression()
model.fit(X, y)

def predict_temperature(hour):
    return model.predict([[hour]])[0]

while True:
    current_hour = time.localtime().tm_hour
    predicted_temp = predict_temperature(current_hour)
    print(f"Predicted Temperature for {current_hour}:00 is {predicted_temp:.1f}°C")
    time.sleep(3600)


