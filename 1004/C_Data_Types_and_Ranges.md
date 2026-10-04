# C언어 기본 자료형과 데이터 표현

##  학습 목표

* C언어의 기본 자료형 이해하기
* 정수형과 실수형 자료형의 차이 이해하기
* `signed`와 `unsigned`의 차이 이해하기
* 자료형별 메모리 크기 확인하기
* 자료형의 최소값과 최대값 확인하기
* 정수 오버플로우와 실수 오버플로우 및 언더플로우 이해하기
* `sizeof`, `limits.h`, `stdint.h`, `float.h` 활용하기

---

## 1. 정수형 변수 선언과 출력

### 코드

```c
#include <stdio.h>

int main()
{
    int num1 = 10, num2 = 20, num3 = 30;

    printf("%d %d %d\n", num1, num2, num3);

    return 0;
}
```

### 코드 설명

* `int` : 정수를 저장하는 자료형이다.
* `num1`, `num2`, `num3` : 각각 10, 20, 30으로 초기화한다.
* `printf()` : 변수에 저장된 값을 출력한다.
* `%d` : 정수형 데이터를 출력할 때 사용하는 서식 지정자이다.
* `\n` : 줄바꿈을 의미한다.
* `return 0` : 프로그램이 정상적으로 종료되었음을 나타낸다.

### 배운 점

* 변수를 선언할 때 자료형을 지정해야 한다.
* 변수는 선언과 동시에 초기화할 수 있다.
* 여러 개의 동일한 자료형 변수를 한 줄에 선언할 수 있다.
* `printf()`의 서식 지정자를 이용해 변수의 값을 출력할 수 있다.

---

## 2. 정수형 자료형의 종류

### 코드

```c
#include <stdio.h>

int main()
{
    int num1 = 10, num2 = 20, num3 = 30;

    printf("%d %d %d\n", num1, num2, num3);

    return 0;
}
```

### 코드 설명

앞선 실습과 동일한 코드로, 정수형 변수를 선언하고 출력하는 기본 구조를 다시 확인한다.

### 배운 점

* C언어 프로그램은 `main()` 함수에서 실행을 시작한다.
* `#include <stdio.h>`를 통해 표준 입출력 함수를 사용할 수 있다.
* `printf()`를 이용하면 여러 변수를 한 번에 출력할 수 있다.

---

## 3. 다양한 정수형 자료형 사용하기

### 코드

```c
#include <stdio.h>

int main()
{
    char num1 = 10;
    short num2 = 30000;
    int num3 = -1234567890;
    long num4 = 1234567890;
    long long num5 = -1234567890123456789;

    printf("%d %d %d %ld %lld\n", num1, num2, num3, num4, num5);

    return 0;
}
```

### 코드 설명

C언어에서 사용하는 다양한 정수형 자료형을 확인하는 코드이다.

| 자료형         | 설명             | 출력 서식  |
| ----------- | -------------- | ------ |
| `char`      | 문자 또는 작은 정수 저장 | `%d`   |
| `short`     | 짧은 정수 저장       | `%d`   |
| `int`       | 일반적인 정수 저장     | `%d`   |
| `long`      | 긴 정수 저장        | `%ld`  |
| `long long` | 더 큰 범위의 정수 저장  | `%lld` |

`char`와 `short`는 `printf()`에 전달될 때 정수 승격이 일어나므로 여기서는 `%d`를 사용한다.

### 배운 점

* C언어에는 여러 종류의 정수형 자료형이 존재한다.
* 자료형에 따라 표현할 수 있는 값의 범위가 달라진다.
* `long`과 `long long`은 서로 다른 자료형이다.
* 자료형에 맞는 출력 서식 지정자를 사용해야 한다.
* 자료형의 정확한 크기는 운영체제와 컴파일러 환경에 따라 달라질 수 있다.

---

## 4. 부호 없는 정수형 unsigned

### 코드

```c
#include <stdio.h>

int main()
{
    unsigned char num1 = 200;

    unsigned short num2 = 60000;

    unsigned int num3 = 4123456789;

    unsigned long num4 = 4123456789;

    unsigned long long num5 = 12345678901234567890;

    printf("%u %u %u %lu %llu\n", num1, num2, num3, num4, num5);

    return 0;
}
```

### 코드 설명

`unsigned`는 음수를 표현하지 않고 0 이상의 정수를 표현하는 자료형이다.

