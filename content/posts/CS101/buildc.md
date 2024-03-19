
+++
title = 'C build'
date = 2023-11-03
featured_image = "http://t1.daumcdn.net/cfile/180D9C41504A57C90D"
tags = ['C', '42Seoul', 'CS101']
+++

{{<freshquote>}}
컴파일 언어(compiled language)는 코드가 실행되기 전 컴파일러를 거쳐서 기계어로 모두 변환되어 실행되는 프로그래밍 언어이다.
{{</freshquote>}}

<br>

## 1. Preprocess
- 전처리기 **cpp** 에 의해 수행
- header inclusion
	- 헤더 파일에 정의된 변수와 함수를 포함하는 과정
- macro expansion
	- `#define` 같은 매크로 등을 소스코드로 변경
- **`.c`** -> **`.i`**

<br>

## 2. Complie
- 컴파일러 **ccl** 에 의해 수행
- c언어 코드를 어셈블리어로 변환
- **`.i`** -> **`.s`**

<br>

## 3. Assemble
- 어셈블러 **as** 에 의해 수행
- 어셈블리어를 바이너리 형태로 변환 (목적 파일 생성)
- **`.s`** -> **`.o`**

<br>

## 4. Link
- 여러 목적파일과 라이브러리들을 모아 실행 가능한 단일 파일로 결합
- 정적 라이브러리도 함께 결합됨
	- 라이브러리는 이미 컴파일 되어있으므로 링크만 하면 바로 사용 가능
- 빌드 과정의 마지막 단계로서, 실행 파일이 생성되면 프로그램이 **빌드**되었다고 함

<br>

## 5. **Runtime**
- 목적 파일 처럼 중간 과정을 거치는 이유?
	- 소스를 각기 다른 언어로 작성했을 수도 있음
	- 한 파일에 모든 함수나 기능을 넣는 것이 비효율적이고 불가능에 가까움
	- 결국 쪼개진 각기 다른 여러 파일을 잘 합치기 위함

<br>
{{<alert>}}
<a href="https://elecbrandy.github.io/tags/CS101"> CS101 </a>
{{</alert>}}
<br>