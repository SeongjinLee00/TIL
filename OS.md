# Operating System

Reference : http://www.kocw.net/home/search/kemView.do?kemId=1046323

[TOC]

# Chapter 1. Introduction to Operation Systems

OS : 협의의 운영체제(커널) : 운영체제의 핵심 부분으로 메모리에 상주하는 부분

​		광의의 운영체제 : 커널 뿐 아니라 각종 주변 시스템 유틸리티를 포함한 개념



운영체제의 목적 : 자원을 효율적으로 관리, 사용자로 하여금 편리하게 사용할 수 있게 해줌



운영체제의 분류 

 1. 동시 작업 가능 여부 : 싱글태스킹 vs 멀티태스킹

 2. 사용자의 수 : 단일사용자(single user) vs 다중사용자(multi user)

 3. 처리 방식 : 일괄처리(batch processing) vs 시분할(time sharing) vs 실시간(realtime)

    **시분할 방식은 데드라인을 보장하지는 않음, 사람이 많으면 동작 느려짐**

    실시간? 정해진 시간안에 어떤 일이 반드시 종료됨이 보장되어야 함



# Chapter 2. System Structure & Program Execution

## System Structure

운영체제를 설명하기에 앞서 하드웨어에 대해 설명

![image-20220502224228916](OS.assets/image-20220502224228916.png)

cpu : 매 클럭마다 메모리에서 instruction을 읽어서 수행하는 일만 계속함

register : 메모리보다 빠르면서 정보를 저장할 수 있는 작은 공간

​	program counter register도 여기에 있음

mode bit : 지금 실행되는게 운영체제(0)인지(=커널모드, 시스템모드, 모니터모드) 사용자 프로그램(1)(=사용자모드) 인지

mode bit이 0일때는 cpu는 뭐든지다할수있음, 1일때는 제한된 동작만 가능(I/O 접근은 안됨)

인터럽트 라인 : CPU는 메모리랑만 노는데, 다른 애가 일 끝냈는지 알려고

​	cpu는 매 인스트럭션을 수행할 때 마다 인터럽트 라인을 체크함

​	인터럽트가 걸리면 기본적으로 cpu가 os에게 넘어감

타이머 : 일정 시간간격마다 인터럽트를 걸어줌. cpu 독점을 방지하기 위해서.



device controller : IO device에는 전담하는 작은 cpu가 붙어 있음

local buffer : device controller의 작업 공간, I/O는 device와 local buffer 사이에서 일어남



시스템콜 : 사용자 프로그램이 운영체제의 서비스를 받기 위해 인터럽트 라인을 세팅하고(소프트웨어 인터럽트) 커널 함수를 호출하는 것<->하드웨어 인터럽트(by I/O)



DMA(Direct Memory Access) : IO 장치에 의해 인터럽트가 너무 자주 걸려서 생기는 비효율을 방지.

device controller가 buffer storage의 내용을 메모리에 block 단위로 전송, 바이트 단위가 아니라 블록 단위로 인터럽트를 발생하도록 함

cpu도, dma controller도 메모리에 접근할 수 있으므로 이를 memory controller가 중재하는 역할



사용자 프로그램이 I/O를 요청하는 방법(=운영체제의 서비스를 받기 위해 커널 함수를 호출)

mode bit을 0으로 바꾸고 interrupt를 건다. 이를 system call이라고 한다. 이러한 interrupt를 또 다른 말로 소프트웨어 인터럽트 혹은 trap 이라고 부른다.

(참고 : 타이머, IO 컨트롤러 인터럽트 등을 하드웨어 인터럽트라고 한다)

I/O를 위해서는 두 가지 interrupt가 모두 걸림 : I/O 요청 -> trap, I/O 완료 -> interrupt



## Interrupt

인터럽트 당한 시점의 레지스터와 program counter를 save한 후, CPU의 제어를 인터럽트 처리 루틴에 넘기게 됨

