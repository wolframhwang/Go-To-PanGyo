## 프로세스의 개념

### 프로세스는 실행중인 프로그램
	- 운영체제 입장에서는 작업의 단위
	- 하나의 프로세스가 실행되기 위해서는 자원이 필요하다
		- CPU time
		- memory
		- files,
		- and I/O devices

> OS가 해야할 가장 기본적인 일은 프로세스를 관리하는 것이다.

### 여러개의 프로세스들이 가지는 메모리 섹션
	-Text Section
		- 실행 코드
	- Data Section
		- 전역 변수들
	- Heap Section
		- 동적 할당 영역
		- 메모리 동적으로 할당해주는 영역
	- Stack Section
		- 함수 호출시 쌓이는 섹션을 말한다.
		- 지역변수 저장 영역

> Memory 도표 만들때는 Logical 주소로 시작을한다. 실제 메모리 영역과는 조금다르다.

과정)

메인함수가 Stack Section에 쌓임 -> 코드 내부의 Dynamic 할당, 실행 코드는 Text Section


### As a Process Executres, it changes its State
	- New : 프로세스가 생성된 상태
	- Running : CPU를 점유해서 프로세스의 명령을 로드해서 실행하는 상태를 말함 
	- Wating : CPU를 점유하고있는 프로세스의 작업을 기다리는 상태 (ex. IO를 했을때, CPU점유하다 양보하는 상태)
	- Ready : 프로세스가 CPU를 바로 점유할수 없기 떄문에 Ready Queue에서 실행을 대기한다.
	- Terminated : 프로세스의 모든 과정이 끝났을 때를 말한다.

### PCB(Process Control Block) or TCB(Task Control Block)
	- 프로세스가 가질수있는 모든 정보를 담아서 구조체로 프로세스를 관리한다.

### PCB가 가지고있는 정보
	- Process State
	- Program Counter -> (Instruction Register)에 프로그램 카운터에있는 값을 통해 메모리에서 Fetch해온다.
	- CPU register
	- CPU-Scheduling Information
	- Memory-management information
	- Accounting information
	- I/O status information

### A Process
	- A program that performs a single thread of execution.// 실행이 한줄로 된다는 얘기.. 우리가 아는 스레드와는 다르다.
	- The single Thread of control allows the process to perform
		- only one task at a time
	- Modern Operating systems have extended the process concept
	- and thus to perform more than one task at a time

> Concurrency 를 제공하는 가장작은 단위인 스레드를 알아보자.

### A thread is a lightweight process
	- Chapter 4 explores multithreading in detail

### The Objective of multiprogramming is
	- to have some process running at all times
	- so as to maximize CPU utilization

### The Objective of time Sharing is
	- CPU를 계속 스위칭해서 동시에 도는것 처럼 보이게 한다.

### Scheduling Queues
	- 어떤 프로세스가 시스템에 들어오면 일단 Ready Queue에 진입한다.
	- 실행을 하고 다 쓰게 되면 다시 Ready Queue로 간다.
	- Wating Queue와는 위치가 다르다.

### Context Switch
	- 문맥이라는것은 프로세스 입장에서 프로세스가 사용되고 있는 상태를 Context라고하고 이 정보는 모두 PCB에 저장되어있다
	- 즉 문맥은 다시 말하면 PCB다.
	- 문맥 교환이라는 것은 어떤 Task가 CPU Core를 다른 프로세스 한테 넘겨 주는것 인데, 두가지 일을한다.
		- 현재 프로세스의 State를 저장한다.
		- 새로 획득할 프로세스의 State를 복원한다.
### An operating System must provide a mechanism for
	- 프로세스를 생성하고,
	- 프로세스를 종료해야한다.

### 프로세스가 어떤 새로운 프로세스를 생성할수 있다.
	- Creating Process : a Parent Process
	- Created Process : a Child Process
ex) fork()


### 프로그램 Terminates
	- 마지막 문장을 실행할때 마무리가 된다.
	- exit() 시스템 콜을 통해 OS에게 삭제 요청을 한다.
	- OS 는 자원을 메모리상에서 해제한다.

### Zombie and Orphan
	- 좀비 프로세스 : 자식 프로세스가 부모 프로세스보다 먼저 죽은 상황 
	- Orphan 프로세스 : 부모 프로세스가 wait()를 호출하지 않고 종료한 상황
