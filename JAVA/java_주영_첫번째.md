# JAVA 대비 

## Checked Exception과 Unchecked Exception 비교


Java에서 `Checked Exception` 과 `Unchecked Exception`의 차이를 알아보기 전에 먼저 exception 과 error가 어떤 차이를 가지고 있는지를 먼저 알아야한다.

- 예외(exception) : 입력 값에 대한 처리가 불가능하거나, 프로그램 실행 중에 참조된 값이 잘못된 경우 -> 즉, 정상적인 프로그램의 흐름을 어긋나는 것 
- 에러(Error): 시스템에 무엇인가 비정상적인 상황이 발생한 경우 -> 주로 JVM에서 발생시키는 것이며 예외와 반대로 이를 애플리케이션 코드에서 잡으려고 하면 안된다. 
ex) `OutOfMemoryError`, `ThreadDeath`, `StackOverflowError`,  


예외는 크게 `Checked Exception` 과 `Unchecked Exception` 으로 구분할 수 있는데 간단히 말하면 **`RuntimeException`** 을 상속하지 않은 클래스는 Checked Exception, 상속한 클래스는 Unchecked Exception 으로 분류할 수 있다. 

자세한 내용은 다음 그림을 참조하면 된다. 

![exception](https://user-images.githubusercontent.com/37646197/118981775-b01f6a00-b9b5-11eb-811e-8bfb4ae9d900.PNG)

![exception](/JAVA/img/exception.png)

표로 정리를 해보면 다음과 같다. 

| 구분 | `Checked Exception` | `Unchecked Exception` | 
| :----: | :----: | :----: |
| 확인 시점 | 컴파일(Compile)시점 | 런타임(Runtime) 시점 |
| 처리 여부 | 반드시 예외 처리 | 명시적으로 안해도 됨 |
| 트랜잭션 처리| 예외 발생시 롤백(rollback) X | 예외 발생 시 롤백| 
| 종류 | IOException, ClassNotFoundException| NullPointerException, ClassCastException 등 |

여기서 컴파일 시점과 런타임 시점을 생각해볼 필요가 있다. (간단하게 생각해보면)
- `컴파일 시점` : 프로그램을 생성하기 위해 소스코드를 작성하고 작성된 소스코드를 기계어 코드로 변환하는 것을 컴파일 이라고 하며 그렇게 변환되는 과정을 컴파일시점이라고 한다. 
- `런타임 시점` : 컴파일이 끝나고 기계어로 변환된 프로그램이 실행되는 것을 런타임이라고 하며 실행되는 시점을 런타임 시점이라 생각하면 된다. 


## Summary 

자바에서 예외는 RuntimeException 을 상속하는지 안하는지, 명시적으로 처리해야하는지 안해도 되느지에 따라 구분되며 자세한건 결국 자기가 머릿속에서 이해를 해야한다..... 