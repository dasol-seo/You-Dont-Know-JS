
## Functions

전화 가게 직원은 아마도 세금과 최종결제 금액에 대한 계산에 대해 책임을 질 필요가 없습니다. 그 일에 그녀는 한번 정의할 필요가 있고 여러번이고 다시 사용합니다. 확률상 회사는 그 함수가 내장되어있눈 계산기 포스기(컴퓨터, 태블릿, 그외) 가 있을것입니다.

비슷하게 당신의 프로그램을 반복에 반복이되는것 대신에 거의 정확하게 코드가 재사용이 가능한 부분들을 분리하기를 원할것이다. 이것이 '함수를 정의하는 방법이다.

함수는 이름으로 “호출(called)”되며 그 안의 코드는 호출될때마다 작동되는 한 부분이다. 
고려사항:

```js
function printAmount() {
	console.log( amount.toFixed( 2 ) );
}

var amount = 99.99;

printAmount(); // "99.99"

amount = amount * 2;

printAmount(); // "199.98"
```

함수는 추가적으로 인자들(매개변수라고도 한다)을 가질수 있다. 값이 들어오면 함수는 추가적으로 값을 다시 리턴한다.

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

`printAmount(..)` 함수는 `amt` 매개변수를 가진다. `formatAmount()`함수는 값을 리턴한다. 당연히 두가지가 한 함수에 쓰일수 있다.

여러번 호출하는 코드 함수는 종종 쓰는 코드에 쓰인다. 하지만 그 함수들은 컬랙션 안에 한번만 불릴지라도 유용하다
고려사항:

```js
const TAX_RATE = 0.08;

function calculateFinalPurchaseAmount(amt) {
	// 세금이 합쳐진 새로운 금액의 계산
	amt = amt + (amt * TAX_RATE);

	// 리턴된 새로운 금액
	return amt;
}

var amount = 99.99;

amount = calculateFinalPurchaseAmount( amount );

console.log( amount.toFixed( 2 ) );		// "107.99"
```
비록 "calculateFinalPurchaseAmount()"가 한번 호출될지라도 분리된 함수라고 불리어 지는 코드들 일지라도 함수로 불리어지는 명확하게 논리적인 함수가 사용된다. 만약 그 함수가 더 '-----' 장점은 더욱더 확고해집니다.
Although `calculateFinalPurchaseAmount(..)` is only called once, organizing its behavior into a separate named function makes the code that uses its logic (the `amount = calculateFinal...` statement) cleaner. If the function had more statements in it, the benefits would be even more pronounced.

### Scope
스코프

핸드폰 가계를 가서 점원에게 핸드폰 기종을 물어봤을때 그 기종이 없다면 그 점원은 당신에게 핸드폰을 팔수 없을것 입니다. 그 점원은 그 가게의 재고만 접근 할수 있기때문입니다. 당신은 다른 가게에 가서 당신이 원하는 기종의 핸드폰이 있는지 찾아봐야 합니다. 

프로그래밍도 이와같은 개념을 가지고 있습니다. *스코프(scope)* (기술적으로 말하자면 *lexical scope*). 자바스크립트 안에서 각각의 함수는 각자의 스코프를 가지고 있습니다. 스코프는 기본적으로 변수의 컬랙션이며 그 변수에 이름으로 어떻게 접근 하는가 하는 규칙들이 있습니다. 함수의 스코프에 속한 변수만 접근 가능한 코드만 함수 안에 있습니다.

변수 이름은 같은 스코프 안이라면 특별해야 합니다. 즉 각기 다른 변수 `a`가 서로의 옆자리에 앉을수 없습니다. 하지만 같은 변수의 이름일지라도 다른 스코프에 속해 있다면 가능합니다.