| 자료형                  | 설명            | 출력 서식  |
| -------------------- | ------------- | ------ |
| `unsigned char`      | 부호 없는 작은 정수   | `%u`   |
| `unsigned short`     | 부호 없는 짧은 정수   | `%u`   |
| `unsigned int`       | 부호 없는 정수      | `%u`   |
| `unsigned long`      | 부호 없는 긴 정수    | `%lu`  |
| `unsigned long long` | 부호 없는 매우 큰 정수 | `%llu` |

일반적인 8비트 환경에서 `unsigned char`는 0부터 255까지 표현할 수 있다.

### 배운 점

* `unsigned`는 음수를 표현하지 않는다.
* 같은 비트 수라면 signed보다 양수 표현 범위가 넓어진다.
* 음수가 필요하지 않은 데이터에 활용할 수 있다.
* `unsigned` 자료형에 맞는 출력 서식 지정자를 사용해야 한다.

---

## 5. 자료형의 표현 범위를 벗어난 값

### 코드

```c
#include <stdio.h>

int main()
{
    char num1 = 128;

    unsigned char num2 = 256;

    printf("%d %u\n", num1, num2);

    return 0;
}
```

### 코드 설명

자료형이 표현할 수 있는 범위보다 큰 값을 대입하는 실습이다.

일반적인 8비트 환경에서:

* signed `char` : -128 ~ 127
* unsigned `char` : 0 ~ 255

따라서 `128`과 `256`은 각각 해당 자료형의 일반적인 표현 범위를 벗어난다.

signed `char`에 범위를 벗어난 값을 변환하는 결과는 구현에 따라 달라질 수 있다. unsigned `char`의 경우에는 해당 자료형의 범위에 맞춰 모듈러 방식으로 변환된다.

### 배운 점

* 모든 자료형은 표현할 수 있는 값의 범위가 정해져 있다.
* 범위를 초과하는 값을 저장하면 데이터가 의도한 값과 달라질 수 있다.
* signed와 unsigned의 범위 초과 처리 방식은 다르다.
* 변수를 선언할 때 저장할 데이터의 크기를 고려해야 한다.

---

## 6. sizeof 연산자로 메모리 크기 확인하기

### 코드

```c
#include <stdio.h>

int main()
{
    int num1 = 0;
    int size;

    size = sizeof num1;

    printf("num1의 크기 : %d\n", size);

    return 0;
}
```

### 코드 설명

`sizeof`는 자료형이나 변수가 차지하는 메모리 크기를 바이트(Byte) 단위로 반환하는 연산자이다.

```c
sizeof num1
```

위 코드는 `num1` 변수의 메모리 크기를 확인한다.

일반적인 환경에서 `int`는 4바이트이다.

### 배운 점

* `sizeof`를 사용하면 자료형과 변수의 메모리 크기를 확인할 수 있다.
* 메모리 크기의 단위는 바이트이다.
* `int`가 항상 4바이트인 것은 아니며 시스템에 따라 달라질 수 있다.
* `sizeof`의 반환형은 `size_t`이므로 `%zu`를 사용해 출력하는 것이 적절하다.

---

## 7. 정수형 자료형의 최소값 확인하기

### 코드

```c
#include <stdio.h>
#include <limits.h>

int main()
{
    char num1 = CHAR_MIN;
    short num2 = SHRT_MIN;
    int num3 = INT_MIN;
    long num4 = LONG_MIN;
    long long num5 = LLONG_MIN;

    printf("%d %d %d %ld %lld\n", num1, num2, num3, num4, num5);

    return 0;
}
```

### 코드 설명

`<limits.h>` 헤더 파일에는 정수형 자료형의 최소값과 최대값을 나타내는 매크로가 정의되어 있다.

| 매크로         | 의미             |
| ----------- | -------------- |
| `CHAR_MIN`  | char의 최소값      |
| `SHRT_MIN`  | short의 최소값     |
| `INT_MIN`   | int의 최소값       |
| `LONG_MIN`  | long의 최소값      |
| `LLONG_MIN` | long long의 최소값 |

각 자료형의 최소값을 변수에 저장하고 출력한다.

### 배운 점

* `<limits.h>`를 사용하면 정수형 자료형의 범위를 확인할 수 있다.
* 직접 숫자를 입력하지 않아도 자료형의 최소값과 최대값을 사용할 수 있다.
* 시스템마다 자료형의 범위가 다를 수 있으므로 매크로를 사용하는 것이 유용하다.

---

