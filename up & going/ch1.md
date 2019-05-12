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

## Code Comments

The phone store employee might jot down some notes on the features of a newly released phone or on the new plans her company offers. These notes are only for the employee -- they're not for customers to read. Nevertheless, these notes help the employee do her job better by documenting the hows and whys of what she should tell customers.

One of the most important lessons you can learn about writing code is that it's not just for the computer. Code is every bit as much, if not more, for the developer as it is for the compiler.

Your computer only cares about machine code, a series of binary 0s and 1s, that comes from *compilation*. There's a nearly infinite number of programs you could write that yield the same series of 0s and 1s. The choices you make about how to write your program matter -- not only to you, but to your other team members and even to your future self.

You should strive not just to write programs that work correctly, but programs that make sense when examined. You can go a long way in that effort by choosing good names for your variables (see "Variables") and functions (see "Functions").

But another important part is code comments. These are bits of text in your program that are inserted purely to explain things to a human. The interpreter/compiler will always ignore these comments.

There are lots of opinions on what makes well-commented code; we can't really define absolute universal rules. But some observations and guidelines are quite useful:

* Code without comments is suboptimal.
* Too many comments (one per line, for example) is probably a sign of poorly written code.
* Comments should explain *why*, not *what*. They can optionally explain *how* if that's particularly confusing.

In JavaScript, there are two types of comments possible: a single-line comment and a multiline comment.

Consider:

```js
// This is a single-line comment

/* But this is
       a multiline
             comment.
                      */
```

The `//` single-line comment is appropriate if you're going to put a comment right above a single statement, or even at the end of a line. Everything on the line after the `//` is treated as the comment (and thus ignored by the compiler), all the way to the end of the line. There's no restriction to what can appear inside a single-line comment.

Consider:

```js
var a = 42;		// 42 is the meaning of life
```

The `/* .. */` multiline comment is appropriate if you have several lines worth of explanation to make in your comment.

Here's a common usage of multiline comments:

```js
/* The following value is used because
   it has been shown that it answers
   every question in the universe. */
var a = 42;
```

It can also appear anywhere on a line, even in the middle of a line, because the `*/` ends it. For example:

```js
var a = /* arbitrary value */ 42;

console.log( a );	// 42
```

The only thing that cannot appear inside a multiline comment is a `*/`, because that would be interpreted to end the comment.

You will definitely want to begin your learning of programming by starting off with the habit of commenting code. Throughout the rest of this chapter, you'll see I use comments to explain things, so do the same in your own practice. Trust me, everyone who reads your code will thank you!

## Variables

Most useful programs need to track a value as it changes over the course of the program, undergoing different operations as called for by your program's intended tasks.

The easiest way to go about that in your program is to assign a value to a symbolic container, called a *variable* -- so called because the value in this container can *vary* over time as needed.

In some programming languages, you declare a variable (container) to hold a specific type of value, such as `number` or `string`. *Static typing*, otherwise known as *type enforcement*, is typically cited as a benefit for program correctness by preventing unintended value conversions.

Other languages emphasize types for values instead of variables. *Weak typing*, otherwise known as *dynamic typing*, allows a variable to hold any type of value at any time. It's typically cited as a benefit for program flexibility by allowing a single variable to represent a value no matter what type form that value may take at any given moment in the program's logic flow.

JavaScript uses the latter approach, *dynamic typing*, meaning variables can hold values of any *type* without any *type* enforcement.

As mentioned earlier, we declare a variable using the `var` statement -- notice there's no other *type* information in the declaration. Consider this simple program:

```js
var amount = 99.99;

amount = amount * 2;

console.log( amount );		// 199.98

// convert `amount` to a string, and
// add "$" on the beginning
amount = "$" + String( amount );

console.log( amount );		// "$199.98"
```

The `amount` variable starts out holding the number `99.99`, and then holds the `number` result of `amount * 2`, which is `199.98`.

The first `console.log(..)` command has to *implicitly* coerce that `number` value to a `string` to print it out.

Then the statement `amount = "$" + String(amount)` *explicitly* coerces the `199.98` value to a `string` and adds a `"$"` character to the beginning. At this point, `amount` now holds the `string` value `"$199.98"`, so the second `console.log(..)` statement doesn't need to do any coercion to print it out.

JavaScript developers will note the flexibility of using the `amount` variable for each of the `99.99`, `199.98`, and the `"$199.98"` values. Static-typing enthusiasts would prefer a separate variable like `amountStr` to hold the final `"$199.98"` representation of the value, because it's a different type.

