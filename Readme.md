# 조도에 따라 자동으로 출력을 조절하는 헤드라이트

# 결과
</br>
<img src="/pic/led_test.GIF" width="40%" height="30%" title="opamp_1_off" alt="opamp_1_off"></img>

# 회로도
 - 무료 버전 사용으로 75node 이상에서 사용이 어려워 여러 부분으로 나누어 제작하였습니다.
 - 비교기
</br>
<img src="/pic/비교기.png" width="40%" height="30%" title="opamp_1_off" alt="opamp_1_off"></img>
 - 전압 레귤레이터
</br>
<img src="/pic/전압 레귤레이터 회로.png" width="40%" height="30%" title="opamp_1_off" alt="opamp_1_off"></img>
 - 조도 센서 회로 (R3= 조도 센서)
</br>
<img src="/pic/병렬과직렬/가능한영역최대.png" width="40%" height="30%" title="opamp_1_off" alt="opamp_1_off"></img>

# op-amp 출력 결과
- 1번 op-amp의 출력 결과 (On / Off)
</br>
<img src="/pic/opamp_1_off.jpg" width="40%" height="30%" title="opamp_1_off" alt="opamp_1_off"></img>
<img src="/pic/opamp_1_on.jpg" width="40%" height="30%" title="opamp_1_off" alt="opamp_1_off"></img>
- 2번 op-amp의 출력 결과 (On / Off)
</br>
<img src="/pic/opamp_2_off.jpg" width="40%" height="30%" title="opamp_1_off" alt="opamp_1_off"></img>
<img src="/pic/opamp_2_on.jpg" width="40%" height="30%" title="opamp_1_off" alt="opamp_1_off"></img>


## 사용한 부품
 - NE5532n
 - LM317
 - cds Cell (GL3526)

# 전압 레귤레이터 회로
 - lm317 IC 사용하였습니다.
 - R2/R1 = 6.6이 되도록 설정하였습니다.
 - V_out = 9.5 = 1.25*(1+6.6)
 - 9V로 설정한 이유는 다른 파트의 부품을 연결하기 위해 포함하였습니다.

# 논리회로
 - NE5532n  사용하였습니다.
 - 2개의 op-amp(비교기)
 - 비반전 입력에는 조도 센서를 포함한 병렬 연결의 전압
 - 반전 입력에는 전압분배(0.5*V_cc,0.25*V_cc)의 구간의 전압
 - 조도 센서의 저항이 증가함에 따라 비반전 입력 전압이 증가하게 되며 출력이 H가 되도록 하였습니다.

## 조도 센서
 - cds Cell (GL3526) 사용
 - 조도 센서 특성
 - 1k ~ 600k의 저항을 갖으며 높을수록 빛이 없는 상태
 - 전체 저항의 안정성을 조절하기 위해 5k옴의 직렬 저항 연결
 - 주 측정 영역이 1k~20k옴( 100Lux에서 5lux) 이내이므로 이외 영역에서 가변 저항의 영향을 줄이기 위해 병렬 연결로 10k옴을 연결하였습니다.

## 조도센서 측정 결과 
 - 2V ~ 5V까지의 전압을 확인하였습니다.
 

## 비교기의 출력 결과
 - 밝은 환경 - 두 비교기 모두 0을 출력을 확인하였습니다.
 - 적당한 환경 - 1개의 비교기만 8V의 전압(Hight)을 출력을 확인하였습니다.
 - 어두운 환경 - 2개의 비교기만 8V의 전압(Hight)을 출력을 확인하였습니다.

# 신호 구동 회로
 - led 특성
 - 12V의 전압, 전류는 datasheet을 구할 수 없어 일반 led 특성에 따라 20mA

 - 각  led에 직렬 저항 220옴 연결하여 전력 감소를 최소화 
 - 조도 센서의 소스 전원을 이용할 경우, 전류가 부족할 것으로 판단하여 싱크 구동 방식으로 작업하였습니다. (소스 전원으로 구동 희망시, 비교기 비/반전만 반대로입력)


# 시행 착오

1. 조도 센서 회로 안정성

 - 초기 조도 센서를 고정 저항 1개와 직렬 연결하여 전압 분배로 사용하였습니다.
 - 시뮬레이션 결과 생각보다 큰 저항 변화로 불안정하다고 판단하였고, 병렬 연결을 통해 제어하는 방식을 고안하였습니다.
- 전체 저항에 직렬 저항을 추가함으로써, 병렬 연결에서의 가변 저항의 문제를 해결하였습니다.

2. 소스 전원,싱크 전원
 - 싱크 구동 방식을 연결함에 있어, 몇번의 시행착오 후 이해하였습니다.

# 추가할 사항
 - 거리 유지 센서를 통해 pid 제어로 led의 전류 제어 회로
 - mcu의 환경 분석을 통해 pid 변수 제어 회로

# 테스트 이미지
</br>
<img src="/pic/led_test_1.PNG" width="40%" height="30%" title="opamp_1_off" alt="opamp_1_off"></img>
</br>
<img src="/pic/led_test_2.PNG" width="40%" height="30%" title="opamp_1_off" alt="opamp_1_off"></img>
</br>
<img src="/pic/led_test_3.PNG" width="40%" height="30%" title="opamp_1_off" alt="opamp_1_off"></img>