Interrupt vector : 해당 인터럽트의 처리 루틴 주소를 가지고 있음

Interrupt Service Routine(=인터럽트 처리 루틴, 인터럽트 핸들러) : 해당 인터럽트를 처리하는 커널 함수



Interrupt의 종류 : interrupt(하드웨어), trap(소프트웨어)

​	trap의 예시 : Exception, system call

키보드 컨트롤러가 interrupt를 걸면, local buffer의 내용을 memory에 복사하고, 키보드 I/O를 요청했던 프로세스에는 CPU를 얻을 수 있다고 알려야함

Timer가 interrupt를 걸면, CPU를 뺐어서 다른 프로레스에 넘겨야함



## 동기식 입출력과 비동기식 입출력

- 동기식 입출력 (synchronous I/O)
  - I/O 요청 후, 입출력 작업이 완료된 후에야 제어가 사용자 프로그램에 넘어감
  - 구현 방법1
    - I/O가 끝날 때까지 한 프로그램에서 CPU를 점유하여 낭비시킴
    - 매 시점 하나의 I/O만 일어날 수 있음
  - 구현 방법2
    - I/O가 완료될 때까지 해당 프로그램에게서 CPU를 뺐어 다른 프로그램에 넘김
    - I/O 처리를 기다리는 프로그램들을 줄세움
- 비동기식 입출력 (asynchronous I/O)
  - I/O가 시작된 후 입출력 작업이 끝나기를 기다리지 않고 제어가 사용자 프로그램에 즉시 넘어감
- 두 경우 모두 인터럽트를 통해 I/O가 끝났음을 알림



## 프로그램의 실행 (메모리 load)

![image-20220426203606614](OS.assets/image-20220426203606614-16598970704823.png)

- File system에 저장되어있는 프로그램의 실행파일을 실행하면, 그 프로그램 만의 독자적인 주소 공간이 생김
  - 주소 공간은 아래의 영역으로 구성됨
    - code
      - CPU에서 실행할 기계어 저장
    - data
      - 프로그램이 사용할 변수 등의 자료구조 저장
    - stack
      - 함수를 호출하고 리턴할 때 데이터를 저장
  - 이 주소 공간 전체를 실제 메모리에 올리면 메모리가 낭비됨
    - 당장 필요한 부분만 메모리에 올림
      - 메모리에 올라간 코드가 필요없으면 버리거나, 하드디스크를 메인 메모리의 연장선으로 사용하는 swap area에 넘김
    - 이런 특성 때문에 Virtual memory라고 부름
    - 하드웨어의 도움을 받아 가상 메모리의 주소를 실제 메모리 주소로 변환(=address traslation)해주는 계층 존재



### OS 커널 주소 공간의 내용

- code

  - 커널 코드
    - 시스템 콜, 인터럽트 처리 코드
    - 자원 관리를 위한 코드
    - 편리한 서비스 제공을 위한 코드

- data

  - 하드웨어를 관리하고 통제하기 위해 OS가 사용하는 자료구조
  - 각 프로그램을 관리하기 위한 자료 구조 (PCB)

- stack

  - 사용자 프로그램 마다 커널 스택을 별도로 둠

    

# Chapter 3. Process

Process is a program in execution

![image-20220503114346195](OS.assets/image-20220503114346195.png)



프로세스의 문맥 : 프로세스의 현재 상태를 나타내는데 필요한 모든 요소

1. 하드웨어 문맥 : 레지스터가 무슨 값인가, 프로그램 카운터가 어딜 가리키고있는가
2. 프로세스의 주소 공간 : code, data, stack
3. 프로세스 관련 커널 자료 구조 : PCB, Kernel stack



![image-20220503124153196](OS.assets/image-20220503124153196.png)

프로세스의 상태