Either way, you'll note that `amount` holds a running value that changes over the course of the program, illustrating the primary purpose of variables: managing program *state*.

In other words, *state* is tracking the changes to values as your program runs.

Another common usage of variables is for centralizing value setting. This is more typically called *constants*, when you declare a variable with a value and intend for that value to *not change* throughout the program.

You declare these *constants*, often at the top of a program, so that it's convenient for you to have one place to go to alter a value if you need to. By convention, JavaScript variables as constants are usually capitalized, with underscores `_` between multiple words.

Here's a silly example:

```js
var TAX_RATE = 0.08;	// 8% sales tax

var amount = 99.99;

amount = amount * 2;

amount = amount + (amount * TAX_RATE);

console.log( amount );				// 215.9784
console.log( amount.toFixed( 2 ) );	// "215.98"
```

**Note:** Similar to how `console.log(..)` is a function `log(..)` accessed as an object property on the `console` value, `toFixed(..)` here is a function that can be accessed on `number` values. JavaScript `number`s aren't automatically formatted for dollars -- the engine doesn't know what your intent is and there's no type for currency. `toFixed(..)` lets us specify how many decimal places we'd like the `number` rounded to, and it produces the `string` as necessary.

The `TAX_RATE` variable is only *constant* by convention -- there's nothing special in this program that prevents it from being changed. But if the city raises the sales tax rate to 9%, we can still easily update our program by setting the `TAX_RATE` assigned value to `0.09` in one place, instead of finding many occurrences of the value `0.08` strewn throughout the program and updating all of them.

The newest version of JavaScript at the time of this writing (commonly called "ES6") includes a new way to declare *constants*, by using `const` instead of `var`:

```js
// as of ES6:
const TAX_RATE = 0.08;

var amount = 99.99;

// ..
```

Constants are useful just like variables with unchanged values, except that constants also prevent accidentally changing value somewhere else after the initial setting. If you tried to assign any different value to `TAX_RATE` after that first declaration, your program would reject the change (and in strict mode, fail with an error -- see "Strict Mode" in Chapter 2).

By the way, that kind of "protection" against mistakes is similar to the static-typing type enforcement, so you can see why static types in other languages can be attractive!

**Note:** For more information about how different values in variables can be used in your programs, see the *Types & Grammar* title of this series.

## Blocks

The phone store employee must go through a series of steps to complete the checkout as you buy your new phone.

Similarly, in code we often need to group a series of statements together, which we often call a *block*. In JavaScript, a block is defined by wrapping one or more statements inside a curly-brace pair `{ .. }`. Consider:

```js
var amount = 99.99;

// a general block
{
	amount = amount * 2;
	console.log( amount );	// 199.98
}
```

This kind of standalone `{ .. }` general block is valid, but isn't as commonly seen in JS programs. Typically, blocks are attached to some other control statement, such as an `if` statement (see "Conditionals") or a loop (see "Loops"). For example:

```js
var amount = 99.99;

// is amount big enough?
if (amount > 10) {			// <-- block attached to `if`
	amount = amount * 2;
	console.log( amount );	// 199.98
}
```

We'll explain `if` statements in the next section, but as you can see, the `{ .. }` block with its two statements is attached to `if (amount > 10)`; the statements inside the block will only be processed if the conditional passes.

**Note:** Unlike most other statements like `console.log(amount);`, a block statement does not need a semicolon (`;`) to conclude it.

## Conditionals

"Do you want to add on the extra screen protectors to your purchase, for $9.99?" The helpful phone store employee has asked you to make a decision. And you may need to first consult the current *state* of your wallet or bank account to answer that question. But obviously, this is just a simple "yes or no" question.

There are quite a few ways we can express *conditionals* (aka decisions) in our programs.

The most common one is the `if` statement. Essentially, you're saying, "*If* this condition is true, do the following...". For example:

```js
var bank_balance = 302.13;
var amount = 99.99;

if (amount < bank_balance) {
	console.log( "I want to buy this phone!" );
}
```

The `if` statement requires an expression in between the parentheses `( )` that can be treated as either `true` or `false`. In this program, we provided the expression `amount < bank_balance`, which indeed will either evaluate to `true` or `false` depending on the amount in the `bank_balance` variable.

You can even provide an alternative if the condition isn't true, called an `else` clause. Consider:

```js
const ACCESSORY_PRICE = 9.99;

var bank_balance = 302.13;
var amount = 99.99;

amount = amount * 2;

// can we afford the extra purchase?
if ( amount < bank_balance ) {
	console.log( "I'll take the accessory!" );
	amount = amount + ACCESSORY_PRICE;
}
// otherwise:
else {
	console.log( "No, thanks." );
}
```

