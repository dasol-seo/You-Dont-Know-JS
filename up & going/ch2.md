# You Don't Know JS: Up & Going
# Chapter 2: Into JavaScript

In the previous chapter, I introduced the basic building blocks of programming, such as variables, loops, conditionals, and functions. Of course, all the code shown has been in JavaScript. But in this chapter, we want to focus specifically on things you need to know about JavaScript to get up and going as a JS developer.

We will introduce quite a few concepts in this chapter that will not be fully explored until subsequent *YDKJS* books. You can think of this chapter as an overview of the topics covered in detail throughout the rest of this series.

Especially if you're new to JavaScript, you should expect to spend quite a bit of time reviewing the concepts and code examples here multiple times. Any good foundation is laid brick by brick, so don't expect that you'll immediately understand it all the first pass through.

Your journey to deeply learn JavaScript starts here.

**Note:** As I said in Chapter 1, you should definitely try all this code yourself as you read and work through this chapter. Be aware that some of the code here assumes capabilities introduced in the newest version of JavaScript at the time of this writing (commonly referred to as "ES6" for the 6th edition of ECMAScript -- the official name of the JS specification). If you happen to be using an older, pre-ES6 browser, the code may not work. A recent update of a modern browser (like Chrome, Firefox, or IE) should be used.

## Values & Types

As we asserted in Chapter 1, JavaScript has typed values, not typed variables. The following built-in types are available:

* `string`
* `number`
* `boolean`
* `null` and `undefined`
* `object`
* `symbol` (new to ES6)

JavaScript provides a `typeof` operator that can examine a value and tell you what type it is:

```js
var a;
typeof a;				// "undefined"

a = "hello world";
typeof a;				// "string"

a = 42;
typeof a;				// "number"

a = true;
typeof a;				// "boolean"

a = null;
typeof a;				// "object" -- weird, bug

a = undefined;
typeof a;				// "undefined"

a = { b: "c" };
typeof a;				// "object"
```

The return value from the `typeof` operator is always one of six (seven as of ES6! - the "symbol" type) string values. That is, `typeof "abc"` returns `"string"`, not `string`.

Notice how in this snippet the `a` variable holds every different type of value, and that despite appearances, `typeof a` is not asking for the "type of `a`", but rather for the "type of the value currently in `a`." Only values have types in JavaScript; variables are just simple containers for those values.

`typeof null` is an interesting case, because it errantly returns `"object"`, when you'd expect it to return `"null"`.

**Warning:** This is a long-standing bug in JS, but one that is likely never going to be fixed. Too much code on the Web relies on the bug and thus fixing it would cause a lot more bugs!

Also, note `a = undefined`. We're explicitly setting `a` to the `undefined` value, but that is behaviorally no different from a variable that has no value set yet, like with the `var a;` line at the top of the snippet. A variable can get to this "undefined" value state in several different ways, including functions that return no values and usage of the `void` operator.

### 객체

`object` 타입은 여러분이 원하는 이름으로 만든 속성들을 저장할 수 있는 복합적인 값을 참조합니다. 이때 속성들은 각각 자신의 값을 갖고 있고, 그 값의 타입에는 제한이 없습니다. `object` 타입은 자바스크립트에서 가장 유용하게 사용할 수 있는 타입 중 하나입니다.

```js
var obj = {
	a: "hello world",
	b: 42,
	c: true
};

obj.a;		// "hello world"
obj.b;		// 42
obj.c;		// true

obj["a"];	// "hello world"
obj["b"];	// 42
obj["c"];	// true
```

아래 그림은 여러분이 위의 `obj`에 대해 더 잘 이해할 수 있게 도식화하였습니다:

<img src="fig4.png">

속성들에는 *점 표기법* (i.e., `obj.a`)과 *대괄호 표기법* (i.e., `obj["a"]`)으로 접근이 가능합니다. 일반적으로 점 표기법은 짧고, 가독성이 좋기 때문에 객체에 접근할 때 주로 사용됩니다.

대괄호 표기법은 만약 여러분이 지정한 속성의 이름이 obj["hello world!"]처럼 특수 문자를 포함하고 있을 때 유용합니다. 이러한 속성들의 이름은 해당 객체에 대괄호 표기법으로 접근할 때 보통 *키*라고 불립니다. `[ ]` 표기법은 변수(다음에 설명합니다.)나 `string` *리터럴*(`" .. "` 나 `' .. '`로 감싸져 있는)을 필요로 합니다.

대괄호 표기법은 다음과 같이 다른 변수에 속성/키의 이름이 저장된 경우에도 매우 유용합니다:

```js
var obj = {
	a: "hello world",
	b: 42
};

var b = "a";

obj[b];			// "hello world"
obj["b"];		// 42
```

**참고:** 자바스크립트 `object`에 대해 더 자세한 정보를 알고 싶다면, 이 시리즈의 *this & Object Prototypes*(특히 3장)을 참고하세요. 

자바스크립트 프로그램에서 여러분들이 자주 보게 될 몇 가지 다른 타입들이 있습니다: *배열*과 *함수*. 하지만 이 두 타입은 자바스크립트에 내장된 타입이라고 하기보단, `object` 타입에서 조금 더 전문화되어 만들어진 버전, 즉 일종의 하위 타입이라고 생각하는 것이 좋습니다.

#### 배열

배열은 특정한 이름으로 지정된 속성/키 대신 오름차순 숫자 목록을 사용하는 object입니다. 예를 들어:

```js
var arr = [
	"hello world",
	42,
	true
];

arr[0];			// "hello world"
arr[1];			// 42
arr[2];			// true
arr.length;		// 3

typeof arr;		// "object"
```

