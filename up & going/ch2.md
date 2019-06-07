# You Don't Know JS: Up & Going
# Chapter 2: Into JavaScript

이전 장에서는 자바스크립트로 작성된 예제 코드와 함께 변수, 반복문, 조건문, 함수와 같은 프로그래밍의 기본적인 구성 요소를 소개했습니다. 이 장에서는, 여러분이 자바스크립트 개발자가 되기 위해 자바스크립트에 대해 알아야 할 것들에 중점을 두려고 합니다.

이 장에서 *YDKJS* 시리즈의 후속책까지는 자세히 다뤄지지 않을 꽤 많은 개념을 소개할 것입니다. 이 장을 이 시리즈의 나머지 부분에서 자세히 다루는 주제들의 개요로 생각하셔도 좋습니다.

특히 자바스크립트가 처음이라면, 이 장에서 여러 번 개념과 코드 예제를 검토하는 데 꽤 많은 시간을 할애해야 합니다. 기반을 단단히 하려면 벽돌을 하나씩 차근차근 쌓아올려야 하는 것처럼, 처음부터 모든것을 이해하려고 하지 마세요.

자바스크립트를 깊이 있게 배우기 위한 여정은 여기에서 시작됩니다.

**참고:** 1장에서 말했듯이, 이 장에서도 모든 예제 코드를 직접 실행해봐야 합니다. 여기에 있는 코드 중 일부는 이 문서를 작성하는 시점의 최신 자바스크립트 버전인 ES6에 소개된 기능을 전제한다는 점에 유의해주세요. (자바스크립트 기술명세서의 공식 명칭인 ECMAScript의 6번째 버전에 대해서는 일반적으로 "ES6"라고 합니다) ES6 이전 브라우저를 사용한다면 코드가 작동하지 않을 수도 있습니다. 최신 업데이트가 된 브라우저(Chrome, Firefox 혹은 IE)를 사용해주세요.

## 값 & 타입

1장에서 설명한 것처럼 자바스크립트는 타입이 지정된 변수가 아닌, 타입이 지정된 값을 가집니다. 다음과 같은 내장 타입들을 사용할 수 있습니다:

* `string`
* `number`
* `boolean`
* `null`과 `undefined`
* `object`
* `symbol` (ES6에서 추가됨)

자바스크립트에는 값을 검사하고 어떤 타입인지 알려주는 `typeof` 연산자가 있습니다:

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
typeof a;				// "object" -- 이상한 버그

a = undefined;
typeof a;				// "undefined"

a = { b: "c" };
typeof a;				// "object"
```

`typeof` 연산자의 반환값은 항상 여섯개(ES6에서는 "symbol" 타입이 추가된 일곱개!)의 문자열 값 중 하나입니다. 즉, `typeof "abc"`는 `string`이 아니라 `"string"`을 반환합니다.

이 스니펫에서 `a` 변수가 모든 다른 타입의 값을 갖고 있으며, 위와 같은 상황에서 `typeof a`가 "`a`의 타입"이 아니라 "현재 `a`에 있는 값의 타입"을 물어본다는 점에 주목하세요.

`typeof null`은 흥미로운 경우입니다, 왜냐하면 `"null"`을 반환해야한다고 예상하지만 `"object"`를 반환하기 때문입니다.

**주의:** 이것은 자바스크립트의 오래된 버그지만 절대 고쳐지지 않을 것 같습니다. 웹 상의 너무 많은 코드가 버그에 의존하고 있고, 따라서 이것을 고치는 게 더 많은 버그를 초래할 것입니다!

또한 `a = undefined`에도 유의하세요. 명시적으로 `a`에 `undefined`값을 할당했지만, 스니펫의 가장 윗 줄에 있는 `var a;`와 같이 값이 설정되지 않은 변수(초기화 되지 않은 변수)와 동작상으로 다를 바가 없습니다. 변수는 아무 값도 반환하지 않는 함수나 `void` 연산자를 사용하는 방법을 포함한 여러가지 방법으로 "undefined"값 상태가 될 수 있습니다.

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

In addition to the `if` statement we introduced briefly in Chapter 1, JavaScript provides a few other conditionals mechanisms that we should take a look at.

Sometimes you may find yourself writing a series of `if..else..if` statements like this:

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

This structure works, but it's a little verbose because you need to specify the `a` test for each case. Here's another option, the `switch` statement:

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

The `break` is important if you want only the statement(s) in one `case` to run. If you omit `break` from a `case`, and that `case` matches or runs, execution will continue with the next `case`'s statements regardless of that `case` matching. This so called "fall through" is sometimes useful/desired:

```js
switch (a) {
	case 2:
	case 10:
		// some cool stuff
		break;
	case 42:
		// other stuff
		break;
	default:
		// fallback
}
```

Here, if `a` is either `2` or `10`, it will execute the "some cool stuff" code statements.

Another form of conditional in JavaScript is the "conditional operator," often called the "ternary operator." It's like a more concise form of a single `if..else` statement, such as:

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

If the test expression (`a > 41` here) evaluates as `true`, the first clause (`"hello"`) results, otherwise the second clause (`"world"`) results, and whatever the result is then gets assigned to `b`.

The conditional operator doesn't have to be used in an assignment, but that's definitely the most common usage.

**Note:** For more information about testing conditions and other patterns for `switch` and `? :`, see the *Types & Grammar* title of this series.

## Strict Mode

ES5 added a "strict mode" to the language, which tightens the rules for certain behaviors. Generally, these restrictions are seen as keeping the code to a safer and more appropriate set of guidelines. Also, adhering to strict mode makes your code generally more optimizable by the engine. Strict mode is a big win for code, and you should use it for all your programs.

You can opt in to strict mode for an individual function, or an entire file, depending on where you put the strict mode pragma:

```js
function foo() {
	"use strict";

	// this code is strict mode

	function bar() {
		// this code is strict mode
	}
}

