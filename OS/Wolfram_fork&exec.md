### Fork

- system call 인 fork()를 통해 우리는 자식 프로세스를 생성할수 있다.
	 ex) pid_t pid = fork();
> 이렇게 생성된 부모, 자식 프로세스의 공통점은 무엇인가?

	- 부모와 자식은 같은 Instruction을 실시한다.
> 그렇다면 차이점은 무엇인가?

	- Parent Process : pid != 0
	- Child Process : pid == 0
	- 자식 프로세스는 부모의 Address Memory 를 그대로 복사해온다.
	- 복사 하는 만큼, 자식 프로세스가 생겨난 부분에서 부터 Instrcution이 수행된다.

### example
    - 한가지 예제를 보자.
```
#include<stdio.h>
#include<unistd.h>
#include<sys/wait.h>

int main() {
        fork(); //1 
        fork(); //2
        fork(); //3
        return 0;
}
```
  - 총 몇개의 프로세스가 생성이 되는가?
  - A: 총 8개의 프로세스가 생성이 된다.
  - fork로 인해 생성되는 자식 프로세스는 자신이 생겨난 지점에서 부터 Instruction이 수행이된다.
  - 부모 프로세스 : 1, 2, 3 
  - 1번 자식 프로세스 : 2, 3
  - 2번 자식 프로세스 : 3
  - 전체 : 부모, 부모->1, 부모->2,부모->3, 부모->1->2, 부모->1->3, 부모->2-3, 부모->1->2->3
  - 총 8개가 생성이 되고 수식적으로는 2^n(n = fork()수) 가 된다.
  
  
