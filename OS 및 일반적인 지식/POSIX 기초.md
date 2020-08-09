# POSIX 기초 🐇

### ❓ POSIX란?

이식 가능 운영체제 인터페이스의 약자(Portable Operating System Interface for Computer Environnment)

유닉스 운영체제에 기반을 둔 다른 운영체제들 사이의 호환성을 위해 만든 표준 운영체제 인터페이스

시스템 콜, 프로세스 환경, 파일&디렉토리, 시스템 데이터 베이스, tar 압축 포맷 등 다양한 내용 포함

✔ POSIX 표준을 지키는 운영체제의 프로그램은 다른 운영체제로 쉽게 포팅이 가능

<br/>

### ❗ POSIX를 따르는 운영체제들

Solaris와 macOS 는 POSIX 인증을 받음

Linux와 VxWorks, Android는 POSIX 인증을 받지는 않았지만 대부분의 기능이 POSIX 표준을 지킴

Windows는 일부 POSIX 표준을 지키는 것이 있지만 대부분 POSIX 표준을 따르지 않음

<br/>

### ❗ stdin (standard input)

표준 입력 스트림. 키보드 대상으로 입력

프로그램에 입려되는 데이터의 표준적 출처(장비나 파일)를 뜻함

File descriptor의 값은 0. C의 <stdio.h> 에서 FILE* stdin 으로 접근

✔ stdin 사용법

~~~
char a;
fprintf(stdout, "문자를 입력하세요.");
fscanf(stdin, "%c", &a);
~~~

사용자에게 키보드로 입력을 받아 a 라는 변수에 저장한다.

<br/>

### ❗ stdout (standard output)

표준 출력 스트림. 모니터 대상으로 출력

프로그램에서 출력되는 데이터의 표준적인 방향(장비나 파일)을 뜻함

정상적인 출력이 반환되는 방향을 말함

File descriptor의 값은 1. C의 <stdio.h> 에서 FILE* stdout 으로 접근 

✔ stdout 사용법

~~~
fprintf(stdout, "stdout 사용 예시입니다.");
~~~

fprintf와 stdout을 사용해 printf 와 같은 출력 결과를 낸다.

<br/>

### ❗ stderr

표준 에러 스트림. 모니터 대상으로 출력

프로그램의 비정상 종료시에 반환됨

File descriptor의 값은 2. C의 <stdio.h> 에서 FILE* stderr로 접근 

✔ stderr 사용법

~~~
if (wiringPiSetup () < 0) 
{
		fprintf (stderr, "Unable to setup wiringPi: %s\n", strerror (errno));
		return 1;
}
~~~

만약 에러가 발생할 경우 Unable to setup wiringPi 와 에러의 종류를 화면에 출력한다.

<br/>

### ❗ pipe

pipe의 정의는 [TIL](https://github.com/hjyeon-n/BE_TIL/blob/master/OS%20%EB%B0%8F%20%EC%9D%BC%EB%B0%98%EC%A0%81%EC%9D%B8%20%EC%A7%80%EC%8B%9D/IPC%20%ED%86%B5%EC%8B%A0.md) 내용을 참고

pipe() 함수를 통해 서로 독립된 프로세스들이 데이터를 주고 받음

```
int pipe_fd[2];
if (pipe(pipe_fd) == -1) //pipe 생성
	exit(1);
```

pipe()는 크기가 2인 int형 배열을 parameter로 가진다.

* fd[0]: 데이터를 입력받을 수 있는 파일 디스크립터가 담김. read
* fd[1]: 데이터를 출력할 수 있는 파일 디스크립터가 담김. write

✔ 파이프는 기본적으로 단방향이므로 양방향 통신을 하려면 파이프가 2개 필요

<br/>

⌨ 아래는 과거 시스템 프로그래밍 수업에서 짰던 자식과 부모 프로세스간 통신 코드

```
#include <string.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <sys/stat.h>
#define BUF_SIZE 2000
int main(void) {
	pid_t pid;
	int pipe_fd[2], size;
	int count = 0;
	char buf[BUF_SIZE];
	
	if (pipe(pipe_fd) == -1) //pipe 생성
		exit(1);
	
	switch (pid = fork()) {
		case -1: //fork 실패
			perror("fork");
			exit(1);
			break;
		case 0: //자식 프로세스
			close(pipe_fd[1]);
			read(pipe_fd[0], buf, BUF_SIZE);
			sleep(2);
			printf("From Parent: %s\n", buf);
			break;
		default: //부모 프로세스
			close(pipe_fd[0]);
			printf("To Child: ");
			scanf("%s", buf);
			write(pipe_fd[1], buf, strlen(buf) + 1);
			sleep(2);
			break;
	}
	return 0;
}
```

위의 코드를 gcc 를 이용해 컴파일 하면 다음과 같은 결과를 가진다.

![image](https://user-images.githubusercontent.com/64277114/89727051-700d7d00-da5c-11ea-95a8-b74171d508ea.png)

<br/>

🚩 용어정리

스트림: 한 방향으로 흐르는 데이터의 흐름. 즉 데이터 전송은 단방향으로만 이루어진다.

<br/>

[참고자료](https://ko.wikipedia.org/wiki/%ED%91%9C%EC%A4%80_%EC%8A%A4%ED%8A%B8%EB%A6%BC)