// this code is not strict mode
```

Compare that to:

```js
"use strict";

function foo() {
	// this code is strict mode

	function bar() {
		// this code is strict mode
	}
}

// this code is strict mode
```

One key difference (improvement!) with strict mode is disallowing the implicit auto-global variable declaration from omitting the `var`:

```js
function foo() {
	"use strict";	// turn on strict mode
	a = 1;			// `var` missing, ReferenceError
}

foo();
```

If you turn on strict mode in your code, and you get errors, or code starts behaving buggy, your temptation might be to avoid strict mode. But that instinct would be a bad idea to indulge. If strict mode causes issues in your program, almost certainly it's a sign that you have things in your program you should fix.

Not only will strict mode keep your code to a safer path, and not only will it make your code more optimizable, but it also represents the future direction of the language. It'd be easier on you to get used to strict mode now than to keep putting it off -- it'll only get harder to convert later!

**Note:** For more information about strict mode, see the Chapter 5 of the *Types & Grammar* title of this series.

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

### 클로져

*클로져*는 자바스트립트 개념에서 가장 중요한 개념이기도 하면서 이해도가 낮기도 합니다. 이 장에서는 세부사항까지 깊게 다루지 않을 것입니다. 대신에, 이 시리즈의 *Scope & Closure*를 참고하세요. 하지만 여러분에게 일반적인 개념을 이해시켜 드리기 위해 약간의 설명을 드리려고 합니다. 자바스크립트 기술 중에 가장 중요한 부분이 될 것입니다.

클로져는 함수 실행이 끝났음에도 불구하고, 함수 스코프를(내부 변수) “기억” 하고 계속 접근하는 방법이라고 생각하셔도 좋습니다.

생각해보세요:

```js
function makeAdder(x) {
	// 파라미터 ‘x’는 내부 변수입니다.

	// 내부 함수 `add()`는 `x`를 사용하기 때문에
	// "closure"를 가지고 있습니다.
	function add(y) {
		return y + x;
	};

	return add;
}
```

외부 `makeAdder()`함수 호출에 따라 반환되는 내부 `add()`함수 참조는 `makeAdder()`로 어떤 `x` 값이 들어오든지 기억을 할 수 있습니다. 그럼, `makeAdder(..)`를 사용해보겠습니다:

```js
// ‘plusOne’은
// 외부 `makeAdder(..)`함수의 `x` 파라미터 클로저를 가지는
// 내부 `add()`함수에 대한 참조를 갖습니다.
var plusOne = makeAdder( 1 );

// ‘plusTen’은
// 외부 `makeAdder(..)`함수의 `x` 파라미터 클로저를 가지는
// 내부 `add()`함수에 대한 참조를 갖습니다.
var plusTen = makeAdder( 10 );

plusOne( 3 );		// 4  <-- 1 + 3
plusOne( 41 );		// 42 <-- 1 + 41

