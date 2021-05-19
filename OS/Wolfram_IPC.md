# Interprocess Communication

### Processes Executing concurrently may be

	- Independent하게 실행되거나, 서로 영향을 Cooperate하게 실행될수 있다.



### 프로세스가 Independent 하다는 것은?


	- 어떤 프로세스와도 자원을 공유하지 않는 것을 말함


### 프로세스가 cooperate 하다는 것은?


	- 서로 다른 프로세스에게 영향을 주거나 또는 받는 상황


	- 어떤 프로세스가 데이터를 공유하거나 메세지를 주고 받는 상황



> 이렇게 자원이 공유되거나 메세지의 주고받음이 필요할때 해결책은 무엇인가?



### IPC - Inter-Process Communication


	- Cooperating processes require an IPC mechanism


		- 서로 데이터 교환을 하는것을 허용하는것


		- 서로에게 “send data”, 그리고 “receive data”가 가능하다는 것


### 두가지 IPC 모델을 보자


	- shared memory( 공유 메모리 )


	- message passing



#### Shared Memory


	- fork같은 것이있다.


	- Process A에 의해 Process B라는 자식 프로세스가 생겨났다면


	- 해당 프로세스들은 데이터를 공유할수 있다.


#### Message Passing


	- 운영체제에 메세지를 맡기는 것


	- 예를들어 내(Process A)가 송금을하면 은행(운영체제)에서 다른사람(Process B)의 통장에 입금을 하고 확인 메세지를 보내는 과정을 생각해볼수 있다.



### Consider the Producer-Consumer Problem


	- 생산자가 정보를 생산하고, 정보를 소비하는 모델을 상상해보자.


	- 컴파일러가 어셈블리 코드를 생산해내고, 어셈블러는 그것을 소비한다.


	- 웹 서버는 HTML파일을 생산해내고, 브라우저는 그것을 소비한다.



### 두개의 프로세스 문제를 생각해보자


	- 생산자 프로세스, 소비자 프로세스가 있다고 가정하자


	- 소비자 프로세스는 영상을 받아서 화면에 뿌려줘야한다


	- 이러한 상황을 해결하기 위한 방법으론 무엇이있을까


### Shared Memory


	- Process A, B는 각각의 역할만 하면된다.


	- Context Switching을 하면서 Concurrently하게 실행이 될것이고


	- 그렇다면 생산자 Process A는 메모리에 채워주기만 하면되고


	- Process B는 소비자로서 메모리를 소비만 하면된다.



### Message Passing


	-  OS가 메세지 패싱을 제공한다


	- Pipe 사용



### Non Blocking / Blocking


	- Non Blocking - Async 


	- Blocking - Sync

