# TIL-day5-ov

## File Upload

공격 스크립트가 담긴 파일을 서버로 업로드하는 공격이다. WebShell이 가능한 코드가 담긴 파일을 업로드하고 해커가 URL을 통해 접근 가능해지면 Command Injection과 같은 효과를 볼 수 있다.

![https://kciter.so/images/2021-02-28-basic-web-hacking/file-upload-attack.png](https://kciter.so/images/2021-02-28-basic-web-hacking/file-upload-attack.png)

해커가 개발 언어에 따른 공격 스크립트를 업로드하는데 성공하고 해당 파일을 브라우저로 접근 할 수 있다면 Command Injection처럼 WebShell 접근이 가능하다. 꼭 PHP, JSP와 같은 스크립트가 아니더라도 CSRF Attack을 유발시킬 수 있는 파일을 업로드할 수도 있다.

### web shell

웹사이트에 파일을 올리고 url을 이용해 파일에 접근한 후 파일을 실행한다.

[https://sushant747.gitbooks.io/total-oscp-guide/content/webshell.html](https://sushant747.gitbooks.io/total-oscp-guide/content/webshell.html)

![Untitled](TIL-day5-ov%202ae8471e8e344b18b24414736910ea04/Untitled.png)

![Untitled](TIL-day5-ov%202ae8471e8e344b18b24414736910ea04/Untitled%201.png)

whoami로 실행이 가능하면 reverse shell 코드를 작성하고 내 아이피를 넣으면 내 로컬 컴퓨터에서 shell에 접근할 수 있다.

![Untitled](TIL-day5-ov%202ae8471e8e344b18b24414736910ea04/Untitled%202.png)

### LFI & RFI

LFI가 더 흔하다.

![Untitled](TIL-day5-ov%202ae8471e8e344b18b24414736910ea04/Untitled%203.png)

![Untitled](TIL-day5-ov%202ae8471e8e344b18b24414736910ea04/Untitled%204.png)