plusTen( 13 );		// 23 <-- 10 + 13
```

어떻게 코드가 동작하는지 자세히 살펴보면:

1. `makeAdder(1)`를 호출할 때, `x`를 `1`이라고 기억하는 내부 `add(..)`에 대한 참조를 돌려받습니다. 우리는 이 함수 참조 `plusOne(..)`을 호출합니다.
2. `makeAdder(10)`를 호출할 때, `x`를 `10`이라고 기억하는 내부 `add(..)`에 대한 참조를 돌려받습니다. 우리는 이 함수 참조 `plusTen(..)`을 호출합니다.
3. `plusOne(3)`을 호출할 때, 함수는 `3`(내부 `y`)을 `1`(`x`로 기억된)과 더하고, `4`를 결괏값으로 받습니다.
4. `plusOne(13)`을 호출할 때, 함수는 `13`(내부 `y`)을 `10`(`x`로 기억된)과 더하고, `23`을 결괏값으로 받습니다.

만약 처음에 이상해 보이고 헷갈리시면 걱정하지 마세요 —- 처음에는 그럴 수도 있습니다! 완전히 이해하는 데에는 수많은 연습이 필요할 것입니다.

하지만 저를 믿으십시오, 그러면 프로그래밍에서 가장 강력하고 유용한 기술 중 하나가 될 것입니다. 클로져에 대해서 충분히 생각해보는 것은 확실히 가치가 있습니다. 다음 섹션에서는, 클로져를 가지고 더 실습해 볼 것입니다.

#### 모듈

자바스크립트에서 가장 일반적 클로져 사용은 모듈 패턴입니다. 모듈은 외부 세계로부터 은닉된 수행 세부사항(변수, 함수)과 외부에서 접근 가능한 공개 API를 정의할 수 있게 합니다.

생각해보세요:

```js
function User(){
	var username, password;

	function doLogin(user,pw) {
		username = user;
		password = pw;

		// 나머지 로그인 과정을 수행
	}

	var publicAPI = {
		login: doLogin
	};

	return publicAPI;
}

// ‘User’ 모듈 인스턴스 만들기
var fred = User();

fred.login( "fred", "12Battery34!" );
```

‘User()’함수는 변수 `username`과 `password`를 가지고 있는 외부 스코프 역할과 내부 `doLogin()`함수 스코프 역할을 합니다. 이러한 것들은 전부 외부 세계에서 접근할 수 없는 `User` 모듈의 은닉화된 내부 사항입니다.

**경고:** 대부분 독자들에게 더 일반적 일지라도, 우리는 여기서 의도적으로 `new User()`를 호출하지 않을 것입니다. `User()`는 인스턴스화되는 클래스가 아니라 단지 일반 함수이기 때문에, 그냥 일반적으로 호출될 것입니다. `new`를 사용하는 것은 적절하지 못하고 사실 자원 낭비일 것입니다.

`User()`를 실행하는 것은 `User` 모듈의 *인스턴스*를 생성합니다. —- 완전히 새로운 스코프가 생성되고, 각 내부 변수/함수들에 대한 완전히 새로운 복사가 이루어집니다. 우리는 이 인스턴스를 `fred`에 할당을 했습니다. 만약에 `User()`를 다시 실행하게 되면, 우리는 `fred`와는 완전히 독립적인 새로운 인스턴스를 얻게 됩니다.

내부 `doLogin()` 함수는 `username`과 `password`에 대해 클로져를 가지고, 이는 `User()`함수 실행이 끝난 이후에도 그 변수들에 접근 가능하다는 것을 의미합니다.

`publicAPI`는 `login`이라는 하나의 프로퍼티/메소드를 가지고 있는 객체 입니다. 이 객체는 내부 `doLogin()`함수를 참조합니다. `User()`로부터 `publicAPI`를 반환할 때, 이 객체는 `fred`라는 인스턴스가 됩니다.

이 시점에서, 외부 `User()` 함수는 실행이 종료됩니다. 일반적으로, `username`과 `password` 변수는 사라진다고 생각할 것입니다. 하지만 그렇지 않습니다. 왜냐하면, `login()` 함수에 변수들을 기억하는 클로져가 있기 때문입니다.

이러한 이유로 우리는 `fred.login(..)` —- 내부 `doLogin(..)`을 호출하는 것과 같은 -— 을 호출할 수 있고, 내부변수 `username`과 `password`에 접근할 수 있습니다.

이렇게 클로져와 모듈 패턴을 잠깐 살펴볼 기회가 있었습니다. 이중 몇몇은 여전히 헷갈릴 것입니다. 괜찮습니다! 머리속에 정리되는 데에 조금의 노력이 필요합니다.

더 깊은 내용에 대해 알고 싶으시면 이 시리즈의 *Scope & Closures*를 읽어보세요.

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
