# You Don't Know JS: Up & Going

# Chapter 1: Into Programming

*You Don't Know JS* (*YDKJS*) 시리즈에 오신걸 환영합니다.

*Up & Going*은 프로그래밍의 여러가지 기본 개념에 대한 소개입니다. -- 물론 우리는 주로 자바스크립트를 집중해서 배울 것입니다(가끔은 JS 외적인 부분도 포함 합니다). -- 그리고 시리즈의 나머지 부분들에 대한 접근법과 이해하기 위한 방법이기도 합니다. 특히 여러분이 프로그래밍 혹은 자바스크립트에 입문하는 경우라면 이 책은 *첫 시작*에 필요한 것들을 간단히 설명해 줄 것입니다.

이 책은 프로그래밍 기본원리에 대해서 아주 자세히 시작합니다. 이 책은 주로 여러분이 사전 프로그래밍 경험이 거의 없는 상태에서 *YDKJS*를 처음 시작하는 경우와, 자바스크립트에 대한 내용을 통해 프로그래밍에 대한 이해를 시작하려는 사람을 대상으로 합니다.

1장은 *프로그래밍을 시작*하는데 있어서 여러분들이 배워야 하고 연습해야 하는 것들에 대해 전반적으로 다룰 것입니다. 이러한 주제들에 대해 더 자세히 설명해주는 다른 훌륭한 프로그래밍 소개 자료들이 많습니다. 이 장 뿐만 아니라 다른 자료들도 참고하시길 권장드립니다.

전반적인 프로그래밍 기초에 편해지셨다면, 2장은 자바스크립트에 조금 더 익숙해지도록 도와 줄 것입니다. 2장은 자바스크립트가 무엇인지 소개 합니다. 다시 말씀드리지만, 이 시리즈는 종합적인 가이드가 아닙니다. 다른 YDKJS 책들이 준비되어 있습니다!

이미 자바스크립트에 어느정도 익숙하시다면, YDKJS에서 기대할 수 있는 내용을 잠깐 엿볼 수 있는 3장을 먼저 살펴보고 바로 (다른 시리즈로) 건너 뛰셔도 좋습니다!

## 코드

처음부터 시작해봅시다.

종종 *소스코드* 혹은 *코드*라고 언급되는 프로그램은 컴퓨터에게 업무를 수행하도록 전달하는 특별한 명령의 집합 입니다. 자바스크립트로 직접 브라우저에 있는 개발자 콘솔에서 직접 코드를 입력할수 있지만 보통 코드는 텍스트 파일로 저장이됩니다. 이는 곧 다루게 될 것입니다.

유효한 형식과 명령들의 조합으로 구성된 규칙들을 *컴퓨터 언어*라고 합니다. 때로는 *문법*이라고도 합니다. 영어에서 처럼, 단어를 철자하는 방법과 단어와 구두점을 사용하여 문장을 만드는 방법과 아주 비슷합니다.

### 문

컴퓨터 언어에서는 단어, 숫자, 특정한 일을 수행하는 연산자의 집합을 *문*이라고 합니다. 자바스크립트에서, 문은 다음과 같습니다.

```js
a = b * 2;
```

철자 `a`와 `b`를 *변수*라고 합니다.("변수"를 참고하세요). 이는 어떤 물건을 보관 할 수 있는 단순한 상자와 같습니다. 변수는 프로그램에서 사용되는 값(숫자 42와 같은)들을 가지고 있습니다. 값 자체를 기호로 표시된 상징적인 값 처럼 생각할 수 있습니다.

반대로, 2는 *상수값*이라고 하는 단순한 값 그 자체 입니다. 왜냐하면 변수가 어디에 저장되지 않고 독립적으로 있기 때문입니다.

`=` 과 `*` 문자들은 *연산자*("Operators"를 참고하세요) 입니다. 값과 변수를 이용하여 할당과 수학곱셈과 같은 동작을 수행합니다.

자바스크립트에서 대부분의 문은 세미콜론(`;`)으로 끝납니다.

문 `a = b * 2;` 는 대략적으로 컴퓨터에게 현재 값을 변수 `b`에 저장시키고, 그 값을 `2`로 곱한다음에, 돌려받은 결과값을 `a` 라고하는 변수에 저장하라고 명령 합니다.

프로그램은 단지 여러 문들의 집합입니다. 각각의 문들은 프로그램의 목적을 수행하기 위해 모든 단계에서 차례로 기술됩니다.

### 표현식

문은 하나 이상의 *표현식*으로 이루어 집니다. 표현식은 변수나 값, 혹은 변수들의 집합이나 연산자와 함께 결합된 값들에 대한 참조입니다.

예를들면:

```js
a = b * 2;
```

이 문은 네가지 표현식을 포함하고 있습니다:

* `2`는 *상수 값 표현식* 입니다.
* `b`는 현재값을 가져오는 *변수 표현식* 입니다.
* `b * 2`는 곱셈을 하는 *산술 표현식* 입니다.
* `a = b * 2`는 *할당 표현식* 입니다. 이는, `b * 2` 표현식을 변수 `a`에 할당하는 것입니다.(할당에 대해서는 다음에 자세히 다루겠습니다.)

아래와 같이, 독립적으로 있는 일반적인 표현식은 또한 *표현문*이기도 합니다.

```js
b * 2;
```

이러한 표현문은 일반적이지 않고 유용하지도 않을뿐더러 프로그램 실행에 어떠한 영향도 주지 않습니다. 즉 `b` 값을 가져와서 `2`로 곱셈을 하지만, 그 결과값으로 어떠한 것도 수행하지 않습니다.

전체문은 함수호출 표현식 자체 이므로, 더 일반적인 표현문은 *호출 표현식* 문("함수"를 확인해보세요) 입니다.

```js
alert( a );
```

### 프로그램 실행하기

프로그래밍을 할 때의 문집합들은 어떻게 컴퓨터가 원하는 동작을 수행하게 만들수 있을까요? 프로그램은 *실행*이 필요합니다. 이는 또한 *프로그램 실행* 이라고도 합니다.

