# TIL-day2-ov

### Recon

subdomain을 찾으면 일단 dirb를 이용해서 directory를 뒤진다.

### URL Hacking

소스 코드를 보면서 파일을 찾고 갈 수 없는 페이지도 본다.

### Installing Juice Shop

**OWASP이란**: Open Web Application Security Project의 약자로

2001년 12월에 창립된 오픈소스 온라인 보안 단체이다. 주로 웹에 관한 보안 취약점 등을 연구하며 발표한다.

**OWASP TOP 10**: 웹 어플리케이션 취약점 중 발생 빈도가 매우 높으며

보안상 크게 영향을 줄 수 있는 보안 고 위험군 상위 10개 항목을 선정하여

발표하는 보고서이다.

1. Injection : 인젝션

2. Broken Authentication : 인증 취약점

3. Sensitive Data Exposure : 민감한 데이터 노출

4. XML External Entities (XXE) : XML 외부 개체

5. Broken Access Control : 취약한 접근 통제

6. Security Misconfiguration : 잘못된 보안 구성

7. Cross-Site Scripting (Xss) : 크로스사이트 스크립팅

8. Insecure Deserialization : 안전하지 않은 역 직렬화

9. Using Components with Known Vulnerabilities : 알려진 취약점이 있는 구성요소 사용

10. Insufficient Logging & Monitoring : 불충분한 로깅과 모니터링

**OWASP Juice Shop**이란: 

OWASP가 만든 주요 웹 취약점을 테스트할 수 있는 실습용 서버이다. 2010년 이후 PHP 기반의 웹 어플리케이션이 많이 줄어들고 JavaScript와 관련 프레임워크들로 제작된 웹 앱이 주를 이루기 시작했는데 주스샵은 이러한 변화를 수용하여 NodeJS, Express, Angular 등을 이용해 만들어졌다. OWASP TOP 10의 모든 취약점들이 들어가 있어 모의 해킹을 공부하고 실습하기에 더없이 좋은 환경이다.

### IDOR & BL

IDOR(Insecure Direct Object Reference): 직역하면 안전하지 않은 직접 객체 참조이며 **부적절한 인가**라고 표현한다.

- OWASP(Open Web Application Security Project, 소프트웨어 보안 발전을 위해 노력하는 비영리 단체)에서 3~4년 주기로 발표하는 웹 취약점 TOP 10의 1위인 **Broken Access Control**과 연관이 있다.
- 서버에서 수행해야할 권한 검증 및 접근 제어를 클라이언트에서 수행하는 경우가 잦아지면서 많이 발견되는 추세이다.
- 수평적/수직적 권한 상승이 발생하며, 이를 통해 타 사용자 정보에 접근해 유출하거나 기존 권한으로는 사용이 불가능한 기능을 이용하는 문제가 생긴다. 수평적 권한 상승의 경우 동일한 권한을 가진 다른 사용자의 객체에 접근할 수 있을 때를 말한다. 수직적 권한 상승의 경우 지닌 권한을 넘어서는 기능을 수행할 수 있을 때를 말한다.
- 가장 많은 양의 버그를 차지한다.

가능한 것 

1. skip login page
2. 다른 사람 계정에 들어가지
3. 다른 사람 피드에 글 쓰기
4. 마치 다른 사람인 것처럼 기록 남기기

방법

- 계정이 두 개 필요하다 그래야지 test할 수 있다. 그래야 버그를 확인할 수 있다.
- Admin 전용 hidden field 찾기. <input type = “hidden” name=”admin” value = “no”> 내 계정을 Admin으로 바꾸기.
- 쿠키내에 Userid 를 바꿔서 접근이 가능한지 확인한다.
- 쿠키를 복사하고 나갔다 들어와서 붙여넣기 했을 때 확인하기.
- 대부분 burp를 통해서 한다.

권한 확장

![Untitled](TIL-day2-ov%2048682865a3cf4bd1a7e2ec03d67a2081/Untitled.png)

