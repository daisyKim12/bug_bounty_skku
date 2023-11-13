# TIL-day1-ov

## Basic of Bug bounty hunting

Bug bounty hunting platforms: Vulnerablility co-ordination platform or bug bounty hunting platform helps contacting the web application owners to easily report vulnerability in the website.
- HackerOne
- Bugcrowd
- Cobalt
- Synack

 Vulnerable Web Applications: These are intentionally vulnerable virtual machines or web app packages. Vulnerable web application`s` are available as general variants that contain many types of vulnerabilities and as dedicated variants that focus on a single vulnerability and its subtleties. Some examples are: 

- BWapp
- DVWA
- OWASP Webgoat
- Cyclone Transfers
- Bricks
- Butterfly Security Project
- Hacme
- Juice Shop
- Rails Goat
- SQLol
- BWapp, DVWA(Damn Vulnerable Web Application), and Webgoat are the best for beginners

Staying Current on Latest Vulnerabilities: For this, you can follow elite researchers and learn from their work. You can also read disclosed reports on bug bounty platforms like HackerOne. Some recommended researchers to follow are: 

- Frans Rosén
- Jason Haddix
- Geekboy
PortSwigger
Jobert Abma

## Beginner to Advanced Bug Bounty Hunting Course

[https://www.youtube.com/watch?v=Rp69edBmFFo](https://www.youtube.com/watch?v=Rp69edBmFFo)

### Kali Linux Install

To Run Kali linux there are 2 options, using Virtual box or us VMware.
[vmware](https://www.vmware.com/) → player

![Untitled](TIL-day1-ov%2008fb1a202e0f45bf9c7a629deb2d24b3/Untitled.png)

[Kali linux](https://www.kali.org/get-kali/#kali-platforms) → vmware

![Untitled](TIL-day1-ov%2008fb1a202e0f45bf9c7a629deb2d24b3/Untitled%201.png)

![Untitled](TIL-day1-ov%2008fb1a202e0f45bf9c7a629deb2d24b3/Untitled%202.png)

using UTM better

[https://www.youtube.com/watch?v=9zdjQ9w_v_4](https://www.youtube.com/watch?v=9zdjQ9w_v_4)

### ALL about Recon

1. 기본 공부
    
    해킹의 기본은 대상의 정보를 수집하는 것이다. 대상 정보가 불충분한 상태에서 무작위 대입과 같은 공격을 무리하게 시도한다면 불필요한 흔적을 남겨 뒷덜미가 잡히게 된다. 이러한 정보 수집은 검색 엔진 API 활용, DNS 조회, 응답 패킷 분석, Wordlist 대입, 소스코드 분석 등 여러가지 방법을 통해 이루어질 수 있다. `Recon-ng` 는 다영한 방법의 정보 수집을 자동화하여 사용자가 필요한 결과 값을 얻을 수 있는 도구이다.
    
    | 모듈 | 설명 |
    | --- | --- |
    | Discovery | 웹 서비스 상에 공개된 정보에 의해서 필요 정보 수집
    (cache, php_info, robots, server_status 등) |
    | Exploitation | SQL 쿼리문, Script, Xpath 등의 구문을 입력하여 공격 가능 벡터 수집 |
    | Import | CSV 파일, list 파일 등을 import 하여 결과 값 확인 가능 |
    | Recon | Search Engine API, Wordlist, SNS, Domain, Dump, Geocode, ssl, vpn, netcraft, Brute-Force 등 다양한 방법을 통해 공개된 연락처, 인증 크레딧, 호스트 정보 등의 정보 수집 |
    | Reporting | 각 모듈을 사용하여 수집된 정보를 사용자가 쉽게 파악할 수 있도록 문서화 |
    
    이와 같은 여러가지 모듈 중 사용자가 필요한 모듈을 로드하여 사용할 수 있다. 본 테스트는 칼리 리눅스(Kali-Linux)에서 진행되었으며, ‘Recon-ng’는 칼리 리눅스에 내장되어 있는 도구 중 하나이므로 해당 OS를 사용한다면 별도의 다운로드 및 설치 과정없이 도구를 사용할 수 있다.
    

1. scanning bug bounty program to find certain ports to be open or find directory
- nmap
    
    ![Untitled](TIL-day1-ov%2008fb1a202e0f45bf9c7a629deb2d24b3/Untitled%203.png)
    

Nmap은 원래 Gordon Lyon에 의해 쓰인 보안 스캐너이다. 컴퓨터와 서비스를 찾기 위해 사용된다. Nmap은 서비스 탐지 프로토콜로 자신을 광고하지 않는 수동적인 서비스들도 찾아낼 수 있다. 게다가 Nmap은 원격 컴퓨터들의 상세정보도 알아낼 수 있다. 이 상세정보에는 OS, 장치 종류, 운영 시간, 서비스에 쓰이는 소프트웨어 제품과 버전, 방화벽 기술 존재와 LAN에서 NIC의 공급자 정보도 포함한다.

**Nmap의 특징**

- 호스트 탐지 : 네트워크 상에서 컴퓨터들을 확인한다. 예를 들어 ping 응답이나 특정포트가 열린 컴퓨터들을 나열한다.
- 포트 스캔 : 하나 혹은 그 이상의 대상 컴퓨터들에 열린 포트들을 나열한다.
- 버전 탐지 : 응용프로그램의 이름과 버전 번호를 확인하기 위해 원격 컴퓨터의 서비스를 확인 한다.
- OS 탐지 : 원격으로 OS와 네트워크 장치의 하드웨어 특성을 확인 한다.

**Nmap의 사용처**

- 네트워크 연결을 확인함으로써 컴퓨터의 보안을 감시
- 감시를 위한 준비로 열려있는 포트들을 확인
- 네트워크 목록 작성, 네트워크 매핑 및 유지, 자산 관리
- 허가되지 않은 새로운 서버를 확인함으로써 보안 감시
- ffuf: subdomain, directory, api 찾기
    - sub
    
    ![Untitled](TIL-day1-ov%2008fb1a202e0f45bf9c7a629deb2d24b3/Untitled%204.png)
    
    - directory
    
    ![Untitled](TIL-day1-ov%2008fb1a202e0f45bf9c7a629deb2d24b3/Untitled%205.png)
    
    - api
    
    ⭐️ bypass forbidden: [https://www.youtube.com/watch?v=yjcT6fPKoYk](https://www.youtube.com/watch?v=yjcT6fPKoYk)
    
- dirb: fuff와 같이 실행하면서 확인 특히 recursively 동작한다.
    
    ![Untitled](TIL-day1-ov%2008fb1a202e0f45bf9c7a629deb2d24b3/Untitled%206.png)
    
- wpscan: wordpress security scan 아주 자세히 읽어야함
    
    ![Untitled](TIL-day1-ov%2008fb1a202e0f45bf9c7a629deb2d24b3/Untitled%207.png)
    
    ![Untitled](TIL-day1-ov%2008fb1a202e0f45bf9c7a629deb2d24b3/Untitled%208.png)
    
1. Shodan
    
    쇼단의 근본적인 기능은 IoT 보안을 강화하기 위해 그 취약점을 찾아내는 것이다. 많은 보안 전문가가 쇼단을 사용한다. 보안 전문가들은 쇼단을 통해 자신이 관리하는 장비와 서비스의 보안 취약성을 파악할 수 있다. 쇼단은 보안과 관련된 다양한 자료를 제공하고 전문가들을 보고서를 발행하기도 한다. 사물인터넷 검색 엔진으로 해당 버그 바운티 프로그램이 연결되어 있는 프린터 같은 것들을 찾아내서 연결할 수 있다. 쉽게 버그를 찾을 수 있다. 여기서 `CVE`를 검색하면 된다.
    
    CVE(Common Vulnerabilities and Exposures)는 공개적으로 알려진 컴퓨터 보안 결함 목록입니다. CVE는 보통 CVE ID 번호가 할당된 보안 결함을 뜻합니다.
    
    ![Untitled](TIL-day1-ov%2008fb1a202e0f45bf9c7a629deb2d24b3/Untitled%209.png)
    
    shodan 에 현재 skku 웹 서버 ip 를 넣으면 다양한 정보를 준다. Port와 sub domain을 알려준다.
    
    organization으로 검색
    
    ![Untitled](TIL-day1-ov%2008fb1a202e0f45bf9c7a629deb2d24b3/Untitled%2010.png)
    
    port로 검색
    
    ![Untitled](TIL-day1-ov%2008fb1a202e0f45bf9c7a629deb2d24b3/Untitled%2011.png)
    
2. URL

![Untitled](TIL-day1-ov%2008fb1a202e0f45bf9c7a629deb2d24b3/Untitled%2012.png)

1. DNS

[How DNS works. What is DNS? Learn how step by step.](https://howdns.works/ko/)

1. dig

Zone Transfer는 여러 네임 서버의 동기화를 위한 것으로, 보통 1차 네임 서버에서 2차 네임 서버로 복사를 한다. 방식에는 전체 영역 전달(AXER), 증가 영역 전달(IXFR) 두 가지 방법이 있다.Zone Transfer를 이용하여 다음과 같은 정보를 얻을 수 있다.사용 중인 시스템의 IP 정보 확인시스템의 이름을 통해 시스템의 용도 추측master와 slave 시스템 사이에 zone 정보 동기화된 정보 SOA(Start of Authority)

![Untitled](TIL-day1-ov%2008fb1a202e0f45bf9c7a629deb2d24b3/Untitled%2013.png)

![Untitled](TIL-day1-ov%2008fb1a202e0f45bf9c7a629deb2d24b3/Untitled%2014.png)

zone transfer를 pull off할 수 있으면 리포트 가능

1. nslookup 

![Untitled](TIL-day1-ov%2008fb1a202e0f45bf9c7a629deb2d24b3/Untitled%2015.png)

1. whois

![Untitled](TIL-day1-ov%2008fb1a202e0f45bf9c7a629deb2d24b3/Untitled%2016.png)

1. find subdomains
- harvester: penetration tool, subdomain, email etc..
- crt.sh: subdomain 찾기
    
    ![Untitled](TIL-day1-ov%2008fb1a202e0f45bf9c7a629deb2d24b3/Untitled%2017.png)
    
- wayback: 지워야 하는 과거 subdomain 찾기
    
    ![Untitled](TIL-day1-ov%2008fb1a202e0f45bf9c7a629deb2d24b3/Untitled%2018.png)
    
    ![Untitled](TIL-day1-ov%2008fb1a202e0f45bf9c7a629deb2d24b3/Untitled%2019.png)
    
    ![Untitled](TIL-day1-ov%2008fb1a202e0f45bf9c7a629deb2d24b3/Untitled%2020.png)
    
    ![Untitled](TIL-day1-ov%2008fb1a202e0f45bf9c7a629deb2d24b3/Untitled%2021.png)
    
- sublist3r: subdomain 찾기
    
    ![Untitled](TIL-day1-ov%2008fb1a202e0f45bf9c7a629deb2d24b3/Untitled%2022.png)
    
- amass: 이게 좋다 많은 subdomain 알려준다.
1. tools to find what tech used in a website.
- wappalyzer(extention)
- react developer tool(extention)

1. 많은 url 중에 가능성 높은 거 찾는 방법
- large scope

1. burp setting
- proxy setting in firefox
    
    ![Untitled](TIL-day1-ov%2008fb1a202e0f45bf9c7a629deb2d24b3/Untitled%2023.png)
    
    ![Untitled](TIL-day1-ov%2008fb1a202e0f45bf9c7a629deb2d24b3/Untitled%2024.png)
    
    ![Untitled](TIL-day1-ov%2008fb1a202e0f45bf9c7a629deb2d24b3/Untitled%2025.png)