# this 질문

속성: https://www.notion.so/this-5d8dc47e2a714b23bc7e44779ff36fa2

## 1. 🤔 this가 무엇인가요?

자신이 속한 객체 또는 자신이 생성할 인스턴스를 가리키는 자기 참조 변수(self-reference variable).

## 2. 🤔  전역 공간에서 this는 무엇을 가리킬까요?

전역 공간에서 this는 전역 객체를 가리킵니다.

브라우저 환경에서는 `window`

노드 환경에서는 `global` 

ECMA2020부터는 `globalThis` 로 통합 되어 사용할 수 있습니다.

[globalThis - JavaScript | MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/globalThis)

## 3. 🤔  메서드로 호출할 때 그 메서드 안에서 this는 무엇을 가리킬까요?

호출한 주체에 대한 정보가 this에 담기게 됩니다.

```tsx
Object.method // 이런식으로 호출하면 Object가 this가 됩니다.
```

## 4. 🤔  일반 함수로 호출할 때 그 함수안에서 this는 무엇을 가리킬까요?

일반 함수 안에서의 this는 전역 객체를 가리킵니다.

## 5. 🤔  생성자 함수 내부에서의 this는 무엇을 가리킬까요?

생성자 함수 내부에서의 this는 생성자 함수가 만들 구체적인 인스턴스 자신이 this가 됩니다.

## 6. 🤔일반함수의 this 와 화살표함수 this의 차이.

일반함수에서의 this 는 전역 객체를 가르킨다.

화살표 함수의 this 는 상위 스코프의 this를 가르킨다.

- 예시
    
    ```jsx
    let person = {
        name: "youngjin",
        getName: function () {
            console.log(this) // person 객체를 가리킨다
            setTimeout(() => {
              console.log(this) // person객체를 가리킨다
              console.log(this.name); // youngjin 을 출력한다.
          }, 1000);
      }
    }
    
    person.getName();
    ```
    

## 7. 🤔 use strict 모드에서의 this

use strict 모드에서 일반 함수에서의 this 는 undefined 가 바인딩된다.

사실 일반 함수에서 this를 참조하는 것은 조금 이상한 행동, 우리의 논리적인 행동에는 멀다고 합니다. 보통 this는 자기 참조 변수이니까 객체를 참조하는게 일반적인 상황인데 일반 함수의 this를 찾는다는건 논리적이지 않아서 `use strict`를 사용하게 되면 이상한 상황을 없애서 `undefined`를 반환한다고 하네요.

## 8. 🤔 아래 코드를 실행하면 무엇이 출력될까요. 그 이유는 무엇일까요

```jsx
var idiots ={
	name : 'idiots',
	genre : 'punk rock',
	members :{
		roto : {
			memberName : 'roto',
			play : function(){
				console.log(`band ${this.name} ${this.memberName} play start.`)
			}
		}
	}
}

idiots.members.roto.play();
```

- 해설
    - 정답
        - band undefined roto play start
    - 해설
        - play 함수의 this 내에는 name 이 없기 때문에 undefined 가 출력
    - 해결법
    
    ```jsx
    var idiots = {
      name: 'idiots',
      genre: 'punk rock',
      members: {
        roto: {
          memberName: 'roto',
          play: function() {
            console.log(`band ${idiots.name} ${this.memberName} play start.`)
          } 
        }
      }
    }
    ```
    

## 9. 🤔 아래 코드를 실행하면 무엇이 출력될까요

```jsx
var b = 100;

function test() {
	console.log(this.b);
}

var obj = {
	a: 20,
	func1 : test,
	func2 : function(){
		console.log(this.b);
	}
}

obj.func1();
obj.func2();

this.gFunc1 = obj.func1;
this.gFunc1();
```

- 해설
    - 정답
    
    ```jsx
    undefined // this 가 obj에 바인딩 됐는데 b변수가 없기 때문
    undefined // this 가 obj에 바인딩 됐는데 b변수가 없기 때문
    100 // 전역객체에 바인딩
    ```
    

## 10. 🤔 **`this`가 JavaScript에서 어떻게 작동하는지 설명하세요.**

1. 함수를 호출할 때 `new` 키워드를 사용하는 경우, 함수 내부에 있는 `this`는 완전히 새로운 객체입니다.
2. `apply`, `call`, `bind`가 함수의 호출/생성에 사용되는 경우, 함수 내의 `this`는 인수로 전달된 객체입니다.
3. `obj.method()`와 같이 함수를 메서드로 호출하는 경우, `this`는 함수가 프로퍼티인 객체입니다.
4. 함수가 자유함수로 호출되는 경우, 즉, 위의 조건 없이 호출되는 경우 `this`는 전역 객체입니다. 브라우저에서는 `window` 객체입니다. 엄격 모드(`'use strict'`) 일 경우, `this`는 전역 객체 대신 `undefined`가 됩니다.
5. 위의 규칙 중 다수가 적용되면 더 상위 규칙이 승리하고 `this`값을 설정합니다.
6. 함수가 ES2015 화살표 함수인 경우 위의 모든 규칙을 무시하고 생성된 시점에서 주변 스코프의 `this`값을 받습니다.

## 11. 🤔 아래 코드를 실행하면 무엇이 출력될까요?

```jsx
console.log(1,this);

setTimeout(() => {
  console.log(2,this);
}, 1000);

class Foo {
  methodA() {
    console.log(3,this);

    setTimeout(() => {
      console.log(4,this);
    }, 1000);
  }

  methodB() {
    console.log(5,this);

    setTimeout(function () {
      console.log(6,this);
    }, 1000);
  }
}

const foo = new Foo();
foo.methodA();
foo.methodB();

document.addEventListener('click', function () {
  console.log(this);
});
```

- 해설
    
    ```jsx
    console.log(1,this); // 1, window
    
    setTimeout(() => {
      console.log(2,this); // 2, window 
    }, 1000);
    
    class Foo {
      methodA() {
        console.log(3,this); // 3, Foo
    
        setTimeout(() => {
          console.log(4,this); // 4, Foo
        }, 1000);
      }
    
      methodB() {
        console.log(5,this); // 5, Foo
    
        setTimeout(function() {
          console.log(6,this); // 6, window
        }, 1000);
      }
    }
    const foo = new Foo();
    foo.methodA();
    foo.methodB();
    
    document.addEventListener('click', function () {
      console.log(this); // document
    });
    ```
    

## 12. 🤔 아래 코드를 실행하면 무엇이 출력될까요?

```jsx
var obj = {
	a: console.log(this),  		// --- ①
	fn: function() {
		console.log(this); 		// --- ②
		function fn() {
			console.log(this); 	// --- ③
		}
		fn();
	}
}
obj.a;
obj.fn();
```

- 정답
    
    ```jsx
    ① window
    ② obj
    ③ window
    ```
    
    - 풀이
        - `obj.a()`는 **obj.a = console.log(this)**와 같다. (① window)
        - `obj.fn()`의 `this`는 전역에서 obj로 바인딩 되었다. (② obj)
        - `fn()`의 `this`는 전역을 가리킨다. (③ window)
    - 전역 : window
    - 함수 내부함수를 실행하게 되면 마지막 .앞을 this로 함수에 전달한다.( a.b.c.fn(); → c를 this로 전달 )
        - .앞에 아무것도 없는 경우, 전역을 전달한다.