**참고:** 자바스크립트와 같이 0부터 숫자를 세는 언어는, 배열의 첫 번째 요소의 인덱스로 0을 사용합니다.

아래 그림은 여러분이 위의 `arr`에 대해 더 잘 이해할 수 있게 도식화하였습니다:

<img src="fig5.png">

배열도 typeof가 암시하듯 특별하지만 객체이기 때문에 자동으로 갱신되는 length 속성을 비롯한 다른 속성들을 가질 수 있습니다.

이론적으로는 배열도 여러분이 원하는 이름으로 작성된 속성을 갖는 일반 객체로써 사용할 수 있습니다. 또한 `object`를 숫자로 된 속성(`0`, `1`, etc.)값만을 갖는 배열과 같은 형태로 사용할 수 도 있습니다. 그러나 이런 방법들은 일반적으로 각각의 타입의 관점에서 봤을 때 부적절한 사용법으로 여겨집니다.

위와 같은 이유로, 특정한 이름이 붙여진 속성이 필요하다면 `object`를 이용하고, 순서를 갖는 값들은 배열을 이용하는 것이 가장 자연스럽고 좋은 방법입니다.

#### 함수

함수는 여러분이 자바스크립트 프로그램을 작성할 때 사용하게 될 `object`의 다른 하위 타입입니다:

```js
function foo() {
	return 42;
}

foo.bar = "hello world";

typeof foo;			// "function"
typeof foo();		// "number"
typeof foo.bar;		// "string"
```

다시 말하지만, 함수는 `objects`의 하위 타입입니다. — `typeof`는 함수에 대해서 `"function"`을 반환하는데 이는 `function`이 주요 타입임을 의미합니다 -- 일반적으로 제한적인 경우에만 `foo.bar`와 같은 함수 객체 속성을 사용할 것입니다.

**참고:** 자바스크립트의 값과 타입에 대한 자세한 내용은, *Types & Grammar*시리즈의 처음 두 장을 참고하세요.

### 내장타입 메소드

앞서 말한 내장타입과 하위 타입은 매우 강력하고 유용한 속성과 메소드를 갖고 있습니다.

예를 들어:

```js
var a = "hello world";
var b = 3.14159;

a.length;				// 11
a.toUpperCase();		// "HELLO WORLD"
b.toFixed(4);			// "3.1416"
```

`a.toUpperCase()`를 호출하는 방법은 생각보다 복잡합니다.

요약하면, 일반적으로 "네이티브"라고 부르는 `String`(대문자 `S`)객체 래퍼 형태가 있고, 이는 원시 `string`타입과 짝을 이룹니다; 이는 프로토타입에서 `toUpperCase()` 메소드를 정의하는 객체 래퍼입니다.

`"hello world"`와 같은 원시값을 속성이나 메소드를 참조하는 `object`처럼 사용할 때(예를 들어 이전의 스니펫에서 `a.toUpperCase()` 처럼), 자바스크립트는 원시값을 짝이 맞는 객체 래퍼로 "감쌉니다".

`string`값은 `String`객체로 감쌀 수 있고, `number`는 `Number`객체로 감쌀 수 있고, `boolean`은 `Boolean`객체로 감쌀 수 있습니다. 실제로 모든 경우에 원시값 형태를 사용하는 것을 선호하고 자바스크립트가 여러분을 위해 나머지 부분을 처리해주기 때문에 여러분은 객체 래퍼 형태를 직접 사용할 필요는 없습니다.

**참고:** 자바스크립트 네이티브와 박싱에 대한 자세한 내용은 *Types & Grammar*시리즈의 3장을 참고하세요. 객체의 프로토타입을 잘 이해하려면, *this & Object Prototypes* 시리즈의 5장을 참고하세요.

### 값 비교하기

자바스크립트에는 값 비교를 할 때 사용하는 주요한 타입 두 가지가 있습니다: *동등* 과 *비동등*. 비교되는 값의 타입이 무엇인지 관계 없이, 모든 비교의 결과는 엄격하게 `boolean`값입니다(`true` 또는 `false`).

#### 강제 변환

우리는 1장에서 강제 변환에 대해 간단하게 얘기했는데, 여기에서 다시 한번 다뤄보도록 하겠습니다.

명시적인 강제 변환은 어떤 타입에서 다른 타입으로 변환이 일어나는 것을 코드를 통해 명백하게 알아볼 수 있을 만큼 단순하지만, 암시적인 강제 변환은 타입 변환이 다른 동작의 불분명하고 의도하지 않은 결과처럼 보일 수 있습니다.

여러분은 아마 "강제 변환은 악마다"와 같은 말을 들어봤을 겁니다. 강제 변환이 특정 위치에서는 예상치 못한 결과를 불러올 수 있기 때문에 전해진 말입니다. 아마 언어가 당황스럽게 할 때만큼 개발자들이 좌절감을 느끼는 때도 없을 것입니다.

강제 변환은 악마도 아니고, 놀랄 일도 아닙니다. 사실, 타입 강제 변환을 사용할 수 있는 대부분의 경우는 상당히 알아채기 쉽고 이해할 수 있는 부분이고, 심지어 여러분의 코드의 가독성을 *향상시키는데* 사용될 수 있습니다. 그러나 우리는 이 논쟁에 대해서는 더 이상 진행하지 않을 것입니다 -- *Types & Grammar*시리즈 4장에서 이 부분을 다루고 있습니다.

다음은 *명시적인* 강제 변환의 예시입니다:

```js
var a = "42";

var b = Number( a );

a;				// "42"
b;				// 42 -- 숫자!
```

그리고 다음은 *암시적인* 강제 변환의 예시입니다:

```js
var a = "42";

var b = a * 1;	// "42" "42" 암시적으로 42를 강제 변환

a;				// "42"
b;				// 42 -- 숫자!
```

#### 참 추정 & 거짓 추정

1장에서 "참 추정"과 "거짓 추정"값의 성질에 대해 간략하게 언급했습니다 : `boolean`이 아닌 값을 `boolean`값으로 강제 변환할 때 그 값은 `true` 와 `false` 중 무엇이 될까요?

자바스크립트에서 “거짓 추정”값들은 아래와 같습니다:

* `""` (빈 문자열)
* `0`, `-0`, `NaN` (유효하지 않은 `number`)
* `null`, `undefined`
* `false`

“거짓 추정”목록에 없는 값은 모두 “참 추정”값입니다. 예시는 아래와 같습니다:

* `"hello"`
* `42`
* `true`
* `[ ]`, `[ 1, "2", 3 ]` (배열)
* `{ }`, `{ a: 42 }` (객체)
* `function foo() { .. }` (함수)

여러분이 기억해야 할 것은 `boolean`이 아닌 값들이 `boolean`으로 강제 변환 될 때 오직 "참 추정"/"거짓 추정" 강제 변환을 따르게 된다는 것입니다. 이것을 명심 한다면 `boolean`이 아닌 값이 강제변환이 될때 혼동 될 만큼 어렵게 느껴지지 않을 것입니다.

#### Equality

There are four equality operators: `==`, `===`, `!=`, and `!==`. The `!` forms are of course the symmetric "not equal" versions of their counterparts; *non-equality* should not be confused with *inequality*.

The difference between `==` and `===` is usually characterized that `==` checks for value equality and `===` checks for both value and type equality. However, this is inaccurate. The proper way to characterize them is that `==` checks for value equality with coercion allowed, and `===` checks for value equality without allowing coercion; `===` is often called "strict equality" for this reason.

Consider the implicit coercion that's allowed by the `==` loose-equality comparison and not allowed with the `===` strict-equality:

```js
var a = "42";
var b = 42;

a == b;			// true
a === b;		// false
```

In the `a == b` comparison, JS notices that the types do not match, so it goes through an ordered series of steps to coerce one or both values to a different type until the types match, where then a simple value equality can be checked.

If you think about it, there's two possible ways `a == b` could give `true` via coercion. Either the comparison could end up as `42 == 42` or it could be `"42" == "42"`. So which is it?

The answer: `"42"` becomes `42`, to make the comparison `42 == 42`. In such a simple example, it doesn't really seem to matter which way that process goes, as the end result is the same. There are more complex cases where it matters not just what the end result of the comparison is, but *how* you get there.

The `a === b` produces `false`, because the coercion is not allowed, so the simple value comparison obviously fails. Many developers feel that `===` is more predictable, so they advocate always using that form and staying away from `==`. I think this view is very shortsighted. I believe `==` is a powerful tool that helps your program, *if you take the time to learn how it works.*

We're not going to cover all the nitty-gritty details of how the coercion in `==` comparisons works here. Much of it is pretty sensible, but there are some important corner cases to be careful of. You can read section 11.9.3 of the ES5 specification (http://www.ecma-international.org/ecma-262/5.1/) to see the exact rules, and you'll be surprised at just how straightforward this mechanism is, compared to all the negative hype surrounding it.

To boil down a whole lot of details to a few simple takeaways, and help you know whether to use `==` or `===` in various situations, here are my simple rules:

* If either value (aka side) in a comparison could be the `true` or `false` value, avoid `==` and use `===`.
* If either value in a comparison could be of these specific values (`0`, `""`, or `[]` -- empty array), avoid `==` and use `===`.
* In *all* other cases, you're safe to use `==`. Not only is it safe, but in many cases it simplifies your code in a way that improves readability.

What these rules boil down to is requiring you to think critically about your code and about what kinds of values can come through variables that get compared for equality. If you can be certain about the values, and `==` is safe, use it! If you can't be certain about the values, use `===`. It's that simple.

The `!=` non-equality form pairs with `==`, and the `!==` form pairs with `===`. All the rules and observations we just discussed hold symmetrically for these non-equality comparisons.

You should take special note of the `==` and `===` comparison rules if you're comparing two non-primitive values, like `object`s (including `function` and `array`). Because those values are actually held by reference, both `==` and `===` comparisons will simply check whether the references match, not anything about the underlying values.

For example, `array`s are by default coerced to `string`s by simply joining all the values with commas (`,`) in between. You might think that two `array`s with the same contents would be `==` equal, but they're not:

```js
var a = [1,2,3];
var b = [1,2,3];
var c = "1,2,3";

a == c;		// true
b == c;		// true
a == b;		// false
```

**Note:** For more information about the `==` equality comparison rules, see the ES5 specification (section 11.9.3) and also consult Chapter 4 of the *Types & Grammar* title of this series; see Chapter 2 for more information about values versus references.

#### 비동등

 `<`, `>`, `<=`, `>=` 연산자는 비동등에 사용됩니다, 기술 명세서에 "관계 비교"라고 언급되어 있습니다. 일반적으로 `number`와 같은 서수 비교에 사용되므로, `3 < 4`를 쉽게 이해할 수 있을 것입니다.

하지만 자바스크립트의 `string`값은 일반적인 알파벳 규칙을 사용하므로 비동등으로도 비교가 가능합니다 (`"bar" < "foo"`).