```js
function one() {
	// `a`는 one 함수에만 속해 있습니다.
	var a = 1;
	console.log( a );
}

function two() {
	// `a`는 two 함수에만 속해 있습니다.
	var a = 2;
	console.log( a );
}

one();		// 1
two();		// 2
```
또한 스코프는 다른 스코프안에 겹쳐 질수 있습니다. 마치 광대가 생일 파티에서 풍선 속에 풍선을 부는 것처럼요. 만약 한 스코프가 다른 스코프안에 겹쳐 진다면 가장 깊숙히 있는 스코프는 다른 스코프의 변수에 접근할수 있습니다.

고려사항:

```js
function outer() {
	var a = 1;

	function inner() {
		var b = 2;

		// `a` and `b`에 접근이 가능합니다.
		console.log( a + b );	// 3
	}

	inner();

	// `a`만 접근 할수 있습니다.
	console.log( a );			// 1
}

outer();
```
렉시컬 스코프(Lexical scope: 정적스코프)의 규칙은 한 스코프안에 있는 코드들은 다른 스코프 또는 밖에 있는 어느 스코프든 접근이 가능합니다. 그리서 코드안에 `inner()`함수는 두 변수 `a`와 `b`에 접근이 가능하지만 `outer()` 함수는 `a`만 가능합니다. 
`b`에 접근이 안되는 이유는 `inner()`함수 안에만 있기 때문입니다.

이전 코드 스니펫에 다시 돌아 가봅시다: 

```js
const TAX_RATE = 0.08;

function calculateFinalPurchaseAmount(amt) {
	// 계산된 세금이 포함된 새로운 금액
	amt = amt + (amt * TAX_RATE);

	// 새로운 금액을 리턴
	return amt;
}
```
`TAX_RATE` 정수(변수)는 안에 있는 비록 우리가 그안을 통과할수 없지만 렉시컬 스코프이기 때문에 `calculateFinalPurchaseAmount(..)` 함수에 접근이 가능합니다.

**Note:** 렉시컬 스코프에 관해 더 알고 싶으시면 시리즈중 *Scope & Closures* 에 첫번째의 세번째 챕터를 참고 하면 됩니다.

## Practice 연습

프로그래밍을 배우면서 연습을 대체할 대안은 절대 없습니다. 제가 명확하게 글을 쓴다 할지라도 그것이 당신을 프로그래머로 만들수는 없습니다. 

앞에 언급한 글을 되새기면서 이 챕터에서 우리가 배운 것들을 연습을 해봅시다. 제가 "필수 사항"을 제시 하면 그걸 시도해 주세요. 그다음 아래의 코드들을 보면서 제가 어떻게 접근했는지를 참고해 보세요.

* 핸드폰의 총 구매가격을 계산하는 코드를 써보세요. 당신이 은행계좌에 가지고 있는 돈이 떨어질때까지 핸드폰 구매를 계속 할것입니다.(힌트: loop!) 각각의 핸드폰에 악세서리 또한 당신의 허용하는 구매 한계치까지 구매할것입니다.

* 당신이 구매한 금액이 계산된후 세금을 더합니다. 아마도 형식 갖추어진 계산된 구매한 금액을 출력합니다. 
* 마지막으로 당신의 은행 잔고를 확인하며 더 구매를 할수 있는지 확인합니다. 
* "tax rate(세율)", "phone price(핸드폰 가격)", "accessory price(액세서사 가격)", "spending threshold(한도 금액)," "bank account balance(은행 잔고)" 등의 변수를 설정합니다.
* 세금을 계산하기위한 함수를 정의합니다. 또한 금액은 "$"와 소수점 두자리 까지 정도로 형식화 합니다. 
* **보너스 챌린지:** input를 포함 해보세요. 예전에는 `prompt(..)`가 "Input"를 대신하였습니다. 예를들어 사용자의 은행잔고를 즉시 보여줄수 있는 Input. 창의력을 더한 즐거운 코딩을 해보세요!

좋습니다. 한번 시도 해봐요! 당신이 할수 있는 만큼 해볼때 까지, 제코드를 보지 마시고 시도 해보세요!

