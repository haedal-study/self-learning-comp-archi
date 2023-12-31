# Chapter 02. 데이터

## 2.1 0과 1로 숫자를 표현하는 방법

- 0과 1을 나타내는 가장 작은 정보 단위를 비트라고 한다.
  - n 비트는 2^n 가지 정보를 표현할 수 있다.
  - 표현의 편의를 위해 byte, kB, MB, GB, TB 등의 단위를 사용한다.
- CPU 가 한 번에 처리할 수 있는 데이터 크기를 "word" 라고 한다.
  - 만약, CPU 가 한 번에 16bit 를 처리한다면 1워드는 16bit, 32bit 를 처리한다면 1word 는 32bit 이다.

## 2.2 0과 1로 문자를 표현하는 방법

### 문자 집합

- 컴퓨터가 인식하고 표현할 수 있는 문자의 모음이다.
- 문자 집합을 bit 로 변환하는 작업을 인코딩, 그 역은 디코딩이라 일컫는다.

#### ASCII (American Standard Code for Information Interchange)

- 초창기 문자 집합 중 하나로, 알파벳, 아라비아 숫자, 일부 특수 문자를 포함한다.
- 아스키 문자 집합에 속한 문자는 7bit 로 표현되며, 총 2^7 = 128개의 문자를 표현할 수 있다.
  - 실제론 8bit(1byte) 를 사용하나, 1bit 은 오류 검출을 위해 사용하는 parity bit 이기에 실질적인 문자 표현은 7bit 로 한다.

#### EUC-KR

- [웅장해지는 한글 인코딩 역사](https://d2.naver.com/helloworld/19187)

- 초성, 중성, 종성이 모두 결합된 한글 단어 (완성형 인코딩)에 2바이트 크기의 코드를 부여한다.
  - 즉, 한 글자를 표현하려면 16bit 가 필요하다.
  - 2350개 정도의 한글 단어를 표현할 수 있으나, 이 또한 모든 한글 조합을 표현할 수는 없다.

#### 유니코드와 UTF-8

- 모든 언어를 아우르는 문자 집합과 통일된 표준 인코딩 방식이다.
- ASCII, EUC-KR 이 글자에 부여된 값을 그대로 인코딩 값으로 삼은데 비해, 유니코드는 해당 값을 다양한 방법으로 인코딩한다.
  - 이는 UTF-{8, 16, 32} 가 있으며, 이는 즉 유니코드 문자 부여 값을 인코딩하는 방식이다.

## 여담으로...

### Javascript 의 URL Encoding

- [encodeURI](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/encodeURI)

  - URI 의 **특정 문자**를 UTF-8 로 인코딩해 1~4개의 escape 문자로 나타낸다.

    - 특정 문자

    - ```
      A–Z a–z 0–9 - _ . ! ~ * ' ( )

      ; / ? : @ & = + $ , # // encodeURIComponent 는 얘네도 인코딩한다.
      ```

### 브라우저에서의 EUC-KR 인코딩

- EUC-KR 로 이루어진 웹 페이지에서 2350 자의 한글에 벗어나는 문자가 존재한다면, 브라우저마자 인코딩 처리 방식이 다르다.

- 아래는 "똠방각하" 를 브라우저마다 다르게 인코딩한 결과값이다.

- | 브라우저          | 인코딩된 값                                | 화면에 표시되는 문자열 |
  | ----------------- | ------------------------------------------ | ---------------------- |
  | Internet Explorer | %26%2346624%3B%B9%E6%B0%A2%C7%CF           | `&#46624;방각하`       |
  | Firefox           | %A4%D4%A4%A8%A4%C7%A4%B1%B9%E6%B0%A2%C7%CF | `ㄸㅗㅁ방각하`         |
  | Chome             | %8Cc%B9%E6%B0%A2%C7%CF                     | `c방각하`              |

  - Internet Explorer는 EUC-KR에 없는 문자의 경우 유니코드 포인트 값으로 표현한다. 즉 '똠'의 유니코드 코드 포인트 값인 46624(U+B620)으로 URL 을 인코딩 한다.
  - Chrome은 EUC-KR에 있는 확장 완성형의 문자를 지원하지 않기 때문에 '똠'을 인코딩할 수 없다.
  - Firefox는 한글 채움 문자를 이용하여 음절을 표시하고 있다. 한글 채움 문자는 KS X 1001 표준안에 정의되어 있으며, (채움) 초성 중성 종성의 형태로 표시하고, 초성, 중성, 종성의 값이 없는 경우 (채움)으로 표시한다. EUC-KR 인코딩에서는 (채움) 값이 0xA4 0xD4이므로, 다음과 같이 인코딩된다.