그렇다면 강제 변환은 어떻게 될까요? `==` 비교(완벽하게 같진 않습니다!)와 비슷한 규칙이 비동등 연산자에도 적용됩니다. 특히 "엄격한 비동등" 연산자는 `===` "엄격한 동등"과 마찬가지로 강제변환을 허용하지 않습니다.

생각해보세요:

```js
var a = 41;
var b = "42";
var c = "43";

a < b;		// true
b < c;		// true
```

무슨 일이 일어난 걸까요? ES5의 기술 명세서 중 11.8.5부분에 보면, `<`로 비교하는 두 값이 `string`이면 `b < c`처럼 비교는 사전적으로 (사전에 있는 알파벳정렬처럼) 됩니다. 하지만 `a < b`비교처럼 하나 또는 두 개의 값이 `string`이 아니면, 두 값 모두가 `number`로 강제 변환되어 일반적인 서수 비교를 하게 됩니다.

잠재적으로 타입이 다른 값들을 비교할 때 실수할 수 있는것은 둘 중 하나의 값이 유효한 숫자로 변환할 수 없는 경우 입니다 -- "엄격한 비동등"형식을 사용하지 않는다는것을 기억하세요. -- 예를 들면:

```js
var a = 42;
var b = "foo";

a < b;		// false
a > b;		// false
a == b;		// false
```

어떻게 세 개의 모든 비교가 `false`일까요? 왜냐하면 `<` 와 `>` 비교에서 `b` 값은 강제 변환이 되어 "유효하지 않은 숫자 값" `NaN`이 되기 때문이고, 기술 명세서에서 `NaN`은 어떤 다른 값 과도 크거나 혹은 작지 않다고 설명되어 있습니다.

`==`의 비교의 실패는 다른 원인이 있습니다. 이전 설명했던 경우처럼 `a == b`는 `42 == NaN` 나 `"42" == "foo"` 로 해석될 수 있습니다.

**Note:** 비동등 규칙에 대해서 더 많은 내용을 알고 싶으시면 ES5의 기술 명세서 중 11.8.5 부분을 확인해 보세요. 또한 Types & Grammar시리즈의 4장을 참고하세요.

## Variables

In JavaScript, variable names (including function names) must be valid *identifiers*. The strict and complete rules for valid characters in identifiers are a little complex when you consider nontraditional characters such as Unicode. If you only consider typical ASCII alphanumeric characters, though, the rules are simple.

An identifier must start with `a`-`z`, `A`-`Z`, `$`, or `_`. It can then contain any of those characters plus the numerals `0`-`9`.

Generally, the same rules apply to a property name as to a variable identifier. However, certain words cannot be used as variables, but are OK as property names. These words are called "reserved words," and include the JS keywords (`for`, `in`, `if`, etc.) as well as `null`, `true`, and `false`.

**Note:** For more information about reserved words, see Appendix A of the *Types & Grammar* title of this series.

### Function Scopes

You use the `var` keyword to declare a variable that will belong to the current function scope, or the global scope if at the top level outside of any function.

#### Hoisting

Wherever a `var` appears inside a scope, that declaration is taken to belong to the entire scope and accessible everywhere throughout.

Metaphorically, this behavior is called *hoisting*, when a `var` declaration is conceptually "moved" to the top of its enclosing scope. Technically, this process is more accurately explained by how code is compiled, but we can skip over those details for now.

Consider:

```js
var a = 2;

foo();					// works because `foo()`
						// declaration is "hoisted"

function foo() {
	a = 3;

	console.log( a );	// 3

	var a;				// declaration is "hoisted"
						// to the top of `foo()`
}

console.log( a );	// 2
```

**Warning:** It's not common or a good idea to rely on variable *hoisting* to use a variable earlier in its scope than its `var` declaration appears; it can be quite confusing. It's much more common and accepted to use *hoisted* function declarations, as we do with the `foo()` call appearing before its formal declaration.

#### Nested Scopes

When you declare a variable, it is available anywhere in that scope, as well as any lower/inner scopes. For example:

```js
function foo() {
	var a = 1;

	function bar() {
		var b = 2;

		function baz() {
			var c = 3;

			console.log( a, b, c );	// 1 2 3
		}

		baz();
		console.log( a, b );		// 1 2
	}

	bar();
	console.log( a );				// 1
}

foo();
```

Notice that `c` is not available inside of `bar()`, because it's declared only inside the inner `baz()` scope, and that `b` is not available to `foo()` for the same reason.

If you try to access a variable's value in a scope where it's not available, you'll get a `ReferenceError` thrown. If you try to set a variable that hasn't been declared, you'll either end up creating a variable in the top-level global scope (bad!) or getting an error, depending on "strict mode" (see "Strict Mode"). Let's take a look:

```js
function foo() {
	a = 1;	// `a` not formally declared
}

foo();
a;			// 1 -- oops, auto global variable :(
```

This is a very bad practice. Don't do it! Always formally declare your variables.

In addition to creating declarations for variables at the function level, ES6 *lets* you declare variables to belong to individual blocks (pairs of `{ .. }`), using the `let` keyword. Besides some nuanced details, the scoping rules will behave roughly the same as we just saw with functions:

```js
function foo() {
	var a = 1;

	if (a >= 1) {
		let b = 2;

		while (b < 5) {
			let c = b * 2;
			b++;

			console.log( a + c );
		}
	}
}

foo();
// 5 7 9
```

Because of using `let` instead of `var`, `b` will belong only to the `if` statement and thus not to the whole `foo()` function's scope. Similarly, `c` belongs only to the `while` loop. Block scoping is very useful for managing your variable scopes in a more fine-grained fashion, which can make your code much easier to maintain over time.

