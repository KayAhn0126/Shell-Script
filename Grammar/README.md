# Shell Script Grammar

## 🍎 쉘 스크립트 파일 작성 및 실행
```bash
$ vi script.sh
# ... 작성후 종료
$ chmod +x script.sh or chmod 755 script.sh # 파일에 실행 권한 설정
$ ./script.sh # 쉘 스크립트 실행
```

```bash
$ vi script.sh
# ... 작성후 종료
$ bash script.sh # bash 로 실행하면 권한을 주지 않고도 실행된다.
```

## 🍎 쉘 변수 선언
- 자료형을 기입하지 않는다.
- 값을 사용할 때는 변수명 앞에 특수문자 ‘$’을 사용한다.
- 변수는 모든 값을 문자열로 저장한다 (Ex. num=10) ← “10”과 같음
- 변수 생성 시 대입 연산자(’=’) 앞 뒤로 공백이 없어야 한다. (Ex. num=10)

## 🍎 변수 사용법
```bash
name="Kay"
echo $name
echo "My name is ${name}" # 문자열과 같이 사용할 땐 중괄호를 사용한다.
printf "%s" $name

// 출력
Kay
My name is Kay
Kay Kay@kay-VirtualBox:~$
```
- echo는 출력에 개행을 포함
- printf는 출력에 개행을 포함하지 않음

## 🍎 전역 변수 & 지역 변수
- 기본적으로 쉘에서 선언된 변수는 전역변수.
- 단 함수 안에서만 지역 변수를 사용할 수 있다.
    - 사용하려면 변수 명 앞에 local 을 붙여주면 된다.

## 🍎 환경 변수
- 쉘 스크립트에서 변수 명 앞에 export를 붙여주면 **환경 변수로 설정되어 자식 스크립트에서 사용 가능**하다.
- 다만 환경 변수 사용시 시스템에 미리 정의된 예약 변수와 변수명이 겹치지 않게 주의.
- 자식 스크립트

```bash
# /home/export_test.sh 파일을 만들고 작성

#!/usr/bin/bash

echo ${hello_world}
```

- 부모 스크립트

```bash
# 환경 변수 선언
export hello_world="global hello world"

# 자식 스크립트 호출은 스크립트 경로을 쓰면된다.
/home/export_test.sh
# > 자식스크립트의 코드에서 부모스크립트에서 정의한 hello_world변수값이 출력된다.
```

## 🍎 자료
- [참고 자료](https://inpa.tistory.com/entry/LINUX-쉘-프로그래밍-핵심-문법-총정리)