`a = b * 2` 와 같은 문은 개발자들에게는 읽고 쓰기 쉽습니다. 하지만 컴퓨터가 바로 이해할 수 있는 형식은 아닙니다. 그래서 컴퓨터(*인터프리터* 혹은 *컴파일러*)에 있는 특별한 도구가 컴퓨터가 이해할 수 있는 명령어로 코드를 해석하는것에 사용됩니다.

몇몇 컴퓨터 언어같은경우, 명령어 해석이 주로 위에서 아래로, 한 줄씩, 프로그램이 실행될때 마다 이루어 집니다. 이와 같은 방법을 *해석* 이라고도 합니다.

몇몇 다른 언어들 경우에는, 해석이 미리 이루어집니다. 이러한 것을 *컴파일* 한다고 합니다. 그래서 프로그램 *실행*이 나중에 수행되고, 컴파일 컴퓨터 명령어는 미리 실행 준비를 합니다.

대체로 자바스크립트가 *해석* 된다고 주장합니다. 왜냐하면 자바스크립트 소스 코드는 실행 될때마다 처리 되기 때문입니다. 하지만, 이는 완전히 정확하지 않습니다. 사실 자바스크립트 엔진은 즉시 프로그램을 *컴파일* 하고 나서 컴파일된 코드를 실행합니다.

**참고:** 자바스크립트 컴파일링에대해 더 자세히 알고 싶으시면, *Scope & Closures* 시리즈의 처음 두 장을 보세요

## 직접 해보기

이 장은 자바스크립트로 되어있는 간단한 코드 스니펫으로 각 프로그래밍 개념에 대해서 소개할 것입니다.

강조해도 지나치지 않습니다: 이 장을 진행하는 동안 여러분은 아마 여러번 반복해서 공부해야 할 것입니다. 코드를 직접 치면서 각 개념들을 연습하세요. 가장 쉬운 방법은 여러분의 브라우저(Firefox, Chrome, IE, etc.)의 개발자 도구에 있는 콘솔을 열어 사용 하는 것입니다.