## 8. 최소값과 최대값을 기준으로 연산하기

### 코드

```c
#include <stdio.h>
#include <limits.h>

int main()
{
    char num1 = CHAR_MIN + 1;
    short num2 = SHRT_MIN + 1;
    int num3 = INT_MIN + 1;
    long long num4 = LLONG_MIN + 1;

    printf("%d %d %d %ld %lld\n", num1, num2, num3, num4);

    unsigned char num5 = UCHAR_MAX + 1;

    unsigned short num6 = USHRT_MAX + 1;

    unsigned int num7 = UINT_MAX + 1;

    unsigned long long num8 = ULLONG_MAX + 1;

    printf("%u %u %u %llu\n", num5, num6, num7, num8);

    return 0;
}
```

### 코드 설명

정수형 자료형의 최소값에 1을 더하거나 unsigned 자료형의 최대값에 1을 더하는 실습이다.

signed 정수형은 최소값보다 1 큰 값을 저장한다.

unsigned 정수형은 최대값보다 1 큰 값을 저장하려고 한다.

unsigned 정수는 범위에 따라 모듈러 연산 방식으로 처리된다.

다만 이 코드에서 `UINT_MAX + 1`과 `ULLONG_MAX + 1`은 피연산자의 타입과 연산 규칙에 따라 결과가 달라질 수 있다. 특히 `ULLONG_MAX + 1`은 unsigned long long 연산에서 0으로 순환한다.

### 배운 점

* signed 정수와 unsigned 정수의 범위 처리 방식이 다르다.
* unsigned 정수는 표현 범위를 초과하면 모듈러 연산 방식으로 순환한다.
* signed 정수의 범위를 벗어나는 연산은 정의되지 않은 동작이 발생할 수 있다.
* 정수 연산을 할 때 자료형의 범위를 고려해야 한다.

---

## 9. 정수형 최소값보다 작은 값 연산하기

### 코드

```c
#include <stdio.h>
#include <limits.h>

int main()
{
    char num1 = CHAR_MIN - 1;
    short num2 = SHRT_MIN - 1;
    int num3 = INT_MIN - 1;
    long long num4 = LLONG_MIN - 1;

    printf("%d %d %d %ld %lld\n", num1, num2, num3, num4);

    unsigned char num5 = 0 - 1;

    unsigned short num6 = 0 - 1;

    unsigned int num7 = 0 - 1;

    unsigned long long num8 = 0 - 1;

    printf("%u %u %u %llu\n", num5, num6, num7, num8);

    return 0;
}
```

### 코드 설명

각 signed 정수형의 최소값보다 1 작은 값을 계산한다.

일반적으로 signed 정수형의 최소값보다 작은 값을 표현하려고 하면 정의되지 않은 동작이 발생할 수 있다.

반면 unsigned 정수형은 음수를 표현하지 않기 때문에 해당 unsigned 자료형으로 변환될 때 모듈러 방식으로 값이 변환된다.

예를 들어 8비트 unsigned 정수에서는:

```text
0 - 1 = 255
```

가 된다.

### 배운 점

* signed 정수의 범위를 벗어나는 연산은 위험하다.
* unsigned 정수는 모듈러 방식으로 값이 변환된다.
* unsigned 정수형에서 0보다 작은 값이 변환되면 큰 양수가 될 수 있다.
* 정수형의 오버플로우는 signed와 unsigned를 구분해서 이해해야 한다.

---

## 10. 자료형의 최대 범위를 초과하는 값 대입하기

### 코드

```c
#include <stdio.h>

int main()
{
    unsigned char num1 = 256;
    unsigned short num2 = 65536;
    long long num3 = 9223372036854775808;

    printf("%u %u %lld\n", num1, num2, num3);

    return 0;
}
```

### 코드 설명

자료형의 일반적인 표현 범위를 초과하는 숫자를 변수에 대입하는 실습이다.

일반적인 환경에서:

* `unsigned char` : 0 ~ 255
* `unsigned short` : 0 ~ 65535
* 64비트 `long long` : -9223372036854775808 ~ 9223372036854775807

따라서 앞의 두 변수는 표현 범위를 초과한다.

또한 `9223372036854775808`은 일반적인 64비트 signed `long long`의 최대값보다 1 크다. 이 정수 리터럴의 타입과 변환에도 주의해야 한다.

### 배운 점