**Note:** For more information about scope, see the *Scope & Closures* title of this series. See the *ES6 & Beyond* title of this series for more information about `let` block scoping.

## Conditionals

1장에서 간단하게 소개한 `if`문에 더하여, 우리는 자바스크립트가 제공하는 몇개의 다른 조건 메커니즘을 살펴보려고 합니다.

때때로 여러분은 아래와 같은 일련의 `if..else..if`문을 작성할 겁니다: 

```js
if (a == 2) {
	// do something
}
else if (a == 10) {
	// do another thing
}
else if (a == 42) {
	// do yet another thing
}
else {
	// fallback to here
}
```

물론 위와 같은 구조도 잘 작동하지만 각각의 케이스마다 `a`값이 뭔지 확인을 해야하기때문에 조금은 장황하게 보입니다. 지금과 같은 상황에선 아래와 같은 `switch`문이 대안이 될 수 있습니다:

```js
switch (a) {
	case 2:
		// do something
		break;
	case 10:
		// do another thing
		break;
	case 42:
		// do yet another thing
		break;
	default:
		// fallback to here
}
```

`break`는 여러분이 오직 한 `case`안에서의 문을 실행하려고 할 때 중요합니다. 만약 여러분이 원하는 `case`안에 `break`가 빠져있다면, 그 `case`만 실행되기를 원해도, 다음 단계의 `case`가 실행될 것 입니다. "통과하다"라고 불리는 이 상황은 종종 유용/필요 하기도 합니다:

```js
switch (a) {
	case 2:
	case 10:
		// 코드
		break;
	case 42:
		// 위와는 다른 코드
		break;
	default:
		// 아무 케이스에도 해당 되지 않는 나머지 인자들에 대해 실행
}
```

여기서 `a`가 `2` 또는 `10`이라면 "코드" 에 해당하는 내용의 코드를 실행하게 된다.

자바스크립트의 또 다른 조건문 형태는 "조건 연산자"로써 보통 "삼항 연산자"라고 불린다. 삼항 연산자는 단일 `iif..else`문의 간결한 형태와 같다. 예를 들어:

```js
var a = 42;

var b = (a > 41) ? "hello" : "world";

// similar to:

// if (a > 41) {
//    b = "hello";
// }
// else {
//    b = "world";
// }
```

실험 표현식(여기서는 `a > 41`)이 `true`로 판단된다면, 물음표 뒤의 첫 번째 절(`"hello"`)의 결과가 나오고, 그렇지 않으면 두 번째 절(`"world"`)의 결과가 나옵니다. 여기에서 결과가 무엇이든 `b`에 배정됩니다.

조건 연산자는 할당에 사용될 필요는 없지만, 이는 분명히 가장 일반적인 사용법입니다.

**참고:** `switch` 와 `? :`의 테스트 조건과 다른 패턴들에 대한 자세한 내용은 이 시리즈의 *Types & Grammar*를 참고하세요.

## 엄격 모드

ES5는 자바스크립트에 "엄격 모드"를 추가하여 특정 행동에 대한 규칙을 강화하였습니다. 일반적으로 이러한 제한은 코드를 더 안전하고 일련의 가이드라인에 더 적절하게 유지할 수 있게 합니다. 또한, 엄격 모드를 따르면 엔진에 의해 코드를 더 최적화 할 수 있습니다. 엄격 모드는 코드에서의 큰 승리이며, 여러분은 이를 여러분의 모든 프로그램에서 사용해야 합니다.

여러분은 엄격 모드의 실용성을 어디에 두느냐에 따라 개별 기능, 또는 전체 파일에 대해 엄격 모드의 사용을 선택할 수 있습니다.

```js
function foo() {
	"use strict";

	// 이 코드는 엄격 모드 입니다.

	function bar() {
		// 이 코드는 엄격 모드 입니다.
	}
}

// 이 코드는 엄격 모드가 아닙니다.
```

아래와 비교해봅시다:

```js
"use strict";

function foo() {
	// 이 코드는 엄격 모드입니다.

	function bar() {
		// 이 코드는 엄격 모드 입니다.
	}
}

// 이 코드는 엄격 모드 입니다.
```

엄격 모드를 사용하는 한가지 중요한 차이점(개선!)은 `var`생략함으로써 발생하는 암묵적인 자동-글로벌 변수 선언을 허용하지 않는 것입니다.  

```js
function foo() {
	"use strict";	// 엄격 모드를 사용합니다.
	a = 1;			// `var`를 생략했음으로 참조에러가 닙니다.
}

foo();
```

여러분이 여러분의 코드에서 엄격 모드를 사용했을 때 에러가 발생하거나, 코드가 버그를 일으키기 시작하면, 엄격 모드를 피하고 싶은 유혹에 빠질 수 있습니다. 그러나 그러한 유혹에 빠지는 것은 좋지 않습니다. 만약 엄격 모드가  여러분의 코드에서 어떤 이슈를 발생 시킨다면, 그것은 여러분의 프로그램상에서 고쳐야할 어떤 것이 있다는 분명한 신호입니다. 

엄격 모드는 여러분의 코드를 자바스크립트가 근 미래에 나가야할 방향에 있어서 안전한 경로를 유지해주고, 최적화되게 만들어 줄 것입니다. 여러분에게는 엄격 모드의 사용을 미루는 것보다, 익숙해지는 것이 나중에 변환하는 것보다는 훨씬 쉬울 것입니다. 

**참고:** 엄격 모드에 대한 자세한 내용은 이 시리즈의 *Types & Grammar* 5장을 참고하세요.