**팁:** 일반적으로, 키보드 단축키 혹은 메뉴 아이템에서 개발자 도구 콘솔을 열 수 있습니다. 여러분이 가장 선호하는 브라우저에서 콘솔실행과 사용법에 대한 더 자세한 정보를 알고 싶으시면, "개발자 도구 정복하기" (http://blog.teamtreehouse.com/mastering-developer-tools-console)를 참고하세요. 한번에 여러 줄을 콘솔에 입력하려면, `<shift> + <enter>`를 사용하세요. 여러분이 `<enter>`를 입력한다면, 콘솔은 여러분이 입력한 모든 것을 실행할것 입니다.

콘솔에서 코드 실행 과정을 알아봅시다. 우선, 브라우저에서 빈탭 열기를 권장드립니다. 저는 `about:blank`를 주소바에 입력하는 것을 선호합니다. 그러고나서, 위에서 말씀드린것처럼 개발자 콘솔을 열어보세요.

그럼, 이 코드를 입력하고 어떻게 실행되는지 보세요.

```js
a = 21;

b = a * 2;

console.log( b );
```

위에 코드를 크롬 콘솔에 입력하시면 다음과 같이 보일것입니다:

<img src="fig1.png" width="500">

계속해서 실행해보세요. 프로그래밍을 배우는 데 최고의 방법은 코딩을 하는 것입니다!

### 출력

이전 코드 스니펫에서 우리는 `console.log(..)`를 사용했습니다. 간략하게 이 코드가 의미하는 바가 무엇인지 살펴보겠습니다.

눈치 채셨겠지만, 이렇게 하는 것이 바로 개발자 콘솔에서 텍스트(유저에게는 *출력*이라고 하는)를 출력하는 방법입니다.

첫번째로, `log( b )` 부분은 함수 호출("함수"를 참고하세요)을 참조 하게 됩니다. 이 말은 즉, 값을 받아서 콘솔에 출력하도록 변수`b`를 함수에 전달 해주었습니다.

두번째로, `console.` 부분은 `log(..)`함수가 위치해있는 객체를 참조합니다. 우리는 2장에서 객체와 그 속성들을 상세히 다룰 것입니다.

출력물을 만드는 다른 한가지 방법은 `alert(..)` 문을 실행하는 것입니다. 예를들면:

```js
alert( b );
```

실행을 하면 콘솔에 출력이 되지않고, 변수`b` 내용과 함께 “OK” 박스가 뜨게됩니다. 하지만, 일반적으로 코딩을 연습 할 때에는 `alert(..)`을 사용하는 것보다는 더 쉬운 `console.log(..)`를 사용합니다. 왜냐하면 브라우저의 끊김없이 한번에 많은 값들을 출력할 수 있기 때문입니다.

이 책에서, 우리는 출력으로 `console.log(..)`를 사용할 것입니다.

### 입력

출력값에 대해서 이야기하는동안, 여러분은 아마도 *입력값*(유저에게 정보를 받는)에 대해 궁금했을 것입니다.

HTML페이지에서 유저가 입력을 하게 할 수 있는 가장 흔한 방법은 form엘레멘트(text boxes같은)를 보여주고 입력을 받는 것입니다. 그 후 JS를 사용하여 그 입력 값들을 여러분의 프로그램의 변수로 읽을 수 있게 만들어야 합니다.

하지만 간단한 학습과 이 책을 통해 여러분이 배워갈 부분을 증명하고 실습해보기 위한 쉬운 방법도 있습니다. `prompt(..)`함수를 이용 해보세요:

```js
age = prompt( "Please tell me your age:" );

console.log( age );
```

예상하셨듯이, 여러분이 `prompt(..)`에 전달한 메시지가(`"Please tell me your age:"`) 나타날 것입니다.

다음과 같이 보일 것 입니다.

<img src="fig2.png" width="500">

“OK” 클릭으로 입력 텍스트를 제출하면, `console.log(..)`에서 나오는 *출력*을 통해 여러분이 입력한 값이 `age`에 저장되는 것을 확인할 수 있을 것입니다.

<img src="fig3.png" width="500">

기초 프로그래밍에 대한 개념을 배우는 것을 쉽게 하기 위하여 이 책의 예제들은 입력값을 필요로 하지 않습니다. 하지만 여러분에게 실습이 필요하다고 생각된다면 예제의 input을 `prompt(..)`와 함께 사용해보세요.

## Operators

Operators are how we perform actions on variables and values. We've already seen two JavaScript operators, the `=` and the `*`.

The `*` operator performs mathematic multiplication. Simple enough, right?

The `=` equals operator is used for *assignment* -- we first calculate the value on the *right-hand side* (source value) of the `=` and then put it into the variable that we specify on the *left-hand side* (target variable).

**Warning:** This may seem like a strange reverse order to specify assignment. Instead of `a = 42`, some might prefer to flip the order so the source value is on the left and the target variable is on the right, like `42 -> a` (this is not valid JavaScript!). Unfortunately, the `a = 42` ordered form, and similar variations, is quite prevalent in modern programming languages. If it feels unnatural, just spend some time rehearsing that ordering in your mind to get accustomed to it.

Consider:

```js
a = 2;
b = a + 1;
```

Here, we assign the `2` value to the `a` variable. Then, we get the value of the `a` variable (still `2`), add `1` to it resulting in the value `3`, then store that value in the `b` variable.

While not technically an operator, you'll need the keyword `var` in every program, as it's the primary way you *declare* (aka *create*) *var*iables (see "Variables").

You should always declare the variable by name before you use it. But you only need to declare a variable once for each *scope* (see "Scope"); it can be used as many times after that as needed. For example:

```js
var a = 20;

a = a + 1;
a = a * 2;

console.log( a );	// 42
```

Here are some of the most common operators in JavaScript:

* Assignment: `=` as in `a = 2`.
* Math: `+` (addition), `-` (subtraction), `*` (multiplication), and `/` (division), as in `a * 3`.
* Compound Assignment: `+=`, `-=`, `*=`, and `/=` are compound operators that combine a math operation with assignment, as in `a += 2` (same as `a = a + 2`).
* Increment/Decrement: `++` (increment), `--` (decrement), as in `a++` (similar to `a = a + 1`).
* Object Property Access: `.` as in `console.log()`.

   Objects are values that hold other values at specific named locations called properties. `obj.a` means an object value called `obj` with a property of the name `a`. Properties can alternatively be accessed as `obj["a"]`. See Chapter 2.
* Equality: `==` (loose-equals), `===` (strict-equals), `!=` (loose not-equals), `!==` (strict not-equals), as in `a == b`.

   See "Values & Types" and Chapter 2.
* Comparison: `<` (less than), `>` (greater than), `<=` (less than or loose-equals), `>=` (greater than or loose-equals), as in `a <= b`.

   See "Values & Types" and Chapter 2.
* Logical: `&&` (and), `||` (or), as in `a || b` that selects either `a` *or* `b`.

   These operators are used to express compound conditionals (see "Conditionals"), like if either `a` *or* `b` is true.

**Note:** For much more detail, and coverage of operators not mentioned here, see the Mozilla Developer Network (MDN)'s "Expressions and Operators" (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators).

## Values & Types

If you ask an employee at a phone store how much a certain phone costs, and they say "ninety-nine, ninety-nine" (i.e., $99.99), they're giving you an actual numeric dollar figure that represents what you'll need to pay (plus taxes) to buy it. If you want to buy two of those phones, you can easily do the mental math to double that value to get $199.98 for your base cost.

If that same employee picks up another similar phone but says it's "free" (perhaps with air quotes), they're not giving you a number, but instead another kind of representation of your expected cost ($0.00) -- the word "free."

When you later ask if the phone includes a charger, that answer could only have been either "yes" or "no."

In very similar ways, when you express values in a program, you choose different representations for those values based on what you plan to do with them.

These different representations for values are called *types* in programming terminology. JavaScript has built-in types for each of these so called *primitive* values:

* When you need to do math, you want a `number`.
* When you need to print a value on the screen, you need a `string` (one or more characters, words, sentences).
* When you need to make a decision in your program, you need a `boolean` (`true` or `false`).

Values that are included directly in the source code are called *literals*. `string` literals are surrounded by double quotes `"..."` or single quotes (`'...'`) -- the only difference is stylistic preference. `number` and `boolean` literals are just presented as is (i.e., `42`, `true`, etc.).

Consider:

```js
"I am a string";
'I am also a string';

42;

true;
false;
```

Beyond `string`/`number`/`boolean` value types, it's common for programming languages to provide *arrays*, *objects*, *functions*, and more. We'll cover much more about values and types throughout this chapter and the next.

### Converting Between Types

If you have a `number` but need to print it on the screen, you need to convert the value to a `string`, and in JavaScript this conversion is called "coercion." Similarly, if someone enters a series of numeric characters into a form on an ecommerce page, that's a `string`, but if you need to then use that value to do math operations, you need to *coerce* it to a `number`.

JavaScript provides several different facilities for forcibly coercing between *types*. For example:

```js
var a = "42";
var b = Number( a );

console.log( a );	// "42"
console.log( b );	// 42
```

Using `Number(..)` (a built-in function) as shown is an *explicit* coercion from any other type to the `number` type. That should be pretty straightforward.

But a controversial topic is what happens when you try to compare two values that are not already of the same type, which would require *implicit* coercion.

When comparing the string `"99.99"` to the number `99.99`, most people would agree they are equivalent. But they're not exactly the same, are they? It's the same value in two different representations, two different *types*. You could say they're "loosely equal," couldn't you?

To help you out in these common situations, JavaScript will sometimes kick in and *implicitly* coerce values to the matching types.

So if you use the `==` loose equals operator to make the comparison `"99.99" == 99.99`, JavaScript will convert the left-hand side `"99.99"` to its `number` equivalent `99.99`. The comparison then becomes `99.99 == 99.99`, which is of course `true`.

While designed to help you, implicit coercion can create confusion if you haven't taken the time to learn the rules that govern its behavior. Most JS developers never have, so the common feeling is that implicit coercion is confusing and harms programs with unexpected bugs, and should thus be avoided. It's even sometimes called a flaw in the design of the language.

However, implicit coercion is a mechanism that *can be learned*, and moreover *should be learned* by anyone wishing to take JavaScript programming seriously. Not only is it not confusing once you learn the rules, it can actually make your programs better! The effort is well worth it.

**Note:** For more information on coercion, see Chapter 2 of this title and Chapter 4 of the *Types & Grammar* title of this series.

## 코드 주석

휴대폰 대리점 직원은 최근에 배포된 핸드폰의 특징이나 회사에서 제공하는 새로운 계획들을 메모해둘지도 모릅니다. 이 메모들은 고객들이 읽기 위한 것이 아닌, 직원들을 위한 것입니다. 그렇지만, 직원이 고객에게 전달해야 할 말에 대한 방법과 이유를 문서로 남겨서 자기 일을 더 잘할 수 있도록 도와줍니다.

코드를 작성하면서 배울 수 있는 중요한 교훈 중 하나는 내가 지금 작성하는 코드가 컴퓨터에만 국한되지 않는다는 것입니다. 즉 컴파일러를 위한 코드를 작성하는 것만큼 개발자를 위한 코드를 작성하는 것도 중요합니다. 

여러분의 컴퓨터는 *컴파일*에서 온 이진수 0과 1로 이루어진 기계 코드에 대해서만 관심이 있습니다. 그리고 여러분은 0과 1로 이루어진 거의 무한한 수의 프로그램을 작성할 수 있습니다. 이러한 맥락에서 여러분이 프로그램을 어떻게 작성할지에 대한 선택은 여러분뿐만이 아닌 다른 팀 구성원, 미래의 여러분 자신을 위한 문제이기도 합니다.

여러분은 정확하게 동작하는 프로그램을 작성해야 할 뿐만 아니라 테스트를 할 때도 의미 있는 프로그램을 작성해야 합니다. 여러분의 변수와 ("변수"를 참고하세요) 함수 ("함수" 참고하세요)를 위한 좋은 이름을 선택하는 노력은 여러분의 프로그램이 좋은 결과를 낼 수 있도록 만듭니다.

하지만 또 다른 중요한 부분은 코드 주석입니다. 여러분의 프로그램에는 단순히 여러분의 프로그램을 사람에게 설명하기 위해 삽입된 텍스트 비트들이 있습니다. 인터프리터/컴파일러는 이 주석들을 항상 무시할 것입니다.

주석 처리가 잘 된 코드를 작성하는 것에 대한 많은 의견이 있습니다; 우리는 실제로 반드시 지켜야만 하는 공통된 규칙을 정의할 수 없습니다. 하지만 일부 발언과 가이드라인은 꽤 유용합니다:

* 주석 없는 코드는 차선책입니다.
* 너무 많은 주석 (예를 들어 한 줄에 하나씩)은 잘 못 작성된 코드라는 뜻입니다.
* 주석은 *무엇*이 아닌 *왜*에 대해 설명해야 합니다. 물론 혼동의 여지가 있다면 부가적으로 *어떻게*에 대해 설명할 수 있습니다.

자바스크립트에서는, 주석을 작성하는 방법이 두 가지 있습니다: 한 줄 주석과 여러 줄 주석

생각해보세요:

```js
// 이것은 한 줄 주석입니다.

/* 그리고 이것은
       여러 줄
             주석입니다.
                      */
```

`//`한 줄 주석은 단일 문장 바로 위에 주석을 달거나 줄의 끝 부분에 주석을 넣을 때 적절합니다. `//`이후에 그 줄에 있는 모든 것은 주석으로 처리됩니다(따라서 컴파일러에 의해 무시됩니다). 한 줄 주석 안에 표현할 수 있는 것에 대한 제한은 없습니다.

생각해보세요:

```js
var a = 42;		// 42는 삶의 의미입니다.
```

`/* .. */` 여러 줄 주석은 여러분의 생각을 여러 줄로 설명할 때 적절합니다.

다음은 여러 줄 주석의 일반적인 사용법입니다:

```js
/* 다음의 값은 우주의 모든 질문에 대해
   답을 한다고 여겨지기 때문에 
   사용됩니다. */
var a = 42;
```

`*/`이 주석의 끝이기 때문에 한 줄의 어디에서든, 심지어 줄의 중간에서도 나타날 수 있습니다. 예를 들어:

```js
var a = /* 임의의 값 */ 42;

console.log( a );	// 42
```

여러 줄 주석 안에서 */은 주석의 끝으로 해석되기 때문에, 주석의 중간에 사용할 수 없는 유일한 값입니다.

여러분은 주석 코드를 작성하는 습관을 시작으로 프로그래밍을 배우고 싶을 것입니다. 이 장의 나머지 부분에서는 제가 뭔가를 설명하기 위해 주석을 사용하는 것을 보실 수 있을 것입니다. 그리고 연습할 때 똑같이 적용하세요. 저를 믿으세요, 여러분이 작성한 코드를 읽는 모든 사람들은 여러분에게 감사할 것입니다!

## 변수

대부분의 유용한 프로그램들은 프로그램의 진행 과정에서 값이 변경될 때마다 추적해야 하며, 여러분의 프로그램이 요구하는 다양한 작업을 수행해야 합니다.

여러분의 프로그램에서 그 일을 가장 쉽게 하는 방법은 *변수*라고 불리는 상징적인 컨테이너에 값을 할당하는 것입니다. -- 이 컨테이너에 있는 값은 필요하다면 시간이 지남에 따라 *변경*할 수 있기 때문에 그렇게 불립니다.

일부 프로그래밍 언어에서, 여러분은 `숫자` 또는 `문자열`과 같은 구체적인 값의 타입을 유지하기 위해 변수 (컨테이너)를 선언합니다. *타입 강제*라고 불리기도 하는 *정적 타이핑*은 일반적으로 의도하지 않은 값의 변환을 방지하여 프로그램 정확성에 대한 이점으로 인용됩니다.

다른 언어들은 변수 대신에 값에 대한 타입을 강조합니다. *동적 타이핑*이라고 불리기도 하는 *약한 타이핑*은, 변수가 언제든지 모든 타입의 값을 유지할 수 있게 합니다. 일반적으로 프로그램의 논리 흐름에서 특정 순간에 값이 가질 수 있는 타입 형식이 무엇이든지 상관없이 하나의 변수가 하나의 값을 나타낼 수 있게 함으로써 프로그램의 유연성에 대한 이점으로 인용됩니다.

자바스크립트는 변수들이 어떠한 *타입* 강제 없이 어떤 *타입*의 값이던 가질 수 있는 후자의 접근법(*동적 타이핑*)을 사용합니다.

앞서 언급했듯이, 우리는 `var` 선언문을 사용해 변수를 선언합니다 -- 이 선언문에서는 *타입*에 대한 다른 정보가 없다는 것에 주목하세요. 이 간단한 프로그램을 생각해보세요:

```js
var amount = 99.99;

amount = amount * 2;

console.log( amount );		// 199.98

// `amount`를 문자열로 변환하고
// 시작 부분에 "$"를 추가하세요.
amount = "$" + String( amount );

console.log( amount );		// "$199.98"
```

`amount` 변수는 숫자 `99.99`를 갖고 시작해, `amount * 2`의 `숫자` 결과인 `199.98`을 저장합니다.

첫 번째 `console.log(..)` 명령어는 *암시적으로* `숫자`값을 `문자열`로 출력하도록 강제합니다.

그리고 `amount = "$" + String(amount)`선언문은 *명시적으로* `199.98`값을 `문자열`로 강제하고 시작 부분에 `"$"`문자를 추가합니다. 이때, `amount`에는 문자열 값 `"$199.98"`이 저장되어 있고, 따라서 두 번째 `console.log(..)` 선언문은 출력하기 위해 어떠한 강제 변환을 할 필요가 없습니다.

자바스크립트 개발자들은 `99.99`, `199.98`, 그리고 `"$199.98"` 각각에 대한 `amount`변수 사용에 대한 유연성에 주목할 것입니다. 정적 타이핑 애호가들은 `amountStr`와 같은 별도의 변수를 사용해 최종적인 값을 나타내는 `"$199.98"`를 저장하는 것을 선호합니다. 왜냐하면 다른 타입이기 때문입니다.

어느 쪽이든, 여러분은 변수의 주된 목적을 설명하면서 프로그램의 진행 과정에서 변하는 실행 값을 저장하는 `amount`에 주목할 것입니다: 프로그램의 *상태*를 관리하는 것

즉, *상태*는 여러분의 프로그램이 실행될 때 값의 변화를 추적합니다.

또 다른 변수의 일반적인 사용법은 값 설정을 집중시키는 것입니다. 변수를 선언하고 그 값을 프로그램 전체에서 *변경하지 않으려고* 할 때 일반적으로 *상수*라고 합니다.

종종 프로그램의 맨 위에 이러한 *상수*들을 선언해, 필요한 경우 한 곳에서 값을 변경하는 것이 편리합니다. 일반적으로 상수로 사용되는 자바스크립트 변수는 대문자로 표시되며, 여러 단어 사이에서는 밑줄 `_`과 함께 사용됩니다.

다음은 좋지 않은 예시입니다:

```js
var TAX_RATE = 0.08;	// 8% 판매 세율

var amount = 99.99;

amount = amount * 2;

amount = amount + (amount * TAX_RATE);

console.log( amount );				// 215.9784
console.log( amount.toFixed( 2 ) );	// "215.98"
```

**참고:** `console.log(..)`가 `console`값에 객체 속성으로 접근한 함수 `log(..)`인 것과 비슷하게 `숫자`값에 접근할 수 있는 `toFixed(..)` 함수가 있습니다. 자바스크립트 `숫자`는 자동으로 달러 형식을 지원하지 않습니다 -- 엔진은 여러분의 의도가 무엇이고 알지 못하고 통화에 대한 타입이 없습니다. `toFixed(..)`는 반올림하고 싶은 `숫자`의 위치에 소수점 이하 자릿수를 지정할 수 있게 하고 필요에 따라 `문자열`을 생성합니다.

`TAX_RATE`변수는 일반적으로 *상수*에 해당합니다 -- 이 프로그램에서 `TAX_RATE` 변수가 변경되지 못한다는 것 외에 특별한 것이 없습니다. 하지만 도시가 판매 세율을 9%로 인상하면, 우리는 프로그램 전체에 `0.08` 값이 여러 번 나오는 것을 발견하고 그 모두를 업데이트하는 대신 한 곳에서 `TAX_RATE`값을 `0.09`로 설정해 여전히 쉽게 프로그램을 업데이트할 수 있습니다.

이 글을 쓸 당시의 최신 버전의 자바스크립트 (일반적으로 "ES6"라고 불리는)에는 `var` 대신 `const`를 사용하여 *상수*를 선언하는 새로운 방법이 포함되어 있습니다:

```js
// ES6:
const TAX_RATE = 0.08;

var amount = 99.99;

// ..
```

상수는 초기 설정 후에 실수로 다른 곳에서 값이 변경되는 것을 방지하는 것을 제외하고, 변경되지 않은 값을 가진 변수와 마찬가지로 유용합니다. 초기 선언 후에 다른 값을 `TAX_RATE`에 할당하려고 하면 여러분의 프로그램은 변경을 거부할 것입니다(그리고 엄격 모드에서는 오류와 함께 실패합니다 -- 2장의 "엄격 모드"를 참고하세요).

그런데, 실수를 방지하기 위한 보호는 정적 유형 타입 강제와 유사하므로, 여러분은 왜 정적 타입이 다른 언어에서 매력적일 수 있는지 알 수 있습니다!

**참고:** 변수에서 여러분의 프로그램에서 사용될 수 있는 다양한 값에 대한 자세한 내용은, 시리즈의 *Types & Grammar* 제목을 참고하세요.

## 블록

여러분이 새 휴대폰을 사려고 할 때, 휴대폰 대리점 직원은 일련의 단계를 거쳐 판매를 완료합니다.

마찬가지로, 코드에서 일련의 문을 그룹화해야 하는 경우가 종종 있는데, 이것을 *블록*이라고 부릅니다. 자바스크립트에서 블록은 중괄호 쌍 `{ .. }` 안에 하나 이상의 문을 감싸서 정의됩니다. 생각해보세요:

```js
var amount = 99.99;

// 일반 블록
{
	amount = amount * 2;
	console.log( amount );	// 199.98
}
```

이런 종류의 독립적인 `{ .. }` 일반 블록은 유효하지만, JS 프로그램에서 일반적으로 볼 수 있지 않습니다. 일반적으로 블록은 `if`문("조건"을 참고하세요)이나 반복문("반복"을 참고하세요)과 같은 제어문과 함께 쓰입니다. 예를 들어:

```js
var amount = 99.99;

// amount가 충분히 클까요?
if (amount > 10) {			// <-- `if`와 함께 쓰이는 블록
	amount = amount * 2;
	console.log( amount );	// 199.98
}
```

아래의 `if`문에서 볼 수 있듯이, 두 개의 문이 포함된 `{ .. }` 블록은 `if (amount > 10)`뒤에 따라옵니다. 블록 안의 문은 조건을 통과하는 경우에만 실행됩니다.

**참고:** `console.log(amout);`와 같은 대부분의 다른 문과는 다르게, 블록은 세미콜론(`;`)이 필요하지 않습니다.

## 조건

"액정 보호 필름을 $9.99에 추가로 구매하시겠습니까?"라며 휴대폰 대리점 직원이 구매 의사를 물어봅니다. 이때 여러분은 대답하기 위해 우선 지갑이나 은행 계좌의 현재 *상태*를 확인해야 할 수도 있습니다. 하지만 분명한 것은, 이것은 단순히 "예" 혹은 "아니오"라고 대답하면 되는 질문입니다.

프로그램에서 *조건*(일명 결정)을 표현하는 데는 몇 가지 방법이 있습니다.

가장 일반적인 방법은 `if`문입니다. 핵심만 말하면, "*만약* 이 조건이 참이라면, 다음을 따르십시오...". 예를 들면:

```js
var bank_balance = 302.13;
var amount = 99.99;

if (amount < bank_balance) {
	console.log( "I want to buy this phone!" );
}
```

`if`문은 `( )` 괄호 사이에 `true` 혹은 `false`로 평가될 수 있는 표현식이 필요합니다. 이 프로그램에는 `bank_balance` 변수의 값에 따라서 `true` 혹은 `false`로 평가되는 `amount < bank_balance` 표현식이 있습니다.

조건이 참이 아닐 때는 `else`절이라 불리는 대안을 마련할 수도 있습니다. 생각해보세요:

```js
const ACCESSORY_PRICE = 9.99;

var bank_balance = 302.13;
var amount = 99.99;

amount = amount * 2;

// 추가 구매를 감당할 수 있을까요?
if ( amount < bank_balance ) {
	console.log( "I'll take the accessory!" );
	amount = amount + ACCESSORY_PRICE;
}
// 그렇지 않다면:
else {
	console.log( "No, thanks." );
}
```

보세요, 만약 `amount < bank_balance`가 `true`라면 `"I'll take the accessory!"`가 출력되고 `amount`변수에 `9.99`가 더해질 것입니다. 그렇지 않다면, `else` 절에서 정중하게 `"No, thanks."`를 출력하고 `amount`는 변경되지 않을 것입니다.

앞서 "값 & 타입"에서 논의한 바와 같이, 이미 기대한 타입이 아닌 값은 종종 해당 타입으로 강제 변환 됩니다. `if`문은 `boolean`값을 기대하지만, `boolean`이 아닌 다른 것을 전달하면 강제 변환 됩니다.

자바스크립트는 "거짓"으로 추정되는 특정 값(`boolean`으로 강제 변환 될 때 `false`가 되는 값 --`0`이나 `""` 등)들의 목록을 정의합니다. 이 목록에 없는 다른 모든 값은 자동으로 "참"(`boolean`으로 강제 형변환 하면 `true`가 되는 값)으로 추정됩니다. "참"으로 추정되는 값에는 `99.99`나 `"free"`와 같은 값이 포함됩니다. 2장의 "참 추정 & 거짓 추정"항목에서 더 자세한 내용을 참고해주세요.

*조건*은 `if` 이외의 다른 형태도 있습니다. 예를 들어, `switch`문은 일련의 `if..else`문에 대한 축약어로 사용될 수 있습니다.(2장을 참고하세요) 반복문("반복"을 참고하세요)은 *조건*을 사용하여 반복을 계속 진행할지 또는 중지할지를 결정합니다.

**참고:** *조건*의 조건식에서 암시적으로 발생할 수 있는 강제 변환에 대한 더 자세한 내용은 이 시리즈 중 *Types & Grammar*의 4장을 참고하세요.

## 반복

한창 바쁠 때는, 휴대폰 대리점 직원과 통화를 해야 하는 통화 대기 고객 명단이 생깁니다. 목록에 손님들이 있는 동안에는, 직원은 다음 손님을 계속 응대 해야만 합니다.

특정 조건이 실패할 때까지 일련의 동작을 반복 -- 즉, 조건이 유지되는 동안만 반복 -- 하는 것이 프로그래밍 반복 작업입니다.; 다른 형태를 취할 수 있지만, 모두 이 기본 동작을 만족합니다.

반복문은 조건식과 (일반적으로 `{ .. }`와 같은) 블록을 포함합니다. 반복문 블록이 실행될 때마다, 이를 *이터레이션*이라고 합니다.

예를 들어, `while`문과 `do..while`문 형식은 조건이 더는 `true`가 아닌 것으로 평가될 때까지 블록 안의 문을 반복하는 개념을 보여줍니다.:

```js
while (numOfCustomers > 0) {
	console.log( "How may I help you?" );

	// 손님을 도와줍니다...

	numOfCustomers = numOfCustomers - 1;
}

// 한편:

do {
	console.log( "How may I help you?" );

	// 손님을 도와줍니다...

	numOfCustomers = numOfCustomers - 1;
} while (numOfCustomers > 0);
```

이 두 가지 반복문의 단 한 가지 유일한 차이점은 조건문이 첫 번째 반복 이전에 검사되는지 (`while`) 아니면 첫 번째 반복 이후에 검사되는지 (`do..while`)입니다.

어느 형식이든, 조건식 검사가 `false`인 경우, 다음 반복은 실행되지 않습니다. 즉, 조건식이 처음부터 `false`이면, `while`문은 전혀 실행되지 않지만, `do..while`문은 첫 번째 반복은 실행될 것입니다.

때때로 여러분은 특정 범위의 수(`0`부터 `9`까지의 10개의 수 처럼)를 세기 위해 반복을 합니다. 반복문에서 `i`와 같은 반복 변수를 `0`으로 설정하고 반복 주기마다 `1`씩 증가하도록 하면 가능합니다.

**주의:** 다양한 역사적 이유로, 프로그래밍 언어는 대부분 `1` 대신 `0`부터 수를 세는 관습이 있습니다. 여러분이 이렇게 생각하는 방식에 익숙하지 않다면, 처음에는 조금 혼란스러울 것입니다. 좀 더 익숙해질 수 있도록 잠시 시간을 갖고 `0`부터 수를 세는 연습을 해보세요!

조건은 반복문 안에 암묵적인 `if`문이 있는 것처럼, 매 반복에서 검사됩니다.

자바스크립트의 `break`문을 사용해 반복을 멈출 수 있습니다. 또한, 멈추는(`break`ing) 방법이 없이 영원히 돌아가는 반복문을 만드는 것이 꽤나 쉽다는 것도 알 수 있습니다.

한번 확인해볼까요:

```js
var i = 0;

// `while..true`반복문이 영원히 실행되겠죠?
while (true) {
	// 반복을 멈춰볼까요?
	if ((i <= 9) === false) {
		break;
	}

	console.log( i );
	i = i + 1;
}
// 0 1 2 3 4 5 6 7 8 9
```

**주의:** 위의 예시가 여러분의 반복문에 반드시 사용하게 될 실질적인 형태는 아닙니다. 단지 설명하기 위한 목적으로 보여드렸습니다.

`while`(혹은 `do..while`)이 수동으로 작업을 수행할 수 있는 반면에, 같은 목적을 위한 `for`문이라는 또 다른 구문 형식이 있습니다.:

```js
for (var i = 0; i <= 9; i = i + 1) {
	console.log( i );
}
// 0 1 2 3 4 5 6 7 8 9
```

보시다시피, 두 가지 경우 모두 첫 10번의 반복(`i`가 `0`부터 `9`까지)에 대해서는 조건식 `i <= 9`가 `true`가 됩니다. 하지만 `i`가 `10`일 때 조건식은 `false`가 됩니다.

`for`문 에는 세 개의 절이 있습니다.: 초기식(`var i=0`), 조건식(`i <= 9`), 증감식(`i = i + 1`). 따라서 반복문의 반복 횟수를 세보려면 `for`은 더 간단하며 이해하고 작성하기에 쉬운 형식입니다.

예를 들어, 객체(2장을 참고하세요)의 속성과 같은 특정 값들을 반복하기 위한 또 다른 특별한 반복문 형식이 있습니다. 여기서 암시적 조건 검사는 모든 속성에 대해 반복했는지의 여부만 판단합니다. "조건이 실패할 때까지 반복한다"는 개념은 반복문의 형식에 상관없이 변하지 않습니다.

## Functions

The phone store employee probably doesn't carry around a calculator to figure out the taxes and final purchase amount. That's a task she needs to define once and reuse over and over again. Odds are, the company has a checkout register (computer, tablet, etc.) with those "functions" built in.

Similarly, your program will almost certainly want to break up the code's tasks into reusable pieces, instead of repeatedly repeating yourself repetitiously (pun intended!). The way to do this is to define a `function`.

A function is generally a named section of code that can be "called" by name, and the code inside it will be run each time. Consider:

```js
function printAmount() {
	console.log( amount.toFixed( 2 ) );
}

var amount = 99.99;

printAmount(); // "99.99"

amount = amount * 2;

printAmount(); // "199.98"
```

Functions can optionally take arguments (aka parameters) -- values you pass in. And they can also optionally return a value back.

```js
function printAmount(amt) {
	console.log( amt.toFixed( 2 ) );
}

function formatAmount() {
	return "$" + amount.toFixed( 2 );
}

var amount = 99.99;

printAmount( amount * 2 );		// "199.98"

amount = formatAmount();
console.log( amount );			// "$99.99"
```

The function `printAmount(..)` takes a parameter that we call `amt`. The function `formatAmount()` returns a value. Of course, you can also combine those two techniques in the same function.

Functions are often used for code that you plan to call multiple times, but they can also be useful just to organize related bits of code into named collections, even if you only plan to call them once.

Consider:

```js
const TAX_RATE = 0.08;

function calculateFinalPurchaseAmount(amt) {
	// calculate the new amount with the tax
	amt = amt + (amt * TAX_RATE);

	// return the new amount
	return amt;
}

var amount = 99.99;

amount = calculateFinalPurchaseAmount( amount );

console.log( amount.toFixed( 2 ) );		// "107.99"
```

Although `calculateFinalPurchaseAmount(..)` is only called once, organizing its behavior into a separate named function makes the code that uses its logic (the `amount = calculateFinal...` statement) cleaner. If the function had more statements in it, the benefits would be even more pronounced.

### Scope

If you ask the phone store employee for a phone model that her store doesn't carry, she will not be able to sell you the phone you want. She only has access to the phones in her store's inventory. You'll have to try another store to see if you can find the phone you're looking for.

Programming has a term for this concept: *scope* (technically called *lexical scope*). In JavaScript, each function gets its own scope. Scope is basically a collection of variables as well as the rules for how those variables are accessed by name. Only code inside that function can access that function's *scoped* variables.

A variable name has to be unique within the same scope -- there can't be two different `a` variables sitting right next to each other. But the same variable name `a` could appear in different scopes.

```js
function one() {
	// this `a` only belongs to the `one()` function
	var a = 1;
	console.log( a );
}

function two() {
	// this `a` only belongs to the `two()` function
	var a = 2;
	console.log( a );
}

one();		// 1
two();		// 2
```

Also, a scope can be nested inside another scope, just like if a clown at a birthday party blows up one balloon inside another balloon. If one scope is nested inside another, code inside the innermost scope can access variables from either scope.

Consider:

```js
function outer() {
	var a = 1;

	function inner() {
		var b = 2;

		// we can access both `a` and `b` here
		console.log( a + b );	// 3
	}

	inner();

	// we can only access `a` here
	console.log( a );			// 1
}

outer();
```

Lexical scope rules say that code in one scope can access variables of either that scope or any scope outside of it.

So, code inside the `inner()` function has access to both variables `a` and `b`, but code in `outer()` has access only to `a` -- it cannot access `b` because that variable is only inside `inner()`.

Recall this code snippet from earlier:

```js
const TAX_RATE = 0.08;

function calculateFinalPurchaseAmount(amt) {
	// calculate the new amount with the tax
	amt = amt + (amt * TAX_RATE);

	// return the new amount
	return amt;
}
```

The `TAX_RATE` constant (variable) is accessible from inside the `calculateFinalPurchaseAmount(..)` function, even though we didn't pass it in, because of lexical scope.

**Note:** For more information about lexical scope, see the first three chapters of the *Scope & Closures* title of this series.

## Practice

There is absolutely no substitute for practice in learning programming. No amount of articulate writing on my part is alone going to make you a programmer.

With that in mind, let's try practicing some of the concepts we learned here in this chapter. I'll give the "requirements," and you try it first. Then consult the code listing below to see how I approached it.

* Write a program to calculate the total price of your phone purchase. You will keep purchasing phones (hint: loop!) until you run out of money in your bank account. You'll also buy accessories for each phone as long as your purchase amount is below your mental spending threshold.
* After you've calculated your purchase amount, add in the tax, then print out the calculated purchase amount, properly formatted.
* Finally, check the amount against your bank account balance to see if you can afford it or not.
* You should set up some constants for the "tax rate," "phone price," "accessory price," and "spending threshold," as well as a variable for your "bank account balance.""
* You should define functions for calculating the tax and for formatting the price with a "$" and rounding to two decimal places.
* **Bonus Challenge:** Try to incorporate input into this program, perhaps with the `prompt(..)` covered in "Input" earlier. You may prompt the user for their bank account balance, for example. Have fun and be creative!

OK, go ahead. Try it. Don't peek at my code listing until you've given it a shot yourself!

**Note:** Because this is a JavaScript book, I'm obviously going to solve the practice exercise in JavaScript. But you can do it in another language for now if you feel more comfortable.

Here's my JavaScript solution for this exercise:

```js
const SPENDING_THRESHOLD = 200;
const TAX_RATE = 0.08;
const PHONE_PRICE = 99.99;
const ACCESSORY_PRICE = 9.99;

var bank_balance = 303.91;
var amount = 0;

function calculateTax(amount) {
	return amount * TAX_RATE;
}

function formatAmount(amount) {
	return "$" + amount.toFixed( 2 );
}

// keep buying phones while you still have money
while (amount < bank_balance) {
	// buy a new phone!
	amount = amount + PHONE_PRICE;

	// can we afford the accessory?
	if (amount < SPENDING_THRESHOLD) {
		amount = amount + ACCESSORY_PRICE;
	}
}

// don't forget to pay the government, too
amount = amount + calculateTax( amount );

console.log(
	"Your purchase: " + formatAmount( amount )
);
// Your purchase: $334.76

// can you actually afford this purchase?
if (amount > bank_balance) {
	console.log(
		"You can't afford this purchase. :("
	);
}
// You can't afford this purchase. :(
```

**Note:** The simplest way to run this JavaScript program is to type it into the developer console of your nearest browser.

How did you do? It wouldn't hurt to try it again now that you've seen my code. And play around with changing some of the constants to see how the program runs with different values.

## Review

Learning programming doesn't have to be a complex and overwhelming process. There are just a few basic concepts you need to wrap your head around.

These act like building blocks. To build a tall tower, you start first by putting block on top of block on top of block. The same goes with programming. Here are some of the essential programming building blocks:

* You need *operators* to perform actions on values.
* You need values and *types* to perform different kinds of actions like math on `number`s or output with `string`s.
* You need *variables* to store data (aka *state*) during your program's execution.
* You need *conditionals* like `if` statements to make decisions.
* You need *loops* to repeat tasks until a condition stops being true.
* You need *functions* to organize your code into logical and reusable chunks.

Code comments are one effective way to write more readable code, which makes your program easier to understand, maintain, and fix later if there are problems.

Finally, don't neglect the power of practice. The best way to learn how to write code is to write code.

I'm excited you're well on your way to learning how to code, now! Keep it up. Don't forget to check out other beginner programming resources (books, blogs, online training, etc.). This chapter and this book are a great start, but they're just a brief introduction.

The next chapter will review many of the concepts from this chapter, but from a more JavaScript-specific perspective, which will highlight most of the major topics that are addressed in deeper detail throughout the rest of the series.
