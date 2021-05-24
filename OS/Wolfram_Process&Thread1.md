# Process & Thread


### 프로세스(Process)란?
- Process란, 실행 중에 있는 프로그램을 의미한다.
- 스케줄링의 대상이 되는 작업(Task)와 같은 의미로 사용이 된다.
- 프로세스 내부에는 최소 한개 이상의 Thread 를 가지고 있고, 실제로는 Thread단위로 스케줄링이 이루어진다.
- 하드디스크에 있는 프로그램을 실행하면, 실행을 위해 메모리에 프로그램에 대한 정보가 적재되고, 할당된 메모리 공간으로 bin코드가 올라가게 된다. 이 순간부터 프로세스 라고 불리게 된다.
### 프로세스의 메모리 구조
- Code 영역 : 프로그램을 실행시키는 실행 파일 내의 명령어들이 올라간다.
- Data 영역 : 전역변수와 static 변수 할당.
- Heap 영역 : 동적 할당을 위한 메모리 영역
- Stack 영역 : 지역변수, 함수 호출 시 전달되는 인자를 위한 메모리 영역
### 프로세스 Scheduling
- CPU는 한개인데 동시에 실행되어야할 프로세스가 여러개인 경우
    - CPU가 특정한 순서를 가지고 여러가지 프로세스를 고속으로 실행해서 동시에 되는것처럼 한다.
- Scheduling
    - CPU할당 순서나 방법을 결정하는 일
    - 일정한 기준 = Scheduling Algorithm (흔히 Round Robin)
### 프로세스 상태 변화
- 프로세스의 상태는 크게 Ready, Blocked, Running  상태가 존재한다.
- new->ready : new상태에서 프로세스가 생성이 되면 Kernel에서 Ready Queue에 진입하게 된다.
- Ready->running : Ready Queue에 있는 프로세스들을 OS가 스케줄링 알고리즘을 토대로 Running상태로 가야할 프로세스를 CPU로 할당한다. 이렇게 되면 프로세스는 Running상태에 진입하게 된다.
- Running -> Ready : 현재 Running 상태에 있는 프로세스 A보다 Ready Queue에서 대기하고 있는 프로세스 B가 우선순위가 높을때,  preemptive schedule인 경우 프로세스 A는 Ready Queue로 돌아오고, B는 Running 상태로 진입하여 CPU를 선점하게 되며, 이러한 상태를 Context Change(문맥 교환) 이라고 한다.
- Running -> Blocked : 현재 Running상태에 있는 프로세스 A에서 입출력 이벤트가 발생했을때, 프로세스 A가 Blocked 로 진입하게 된다.
- Blocked -> Ready : 입출력 이벤트가 종료된 프로세스는 다시 Ready Queue로 진입하게 된다.
- Running -> Terminate: 프로세스 종료


### 스레드(Thread)란?
- 프로세스의 최소 실행 단위.
- Thread는 Process 내부의 작업 흐름, 단위에 해당한다.
- Thread는 한 Process 내부에 적어도 하나 존재한다.
- Thread가 여러개 존재하는 것을 Multi Thread 라고 한다.
- Multi Thread 에서 각 Thread 끼리는 프로세스의 일정 메모리 영역을 공유하게 된다
- 일정 메모리 영역을 공유하기 때문에 동일한 프로세스 내부의 Thread간 문맥전환(Context Switching)이, 프로세스 간의 문맥전환(Context switching)을 할때 보다 빠르다.