## Functions As Values

So far, we've discussed functions as the primary mechanism of *scope* in JavaScript. You recall typical `function` declaration syntax as follows:

```js
function foo() {
	// ..
}
```

Though it may not seem obvious from that syntax, `foo` is basically just a variable in the outer enclosing scope that's given a reference to the `function` being declared. That is, the `function` itself is a value, just like `42` or `[1,2,3]` would be.

This may sound like a strange concept at first, so take a moment to ponder it. Not only can you pass a value (argument) *to* a function, but *a function itself can be a value* that's assigned to variables, or passed to or returned from other functions.

As such, a function value should be thought of as an expression, much like any other value or expression.

Consider:

```js
var foo = function() {
	// ..
};

var x = function bar(){
	// ..
};
```

The first function expression assigned to the `foo` variable is called *anonymous* because it has no `name`.

The second function expression is *named* (`bar`), even as a reference to it is also assigned to the `x` variable. *Named function expressions* are generally more preferable, though *anonymous function expressions* are still extremely common.

For more information, see the *Scope & Closures* title of this series.

### Immediately Invoked Function Expressions (IIFEs)

In the previous snippet, neither of the function expressions are executed -- we could if we had included `foo()` or `x()`, for instance.

There's another way to execute a function expression, which is typically referred to as an *immediately invoked function expression* (IIFE):

```js
(function IIFE(){
	console.log( "Hello!" );
})();
// "Hello!"
```

The outer `( .. )` that surrounds the `(function IIFE(){ .. })` function expression is just a nuance of JS grammar needed to prevent it from being treated as a normal function declaration.

The final `()` on the end of the expression -- the `})();` line -- is what actually executes the function expression referenced immediately before it.

That may seem strange, but it's not as foreign as first glance. Consider the similarities between `foo` and `IIFE` here:

```js
function foo() { .. }

// `foo` function reference expression,
// then `()` executes it
foo();

// `IIFE` function expression,
// then `()` executes it
(function IIFE(){ .. })();
```

As you can see, listing the `(function IIFE(){ .. })` before its executing `()` is essentially the same as including `foo` before its executing `()`; in both cases, the function reference is executed with `()` immediately after it.

Because an IIFE is just a function, and functions create variable *scope*, using an IIFE in this fashion is often used to declare variables that won't affect the surrounding code outside the IIFE:

```js
var a = 42;

(function IIFE(){
	var a = 10;
	console.log( a );	// 10
})();

console.log( a );		// 42
```

IIFEs can also have return values:

```js
var x = (function IIFE(){
	return 42;
})();

x;	// 42
```

The `42` value gets `return`ed from the `IIFE`-named function being executed, and is then assigned to `x`.

### Closure

*Closure* is one of the most important, and often least understood, concepts in JavaScript. I won't cover it in deep detail here, and instead refer you to the *Scope & Closures* title of this series. But I want to say a few things about it so you understand the general concept. It will be one of the most important techniques in your JS skillset.

You can think of closure as a way to "remember" and continue to access a function's scope (its variables) even once the function has finished running.

Consider:

```js
function makeAdder(x) {
	// parameter `x` is an inner variable

	// inner function `add()` uses `x`, so
	// it has a "closure" over it
	function add(y) {
		return y + x;
	};

	return add;
}
```

The reference to the inner `add(..)` function that gets returned with each call to the outer `makeAdder(..)` is able to remember whatever `x` value was passed in to `makeAdder(..)`. Now, let's use `makeAdder(..)`:

```js
// `plusOne` gets a reference to the inner `add(..)`
// function with closure over the `x` parameter of
// the outer `makeAdder(..)`
var plusOne = makeAdder( 1 );

// `plusTen` gets a reference to the inner `add(..)`
// function with closure over the `x` parameter of
// the outer `makeAdder(..)`
var plusTen = makeAdder( 10 );

plusOne( 3 );		// 4  <-- 1 + 3
plusOne( 41 );		// 42 <-- 1 + 41

plusTen( 13 );		// 23 <-- 10 + 13
```

More on how this code works:

1. When we call `makeAdder(1)`, we get back a reference to its inner `add(..)` that remembers `x` as `1`. We call this function reference `plusOne(..)`.
2. When we call `makeAdder(10)`, we get back another reference to its inner `add(..)` that remembers `x` as `10`. We call this function reference `plusTen(..)`.
3. When we call `plusOne(3)`, it adds `3` (its inner `y`) to the `1` (remembered by `x`), and we get `4` as the result.
4. When we call `plusTen(13)`, it adds `13` (its inner `y`) to the `10` (remembered by `x`), and we get `23` as the result.

Don't worry if this seems strange and confusing at first -- it can be! It'll take lots of practice to understand it fully.

But trust me, once you do, it's one of the most powerful and useful techniques in all of programming. It's definitely worth the effort to let your brain simmer on closures for a bit. In the next section, we'll get a little more practice with closure.

#### Modules

The most common usage of closure in JavaScript is the module pattern. Modules let you define private implementation details (variables, functions) that are hidden from the outside world, as well as a public API that *is* accessible from the outside.

Consider:

```js
function User(){
	var username, password;

	function doLogin(user,pw) {
		username = user;
		password = pw;

		// do the rest of the login work
	}

	var publicAPI = {
		login: doLogin
	};

	return publicAPI;
}

// create a `User` module instance
var fred = User();

fred.login( "fred", "12Battery34!" );
```

The `User()` function serves as an outer scope that holds the variables `username` and `password`, as well as the inner `doLogin()` function; these are all private inner details of this `User` module that cannot be accessed from the outside world.