### SQL injection

기존 SQL에 **악의적인 SQL 구문을 삽입**하여 데이터 탈취, 삭제 등을 할 수 있다. 대부분 의 SQL 지원 라이브러리에서 SQL Injection을 방어해준다. Prepared Statement로 query를 전달하는 방법으로 인해 많은 SQL Injection은 예방된다.

### Path Traversal

[Path Traversal | OWASP Foundation](https://owasp.org/www-community/attacks/Path_Traversal)

파일 다운로드 취약점은 웹 해킹중 한 기법으로 해당 웹 서비스의 임의 파일을 다운로드 하는 취약점입니다. 만약 서비스의 설정 파일이나 DB파일이 탈취된다면 개인정보를 통한 2차적인 공격이 가능해집니다. 

파일 다운로드 취약점이 발생하는 URL 패턴은 다음과 같습니다.

![https://blog.kakaocdn.net/dn/LMexE/btrKtAjzPQ3/UM2tzzDKX2kSuDKJSQowS0/img.png](https://blog.kakaocdn.net/dn/LMexE/btrKtAjzPQ3/UM2tzzDKX2kSuDKJSQowS0/img.png)

위 주소들은 전부 URL 내에서 파일에 대한 경로로 접근이 가능하다는 것입니다. 그렇기에../ 의 파일 경로를 통해 접근하여 민감한 정보가 담긴 파일 다운로드가 가능해집니다. 이렇게 파일 이름을 직접 입력받아 임의의 디렉토리에 있는 파일을 다운로드 받는 취약점 Path Traversal 취약점입니다.

### XML & XXE

XML 외부 개체(XXE): XXE는 악의적인 자바스크립트를 막기 위한 필터장치를 우회하는 취약점으로 XML 문서에서 동적으로 외부 URI의 리소스를 포함시킬 수 있는 외부 엔티티(Entity)를 사용할 때 발생한다.

XXE Injection: 일반적으로 잘못 구성된 XML Parser를 사용하여 신뢰할 수 없는 XML 공격 코드를 주입시켜 실행시키는 응용프로그램에 대한 공격을 말한다. 해당 공격을 통해서 주요 `시스템 파일 접근(LFI)`이나 외부 `악의적인 파일 참조(RFI)`가 가능하다. 보통 XML Parser설정에서 External Entity 사용을 금지시키지 않아 발생한다.

### XSS Cross Site Scripting

웹 페이지에 악성 자바스크립트를 삽입하는 공격이다. 이 공격을 이용하면 사이트 이용자의 정보를 손쉽게 탈취할 수 있다. 최근엔 React나 Vue.js와 같은 프론트엔드 프레임워크, 라이브러리를 사용하여 XSS에 대한 방어가 어느정도 자동화된다. 그럼에도 불구하고 사용자의 실수로 취약점이 드러날 수 있다. 예를 들어, React에서 다음과 같은 실수를 할 수 있다.

가장 많기 때문에 제일 먼저 보자

PortSwigger: web app 취약점 분석 회사

Burp suite: How to test and proxy web app

Proxy: 빠른 액세스나 안전한 통신등을 확보하기 위한 중계서버를 "프록시 서버"라고 일컫는다. 클라이언트와 Web서버의 중간에 위치하고 있어, 대신 통신을 받아 주는 것이 프록시 서버이다. 클라이언트와 서버 사이에 존재하며, 중계기로서 대리로 통신을 수행하는 것을 `Proxy`라고 하며, 그 중계 기능을 하는 주체를 `Proxy Server`라고 한다.

![Untitled](TIL-day2-ov%2048682865a3cf4bd1a7e2ec03d67a2081/Untitled%201.png)

![Untitled](TIL-day2-ov%2048682865a3cf4bd1a7e2ec03d67a2081/Untitled%202.png)

[https://github.com/payloadbox/xss-payload-list](https://github.com/payloadbox/xss-payload-list)

![Untitled](TIL-day2-ov%2048682865a3cf4bd1a7e2ec03d67a2081/Untitled%203.png)

![Untitled](TIL-day2-ov%2048682865a3cf4bd1a7e2ec03d67a2081/Untitled%204.png)

### HTML & JavaScript

### API Enumeration

### SSRF Server Side Request Forgery

서버 측 요청 위조(Server-Side Request Forgery, SSRF) 공격은 공격자가 서버를 속여 무단 요청을 보내도록 유도하는 수법이다. 공격 이름으로 짐작할 수 있듯, 원래 서버가 하는 요청을 공격자가 위조하는 것을 의미한다. 

SSRF 공격은 사이트 간 요청 위조(Cross-Site Request Forgery, CSRF) 공격보다 훨씬 더 위험하다. CSRF의 악의적인 활동은 클라이언트 측에서 진행되는데, 반면 SSRF 공격은 중간에 사용자를 개입시킬 필요 없이 웹 서버 자체를 노린다. 공격자는 악성 HTTP 요청을 서버에 보내는 것만으로 백엔드에 지시해 악성 작업을 수행할 수 있다.

### Command Injection

Command Injection은 쉘을 실행시키는 로직을 이용한 공격이다. 시스템 권한이 탈취되는 것이나 마찬가지기 때문에 매우 치명적이다.

![https://kciter.so/images/2021-02-28-basic-web-hacking/command-injection.png](https://kciter.so/images/2021-02-28-basic-web-hacking/command-injection.png)

WebShell이 열린거나 마찬가지

각 언어마다 쉘 명령을 실행시키는 함수가 존재한다. 예를 들어, Java의 `System.runtime()`이나 `Runtime.exec()`, Python의 `exec()`, `os.system()` 등이 있다. 마찬가지로 각 언어마다 존재하는 `eval()` 함수도 매우 취약하다.

### File Upload

공격 스크립트가 담긴 파일을 서버로 업로드하는 공격이다. WebShell이 가능한 코드가 담긴 파일을 업로드하고 해커가 URL을 통해 접근 가능해지면 Command Injection과 같은 효과를 볼 수 있다.

![https://kciter.so/images/2021-02-28-basic-web-hacking/file-upload-attack.png](https://kciter.so/images/2021-02-28-basic-web-hacking/file-upload-attack.png)

해커가 개발 언어에 따른 공격 스크립트를 업로드하는데 성공하고 해당 파일을 브라우저로 접근 할 수 있다면 Command Injection처럼 WebShell 접근이 가능하다. 꼭 PHP, JSP와 같은 스크립트가 아니더라도 CSRF Attack을 유발시킬 수 있는 파일을 업로드할 수도 있다.

### LFI & RFI

### Session, Cookies and Tokens

[https://hongong.hanbit.co.kr/완벽-정리-쿠키-세션-토큰-캐시-그리고-cdn/](https://hongong.hanbit.co.kr/%EC%99%84%EB%B2%BD-%EC%A0%95%EB%A6%AC-%EC%BF%A0%ED%82%A4-%EC%84%B8%EC%85%98-%ED%86%A0%ED%81%B0-%EC%BA%90%EC%8B%9C-%EA%B7%B8%EB%A6%AC%EA%B3%A0-cdn/)

HTTP 통신은 요청(Request) -> 응답(Response) 이 종료되면 stateless*(상태가 유지되지 않은)*한 특징 때문에 연결을 끊는 처리 방식입니다. 로그인과 같은 일을 할 때, '누가' 로그인 중인지 **상태** 를 기억하기 위해 쿠키, 세션, 토큰을 사용합니다.

Cookie: 쿠키는 공개 가능한 정보를 사용자의 브라우저에 저장시킨다.

웹 서핑을 하면서 어떤 사이트에 들어가면 쿠키를 설정하라는 문구를 본 적이 있을 거예요. 이 쿠키 때문에 쇼핑 사이트에 로그인하지 않아도 장바구니에 물건을 담아두거나 검색 기록에서 이전에 입력했던 검색어들을 찾아볼 수 있습니다. 나의 웹 서핑 내역이 마케팅과 광고에 활용되는 것도 쿠키를 통해 이뤄지는 일이죠.

**쿠키**는 크롬이나 사파리 같은 브라우저에 저장되는 작은 텍스트 조각입니다. 브라우저는 사용자의 컴퓨터에 설치된 소프트웨어이므로 쿠키는 사용자가 갖고 있는 정보라고 할 수 있죠.

![http://hongong.hanbit.co.kr/wp-content/uploads/2022/05/%EB%B8%8C%EB%9D%BC%EC%9A%B0%EC%A0%80%EC%97%90-%EC%A0%80%EC%9E%A5%EB%90%98%EB%8A%94-%EC%A0%95%EB%B3%B4-%EC%BF%A0%ED%82%A4.png](http://hongong.hanbit.co.kr/wp-content/uploads/2022/05/%EB%B8%8C%EB%9D%BC%EC%9A%B0%EC%A0%80%EC%97%90-%EC%A0%80%EC%9E%A5%EB%90%98%EB%8A%94-%EC%A0%95%EB%B3%B4-%EC%BF%A0%ED%82%A4.png)

Session: 세션은 서버가 사용자를 확인하기 위해 저장하는 식별자.

서버는 아이디와 비밀번호를 입력해 로그인에 성공한 사용자와 로그인한 다음 마이페이지 버튼을 누른 사용자가 동일 인물임을 알지 못한다는 것입니다. 그렇기 때문에 사용자가 사이트에 로그인한 상태라는 점을 서버에 인증하지 못하면 클릭을 할 때마다 반복해서 아이디와 비밀번호를 서버에 제공해야 합니다. 이런 번거로움을 해결하기 위해 사용하는 것이 바로 **세션**입니다.

사용자가 사이트에 한 번 로그인하면 유효기간이 끝날 때까지 더 이상 아이디와 비밀번호를 입력하지 않아도 되도록 사용자가 이미 서버로부터 인증받았음을 증명해 주는 세션이라는 증서가 필요합니다. 사용자가 서버에 올바른 아이디와 비밀번호로 로그인에 성공하면 서버는 세션 아이디라는 데이터를 만듭니다. 보통은 ‘2sd98dbawix4’와 같은 식으로 알파벳과 숫자가 혼합된 형식을 갖고 있습니다. 서버는 영화관에서 티켓을 보관용 부분만 찢어 건네주듯 세션 아이디를 사용자에게 전달하고, 메모리에 아이디 사본을 어떤 사용자의 것인지 적어서 보관합니다.

![http://hongong.hanbit.co.kr/wp-content/uploads/2022/05/%ED%98%BC%EA%B3%B5%EC%96%84%EC%BD%94-%EC%84%B8%EC%85%98.png](http://hongong.hanbit.co.kr/wp-content/uploads/2022/05/%ED%98%BC%EA%B3%B5%EC%96%84%EC%BD%94-%EC%84%B8%EC%85%98.png)

Token: 세션과는 다른 로그인 유지 방식

메모리 공간을 많이 차지하는 세션 방식의 대안은 로그인한 사용자에게 세션 아이디 대신 **토큰**을 발급해 주는 것입니다. 이러한 토큰에는 특수한 수학적 원리가 적용되어 있어서 마치 위조 방지 장치가 있는 지폐처럼 서버만이 유효한 토큰을 발행할 수 있습니다.

![http://hongong.hanbit.co.kr/wp-content/uploads/2022/05/%EC%84%B8%EC%85%98%EA%B3%BC%EB%8A%94-%EB%98%90-%EB%8B%A4%EB%A5%B8-%EB%A1%9C%EA%B7%B8%EC%9D%B8-%EC%9C%A0%EC%A7%80-%EB%B0%A9%EC%8B%9D-%ED%86%A0%ED%81%B0.png](http://hongong.hanbit.co.kr/wp-content/uploads/2022/05/%EC%84%B8%EC%85%98%EA%B3%BC%EB%8A%94-%EB%98%90-%EB%8B%A4%EB%A5%B8-%EB%A1%9C%EA%B7%B8%EC%9D%B8-%EC%9C%A0%EC%A7%80-%EB%B0%A9%EC%8B%9D-%ED%86%A0%ED%81%B0.png)

그렇기 때문에 토큰을 받아간 사용자가 이를 쿠키로 저장해 두고 필요할 때마다 제시하면 서버는 따로 책상에 올려놓은 것을 확인할 필요 없이 자기가 발급한 토큰임을 알아보고 사용자의 요청을 허가해 주는 것입니다. 더 이상 이미 로그인한 사용자의 티켓을 책상(메모리)에 올려 두고 있을 필요가 없으니 서버 부하를 줄일 수 있는 것이죠.

✅토큰 방식은 해당 서버만이 만들 수 있는 토큰을 발급함으로써 상태를 저장하지 않고도 사용자의 로그인 여부를 파악할 수 있도록 합니다.

물론 토큰 방식에도 한계는 있습니다. 여러 기기에서의 로그인을 제한하기 위해 필요한 때 에 로그인되어 있는 사용자를 서버가 강제로 로그아웃을 시킬 수 있어야 하는데, 토큰 방식에서는 이것이 불가능합니다. 한 번 발행한 토큰은 유효기간이 끝나기 전까지 따로 통제할 수 없기 때문에 세션에 비해 토큰 정보를 탈취 당할 가능성이 높습니다. 그러나 토큰은 쿠키처럼 만료 기간을 정할 수 있어서 만료 시간을 짧게 지정해 피해를 줄일 수 있습니다. 토큰방식은 쿠키와 세션을 적절히 섞은 것과 비슷합니다.

### Wordpress and CMS

CMS(Content Management System): 

거의 모든 CMS는 프론트 엔드와 백엔드로 구성됩니다. 프론트 엔드는 사용자가 상호 작용하는 부분으로, 웹 사이트의 시각적 구조화 및 스타일 지정이 이루어지는 방식입니다. 프론트 엔드는 HTML, CSS 및 JavaScript를 함께 사용하여 회사 브랜딩에 맞게 스타일이 지정된 상호 작용 방식의 풍부한 콘텐츠를 제공합니다.

CMS의 백엔드는 웹 사이트에 새로운 콘텐츠를 게시하는 데 사용되는 애플리케이션입니다. 이때 콘텐츠를 CMS의 프론트 엔드에 쉽게 추가, 제작 및 게시하기 위해 웹 인터페이스에 액세스하는 것으로 절차가 시작됩니다. 사용자는 HTML, CSS 및 JavaScript를 파악하는 대신 Microsoft Word와 유사한 인터페이스에서 콘텐츠를 제작합니다. 백엔드는 이렇게 제작된 콘텐츠를 데이터베이스에 저장하고 웹 사이트의 프론트 엔드에 게시합니다.

이 두 시스템을 합하면 CMS가 됩니다. 두 시스템은 웹 기술을 이해하거나 웹 애플리케이션을 처음부터 구축하지 않고도 콘텐츠를 게시할 수 있도록 지원합니다.

![Untitled](TIL-day2-ov%2048682865a3cf4bd1a7e2ec03d67a2081/Untitled%205.png)

## ****How To Find First Bug in Bug Bounty****

[https://www.youtube.com/watch?v=PvXeyyD97LQ](https://www.youtube.com/watch?v=PvXeyyD97LQ)

1. 취약점 하나당 4시간
2. XSS
3. IDOR: make a list of all the endpoint of all the point where idol might be

### XSS Protection

<script> alert(1) </script> usually doesn’t work.