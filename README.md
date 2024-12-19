# 14주차 개별 프로젝트 진행상황

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