* 자료형이 표현할 수 있는 범위를 넘어서는 값을 저장할 때 주의해야 한다.
* 정수 리터럴도 크기에 따라 타입이 결정된다.
* 큰 숫자를 다룰 때는 적절한 자료형과 리터럴 접미사를 고려해야 한다.
* 단순히 자료형을 크게 지정하는 것만으로 모든 범위 문제가 해결되는 것은 아니다.

---

## 11. 여러 자료형의 메모리 크기 합산하기

### 코드

```c
#include <stdio.h>

int main()
{
    short num1;
    long long num2;

    printf("%d\n", sizeof(num1) + sizeof(num2) + sizeof(int));

    return 0;
}
```

### 코드 설명

`sizeof`를 이용해 여러 자료형이 차지하는 메모리 크기를 더하는 코드이다.

일반적인 환경을 기준으로:

* `short` : 2바이트
* `long long` : 8바이트
* `int` : 4바이트

위 환경에서는 총 14바이트가 출력된다.

실제 크기는 컴파일러와 시스템에 따라 달라질 수 있다.

### 배운 점

* `sizeof`는 변수뿐 아니라 자료형에도 사용할 수 있다.
* 여러 자료형의 크기를 합산할 수 있다.
* 자료형마다 사용하는 메모리 크기가 다르다.
* 메모리 사용량을 확인할 때 `sizeof`를 활용할 수 있다.

---

## 12. 정수형 자료형의 최대값 확인하기

### 코드

```c
#include <stdio.h>
#include <limits.h>

int main()
{
    char num1 = CHAR_MAX;
    short num2 = SHRT_MAX;
    int num3 = INT_MAX;
    long num4 = LONG_MAX;
    long long num5 = LLONG_MAX;

    printf("%d %d %d %ld %lld\n", num1, num2, num3, num4, num5);

    return 0;
}
```

### 코드 설명

`<limits.h>`에서 제공하는 매크로를 사용하여 각 정수형 자료형의 최대값을 저장하고 출력한다.

| 매크로         | 의미             |
| ----------- | -------------- |
| `CHAR_MAX`  | char의 최대값      |
| `SHRT_MAX`  | short의 최대값     |
| `INT_MAX`   | int의 최대값       |
| `LONG_MAX`  | long의 최대값      |
| `LLONG_MAX` | long long의 최대값 |

### 배운 점

* `limits.h`를 이용해 자료형의 최대값을 확인할 수 있다.
* 정수형 자료형마다 최대 표현 범위가 다르다.
* 최소값과 최대값을 함께 확인하면 자료형의 전체 표현 범위를 이해할 수 있다.

---

## 13. stdint.h를 이용한 정확한 비트 수 자료형

### 코드

```c
#include <stdio.h>
#include <stdint.h>

int main()
{
    int8_t num1 = INT8_MIN;
    uint16_t num2 = UINT16_MAX;
    int32_t num3 = INT32_MAX;
    uint64_t num4 = UINT64_MAX;

    printf("%d %u %d %llu\n", num1, num2, num3, num4);

    return 0;
}
```

### 코드 설명

`<stdint.h>`는 정확한 비트 수를 지정할 수 있는 정수형 자료형을 제공한다.

| 자료형        | 설명            |
| ---------- | ------------- |
| `int8_t`   | 8비트 부호 있는 정수  |
| `uint16_t` | 16비트 부호 없는 정수 |
| `int32_t`  | 32비트 부호 있는 정수 |
| `uint64_t` | 64비트 부호 없는 정수 |

또한 다음과 같은 매크로를 사용할 수 있다.

* `INT8_MIN` : 8비트 signed 정수의 최소값
* `UINT16_MAX` : 16비트 unsigned 정수의 최대값
* `INT32_MAX` : 32비트 signed 정수의 최대값
* `UINT64_MAX` : 64비트 unsigned 정수의 최대값

### 배운 점

* `<stdint.h>`를 이용하면 비트 수가 명확한 정수형을 사용할 수 있다.
* `int`, `long`처럼 시스템에 따라 크기가 달라지는 자료형의 한계를 보완할 수 있다.
* 시스템 간 데이터 크기를 일정하게 유지해야 하는 프로그램에서 유용하다.
* 실제 출력에서는 `<inttypes.h>`의 `PRId8`, `PRIu16`, `PRId32`, `PRIu64` 같은 매크로를 활용하면 이식성을 높일 수 있다.

---

## 14. 실수형 자료형과 지수 표기법

### 코드

