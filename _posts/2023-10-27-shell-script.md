---
layout: single
title: "UNIX/Linux 시스템 관리자를 위한 쉘 스크립트 활용 가이드 - 요약"
categories: script
tags: [unix, linux, shell]
toc: true             # Heading을 이용하여 자동으로 목차가 생성됨
---

# UNIX/Linux 계보

![image](https://github.com/Soonbum/Soonbum.github.io/assets/16474083/463bf146-768b-49e7-b9a0-31192731db39)


# UNIX/Linux 기본 명령어와 개념

## 입출력 재지정 (Redirection)

| fd (file descriptor) | fd 이름 | 용도 | 표준 장치 |
| -------------------- | ------- | ---- | -------- |
| 0 | stdin (표준 입력) | 명령어에 입력할 내용을 저장 | 키보드 |
| 1 | stdout (표준 출력) | 명령어에서 출력할 내용을 저장 | 화면 |
| 2 | stderr (표준 오류) | 명령어에서 출력할 오류 메시지를 저장 | 화면 |

* 항상 명령어는 좌측, 파일은 우측에 온다는 것을 명심하자.

* fd 0과 1은 생략이 가능하다.
  - 표준 오류(2)는 반드시 표기해야 함

* 예제: 표준 입력 리디렉션
  - `명령어 < 파일`
  - `명령어 0< 파일`
```
$ cat sample.txt                    # sample.txt 파일의 내용을 보여줌
$ tr '[A-Z]' '[a-z]' < sample.txt   # sample.txt 파일의 대문자를 소문자로 바꾸고 내용을 보여줌
```

* 예제: 표준 출력 리디렉션
  - `명령어 >> 파일` ('>'는 덮어쓰기, '>>'는 이어쓰기)
  - `명령어 1>> 파일`
```
$ date >> day-time  # date 명령어의 결과를 day-time 파일로 기록
$ cat day_time      # day_time 파일 보기
```

* 예제: 표준 오류 리디렉션
  - `명령 > 파일a 2> 파일e` (명령어의 결과를 파일a에 기록하고, 오류 메시지를 파일e에 기록함)
  - `명령 1> 파일a 2> 파일e`
  - `명령 > 파일 2>&1` (명령어의 결과와 오류 메시지를 파일에 기록)
  - `명령 1> 파일 2>&1`

## 파이프 (Pipe)

* 문법: `명령어1 | 명령어2 | 명령어3`
  - 파이프는 재지정(Redirection)과 달리 파일 입출력을 하지 않고 메모리 상에서 명령어 처리 결과를 즉시 다른 명령어의 입력으로 넘기므로 속도가 빠르다.

## 기본 명령어

* at 명령어: 명령어 또는 스크립트 파일이 특정 시간에 실행되도록 *예약*
  - /etc/at.allow, /etc/at.deny 설정을 기반으로 예약 명령어에 대한 권한 부여 가능
  - atd 데몬을 구동 중이어야만 사용 가능 (/etc/init.d/atd)

* cat 명령어: *파일의 내용*을 보여줌 (conCATenate)

* cd 명령어: *현재 디렉토리를 변경*함 (Change Directory)

* chgrp 명령어: 소유 그룹을 변경함 (Change Group)

* chmod 명령어: 파일, 디렉토리, 장치 등의 *권한 변경*
  - '- rwx rwx rwx': 파일 타입, 소유자 퍼미션, 소유자 그룹 퍼미션, 기타 모든 사용자의 퍼미션을 의미함
  - 타입: -(일반파일), d(디렉토리), l(심볼릭 링크), c(캐릭터형 디바이스), b(블록형 디바이스)
  - 8진수로 퍼미션 지정 가능: r(4), w(2), x(1) (즉, 7은 rwx, 5는 r-x를 의미함)
  - 기호를 통해 퍼미션 지정 가능: [u(소유자), g(소유자 그룹), o(기타 소유자), a(ugo 전부)]
  - 그 외에도 실행 권한 관련된 기능이 있음: SetUID(s), SetGID(s), StickyBit(t)

* chown 명령어: 파일 *소유자를 변경*함 (root만 사용 가능) (Change Owner)

* cmp 명령어: 파일을 *비교*함, diff와 달리 차이점의 유무만 알려줌 (Compare)

* col 명령어: 텍스트 파일 내 *개행(특수) 문자와 공백 등을 변환*하는 필터 역할을 함
  - 예: '\n\r' --> '\n', ' ' --> '\t' 등

* colcrt 명령어: *밑줄*(_)을 감추거나 변환함

* cp 명령어: 특정 파일을 현재 디렉토리 또는 다른 디렉토리로 *복사*함

* cut 명령어: 텍스트 파일이나 파이프된 결과 중에 *지정된 부분만 표시*함 (텍스트 파일 출력 편집)

* date 명령어: 시스템의 *날짜와 시간*을 알려주거나 설정함

* df 명령어: 파일 시스템의 *디스크 공간*을 표시함

* diff 명령어: 파일을 *비교*함, 차이점을 자세하게 표시함

* domainname 명령어: 운영체제에 설정된 *도메인 이름* 정보를 확인함

* du 명령어: 현재 디렉토리의 *사용량*을 표시함

* echo 명령어: 지정된 문자열을 *화면에 출력*함

* find 명령어: 조건에 맞는 *파일을 찾음*

* free 명령어: 운영체제에서 *사용/비사용* 메모리를 보여줌

* ftp 명령어: *FTP(File Transfer Protocol) 서비스*

* ifconfig 명령어: 운영체제의 *네트워크 인터페이스의 설정*을 확인 및 변경함

* grep 명령어: 텍스트 형식으로 된 파일의 내용이나 명령어의 실행 결과를 *특정 문자나 단어로 검색*함
  - 단독으로 사용하면 텍스트 파일 또는 결과의 *특정 문자나 단어가 포함된 행이 출력됨*

* groupadd 명령어: 그룹을 생성함

* groupdel 명령어: 그룹을 삭제함

* groups 명령어: 자신이 소속된 그룹의 목록을 표시함

* id 명령어: 자신의 기본 그룹이나 그 외 소속되어 있는 그룹을 알려줌

* jobs 명령어: *현재 가동 중인 작업*을 번호를 붙여 목록으로 표시함

* kill 명령어: 프로세스를 *강제로 종료*함

* ln 명령어: 파일이나 디렉토리에 대한 *심볼릭 링크*를 생성함
  
* logger 명령어: 운영체제의 *주요 로그 저장 파일(/var/log/messages)에 메시지를 저장*함

* ls 명령어: 현재 디렉토리 내 정보를 표시함

* lsof 명령어: list open files 명령어는 시스템에서 *열린 파일 목록*을 알려주고 *사용하는 프로세스, 디바이스 정보, 파일의 종류 등*을 표시함

* man 명령어: 명령어에 대한 *매뉴얼*을 보여줌

* mkdir 명령어: 새로운 디렉토리를 생성함

* mv 명령어: 특정 파일을 현재 디렉토리 또는 다른 디렉토리로 *이동*시키거나 이름을 *변경*함

* netstat 명령어: *현재 시스템에 연결되어 있는 네트워크 연결 상태 및 포트 정보*를 표시함

* newgrp 명령어: 하위 그룹을 기본 그룹으로 만듦

* nl 명령어: 텍스트 형태의 파일을 읽어 *행 번호*를 부여함

* nslookup 명령어: 지정한 호스트명(DNS명 또는 IP주소)에 관한 정보를 DNS 서버에서 가져와서 보여줌

* ntpdate 명령어: 지정된 time 서버로부터 *시간 정보를 동기화*시킴

* passwd 명령어: 계정의 비밀번호를 변경함 (Password)

* ping 명령어: ICMP 프로토콜을 이용하여 네트워크에 연결된 *호스트의 연결 상태를 확인*하고, *호스트 간에 패킷이 왕복된 시간을 측정*하여 표시함

* pmap 명령어: 시스템의 프로세스 ID를 기준으로 *메모리 맵 정보*를 출력함

* pr 명령어: 텍스트 파일을 *인쇄가 가능한 표준 출력 형식*으로 변환함

* ps 명령어: 현재 시스템의 *프로세스 상태*를 출력함 (Process Status)

* pwd 명령어: *현재 작업 중인 디렉토리* 이름을 출력함 (Print Work Directory)

* rm 명령어: 파일이나 디렉토리를 *삭제*함

* rmdir 명령어: 빈 디렉토리를 삭제함

* route 명령어: *네트워크 라우팅 테이블*을 출력하거나 설정함

* script 명령어: *터미널에서 수행하는 작업한 모든 내용*을 텍스트 형식으로 저장함

* shutdown 명령어: 시스템을 종료하거나 재시작함

* sort 명령어: 텍스트 파일을 *행 단위로 정렬*함

* su 명령어: 다른 사용자로 *전환*함 (Switch User)

* sudo 명령어: 명령어를 root 권한으로 실행함

* tail 명령어: 텍스트 파일의 *마지막 행의 내용부터 출력*함

* tar 명령어: *여러 파일들을 하나의 파일로 묶음*

* time 명령어: 특정 *프로세스나 명령어에 사용된 시스템 자원 정보*를 출력함

* touch 명령어: 0바이트의 *빈 파일을 생성*하거나, 기존 파일이 있을 경우 *파일의 수정 시간을 현재 시간으로 변경*함

* tr 명령어: 특정 문자를 *다른 문자로 변경*함

* traceroute 명령어: 네트워크 경로를 확인하기 위해 *패킷이 거쳐 가는 경로를 추적*하여, 경로 중에 네트워크 부하가 높은 곳을 찾을 때 활용됨

* type 명령어: *명령어의 종류*를 알려줌

* uptime 명령어: *평균 시스템 부하 정보*를 출력함

* useradd 명령어: 사용자 계정을 생성함

* userdel 명령어: 사용자 계정을 삭제함

* usermod 명령어: 사용자를 그룹에 등록함 (User Modify)

* vmstat 명령어: *가상 메모리 상태*를 확인함

* w 명령어: 시스템에 *로그인한 사용자의 정보*를 출력함

* who 명령어: 사용자명과 로그인 일시를 표시함

## 스트림 편집기 sed

* grep처럼 정규표현식을 사용하며, 파이프를 이용하여 사용자가 필요로 하는 결과로 재처리할 수 있음
  - sed는 편집하고 있는 파일을 바꾸지 않는다.
  - sed의 연산자들은 입력 받은 모든 라인에 적용된다.

## awk (Aho Weinberger Kernighan)

* 텍스트 형태의 데이터를 *행과 열*로 구분하여 처리하고 결과를 출력하는 도구

## vi 편집기

### 모드의 종류

* 명령 모드
  - 다른 모드로 전환할 수 있는 기본 상태
  - 실행 직후, 또는 다른 모드에서 Esc 키를 누르면 됨
  - h (왼쪽 1칸 이동), j (아래로 1칸 이동), k (위로 1칸 이동), l (오른쪽으로 1칸 이동)
  - + (다음 라인의 첫 문자로 이동), - (위 라인의 첫 문자로 이동)
  - ^ 또는 0 (현재 라인에서 맨 앞의 첫 문자로 이동), $ (현재 라인에서 맨 뒤의 마지막 문자로 이동)
  - G (제일 마지막 라인의 맨 앞의 첫 문자로 이동)
  - r (커서가 위치한 문자를 다른 문자로 수정)
  - cw, [숫자]cw (커서의 위치부터 현재 단어의 끝까지 수정)
  - s, [숫자]s (커서의 위치부터 지정된 글자 수까지 내용을 대체함)
  - cc (커서가 위치한 행의 내용을 모두 수정)
  - C (커서의 위치부터 행의 끝까지 수정)
  - x, [숫자]x (커서가 위치한 문자 및 지정된 글자 수만큼 삭제)
  - dw, [숫자]dw (커서 위치의 단어 및 지정된 단어 수만큼 삭제)
  - dd, [숫자]dd (커서가 위치한 행 및 지정된 행 수만큼 삭제)
  - u (방금 수행한 명령 취소)
  - yy, [숫자]yy (커서가 위치한 행 및 지정된 행의 수를 복사)
  - p (커서가 위치한 행의 아래쪽에 붙여넣기)
  - P (커서가 위치한 행의 위쪽에 붙여넣기)

* ex 모드
  - 저장, 종료, 검색, 치환 등과 같은 명령을 내리기 위한 상태
  - :q (저장하지 않고 종료)
  - :q! (저장하지 않고 강제 종료)
  - :w (저장)
  - :w 파일명 (다른 이름으로 저장)
  - :wq (저장하고 종료)
  - :set nu (파일 내용의 각 행에 행 번호를 표시함)
  - :set nonu (행 번호 감추기)
  - :set list (눈에 보이지 않는 특수(개행) 문자를 표시함)
  - :set nolist (특수(개행) 문자 감추기)
  - :set showmode (현재 모드 표시)
  - :set noshowmode (현재 모드 감추기)
  - /키워드 (현재 커서로부터 뒤로 검색), n (뒤로 계속 찾기)
  - ?키워드 (현재 커서로부터 앞으로 검색), N (앞으로 계속 찾기)
  - :s/키워드1/키워드2/옵션 (키워드1을 키워드2로 치환)
  - (치환) s 앞에 %는 파일 전체이고 m,n은 m행부터 n행까지 적용한다는 뜻이다.
  - (옵션) g를 붙이면 전역 치환, 붙이지 않으면 1번째만 치환
  - (옵션) i를 붙이면 대소문자를 구분하지 않음
  - (옵션) c를 붙이면 치환할 때 물어봄

* 입력 모드
  - 편집기에 텍스트를 입력할 수 있는 상태
  - 명령 모드에서 i, I, a, A, o, O를 누르면 됨
  - i는 커서가 위치한 앞자리부터 입력할 수 있다.
  - I는 커서가 있는 행의 맨 앞부터 입력할 수 있다.
  - a는 커서가 위치한 뒷자리부터 입력할 수 있다.
  - A는 커서가 있는 행의 맨 끝에서 입력할 수 있다.
  - o는 커서가 위치한 다음 행으로 이동하여 입력을 시작한다.
  - O는 커서가 위치한 이전 행으로 이동하여 입력을 시작한다.

* 비주얼 모드
  - 편집하지 않고 문서를 보기만 할 수 있는 상태
  - 명령 모드에서 v를 누르면 됨
  - 명령 모드와 비슷하나 편집이 안됨

![image](https://github.com/Soonbum/Soonbum.github.io/assets/16474083/5cd5fdd0-54ce-4d99-8a0c-fe675656447d)

그 외에도 많은 명령어 및 기능이 있으므로 더 많은 정보를 알려면 검색을 해보십시오.

# 쉘 프로그래밍 문법

## 쉘 프로그래밍 시작하기

### 쉘 스크립트의 일반적인 구조

* 쉘 명령어 뒤에 스크립트 파일을 옵션으로 제공하여 실행함: `sh ./script.sh`
  - 만약 스크립트 파일에게 실행 권한을 부여하면 다음과 같이 실행할 수 있음: `./script.sh`

* 첫 라인에 다음 내용을 추가: `#!/bin/sh`
  - 작성된 스크립트가 Bourne Shell임을 커널에게 알려줌

* 변수명 앞에는 $ 기호를 붙임

* 주석 앞에는 # 기호를 붙임

### 변수

* 주의사항
  - "변수명=값" 형태로 작성하며, 숫자와 문자열 아무 형태가 가능함
  - "=" 문자 좌우에 공백이 없어야 함
  - 변수의 값에 공백이 있으면 ""로 감싸야 함
  - 변수명은 영문자로 시작해야 하며, 영문자와 숫자와 밑줄문자가 사용될 수 있음
* 전역 변수
  - 현재 쉘뿐만 아니라 해당 쉘에서 파생되는 자식 프로세스에서도 사용할 수 있음
  - export 명령어로 등록할 수 있음
  - env 또는 printenv 명령어로 등록된 전역 변수 확인 가능
* 지역 변수
  - 현재의 쉘에서만 사용 가능한 변수
  - set 명령어로 등록된 지역 변수 확인 가능
  - unset 명령어로 생성된 변수를 제거할 수 있음

## 주요 문법

* 사용자 입력 받기: read <변수명>
  - 해당 명령어를 입력하고 값을 입력하면, 변수에 사용자가 입력한 값이 저장됨 (Python의 input() 함수 역할)

* 수치 연산: expr <수식>
  - 연산자: +, -, *, /, %
  - 연산자와 숫자 또는 숫자형 변수 사이에는 반드시 공백이 있어야 함
  - 괄호를 사용할 때나 * 및 / 연산 시에는 \를 반드시 사용해야 함
```
$ CALC='expr 20 + 20'
$ CALC2='expr 205 + \( 3 \* 4 \)'
$ echo $CALC
40
$ echo $CALC2
217
```

* if문
  - if의 개수만큼 fi로 반드시 조건문을 종결시켜야 함
  - 단, elif를 사용할 경우에는 종결을 위한 개수에 구애 받지 않음

```
if 조건문
  then 명령어
    elif 조건문
      then 명령어
  else 명령어
if
```

조건문을 사용한 예시는 다음과 같습니다. (코드의 각 라인은 ;을 이용하여 합칠 수도 있음)

```
#!/bin/sh

echo -n "숫자 A를 입력하세요: "
read VAR1
echo -n "숫자 B를 입력하세요: "
read VAR2

if [ $VAR1 -eq $VAR2 ]
  then echo " 숫자 A와 B는 같습니다."
    elif [ $VAR1 -ge $VAR2 ]
      then echo " 숫자 A는 B보다 크거나 같습니다."
    elif [ $VAR1 -le $VAR2 ]
      then echo " 숫자 A는 B보다 작거나 같습니다."
fi
```

* test문
  - '[' 뒤와 ']' 앞에는 공백이 반드시 있어야 함
  - 문자열 변수를 사용할 때에는 ""로 감싸야 함

```
test 표현식
[ 표현식 ]
```

1. 수치 비교 (소수점 이하의 숫자는 무시함)

| 표현식        | true인 경우              |
| ------------- | ------------------------ |
| [ $A -eq $B ] | A와 B의 값이 같은 경우    |
| [ $A -ne $B ] | A와 B의 값이 다를 경우    |
| [ $A -gt $B ] | A가 B보다 큰 경우         |
| [ $A -lt $B ] | A가 B보다 작은 경우       |
| [ $A -ge $B ] | A가 B보다 크거나 같은 경우 |
| [ $A -le $B ] | A가 B보다 작거나 같은 경우 |

2. 파일 비교

| 표현식      | true인 경우                         |
| ----------- | ----------------------------------- |
| [ -s ]      | 파일이 존재하면서 크기가 0보다 큰 경우 |
| [ -f ]      | 디렉토리를 제외한 파일일 경우          |
| [ -d ]      | 파일을 제외한 디렉토리일 경우          |
| [ -w ]      | 쓰기가 가능한 경우                    |
| [ -r ]      | 읽기가 가능한 경우                    |
| [ ! -옵션 ] | 옵션의 조건이 거짓이 되는 경우         |

3. 문자열 비교

| 표현식                   | true인 경우                |
| ------------------------ | -------------------------- |
| ["문자열1" = "문자열2" ]  | 두 문자열이 같은 경우        |
| ["문자열1" != "문자열2" ] | 두 문자열이 다른 경우        |
| [ -z "문자열 ]           | 문자열의 길이가 0인 경우      |
| [ -n "문자열 ]           | 문자열의 길이가 0이 아닌 경우 |

```
#!/bin/sh
# 문자열 비교 예제입니다.
# X$n 파라미터에서 X는 NULL이 입력되는 것을 방지하는 안전장치입니다.

if [ X$1 = X$2 ]
  then
    echo "입력된 두 인수는 같습니다."
  elif [ X$1 != X$2 ]
    then
      echo "입력된 두 인수는 다릅니다."
fi
```

* Bourne Shell의 특수 파라미터: $1는 1번째 인수, $2는 2번째 인수를 의미한다. 다음 표는 특수 파라미터를 요약한 것이다.

| 특수 파라미터 | 설명 |
| --- | -------------- |
| $*  | 모든 인수 |
| $#  | 인수의 개수 |
| $?  | 가장 최근에 실행한 포그라운드 파이프라인의 종료 상태를 가지고 있다. 수행 결과가 error이면 1, 발생하지 않으면 0이다. |
| $$  | 현재 쉘의 프로세스 ID를 가지고 있다. |
| $!  | 가장 최근에 백그라운드로 실행된 프로세스의 ID를 가지고 있다. |
| $0  | 쉘 또는 쉘 스크립트의 이름을 가지고 있다. |
| $_  | 쉘이 시작되면서 설정되며, 실행된 쉘 스크립트의 절대 경로를 포함한다. |

* for문
  - 원소 목록의 유한한 수만큼의 명령을 반복하기 위해 사용됨
  - in 뒤의 원소들을 for 다음에 나오는 변수 값으로 하나씩 대치시켜 명령어A를 수행하고, in 뒤의 원소 개수만큼 실행하고 나서 done 뒤의 명령어B를 마지막으로 반복을 종료한다.

```
for 변수 in 원소1 원소2 원소3 ...
do
  명령어A
done
  명령어B
```

* while문
  - 조건이 만족하면 do와 done 사이의 명령어들을 반복해 실행한다.
  - 조건문이 항상 참이거나 0보다 크면 무한 반복문이 된다는 것을 유의하라. (Ctrl+C를 누르면 무한반복을 중단함)

```
while [ 조건 ]
do
  명령어
done
```

* until문
  - while문과 달리 반대로 조건문이 거짓이면 do와 done 사이의 명령어를 실행하고, 참이면 반복을 종료한다.

```
until [ 조건 ]
do
  명령어
done
```

* continue문과 break문
  - continue문은 반복문 수행 중간에서 continue 이하의 내용들을 무시하고 조건 검사를 다시 진행한다.
  - break문은 반복문을 종료하고 강제로 빠져나올 때 활용한다.
  - 단 중첩된 반복문의 경우, `continue n`을 이용해 continue 범위를 지정할 수 있음 (숫자 1은 인접한 1번째 반복문, 2는 인접한 2번째 반복문...)

* case문
  - 지정된 변수에 따라 사전 변수에 지정된 작업을 수행할 때 활용되며, 보통 쉘 프로그래밍 시 메뉴를 구성할 때 많이 사용된다.
  - case의 각 항목을 끝낼 때는 ;;를 사용하여 패턴을 종결짓도록 한다.
  - 앞의 패턴에서 지정되지 않은 입력 값이 입력될 때는 *) 부분에 기술된 명령을 수행한다.

```
case 변수 in
  패턴1)
    명령;;
  패턴2)
    명령;;
  패턴3)
    명령;;
  *)
    명령;;
esac
```

* 함수 만들기

```
함수명()
{
  명령
}
```

<!--

# 시스템 관리 쉘 스크립트

## 디스크 사용량 분석/보고
## 사용자 계정 일시 정지
## guest 및 공용 계정 초기화
## 서버의 네트워크 상태 감시
## 서비스 프로세스 상태 점검
## 특정 디렉토리의 파일 내용 일괄 수정하기
## 지정된 날짜의 웹 접속 통계
## 점검 결과를 메일로 보고
## ftp를 이용한 파일 전송 자동화
## cron 스케줄 등록
## 데몬 및 서비스 프로세스의 시작과 정지
## 로그 파일 로테이션

# 시스템 보안 쉘 스크립트

## SetUID와 SetGUI 설정 파일 점검
## 시스템 파일 접근 권한 확인
## 장치 디렉토리 내 일반 파일 존재 유무 점검
## root 이외의 UID가 0인 사용자 점검
## 패스워드 최소 길이 및 최대 사용 기간 설정 점검
## 불필요한 계정 존재 여부 점검
## 불필요한 서비스 존재 여부 점검
## 침해 시스템 분석용 로그 추출

# 나만의 시스템 관리 도구를 만들어 보자

## 시스템 관리 도구의 구조
## 시스템 관리 도구의 메뉴별 실행 결과
## 시스템 관리 도구의 쉘 스크립트 분석
## 시스템 관리 도구의 확장 방안

-->