**Warning:** We are not calling `new User()` here, on purpose, despite the fact that probably seems more common to most readers. `User()` is just a function, not a class to be instantiated, so it's just called normally. Using `new` would be inappropriate and actually waste resources.

Executing `User()` creates an *instance* of the `User` module -- a whole new scope is created, and thus a whole new copy of each of these inner variables/functions. We assign this instance to `fred`. If we run `User()` again, we'd get a new instance entirely separate from `fred`.

The inner `doLogin()` function has a closure over `username` and `password`, meaning it will retain its access to them even after the `User()` function finishes running.

`publicAPI` is an object with one property/method on it, `login`, which is a reference to the inner `doLogin()` function. When we return `publicAPI` from `User()`, it becomes the instance we call `fred`.

At this point, the outer `User()` function has finished executing. Normally, you'd think the inner variables like `username` and `password` have gone away. But here they have not, because there's a closure in the `login()` function keeping them alive.

That's why we can call `fred.login(..)` -- the same as calling the inner `doLogin(..)` -- and it can still access `username` and `password` inner variables.

There's a good chance that with just this brief glimpse at closure and the module pattern, some of it is still a bit confusing. That's OK! It takes some work to wrap your brain around it.

From here, go read the *Scope & Closures* title of this series for a much more in-depth exploration.

## `this` Identifier

Another very commonly misunderstood concept in JavaScript is the `this` identifier. Again, there's a couple of chapters on it in the *this & Object Prototypes* title of this series, so here we'll just briefly introduce the concept.

While it may often seem that `this` is related to "object-oriented patterns," in JS `this` is a different mechanism.

If a function has a `this` reference inside it, that `this` reference usually points to an `object`. But which `object` it points to depends on how the function was called.

It's important to realize that `this` *does not* refer to the function itself, as is the most common misconception.

Here's a quick illustration:

```js
function foo() {
	console.log( this.bar );
}

var bar = "global";

var obj1 = {
	bar: "obj1",
	foo: foo
};

var obj2 = {
	bar: "obj2"
};

// --------

foo();				// "global"
obj1.foo();			// "obj1"
foo.call( obj2 );		// "obj2"
new foo();			// undefined
```

There are four rules for how `this` gets set, and they're shown in those last four lines of that snippet.

1. `foo()` ends up setting `this` to the global object in non-strict mode -- in strict mode, `this` would be `undefined` and you'd get an error in accessing the `bar` property -- so `"global"` is the value found for `this.bar`.
2. `obj1.foo()` sets `this` to the `obj1` object.
3. `foo.call(obj2)` sets `this` to the `obj2` object.
4. `new foo()` sets `this` to a brand new empty object.

Bottom line: to understand what `this` points to, you have to examine how the function in question was called. It will be one of those four ways just shown, and that will then answer what `this` is.

**Note:** For more information about `this`, see Chapters 1 and 2 of the *this & Object Prototypes* title of this series.

## Prototypes

The prototype mechanism in JavaScript is quite complicated. We will only glance at it here. You will want to spend plenty of time reviewing Chapters 4-6 of the *this & Object Prototypes* title of this series for all the details.

When you reference a property on an object, if that property doesn't exist, JavaScript will automatically use that object's internal prototype reference to find another object to look for the property on. You could think of this almost as a fallback if the property is missing.

The internal prototype reference linkage from one object to its fallback happens at the time the object is created. The simplest way to illustrate it is with a built-in utility called `Object.create(..)`.

Consider:

```js
var foo = {
	a: 42
};

// create `bar` and link it to `foo`
var bar = Object.create( foo );

bar.b = "hello world";

bar.b;		// "hello world"
bar.a;		// 42 <-- delegated to `foo`
```

It may help to visualize the `foo` and `bar` objects and their relationship:

<img src="fig6.png">

The `a` property doesn't actually exist on the `bar` object, but because `bar` is prototype-linked to `foo`, JavaScript automatically falls back to looking for `a` on the `foo` object, where it's found.

This linkage may seem like a strange feature of the language. The most common way this feature is used -- and I would argue, abused -- is to try to emulate/fake a "class" mechanism with "inheritance."

But a more natural way of applying prototypes is a pattern called "behavior delegation," where you intentionally design your linked objects to be able to *delegate* from one to the other for parts of the needed behavior.

**Note:** For more information about prototypes and behavior delegation, see Chapters 4-6 of the *this & Object Prototypes* title of this series.

## Old & New

Some of the JS features we've already covered, and certainly many of the features covered in the rest of this series, are newer additions and will not necessarily be available in older browsers. In fact, some of the newest features in the specification aren't even implemented in any stable browsers yet.

So, what do you do with the new stuff? Do you just have to wait around for years or decades for all the old browsers to fade into obscurity?

That's how many people think about the situation, but it's really not a healthy approach to JS.

There are two main techniques you can use to "bring" the newer JavaScript stuff to the older browsers: polyfilling and transpiling.

### Polyfilling

