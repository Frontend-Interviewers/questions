# this ์ง๋ฌธ

์์ฑ: https://www.notion.so/this-5d8dc47e2a714b23bc7e44779ff36fa2

## 1. ๐คย this๊ฐ ๋ฌด์์ธ๊ฐ์?

์์ ์ด ์ํ ๊ฐ์ฒด ๋๋ ์์ ์ด ์์ฑํ  ์ธ์คํด์ค๋ฅผ ๊ฐ๋ฆฌํค๋ ์๊ธฐ ์ฐธ์กฐ ๋ณ์(self-reference variable).

## 2. ๐คย  ์ ์ญ ๊ณต๊ฐ์์ this๋ ๋ฌด์์ ๊ฐ๋ฆฌํฌ๊น์?

์ ์ญ ๊ณต๊ฐ์์ this๋ ์ ์ญ ๊ฐ์ฒด๋ฅผ ๊ฐ๋ฆฌํต๋๋ค.

๋ธ๋ผ์ฐ์  ํ๊ฒฝ์์๋ `window`

๋ธ๋ ํ๊ฒฝ์์๋ `global` 

ECMA2020๋ถํฐ๋ `globalThis` ๋ก ํตํฉ ๋์ด ์ฌ์ฉํ  ์ ์์ต๋๋ค.

[globalThis - JavaScript | MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/globalThis)

## 3. ๐คย  ๋ฉ์๋๋ก ํธ์ถํ  ๋ ๊ทธ ๋ฉ์๋ ์์์ this๋ ๋ฌด์์ ๊ฐ๋ฆฌํฌ๊น์?

ํธ์ถํ ์ฃผ์ฒด์ ๋ํ ์ ๋ณด๊ฐ this์ ๋ด๊ธฐ๊ฒ ๋ฉ๋๋ค.

```tsx
Object.method // ์ด๋ฐ์์ผ๋ก ํธ์ถํ๋ฉด Object๊ฐ this๊ฐ ๋ฉ๋๋ค.
```

## 4. ๐คย  ์ผ๋ฐ ํจ์๋ก ํธ์ถํ  ๋ ๊ทธ ํจ์์์์ this๋ ๋ฌด์์ ๊ฐ๋ฆฌํฌ๊น์?

์ผ๋ฐ ํจ์ ์์์์ this๋ ์ ์ญ ๊ฐ์ฒด๋ฅผ ๊ฐ๋ฆฌํต๋๋ค.

## 5. ๐คย  ์์ฑ์ ํจ์ ๋ด๋ถ์์์ this๋ ๋ฌด์์ ๊ฐ๋ฆฌํฌ๊น์?

์์ฑ์ ํจ์ ๋ด๋ถ์์์ this๋ ์์ฑ์ ํจ์๊ฐ ๋ง๋ค ๊ตฌ์ฒด์ ์ธ ์ธ์คํด์ค ์์ ์ด this๊ฐ ๋ฉ๋๋ค.

## 6. ๐ค์ผ๋ฐํจ์์ this ์ ํ์ดํํจ์ this์ ์ฐจ์ด.

์ผ๋ฐํจ์์์์ this ๋ ์ ์ญ ๊ฐ์ฒด๋ฅผ ๊ฐ๋ฅดํจ๋ค.

ํ์ดํ ํจ์์ this ๋ ์์ ์ค์ฝํ์ this๋ฅผ ๊ฐ๋ฅดํจ๋ค.

- ์์
    
    ```jsx
    let person = {
        name: "youngjin",
        getName: function () {
            console.log(this) // person ๊ฐ์ฒด๋ฅผ ๊ฐ๋ฆฌํจ๋ค
            setTimeout(() => {
              console.log(this) // person๊ฐ์ฒด๋ฅผ ๊ฐ๋ฆฌํจ๋ค
              console.log(this.name); // youngjin ์ ์ถ๋ ฅํ๋ค.
          }, 1000);
      }
    }
    
    person.getName();
    ```
    

## 7. ๐คย use strict ๋ชจ๋์์์ this

use strict ๋ชจ๋์์ ์ผ๋ฐ ํจ์์์์ this ๋ undefined ๊ฐ ๋ฐ์ธ๋ฉ๋๋ค.

์ฌ์ค ์ผ๋ฐ ํจ์์์ this๋ฅผ ์ฐธ์กฐํ๋ ๊ฒ์ ์กฐ๊ธ ์ด์ํ ํ๋, ์ฐ๋ฆฌ์ ๋ผ๋ฆฌ์ ์ธ ํ๋์๋ ๋ฉ๋ค๊ณ  ํฉ๋๋ค. ๋ณดํต this๋ ์๊ธฐ ์ฐธ์กฐ ๋ณ์์ด๋๊น ๊ฐ์ฒด๋ฅผ ์ฐธ์กฐํ๋๊ฒ ์ผ๋ฐ์ ์ธ ์ํฉ์ธ๋ฐ ์ผ๋ฐ ํจ์์ this๋ฅผ ์ฐพ๋๋ค๋๊ฑด ๋ผ๋ฆฌ์ ์ด์ง ์์์ `use strict`๋ฅผ ์ฌ์ฉํ๊ฒ ๋๋ฉด ์ด์ํ ์ํฉ์ ์์ ์ `undefined`๋ฅผ ๋ฐํํ๋ค๊ณ  ํ๋ค์.

## 8. ๐คย ์๋ ์ฝ๋๋ฅผ ์คํํ๋ฉด ๋ฌด์์ด ์ถ๋ ฅ๋ ๊น์. ๊ทธ ์ด์ ๋ ๋ฌด์์ผ๊น์

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