**Note:**  이 자바스크립트 책은 자바스크립트 언어로 연습문제 풀이가 있습니다. 다른 언어로 해보는게 편하다면 다른언어로 해도 됩니다.

여기 해당 문제의 저의 솔루션 입니다.: 

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

// 잔고가 있을때 까지 핸드폰을 산다
while (amount < bank_balance) {
	// 새로운 폰을 산다!
	amount = amount + PHONE_PRICE;

	// 액세서리까지 할수 있을까?
	if (amount < SPENDING_THRESHOLD) {
		amount = amount + ACCESSORY_PRICE;
	}
}

// 정부에게 돈을 내는것 또한 잊지말자!
amount = amount + calculateTax( amount );

console.log(
	"Your purchase: " + formatAmount( amount )
);
// 구매 금액: $334.76

// 정말 해당금액을 낼수 있을까?
if (amount > bank_balance) {
	console.log(
		"You can't afford this purchase. :("
	);
}
// 당신은 이 금액을 감당할수 없습니다. :(
```
**Note:** 이 자바스크립트 프로그램을 실행시키는 가장 간단한 방법은 당신의 인터넷 브라우저 개발자 콘솔에 코드를 입력하는 것입니다.
어떻게 했나요? 제 코드를 본후에 다시 해보는 것은 그렇게 상처가 될일이 아닐 것입니다. 또한 몇개의 변수를 변경해서 다른 값으로 이 프로그램이 어떻게 실행되는지 시도해 보세요. 

## 리뷰

프로그래밍을 배우는것은 복잡하거나 엄청난 과정이 있어야 하는건 아닙니다. 몇개의 기본컨셉이 당신의 머리에 들어가 있을 뿐입니다.

이 행위는 마치 건물의 블럭과 같습니다. 높은 타워를 짓는다고 생각해보세요. 당신은 벽돌을 층층히 위로 쌓는것부터 시작할것입니다. 프로그래밍도 이와 같습니다. 여기 가장 기본이 되는 몇개의 빌딩 블럭이 있습니다. 

* 값에 대한 작업을 수행하는 *연산자*
* 예를들어 `숫자` 나 `문자열`의 결과값 등 같이 다른 종류에 작업을 실행하는 값과 *타입*
* 당신의 프로그램이 실행되는 동안 데이터를 저장하는 곳(*state* 라고도 한다)을 위한 *변수*
* `if` 조건문과 같은 결정을 할수 있는 *조건*
* 조건이 참이 될때까지 반복해서 작업을 하는 *루프*
* 논리적이고 제 사용이 가능한 덩어리가 정리될수 있는 *함수*


주석은 더 읽기 쉽게 쓸수 있도록 하는 효율적인 방법중 하나입니다. 주석은 당신의 프로그램이 쉽게 이해되어 지고, 유지보수를 하고 나중에 문제가 발생할때 고칠 수 있도록 합니다.

마지막으로 연습의 힘을 무시 하지 마세요. 어떻게 코드를 쓰는지를 배우려고 할때 가장 좋은 방법은 코드를 쓰는 것입니다.

당신은 잘하고 있습니다.
당신이 어떻게 코드 쓰는 법을 배우는 것을 잘 해나가고 있는것이 흥분됩니다. 앞으로도 계속 잘해나가길 바랍니다. 
다른 초보자 프로그래밍 자료들(책, 블로그, 온라인 코스 등등) 또한 찾아보는 것도 잊지 마세요. 간단한 소개 정도 이지만 이챕터와 이 책을 좋은 시작입니다.

다음 챕터는 이챕터에서 다뤘던 많은 컨셉들을 설명할것입니다. 나머지 시리즈 전체에 걸쳐 깊고 자세히 다뤄질 가장 주요한 토픽이 자바스크립트의 특유의 관점에 대해서 다뤄질 것입니다.
