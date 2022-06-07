# 데이터 타입

## 1. 🤔 JS에서 데이터의 종류는 어떤게 있을까요?

크게 두가지로 분리할 수 있습니다. 원시형(기본형)과 참조형

원시형에는 number, string, boolean, null, undefined, Symbol이 존재하고

참조형에는 Object, Array, Function, Date, RegExp 등이 있습니다.

## 2. 🤔 만약 변수에 원시값 데이터를 할당하게 되면 어떤 일이 일어날까요? 메모리 영역을 중심으로 설명해 주세요.

```tsx
var a = '123';
```

메모리 영역은 크게 `변수 영역`과 `데이터 영역`으로 분리할 수 있습니다.

1. 변수 영역에 빈공간을 확보하고
2. 확보한 공간의 식별자를 a로 지정합니다.
3. 데이터 영역의 빈 공간에  ‘123’을 저장하고
4. 데이터 영역의 주소값을 식별자 a의 값에 대입 합니다.

> **이 과정은 모두 Call Stack에서 이루어짐**
> 

## 3. 🤔  변수와 상수 불변값은 어떤 차이점들이 있나요?

변수와 상수를 구분 짓는 변경 가능성은 **변수 영역의 메모리** 입니다.

한 번 데이터 할당이 이루어진 변수 공간에 다른 데이터를 재할당 할 수 있는지 여부로 나뉘고

불변값의 경우 데이터 영역의 메모리를 재할당 할 수 있는지 여부로 불변값을 구분 합니다.

## 4. 🤔  만약 변수에 참조형 데이터를 할당하게 되면 어떤 일이 일어날까요? 메모리 영역을 중심으로 설명해 주세요.

```tsx
var obj1 = {
	a: 1,
	b: 'bbb'
};
```

1. 변수 영역의 빈공간을 확보하고 확보된 공간의 식별자를 obj1으로 지정 합니다.
2. 값 자체가 객체 이므로 내부 프로퍼티 저장을 위한 별도의 변수 영역을 마련하고 프로퍼티 개수에 따라 빈공간을 확보 합니다.
3. 별도의 변수 영역에 식별자로 프로퍼티의 key를 할당 합니다.
4. 데이터 영역에 프로퍼티 value에 대해 저장하고 주소값을 별도의 변수 영역의 값에 할당 합니다.

- `객체안의 값이 다시 재할당이 되면 어떤 일이 일어나나요?`
    
    어떤 데이터에 대해 자신의 주소를 참조하는 변수의 개수를  `참조 카운트` 라고 하는데
    
    참조 카운트는 사용을 안하게 되면 0으로 변하게 됩니다. 
    
    프로퍼티 값이 재할당이 되면 이전 프로퍼티 값에 대한 참조 카운트는 0이 되고
    
    참조 카운트가 0이 되면 가비지 컬렉터의 수거 대상이 됩니다.
    
    이후 GC 스케쥴에 따라서 사라지게 됩니다.
    

## 5. 🤔 undefined와 null의 차이점을 알려주세요

두 개 다 “비어있다" 라는 의미를 가지고 있습니다.

undefined는 자바스크립트 엔진 자체에서 반환해주는 값입니다.

1. 변수 선언만 하고 할당하지 않았을 때 (var)
2. 객체 내부에 존재하지 않는 프로퍼티에 접근하려고 할 때
3. return문이 없거나 호출되지 않은 함수 실행 결과

위와 같은 상황에서 undefined를 자바스크립트 엔진이 내뱉게 되어있습니다.

자바스크립트 코딩을 하면서 “없다" 라는 것을 명시적으로 해주고 싶다면 `null`을 사용하면 됩니다.

이렇게 하면 `undefined`는 자바스크립트 엔진에서 뱉어줬다는 것을 알 수 있기 때문에 위의 세 가지 경우를 추리하면서 대처가 가능합니다.

## 6. 🤔 얕은 복사와 깊은 복사에 대해서 설명해주세요

### 얕은 복사

객체를 복사할 때 한 단계 아래의 메모리 주소까지만 복사를 하는 것 입니다. 그래서 해당 프로퍼티에 대해서 원본과 사본이 모두 동일한 참조형 데이터 주소를 가리키게 됩니다. 그래서 사본을 바꾸면 원본도 바뀌고 원본을 바꾸면 사본도 바뀝니다.

