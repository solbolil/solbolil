# 리눅스 명령어(top, ps, jobs, kill)
---
## 1.top

**top** 명령어는 시스템의 프로세스/메모리 사용 상태를 5초의 간격으로 업데이트하여 출력한다. 
화면에 출력되는 기본값은 현재시간, 시스템 업데이트(1) 시간, 시스템에 로그인한 사용자 수, 지난 1분, 지난 5분, 지난 15분간의 시스템 평균 부하를 출력한다. 
이 목록 아래에 프로세스 정보, CPU 상태, 메모리와 스왑 상태를 출력한다. top 명령어를 실행한 후 초기 화면에서 키를 입력하면 사용할 수 있는 단축키 목록을 확인할 수 있다.


## 2.ps

**ps** 명령어는 프로세스의 현재 상태를 출력한다. ps로 현재 사용하는 프로세스의 상태를 살펴보자. 아래는 PID, TTY, TIME, CMD 헤더의 필드와 내용을 출력한다.

```
$ ps
   PID TTY TIME CMD
  3134 pts/1        00:00:00 bash
 15027 pst/1        00:00:00 ps
```

__ps 주요 옵션__

-A : 모든 프로세스를 출력한다.

-a : 세션 리더 및 터미널에 속하지 않는 프로세스를 제외하고 출력한다.

-e : 커널 프로세스를 제외한 모든 프로세스를 출력한다.

-f : full 포맷 출력한다.

-l : 긴 포맷으로 출력한다.

-o값 : 출력 포맷을 지정하는 옵션으로 값으로는 pid, tty, cmd 등을 지정하여 출력한다.

-M : 64비트 프로세스를 출력한다.

-m : 프로세스들 뿐만 아니라 커널 스레드를 출력한다.

-p : 프로세스 ID를 출력한다.

-r : 현재 실행 중인 프로세스를 출력한다.

-u : 사용자 ID를 지정한다(이름도 지원).

u : 프로세스의 소유자를 기준으로 출력한다.

x : 특정 사용자의 프로세스 정보를 확인할 때 사용한다. 사용자를 지정하지 않으면 현재 사용자를 기준으로 정보를 출력한다.

-x : 로그인 상태에 있는 동안 아직 완료되지 않은 프로세서들을 출력한다.


## 3.jobs

**jobs**는 현재 세션의 작업 상태를 출력한다. 작업이 중지된 상태, 백그라운드로 진행 중인 작업 상태, 변경되었지만 보고되지 않은 상태 등을 표시한다.
현재 환경의 작업 상태를 아래와 같이 확인할 수 있다.
```
$ jobs
 [1]- 정지됨               vi
 [2]+ 정지됨               tail -f /var/log/messages
```

## 4.kill

**kill** 명령어는 프로세스에 종료 시그널을 보낸다. 시스템에 얘기치 않은 문제가 생긴 프로세스를 종료시킬 수 있다. 
만일 kill 명령으로 종료되지 않는 프로세스는 -9 옵션을 사용해서 강제로 종료하면 된다.

ps 명령으로 확인한 PID를 이용하면 원하는 프로세스를 종료시킬 수 있다.

```
# kill 2518
```

만일 kill 명령어로 종료되지 않으면 -9 옵션으로 강제 종료시킬 수 있다.

```
# kill -9 2518
```