- ํด์ค
    - ์ ๋ต
        - band undefined roto play start
    - ํด์ค
        - play ํจ์์ this ๋ด์๋ name ์ด ์๊ธฐ ๋๋ฌธ์ undefined ๊ฐ ์ถ๋ ฅ
    - ํด๊ฒฐ๋ฒ
    
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
    

## 9. ๐คย ์๋ ์ฝ๋๋ฅผ ์คํํ๋ฉด ๋ฌด์์ด ์ถ๋ ฅ๋ ๊น์

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

- ํด์ค
    - ์ ๋ต
    
    ```jsx
    undefined // this ๊ฐ obj์ ๋ฐ์ธ๋ฉ ๋๋๋ฐ b๋ณ์๊ฐ ์๊ธฐ ๋๋ฌธ
    undefined // this ๊ฐ obj์ ๋ฐ์ธ๋ฉ ๋๋๋ฐ b๋ณ์๊ฐ ์๊ธฐ ๋๋ฌธ
    100 // ์ ์ญ๊ฐ์ฒด์ ๋ฐ์ธ๋ฉ
    ```
    

## 10. ๐คย **`this`๊ฐ JavaScript์์ ์ด๋ป๊ฒ ์๋ํ๋์ง ์ค๋ชํ์ธ์.**

1. ํจ์๋ฅผ ํธ์ถํ  ๋ย `new`ย ํค์๋๋ฅผ ์ฌ์ฉํ๋ ๊ฒฝ์ฐ, ํจ์ ๋ด๋ถ์ ์๋ย `this`๋ ์์ ํ ์๋ก์ด ๊ฐ์ฒด์๋๋ค.
2. `apply`,ย `call`,ย `bind`๊ฐ ํจ์์ ํธ์ถ/์์ฑ์ ์ฌ์ฉ๋๋ ๊ฒฝ์ฐ, ํจ์ ๋ด์ย `this`๋ ์ธ์๋ก ์ ๋ฌ๋ ๊ฐ์ฒด์๋๋ค.
3. `obj.method()`์ ๊ฐ์ด ํจ์๋ฅผ ๋ฉ์๋๋ก ํธ์ถํ๋ ๊ฒฝ์ฐ,ย `this`๋ ํจ์๊ฐ ํ๋กํผํฐ์ธ ๊ฐ์ฒด์๋๋ค.
4. ํจ์๊ฐ ์์ ํจ์๋ก ํธ์ถ๋๋ ๊ฒฝ์ฐ, ์ฆ, ์์ ์กฐ๊ฑด ์์ด ํธ์ถ๋๋ ๊ฒฝ์ฐย `this`๋ ์ ์ญ ๊ฐ์ฒด์๋๋ค. ๋ธ๋ผ์ฐ์ ์์๋ย `window`ย ๊ฐ์ฒด์๋๋ค. ์๊ฒฉ ๋ชจ๋(`'use strict'`) ์ผ ๊ฒฝ์ฐ,ย `this`๋ ์ ์ญ ๊ฐ์ฒด ๋์ ย `undefined`๊ฐ ๋ฉ๋๋ค.
5. ์์ ๊ท์น ์ค ๋ค์๊ฐ ์ ์ฉ๋๋ฉด ๋ ์์ ๊ท์น์ด ์น๋ฆฌํ๊ณ ย `this`๊ฐ์ ์ค์ ํฉ๋๋ค.
6. ํจ์๊ฐ ES2015 ํ์ดํ ํจ์์ธ ๊ฒฝ์ฐ ์์ ๋ชจ๋  ๊ท์น์ ๋ฌด์ํ๊ณ  ์์ฑ๋ ์์ ์์ ์ฃผ๋ณ ์ค์ฝํ์ย `this`๊ฐ์ ๋ฐ์ต๋๋ค.

## 11. ๐ค ์๋ ์ฝ๋๋ฅผ ์คํํ๋ฉด ๋ฌด์์ด ์ถ๋ ฅ๋ ๊น์?

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

- ํด์ค
    
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
    

## 12. ๐ค ์๋ ์ฝ๋๋ฅผ ์คํํ๋ฉด ๋ฌด์์ด ์ถ๋ ฅ๋ ๊น์?

```jsx
var obj = {
	a: console.log(this),  		// --- โ 
	fn: function() {
		console.log(this); 		// --- โก
		function fn() {
			console.log(this); 	// --- โข
		}
		fn();
	}
}
obj.a;
obj.fn();
```

- ์ ๋ต
    
    ```jsx
    โ  window
    โก obj
    โข window
    ```
    
    - ํ์ด
        - `obj.a()`๋ย **obj.a = console.log(this)**์ ๊ฐ๋ค. (โ  window)
        - `obj.fn()`์ย `this`๋ ์ ์ญ์์ obj๋ก ๋ฐ์ธ๋ฉ ๋์๋ค. (โก obj)
        - `fn()`์ย `this`๋ ์ ์ญ์ ๊ฐ๋ฆฌํจ๋ค. (โข window)
    - ์ ์ญ : window
    - ํจ์ ๋ด๋ถํจ์๋ฅผ ์คํํ๊ฒ ๋๋ฉด ๋ง์ง๋ง .์์ this๋ก ํจ์์ ์ ๋ฌํ๋ค.( a.b.c.fn(); โ c๋ฅผ this๋ก ์ ๋ฌ )
        - .์์ ์๋ฌด๊ฒ๋ ์๋ ๊ฒฝ์ฐ, ์ ์ญ์ ์ ๋ฌํ๋ค.
