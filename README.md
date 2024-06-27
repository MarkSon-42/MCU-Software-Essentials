# MCU-Software-Essentials

![image](https://github.com/MarkSon-42/MCU-Software-Essentials/assets/84828274/d5deee7a-a44f-49a7-875f-b8f71c15ee08)


[차량 부품 컨트롤러] 신입사원에게 들려주는 - MCU SW 직무 기초 개념완성

### Contents

#### 1. MCU 개념 소개  

#### 2. MCU SW에 대하여

#### 3. Atmega128 & Microchip Studio IDE, STM32... etc

#### 4. Memory

#### 5. Peripheral & Register

#### 6. PCB

#### 7. Assembler & HEX, ELF


---


![image](https://github.com/MarkSon-42/MCU-Software-Essentials/assets/84828274/7f9b5707-ce9c-4483-af0f-e0697fcce185)




## 1. MCU (Micro Controller Unit)
 - MCU는 작은 크기의 컴퓨터이다
 - CPU, RAM 다있다..!
 - 조향, 구동모터, 브레이크, 램프..
 - 자동차 어딘가에 내장되어 있다!

 - 임베디드 SW의 특징
 - 제한된 성능 조건에서 필요한 기능이 모두 수행되도록 구현하는게 목표
 - 최적화가 매우 중요하다
 - "각자의 제품을 제어하기 위한 동작만을 반복해서 수행하고 있다"
   
---

## 2. MCU SW
 - 세탁기, 청소기, 전기차 구동모터
 - 움직인다? -> 모터가 있다..
 - 작은 DC모터를 학습하는 것이 시작
 - 전류를 공급하면 -> 회전력으로 바꾼다
 - 모터 제어 : "회전 방향"과 "회전력의 크기"를 제어하는 것

 - 전기 자동차를 예시로
 - 현재 기어 상태(D, N, P)를 구동모터에 전달해야 하는 경우
 - 상태에 따라 전압을 변경하는 방법이 있음. 5V, 3V, 1V -> 조건문으로 분기하여 구현할 수 있을 것.

 - MCU에 통신 메세지 수신 기능 구현
 - 수신된 메세지 해석 기능 구현

 - 모터의 회전력을 얼마나 출력할 것인가?
 - 현재 가속페달이 얼마나 밟혔는지 -> MCU에 페달 밟힌 정도에 따라 모터 공급전류 크기 결정
 - 차량 고장 상태, 열, 움직임 등등.. -> 다양한 변수 조건 처리

 - 청소기, 세탁기 조차 다 모터가 있다.
 - 구동모터를 제어해야 한다는 의미...
 - 예 : 사용자의 버튼 조작을 감지한다
 - 버튼에 따라 공급 전류 크기 컨트롤
 - USER의 버튼 조작이 결국 INPUT이라 볼 수 있음.



## 2-1. 임베디드 MCU SW 일반적 구조

![image](https://github.com/MarkSon-42/MCU-Software-Essentials/assets/84828274/208abcde-b707-4fc2-95ed-86f89f13e5d4)