1. Running : CPU를 잡고 instruction을 수행중인 상태
2. Ready : CPU를 기다리는 상태(메모리 등 다른 조건을 모두 만족하고)
3. Blocked(wait, sleep) : 당장 instruction을 수행할 수 없는 상태 ex) 디스크에서 파일을 읽어와야 하는 경우
4. (New) : 프로세스가 생성 중인 상태
5. (Terminated) : 수행이 끝난 상태(종료 중인 상태)
6. Suspended : 뒤에서 설명



![image-20220503124734937](OS.assets/image-20220503124734937.png)



**문맥 교환**

CPU를 한 프로세스에서 다른 프로세스로 넘겨주는 과정

1. CPU를 내어주는 프로세스의 상태를 그 프로세스의 PCB에 저장함
2. CPU를 새롭게 얻는 프로세스의 상태를 PCB에서 읽어옴

System call이나 Interrupt가 생긴다고 반드시 context switch가 일어나는 것은 아님. 물론 일부 context를 PCB에 저장하긴 해야한다고함

Kernel mode 이후 프로세스가 바뀔때만 일어남(ex : timer interrupt, I/O 요청 system call). 이때는 캐시메모리를 날려야하므로 오버헤드가 크다



**스케줄러**

Long-term scheduler(job scheduler)

- 시작 프로세스 중 어떤 것들을 ready queue로 보낼지 결정
- 프로세스에 memory를 주는 문제
- degree of multiprogramming(쉽게 말하면, 메모리에 프로그램 몇개 올릴지) 제어
- time sharing system에는 보통 장기 스케줄러가 없음(무조건 ready)



Short-term scheduler(CPU scheduler)

- 어떤 프로세스를 다음번에 running시킬지 결정
- 프로세스에 CPU를 주는 문제
- 충분히 빨라야 함 (ms단위)



Medium-term scheduler(swapper)

- 시분할 시스템의 degree of Multiprogramming을 제어

- 여유 공간 마련을 위해 프로세스를 메모리에서 디스크로 쫓아냄

- 위의 6. suspended : 외부적인 이유로 프로세스의 수행이 정지된 상태(메모리에 너무 많은 프로세스가 올라와 있을 때 디스크로 swap out)

  blocked는 자신이 요청한 event가 만족되면 ready, suspended는 외부에서 resume해주어야 active



**쓰레드 **

프로그램 실행의 단위. 같은 일을 하는 프로세스 여러개 띄우고 싶을 때, 주소공간 하나만 만들고 각 쓰레드마다 프로그램의 다른 구간을 수행할 수 있도록 하면 됨.

쓰레드의 구성 : program counter, register set, stack space

공유하는 부분(=task) : code, data, OS resources



쓰레드를 사용하면 응답성이 빨라지고, 자원을 공유할 수 있고, 경제적(빠름), multiprocessor 환경에서 병렬처리



커널쓰레드 vs 유저쓰레드



# Chapter 11. Disk Management and Scheduling



**Disk Structure**

- logical block : 

  디스크의 외부에서 보는 디스크의 단위 정보 저장 공간들

  주소를 가진 1차원 배열처럼 취급

  정보를 전송하는 최소 단위

- sector : Logical block이 물리적인 디스크에 매핑된 위치

  0번 섹터는 당연히 최외곽 실린더의 첫 트랙에 있는 첫 번째 섹터, 여기에 부트로더가 들어감



![image-20220610124835528](OS.assets/image-20220610124835528.png)

![image-20220610125955371](OS.assets/image-20220610125955371.png)



**Disk Scheduling Algorithm**

FCFS, SSTF, SCAN, C-SCAN, N-SCAN, LOOK, C-LOOK

![image-20220610130434844](OS.assets/image-20220610130434844.png)

![image-20220610130445957](OS.assets/image-20220610130445957.png)

![image-20220610130739949](OS.assets/image-20220610130739949.png)

![image-20220610130859996](OS.assets/image-20220610130859996.png)

![image-20220610131001731](OS.assets/image-20220610131001731.png)

![image-20220610131940981](OS.assets/image-20220610131940981.png)

![image-20220610132442469](OS.assets/image-20220610132442469.png)