

> 2024.07.17 차량전장 직무 멘토링이 진행되기 이전까지 프로젝트를 잠시 보류합니다.


# MCU-Software-Essentials

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
   
---

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

---

 - 전기 자동차를 예시로
 - 현재 기어 상태(D, N, P)를 구동모터에 전달해야 하는 경우
 - 상태에 따라 전압을 변경하는 방법이 있음. 5V, 3V, 1V -> 조건문으로 분기하여 구현할 수 있을 것.

 - MCU에 통신 메세지 수신 기능 구현
 - 수신된 메세지 해석 기능 구현

---

 - 모터의 회전력을 얼마나 출력할 것인가?
 - 현재 가속페달이 얼마나 밟혔는지 -> MCU에 페달 밟힌 정도에 따라 모터 공급전류 크기 결정
 - 차량 고장 상태, 열, 움직임 등등.. -> 다양한 변수 조건 처리

---

 - 청소기, 세탁기 조차 다 모터가 있다.
 - 구동모터를 제어해야 한다는 의미...
 - 예 : 사용자의 버튼 조작을 감지한다
 - 버튼에 따라 공급 전류 크기 컨트롤
 - USER의 버튼 조작이 결국 INPUT이라 볼 수 있음.



## 2-1. 임베디드 MCU SW 일반적 구조

![image](https://github.com/MarkSon-42/MCU-Software-Essentials/assets/84828274/208abcde-b707-4fc2-95ed-86f89f13e5d4)

 - cpu : 명령을 수행하는 역할
 - memory : data를 담아두는 역할
  - flash : 전원 off해도 지워지지 않음
  - RAM : 전원 off하면 값 초기화

[Compile]
C ..... > Build .....> machine language

MCU의 Flash에 data를 옮겨야 한다..! (hex, elf같은 빌드 파일)

debugger 

이것은 가장 유명한 제품을 사례로 알아보자.

![image](https://github.com/MarkSon-42/MCU-Software-Essentials/assets/84828274/389720bf-faa6-48a5-b557-1e6f63a8373d)

아주 작은 싱글 코어 마이크로 컨트롤러 구현 위주의 소규모 임베디드 시스템 부터,

복잡한 SoC(System-on Chip)까지 다양한 개발환경을 지원하는 디버거

- TRACE32로 시뮬레이터, 가상 플랫폼, 실제 하드웨어,
- 테스트 자동화 및 지속적인 통합(CI)을 제공
- 통합된 사용자 인터페이스를 통해 모든 것을 제어



  
[summery]

 - 오늘날의 전자장치 대부분은 sw에 의해 제어된다
 - 이 sw를 실행하는 장치가 MCU
 - C언어를 빌드 (빌드하면 elf, hex파일같은게 생성됨)
 - 빌드 : 소스코드를 cpu가 이해할 수 있는 기계어로 변환해주는 작업











 this is a normal code block.
     code block test.


~~~
this is a normal code block.
    code is awesome.
~~~

임베드시스템에서도 메모리는 너무 중요

메모리 주소

cpu가 값을 읽고 쓸 수 있는 저장장치이다.

MCU는 메모리 맵이 있다
- ㅡcu에 할당된 메모리 주소 현황을 나타냄


MCU 예시

![image](https://github.com/MarkSon-42/MCU-Software-Essentials/assets/84828274/d9322074-d2e5-43e3-8b8f-3591f4bd1bb5)


### 패리펄럴 

: MCU 내부에 패리펄럴들이 내장됨


예를들어, 자동차 산업에 쓰이는 CAN이 있음

#### Atmega128  

![image](https://github.com/MarkSon-42/MCU-Software-Essentials/assets/84828274/51ea5bf9-bead-4d6b-bc1e-e3d1415c29d5)

 - MCU는 제조사 마다 제원 정보가 다 다르기 때문에
 - 꼭.. 공식 문서를 잘 읽어봐야 된다
 - 특히 원하는 기능을 구현할 챕터는 꼭..!

[Atmega 제조사 공식 홈페이지의 도큐먼트 모음](https://www.microchip.com/en-us/product/atmega128#document-table)

 - ATmega128/L Datasheet Summary를 인쇄하여 대강의 구조 파악.


#### MCU SW가 할 수 있는 것
- 메모리에서 값을 읽어온다. (read)
- 읽어온 값으로 사칙연산, 조건문 판단, 반복문 수행
- 메모리에 값을 쓴다. (write)

- 레지스터 : 패리펄럴 내부에 있는 작은 메모리
  - 패리펄럴 내부에 여러개의 레지스터 존재
  - 패리펄럴을 컨트롤하는 리모컨 같은 역할을 한다..
  -  
