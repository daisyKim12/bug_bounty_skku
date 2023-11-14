# TIL-day4-ov

- 매크로 id 뚫어보기
- sql injection
- file upload
- 수강신청 사이트 매크로

## SQL injection

- aa’ or ’1’=’1
- michael12’—
- blind sql injection with time delay

‘||pg_sleep(10)—

![Untitled](TIL-day4-ov%2040dda459dace4c0ab533458966f14e03/Untitled.png)

## Command Injection

Command Injection은 쉘을 실행시키는 로직을 이용한 공격이다. 시스템 권한이 탈취되는 것이나 마찬가지기 때문에 매우 치명적이다.

![https://kciter.so/images/2021-02-28-basic-web-hacking/command-injection.png](https://kciter.so/images/2021-02-28-basic-web-hacking/command-injection.png)

WebShell이 열린거나 마찬가지

각 언어마다 쉘 명령을 실행시키는 함수가 존재한다. 예를 들어, Java의 `System.runtime()`이나 `Runtime.exec()`, Python의 `exec()`, `os.system()` 등이 있다. 마찬가지로 각 언어마다 존재하는 `eval()` 함수도 매우 취약하다.

가장 위험한 취약점이다. 서버의 shell에 들어갈 수 있다.

![Untitled](TIL-day4-ov%2040dda459dace4c0ab533458966f14e03/Untitled%201.png)