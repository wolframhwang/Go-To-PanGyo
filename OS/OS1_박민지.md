# 1. 운영체제 / 210516


## 운영체제 역할

1. 시스템 자원(system Resource)관리자
    - Operation System 또는 os
    - 시스템 자원(System Resource)= 컴퓨터 하드웨어
        - CPU(중앙처리장치), Memory(DRAM, RAM)
        - I/O Devices(입출력 장치)
            - 모니터, 마우스, 키보드, 네트워크
        - 저장매체: SSD,HDD(하드디스크)

### 컴퓨터 하드웨어는 스스로 할 수 있는 것이 없다.

1. CPU:각 프로그램이 얼마나 CPU를 사용하지 결정할 수 없다.

2. Meomory:각 프로그램이 어느 주소에 저장되어야하는지, 어느 정도의 메모리 공간을 확보해줘야 하는지를 결정할 수는 없다.

3. 저장매체(HDD,SSD): 어떻게, 어디에 저장할지는 결정할 수 없다.

4. 키보드/마우스: 스스로 표현 불가능

-->  그래서 운영체제가 필요함


### 대표적인 운영체제

- Window OS, Mac OS, UNIX
- UNIX OS
    - UNIX계열 OS
         - UNIX와 사용법이나, os구조가 유사
    - LINUX(리눅스) OS
         - 프로그래머, 전공자


1. 시스템 자원(System Resource) 관리자
2. 사용자와 컴퓨터간의 커뮤니케이션 지원
3. 컴퓨터 하드웨어와 응용프로그램을 제어

<table border="1" width=250>
    <tr align="center">
        <td colspan= "2">User Programs</td>
    </tr>
    <tr align="center">
       <td rowspan="3">OS</td>
       <td>User Interface</td> 
    </tr>
    <tr align="center">
        <td>System call</td>
    </tr>
    <tr align="center">
        <td>Management</td>
    </tr>
    <tr align="center">
        <td colspan = "2">Hardware</td>
    </tr>

</table>



## 응용 프로그램이란?

- 프로그램 = 소프트웨어
- 소프트웨어 = 운영체제, 응용 프로그램(엑셀, 파워포인트, 내가 만든 프로그램)
- 응용프로그램 = Application(일반 PC에서의 프로그램) = App(스마트폰에서 응용 프로그램)

### 운영체제와 응용 프로그램간의 관계

- 운영체제는 응용프로그램을 관리
    - 응용 프로그램을 실행시킨다.
    - 응용 프로그램 간의 권한을 관리해준다.
        - 관리자 권한으로 실행
    - 응용 프로그램을 사용하는 사용자도 관리
        - 로그인

-  응용 프로그램은 누구나 만들 수 있다.
    - 응용 프로그램에 무한 반복문을 넣었다.
    - 응용 프로그램을 잘 못 작성해서, 프로그램이 다운
    - 모든 파일 삭제 막기(권한/사용자 관리)
    - => 응용프로그램으로 인해 생길 수 있는 문제들을 운영체제가 관리한다.

1. 응용프로그램을 관리한다.
2. 시스템 자원을 관리한다.
3. 사용자와 컴퓨터 간의 커뮤니케이션을 지원한다.

> 운영체제의 목표 : 사용자가 사용하는 응용 프로그램이 효율적으로, 적절하게 동작하도록 지원

> 운영체제는 응용 프로그램이 요청하는 시스템 리소스를 효율적으로 분배하고 지원하는 소프트웨어