```c
#include <stdio.h>

int main()
{
    float num1 = 3.e5f;

    double num2 = -1.3827e-2;

    long double num3 = 5.32e+9l;

    printf("%f %f %Lf\n", num1, num2, num3);

    printf("%e %e %Le\n", num1, num2, num3);

    return 0;
}
```

### 코드 설명

C언어의 대표적인 실수형 자료형인 `float`, `double`, `long double`을 사용하는 코드이다.

| 자료형           | 설명         | 출력 서식        |
| ------------- | ---------- | ------------ |
| `float`       | 단정밀도 실수형   | `%f`, `%e`   |
| `double`      | 배정밀도 실수형   | `%f`, `%e`   |
| `long double` | 확장 정밀도 실수형 | `%Lf`, `%Le` |

지수 표기법은 다음과 같이 사용한다.

```text
3.e5f      = 3 × 10^5
-1.3827e-2 = -1.3827 × 10^-2
5.32e+9l   = 5.32 × 10^9
```

숫자 뒤에 붙는 접미사는 리터럴의 자료형을 나타낸다.

* `f` : float
* `l` : long double

### 배운 점

* C언어에서는 정수뿐 아니라 실수도 다양한 자료형으로 저장할 수 있다.
* `float`, `double`, `long double`은 정밀도와 표현 범위가 다르다.
* `e`를 이용해 지수 표기법으로 숫자를 표현할 수 있다.
* 실수형 자료형에 맞는 출력 서식 지정자를 사용해야 한다.

---

## 15. 실수형 자료형의 메모리 크기 확인하기

### 코드

```c
#include <stdio.h>

int main()
{
    float num1 = 0.0f;
    double num2 = 0.0;
    long double num3 = 0.0l;

    printf("float : %d, double : %d, long double : %d\n",
        sizeof(num1),
        sizeof(num2),
        sizeof(num3)
    );

    return 0;
}
```

### 코드 설명

`sizeof`를 사용하여 실수형 자료형이 사용하는 메모리 크기를 확인한다.

일반적인 환경에서는 다음과 같은 크기를 가진다.

| 자료형           | 일반적인 메모리 크기     |
| ------------- | --------------- |
| `float`       | 4바이트            |
| `double`      | 8바이트            |
| `long double` | 8바이트 또는 16바이트 등 |

`long double`은 운영체제와 컴파일러에 따라 메모리 크기와 정밀도가 달라질 수 있다.

### 배운 점

* `sizeof`는 정수형뿐 아니라 실수형에도 사용할 수 있다.
* 실수형 자료형도 메모리 크기가 서로 다르다.
* 메모리 크기가 크다고 항상 모든 환경에서 정밀도가 같은 것은 아니다.
* `sizeof`의 결과를 출력할 때는 `%zu`를 사용하는 것이 적절하다.

---

## 16. float.h를 이용한 실수형 최소값과 최대값 확인하기

### 코드

```c
#include <stdio.h>
#include <float.h>

int main()
{
    float num1 = FLT_MIN;
    float num2 = FLT_MAX;
    double num3 = DBL_MIN;
    double num4 = DBL_MAX;
    long double num5 = LDBL_MIN;
    long double num6 = LDBL_MAX;

    printf("%.40f\n %.2f\n", num1, num2);

    printf("%e %e\n", num3, num4);

    printf("%Le %Le\n", num5, num6);

    return 0;
}
```

### 코드 설명

`<float.h>`는 실수형 자료형의 표현 범위와 정밀도에 관한 정보를 제공하는 헤더 파일이다.

| 매크로        | 의미                       |
| ---------- | ------------------------ |
| `FLT_MIN`  | float의 양의 정규화된 최소값       |
| `FLT_MAX`  | float의 최대값               |
| `DBL_MIN`  | double의 양의 정규화된 최소값      |
| `DBL_MAX`  | double의 최대값              |
| `LDBL_MIN` | long double의 양의 정규화된 최소값 |
| `LDBL_MAX` | long double의 최대값         |

출력할 때 사용하는 서식 지정자도 확인한다.

* `%.40f` : 소수점 아래 40자리 출력
* `%.2f` : 소수점 아래 2자리 출력
* `%e` : 지수 표기법으로 출력
* `%Le` : long double을 지수 표기법으로 출력

### 배운 점

* `<float.h>`를 통해 실수형 자료형의 최소값과 최대값을 확인할 수 있다.
* 실수형은 정수형과 다른 방식으로 수를 표현한다.
* `%f`와 `%e`를 이용해 실수를 다양한 형태로 출력할 수 있다.
* `FLT_MIN`은 0에 가장 가까운 모든 양수 중 최소값이 아니라 양의 정규화된 값 중 최소값이다.