### 깊은 복사

얕은 복사는 한 단계 아래의 메모리 주소까지만 복사를 하지만, 깊은 복사는 깊은 곳의 모든 참조형 데이터에 대해서 일일이 재귀적으로 복사해서 완전히 새로운 데이터를 만들어내는 것, 원본에 대해서 참조를 하지 않는 것을 말합니다.

얕은 복사와 다르게 모든 프로퍼티에 대해서 완전히 새로운 데이터를 만들어 내야 합니다. 참조형 데이터는 다시 그 내부의 프로퍼티들을 계속해서 복사를 수행해야 하는데 이렇게 복사하는 과정에서 참조형 데이터를 다시 만나면 재귀적으로 복사를 수행해야 깊은 복사가 이뤄집니다.

## 7. 🤔  깊은 복사를 할 수 있는 방법이 무엇이 있을까요?

- 불변성을 지켜주는 라이브러리 (immutable, immer…) 를 사용한다.
- `structuredClone` 을 사용한다. (오페라 안드로이드, 삼성 인터넷 지원 아직 안함)
    - [https://developer.mozilla.org/en-US/docs/Web/API/structuredClone](https://developer.mozilla.org/en-US/docs/Web/API/structuredClone)
- 깊은 복사 함수를 만든다. (옛날 방식)
    
    ```jsx
    const copyObjectDeep = (target) => {
    	let result = {};
    
    	if (typeof target === 'object' && target !== null) {
    		for (const prop in target) {
    			result[prop] = deepObjectCopy(target[prop]);
    		}
    	} else {
    		result = target;
    	}
    
    	return result;
    }
    ```
    
- `JSON.parse()`, `JSON.stringify()` 메서드를 이용한다. (옛날 방식)
    
    ```jsx
    const deepObjectCopyUseJSONMethod = (target) => JSON.parse(JSON.stringify(target));
    ```
    

## 8. 🤔 JSON.parse(), JSON.stringify()를 사용해서 깊은 복사를 이뤄냈을 때 문제점은 무엇일까요?

메서드나 숨겨진 프로퍼티인 `__proto__` (던더프로토)나 `getter/setter` 와 같은 **JSON으로 변경할 수 없는 프로퍼티**들은 모두 무시합니다.

속도가 느립니다.([http://jsben.ch/2KRm3](http://jsben.ch/2KRm3))

그래서 단순 API로 받은 JSON 객체 혹은 순수한 정보를 목적으로 만들어진 JSON 객체를 깊은 복사를 하려고 할 때 사용하면 유용하게 사용할 수 있습니다.

## 9. 🤔 자바스크립트의 call by value에 대해 설명해 주세요.

call by value는 함수의 평가 전략 중 하나로서 함수의 평가 시 인수 값을 새 메모리 영역에 복사하여 해당 함수의 로컬 변수에 바인딩합니다.

자바스크립트는 전부 call by value로 동작합니다.

call by reference는 인자로 객체를 넘기면 참조값의 주소를 복사해서 넘깁니다. 즉 call by value와 다르게 함수의 매개변수와 인수는 동일한 메모리 공간입니다.

(매개변수(parameter)란 함수의 정의에서 전달받은 인수를 함수 내부로 전달하기 위해 사용하는 변수를 의미합니다. 인수(argument)란 함수가 호출될 때 함수의 매개변수에 전달해주는 값을 말합니다.)

- 자세한 내용 : [https://perfectacle.github.io/2017/10/30/js-014-call-by-value-vs-call-by-reference/](https://perfectacle.github.io/2017/10/30/js-014-call-by-value-vs-call-by-reference/)
    - 즉 call by reference에서 function(b){console.log(b)}의 b는 인수와 동일한 메모리 상 객체를 나타냄
    - call by value에서 b는 a와 다른 독립적인 공간의 변수임
        - a를 인자로 넘긴다 가정하자
        - 함수 몸체 안에서 b.a = 1을 하면 인자로 넘어온 객체가 변경됨 ({a:1})
        - b={}; b.b=1; ⇒ {a:1} (참조 잃음) b에는 {b.b:1}

[[프론프엔드 면접 대비] 코어 자바스크립트 : 데이터 타입](https://itchallenger.tistory.com/m/200)

## 10. 🤔 호이스팅에 대해서 설명해주세요.

함수 안에 있는 선언들을 모두 끌어올려서 해당 함수 유효 범위의 최상단에 선언하는 것을 말합니다.
자바스크립트 함수는 실행되기 전에 함수 안에 필요한 변수값들을 모두 모아서 유효 범위의 최상단에 선언합니다.

즉, 함수 내에서 아래쪽에 존재하는 내용 중 필요한 값들을 끌어올리는 것입니다.

[[JavaScript] 호이스팅(Hoisting)이란 - Heee's Development Blog](https://gmlwjd9405.github.io/2019/04/22/javascript-hoisting.html)

## 11. 🤔 let, var, const의 차이점에 대해서 설명해주세요.

var키워드를 사용하여 선언된 변수의 범위는 변수가 생성된 함수로 범위가 지정되며, 함수 외부에서 생성된 경우 전역 객체로 범위가 지정됩니다. `let`그리고 `const` 는 블록 범위를 가집니다 . 즉, 가장 가까운 중괄호(함수, if-else 블록 또는 for 루프) 내에서만 액세스할 수 있습니다.

[JavaScript questions | Front End Interview Handbook](https://www.frontendinterviewhandbook.com/javascript-questions#what-is-the-definition-of-a-higher-order-function)

## 12. 🤔 변수 선언, 초기화, 할당의 차이점에 대해서 설명하세요.

> 변수는 3단계에 걸쳐 생성됩니다.

- 선언 단계 (Declaration phase): 변수 객체에 변수를 등록한다. (변수 객체는 스코프가 참조하는 대상이된다.)
- 초기화 단계(Initialize phase): 변수 객체에 등록된 변수를 메모리에 할당한다. 변수는 undefined 로 초기화된다.
- 할당 단계(Assignment phase): undefined 로 초기화된 변수에 실제값을 할당한다.
- MDN에서는 선언 후 값을 할당하지 않은 변수에 자동으로 undefined 할당된다고 나와있네요.
- [용어 사전 | MDN](https://developer.mozilla.org/ko/docs/Glossary/undefined)

## 13. 🤔 원시 타입과 참조 타입의 대표적인 차이는 무엇인가요?

- **원시타입 (기본형)**
    - 값이 절대 변하지 않는 불변성을 갖고 있기 때문에, 재할당 시 기존 값이 변하는 것처럼 보일지 몰라도 사실 **새로운 메모리에 재할당한 값이 저장되고 변수가 가리키는 메모리가 달라진다.**
    - 값을 통째로 복사해, 변수의 메모리에 담게되기 때문에, 사본의 값이 변경되더라도, 원본에 영향을 주지 않는다.
    - **number, string, boolean, null, undefined, symbol**
- **참조타입**
    - Object의 데이터 자체는 별도의 메모리 공간(heap)에 저장되며, **변수에 할당 시 데이터에 대한 주소(힙(Heap) 메모리의 주소값)이 저장되기 때문에,** 자바스크립트 엔진이 변수가 가지고 있는 **메모리 주소**를 사용해서 변수의 값에 접근하게 된다.
    - 예시  
    	만일 let myArray = []라는 배열을 생성하면 위와 같은 일이 일어난다. 그림에서 볼 수 있듯이 원시타입의 값들은 값들이 직접적으로 저장되어 있지만, myArray (참조타입)는 Heap 메모리의 주소값이 저장되어 있다.

    - 참조 타입의 변수는 실제 데이터가 저장된 **주소를 참조**하기에 참조타입이라고 불린다. 따라서 사본의 객체의 프로퍼티를 변경했을 시 원본에 영향을 줄 수 있다.
    - **object(Map, WeakMap, Set, WeakSet), array, function, date, regexp**

## 14. 🤔 불변 객체가 필요한 이유

- 원본 객체의 가변성을 회피하고, 불변성을 확보하기 위해 내부 속성 변경시마다 매번 새로운 객체를 만들어 재할당하거나 자동으로 새로운 객체를 만드는 도구를 활용한다.
- ex) immutable.js, immer js, immutability-helper 등의 라이브러리.
- ES6의 spread operator, Object.assign 메서드