Here, if `amount < bank_balance` is `true`, we'll print out `"I'll take the accessory!"` and add the `9.99` to our `amount` variable. Otherwise, the `else` clause says we'll just politely respond with `"No, thanks."` and leave `amount` unchanged.

As we discussed in "Values & Types" earlier, values that aren't already of an expected type are often coerced to that type. The `if` statement expects a `boolean`, but if you pass it something that's not already `boolean`, coercion will occur.

JavaScript defines a list of specific values that are considered "falsy" because when coerced to a `boolean`, they become `false` -- these include values like `0` and `""`. Any other value not on the "falsy" list is automatically "truthy" -- when coerced to a `boolean` they become `true`. Truthy values include things like `99.99` and `"free"`. See "Truthy & Falsy" in Chapter 2 for more information.

*Conditionals* exist in other forms besides the `if`. For example, the `switch` statement can be used as a shorthand for a series of `if..else` statements (see Chapter 2). Loops (see "Loops") use a *conditional* to determine if the loop should keep going or stop.

**Note:** For deeper information about the coercions that can occur implicitly in the test expressions of *conditionals*, see Chapter 4 of the *Types & Grammar* title of this series.

## Loops

During busy times, there's a waiting list for customers who need to speak to the phone store employee. While there's still people on that list, she just needs to keep serving the next customer.

Repeating a set of actions until a certain condition fails -- in other words, repeating only while the condition holds -- is the job of programming loops; loops can take different forms, but they all satisfy this basic behavior.

A loop includes the test condition as well as a block (typically as `{ .. }`). Each time the loop block executes, that's called an *iteration*.

For example, the `while` loop and the `do..while` loop forms illustrate the concept of repeating a block of statements until a condition no longer evaluates to `true`:

```js
while (numOfCustomers > 0) {
	console.log( "How may I help you?" );

	// help the customer...

	numOfCustomers = numOfCustomers - 1;
}

// versus:

do {
	console.log( "How may I help you?" );

	// help the customer...

	numOfCustomers = numOfCustomers - 1;
} while (numOfCustomers > 0);
```

The only practical difference between these loops is whether the conditional is tested before the first iteration (`while`) or after the first iteration (`do..while`).

In either form, if the conditional tests as `false`, the next iteration will not run. That means if the condition is initially `false`, a `while` loop will never run, but a `do..while` loop will run just the first time.

Sometimes you are looping for the intended purpose of counting a certain set of numbers, like from `0` to `9` (ten numbers). You can do that by setting a loop iteration variable like `i` at value `0` and incrementing it by `1` each iteration.

**Warning:** For a variety of historical reasons, programming languages almost always count things in a zero-based fashion, meaning starting with `0` instead of `1`. If you're not familiar with that mode of thinking, it can be quite confusing at first. Take some time to practice counting starting with `0` to become more comfortable with it!

The conditional is tested on each iteration, much as if there is an implied `if` statement inside the loop.

We can use JavaScript's `break` statement to stop a loop. Also, we can observe that it's awfully easy to create a loop that would otherwise run forever without a `break`ing mechanism.

Let's illustrate:

```js
var i = 0;

// a `while..true` loop would run forever, right?
while (true) {
	// stop the loop?
	if ((i <= 9) === false) {
		break;
	}

	console.log( i );
	i = i + 1;
}
// 0 1 2 3 4 5 6 7 8 9
```

**Warning:** This is not necessarily a practical form you'd want to use for your loops. It's presented here for illustration purposes only.

While a `while` (or `do..while`) can accomplish the task manually, there's another syntactic form called a `for` loop for just that purpose:

```js
for (var i = 0; i <= 9; i = i + 1) {
	console.log( i );
}
// 0 1 2 3 4 5 6 7 8 9
```

As you can see, in both cases the conditional `i <= 9` is `true` for the first 10 iterations (`i` of values `0` through `9`) of either loop form, but becomes `false` once `i` is value `10`.

The `for` loop has three clauses: the initialization clause (`var i=0`), the conditional test clause (`i <= 9`), and the update clause (`i = i + 1`). So if you're going to do counting with your loop iterations, `for` is a more compact and often easier form to understand and write.

There are other specialized loop forms that are intended to iterate over specific values, such as the properties of an object (see Chapter 2) where the implied conditional test is just whether all the properties have been processed. The "loop until a condition fails" concept holds no matter what the form of the loop.

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