---

## 17. 실수형 언더플로우와 오버플로우

### 코드

```c
#include <stdio.h>
#include <float.h>

int main()
{
    float num1 = FLT_MIN;
    float num2 = FLT_MAX;

    num1 = num1 / 100000000.0f;

    num2 = num2 * 1000.0f;

    printf("%e %e\n", num1, num2);

    return 0;
}
```

### 코드 설명

실수형 자료형의 표현 범위를 벗어나는 연산을 확인하는 코드이다.

첫 번째 연산:

```c
num1 = num1 / 100000000.0f;
```

`FLT_MIN`을 매우 작은 값으로 나눈다.

이를 통해 실수형의 표현 가능한 범위보다 작은 값이 만들어지는 언더플로우(Underflow)를 확인한다.

두 번째 연산:

```c
num2 = num2 * 1000.0f;
```

`FLT_MAX`에 1000을 곱해 표현 가능한 최대 범위보다 큰 값을 만들려고 한다.

이를 통해 실수형의 오버플로우(Overflow)를 확인한다.

일반적인 IEEE 754 환경에서는 오버플로우 결과가 양의 무한대(`inf`)로 나타날 수 있다.

### 배운 점

* 실수형 자료형도 표현할 수 있는 범위가 정해져 있다.
* 언더플로우는 너무 작은 값을 표현하려 할 때 발생한다.
* 오버플로우는 너무 큰 값을 표현하려 할 때 발생한다.
* 실수형은 정수형과 달리 무한대와 비정규화 수 등의 표현을 지원할 수 있다.
* 실수 계산을 할 때도 자료형의 표현 범위를 고려해야 한다.

---

#  전체 학습 정리

## 1. 기본 정수형 자료형

| 자료형         | 설명         |
| ----------- | ---------- |
| `char`      | 문자 및 작은 정수 |
| `short`     | 짧은 정수      |
| `int`       | 일반적인 정수    |
| `long`      | 긴 정수       |
| `long long` | 더 큰 범위의 정수 |

## 2. 부호에 따른 차이

| 구분         | 설명        |
| ---------- | --------- |
| `signed`   | 음수와 양수 표현 |
| `unsigned` | 0과 양수만 표현 |

## 3. 실수형 자료형

| 자료형           | 설명        |
| ------------- | --------- |
| `float`       | 단정밀도 실수   |
| `double`      | 배정밀도 실수   |
| `long double` | 확장 정밀도 실수 |

## 4. 주요 헤더 파일

| 헤더 파일      | 역할                     |
| ---------- | ---------------------- |
| `stdio.h`  | 표준 입출력 함수 제공           |
| `limits.h` | 정수형 자료형의 범위 정보 제공      |
| `stdint.h` | 정확한 비트 수를 지정하는 정수형 제공  |
| `float.h`  | 실수형 자료형의 범위와 정밀도 정보 제공 |

## 5. 핵심 연산자와 개념

| 개념        | 설명                       |
| --------- | ------------------------ |
| `sizeof`  | 자료형 및 변수의 메모리 크기 확인      |
| `%d`      | int 출력                   |
| `%u`      | unsigned int 출력          |
| `%ld`     | long 출력                  |
| `%lld`    | long long 출력             |
| `%f`      | double 또는 float 출력       |
| `%Lf`     | long double 출력           |
| Overflow  | 표현 가능한 최대 범위를 초과하는 현상    |
| Underflow | 표현 가능한 작은 값의 범위를 벗어나는 현상 |

---

##  이번 학습을 통해 배운 점

이번 실습을 통해 C언어의 자료형이 단순히 데이터를 저장하는 역할만 하는 것이 아니라, 데이터의 표현 범위와 메모리 사용량, 연산 결과에도 영향을 준다는 것을 배웠다.

특히 `signed`와 `unsigned`의 차이, `sizeof`를 활용한 메모리 크기 확인, `limits.h`와 `float.h`를 이용한 자료형의 표현 범위 확인 방법을 익혔다.

또한 정수형과 실수형은 범위를 초과했을 때 동작 방식이 다르다는 점을 이해했다.

앞으로 프로그램을 작성할 때는 저장하려는 데이터의 크기와 범위를 고려하여 적절한 자료형을 선택해야 한다.