The word "polyfill" is an invented term (by Remy Sharp) (https://remysharp.com/2010/10/08/what-is-a-polyfill) used to refer to taking the definition of a newer feature and producing a piece of code that's equivalent to the behavior, but is able to run in older JS environments.

For example, ES6 defines a utility called `Number.isNaN(..)` to provide an accurate non-buggy check for `NaN` values, deprecating the original `isNaN(..)` utility. But it's easy to polyfill that utility so that you can start using it in your code regardless of whether the end user is in an ES6 browser or not.

Consider:

```js
if (!Number.isNaN) {
	Number.isNaN = function isNaN(x) {
		return x !== x;
	};
}
```

The `if` statement guards against applying the polyfill definition in ES6 browsers where it will already exist. If it's not already present, we define `Number.isNaN(..)`.

**Note:** The check we do here takes advantage of a quirk with `NaN` values, which is that they're the only value in the whole language that is not equal to itself. So the `NaN` value is the only one that would make `x !== x` be `true`.

Not all new features are fully polyfillable. Sometimes most of the behavior can be polyfilled, but there are still small deviations. You should be really, really careful in implementing a polyfill yourself, to make sure you are adhering to the specification as strictly as possible.

Or better yet, use an already vetted set of polyfills that you can trust, such as those provided by ES5-Shim (https://github.com/es-shims/es5-shim) and ES6-Shim (https://github.com/es-shims/es6-shim).

### Transpiling

There's no way to polyfill new syntax that has been added to the language. The new syntax would throw an error in the old JS engine as unrecognized/invalid.

So the better option is to use a tool that converts your newer code into older code equivalents. This process is commonly called "transpiling," a term for transforming + compiling.

Essentially, your source code is authored in the new syntax form, but what you deploy to the browser is the transpiled code in old syntax form. You typically insert the transpiler into your build process, similar to your code linter or your minifier.

You might wonder why you'd go to the trouble to write new syntax only to have it transpiled away to older code -- why not just write the older code directly?

There are several important reasons you should care about transpiling:

* The new syntax added to the language is designed to make your code more readable and maintainable. The older equivalents are often much more convoluted. You should prefer writing newer and cleaner syntax, not only for yourself but for all other members of the development team.
* If you transpile only for older browsers, but serve the new syntax to the newest browsers, you get to take advantage of browser performance optimizations with the new syntax. This also lets browser makers have more real-world code to test their implementations and optimizations on.
* Using the new syntax earlier allows it to be tested more robustly in the real world, which provides earlier feedback to the JavaScript committee (TC39). If issues are found early enough, they can be changed/fixed before those language design mistakes become permanent.

Here's a quick example of transpiling. ES6 adds a feature called "default parameter values." It looks like this:

```js
function foo(a = 2) {
	console.log( a );
}

foo();		// 2
foo( 42 );	// 42
```

Simple, right? Helpful, too! But it's new syntax that's invalid in pre-ES6 engines. So what will a transpiler do with that code to make it run in older environments?

```js
function foo() {
	var a = arguments[0] !== (void 0) ? arguments[0] : 2;
	console.log( a );
}
```

As you can see, it checks to see if the `arguments[0]` value is `void 0` (aka `undefined`), and if so provides the `2` default value; otherwise, it assigns whatever was passed.

In addition to being able to now use the nicer syntax even in older browsers, looking at the transpiled code actually explains the intended behavior more clearly.

You may not have realized just from looking at the ES6 version that `undefined` is the only value that can't get explicitly passed in for a default-value parameter, but the transpiled code makes that much more clear.

The last important detail to emphasize about transpilers is that they should now be thought of as a standard part of the JS development ecosystem and process. JS is going to continue to evolve, much more quickly than before, so every few months new syntax and new features will be added.

If you use a transpiler by default, you'll always be able to make that switch to newer syntax whenever you find it useful, rather than always waiting for years for today's browsers to phase out.

There are quite a few great transpilers for you to choose from. Here are some good options at the time of this writing:

* Babel (https://babeljs.io) (formerly 6to5): Transpiles ES6+ into ES5
* Traceur (https://github.com/google/traceur-compiler): Transpiles ES6, ES7, and beyond into ES5

## Non-JavaScript

So far, the only things we've covered are in the JS language itself. The reality is that most JS is written to run in and interact with environments like browsers. A good chunk of the stuff that you write in your code is, strictly speaking, not directly controlled by JavaScript. That probably sounds a little strange.

The most common non-JavaScript JavaScript you'll encounter is the DOM API. For example:

```js
var el = document.getElementById( "foo" );
```

The `document` variable exists as a global variable when your code is running in a browser. It's not provided by the JS engine, nor is it particularly controlled by the JavaScript specification. It takes the form of something that looks an awful lot like a normal JS `object`, but it's not really exactly that. It's a special `object,` often called a "host object."

Moreover, the `getElementById(..)` method on `document` looks like a normal JS function, but it's just a thinly exposed interface to a built-in method provided by the DOM from your browser. In some (newer-generation) browsers, this layer may also be in JS, but traditionally the DOM and its behavior is implemented in something more like C/C++.

Another example is with input/output (I/O).

Everyone's favorite `alert(..)` pops up a message box in the user's browser window. `alert(..)` is provided to your JS program by the browser, not by the JS engine itself. The call you make sends the message to the browser internals and it handles drawing and displaying the message box.

The same goes with `console.log(..)`; your browser provides such mechanisms and hooks them up to the developer tools.

This book, and this whole series, focuses on JavaScript the language. That's why you don't see any substantial coverage of these non-JavaScript JavaScript mechanisms. Nevertheless, you need to be aware of them, as they'll be in every JS program you write!

## Review

The first step to learning JavaScript's flavor of programming is to get a basic understanding of its core mechanisms like values, types, function closures, `this`, and prototypes.

Of course, each of these topics deserves much greater coverage than you've seen here, but that's why they have chapters and books dedicated to them throughout the rest of this series. After you feel pretty comfortable with the concepts and code samples in this chapter, the rest of the series awaits you to really dig in and get to know the language deeply.

The final chapter of this book will briefly summarize each of the other titles in the series and the other concepts they cover besides what we've already explored.
