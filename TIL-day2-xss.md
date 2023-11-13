# TIL-day2-xss

### escaping <script> detection

- using html character code
    
    [https://www.rapidtables.com/web/html/html-codes.html](https://www.rapidtables.com/web/html/html-codes.html)
    

## portswigger xss lab

1. basic xss vulnerablility: just <script>alert(1)</script>

![Untitled](TIL-day2-xss%20fd3b08264785453c9a160a97e22f96a5/Untitled.png)

url 앞에 view-source:으로 source 볼 수 있음

1. 모든 입력 가능 한 곳에 <icode> number 이런 걸 넣어 보고 encode되는지 확인
2. 입력값이 js의 parameter로 들어갈 때 합쳐진 문장이 html에 들어갈 수 이다.

### JS bug 찾기 js 소스 파일 보기

[https://www.youtube.com/watch?v=jpiEhfiTtYg](https://www.youtube.com/watch?v=jpiEhfiTtYg)

- api key
- user id
- id
- pw
- password
- key

subdomain에서 보기