# Typescript Style Guide



[TOC]

## 들여쓰기 (Indentation)

- 들여쓰기 단위를 `2칸`을 사용합니다.
- 들여쓰기에 탭을 사용하지 않고 스페이스(space)를 사용합니다.





## 라인 길이(Line length)

- 라인은 140글자를 넘지 않습니다.
- 명령문이 한 줄에 140자를 넘으면 쉼표 나 붙임 연산자를 이용해서 줄을 내려 줍니다.





## 주석 (Comments)

### 일반 주석

- 주석 강력히 권장합니다. 의견을 읽고 주어진 코드 블록의 의도를 이해 할 수 있도록 기술 합니다.

```typescript
// 인덱스의 시작은 1부터 시작.
let startIndex = 1;
```

* 모든 공개 함수(public functions)에는 [JSDoc](https://jsdoc.app/) 스타일의 주석( `/**.. */`)을 달아 줍니다.

```typescript
/**
 * 인사말을 가져온다.
 *
 * @param 사용자 이름
 */
function getGreeting(name: string): string {
  return 'Hello ' + name + '!';
}
```

### 인라인 주석 (inline comments)

- 인라인(inline) 주석은 표현식 중간에 쓰지 않습니다. (예: 반복문, 함수)
- 인라인 주석은 `//`만을 사용합니다.
- 인라인 주석을 사용할 경우 빈줄을 추가해서 사용합니다. 주석의 가독성이 좀 더 좋아 집니다.
  - 함수나 반복문의 바로 다음에 나오는 줄에서는 빈줄을 추가해 주지 않아도 됩니다.

```typescript
// ✋ 나쁨
let lines: string[]; // 파일에서 읽은 내용.

// 👍 좋음
// 파일에서 읽은 내용.
let lines: string[];

// ✋ 나쁨
function walkFor(name: string, millis: number): void {
  console.log(name + '님이 걷고 있습니다.');
  // 걸음이 멈출때 까지 대기
  setTimeout(() => {
      console.log(name + '님이 걸음을 멈췄습니다.');
  }, millis);
}

// 👍 좋음
function walkFor(name: string, millis: number): void {
  console.log(name + '님이 걷고 있습니다.');

  // 걸음이 멈출때 까지 대기
  setTimeout(() => {
    console.log(name + '님이 걸음을 멈췄습니다.');
  }, millis);
}
```

### Todo, Fixme

- `TODO`, `FIXME` 등을 적극적으로 사용하길 권장합니다.
  - [VSCODE-TODO-HIGHLIGHT](https://github.com/wayou/vscode-todo-highlight)를 같이 사용할 것을 권장합니다.
- `// TODO: ` 구현해야 할 경우 표시해 줍니다.
- `// FIXME:` 꼭 수정이 필요한 경우 표시해 줍니다.

```typescript
// TODO: 문제를 파악 해야 함.
// FIXME: 데이터베이스 문제 해결 후 수정 필요.
```





## 따옴표(Quotes)

- 따옴표는 작은 따옴표(single-quotes `''`)를 사용합니다. 문자열(string) 내에서는 큰따옴표(double-quotes `""`)를 사용합니다.
- 문자열 내에서 작은 따옴표를 사용해야 하는 경우에는 큰따옴표를 사용해도 좋습니다.
- 템플릿 리터럴을 사용 할 때만 템플릿 스트링(template strings) ${}를 사용합니다.

```typescript
// ✋ 나쁨
let greeting = "Hello World";

// 👍 좋음
let greeting = 'Hello World';

// ✋ 나쁨
let phrase = 'It\'s Friday!';

// 👍 좋음
let phrase = "It's Friday!";

// ✋ 나쁨
let html = "<div class='bold'>Hello World</div>";

// ✋ 나쁨
let html = '<div class=\'bold\'>Hello World</div>';

// 👍 좋음
let html = '<div class="bold">Hello World</div>';

// ✋ 나쁨
let template = `string text string text`;

// 👍 좋음
let template = `string text ${expression} string text`;
```





## 콤마 (Commas)

- 항상 콤마를 후행에 사용합니다. 줄 앞에 쓰지 마세요.
- 배열이나 객체에는 항상 추가 콤마를 사용합니다.

```typescript
// ✋ 나쁨
const person = {
  firstName: 'John'
, lastname: 'Doe'
, email: 'johndoe@mail.com'
};

// ✋ 나쁨
const person = {
  firstName: 'John',
  lastname: 'Doe',
  email: 'johndoe@mail.com'
};

// 👍 좋음
const person = {
  firstName: 'John',
  lastname: 'Doe',
  email: 'johndoe@mail.com',
};
```





## 클래스 (Class)

* 모든 클래스는 모든 공용 변수와 함수에 대한 블록 주석을 `/**...*/`이 있어야합니다.
* 모든 공개 함수(public function)은  [JSDoc](https://jsdoc.app/) 스타일의 주석을 사용합니다.
* 클래스의 메서드명이 확실 할 경우 설명을 생략 할 수 도 있습니다.
* 클래스 생성자의 경우에는 입력 파라미터(input parameters)만 넣어줍니다.

```typescript
/**
 * 직사각형 영역
 */
class Rect {
  // 넓이
  private _width : number;
  // 높이
  private _height: number;

  /**
   * @param width 시작 넓이
   * @param height 시작 높이
   */
  constructor(width: number, height: number) {
    this._width  = width;
    this._height = height;
  }

  /**
   * 넓이 지정
   * @param 넓이 값
   */
  set width(width: number) {
    this._width = width; 
  }
}
```



## 변수 선언 (Variable Declarations)

- 모든 변수를 사용하기 전에 선언해야합니다. 
- 묵시적인 전역 변수를 사용할 수 없습니다.
- 작은 범위(smaller scope) 내에서 전역 범위(global scope)의 변수를 정의해서는 안됩니다.

```typescript
// ✋ 나쁨
function add(a: number, b: number): number {
  // c 는 전역 범위 변수 입니다.
  c = 6;

  return a + b + c;
}
```

- 각 변수를 선언 할 때는 줄바꿈을 해 줍니다.

```typescript
// ✋ 나쁨
let a = 2,
    b = 2,
    c = 4;
    
// ✋ 나쁨
let a = b = 2, c = 4;

// 👍 좋음
let a = 2;
let b = 2;
let c = 4;
```



## 함수 선언 (Function Declarations)

- 사용되기 전에 모든 기능을 선언해야합니다.
- 함수의 이름과 왼쪽 괄호`(`의 매개 변수의 목록 사이에는 공백이 없어야합니다.
- 하나 개 오른쪽 괄호 사이의 공간`)`와 문 본문을 시작하는 곱슬 왼쪽 `{`중괄호가 있어야합니다.

```typescript
// ✋ 나쁨
함수 foo () {
  // ...
}

// 👍 좋음
함수 foo () {
  // ...
}
```

- 오른쪽 중괄호는`}`새 행에 있어야합니다.

- 오른쪽 중괄호는`}`함수 문을 시작 왼쪽 중괄호 `{`포함하는 행과 일치해야합니다.

```typescript
// ✋ 나쁨
function foo(): string {
  return 'foo';}

// 👍 좋음
function foo(): string {
  return 'foo';
}
```

- 모든 fat-arrow / lambda 함수는 함수 매개 변수 주위에 괄호 ()가 있어야합니다.

```typescript
// ✋ 나쁨
clickAlert() {
  let element = document.querySelector('div');

  this.foo = 'foo';

  element.addEventListener('click', function(ev: Event) {
    // this.foo does not exist!
    alert(this.foo);
  });
}

// 👍 좋음
clickAlert() {
  let element = document.querySelector('div');

  this.foo = 'foo';

  element.addEventListener('click', (ev: Event) => {
    // TypeScript allows this.foo to exist!
    alert(this.foo);
  });
}
```

- 항상`{}`중괄호와 펑션 블록을 둘러 쌓아 줍니다.

```typescript
// ✋ 나쁨
element.addEventListener('submit', ev => ev.preventDefault());

// ✋ 나쁨
element.addEventListener('submit', (ev: Event) => ev.preventDefault());

// 👍 좋음
element.addEventListener('submit', (ev: Event) => {
  ev.preventDefault();
});
```

- 오른쪽 괄호 `()`와 `=>` 사이에는 공백이 있어야합니다.
- 명령문 본문을 시작하는 `=>`와 왼쪽 중괄호 `{` 사이에는 공백이 있어야합니다.

```typescript
// ✋ 나쁨
element.addEventListener('click', (ev: Event)=>{alert('foo');});

// 👍 좋음
element.addEventListener('click', (ev: Event) => {
    alert('foo');
});
```



## 작명 (Names)

- 모든 변수 및 함수 이름은 영숫자 `A-Z`, `a-z`, `0-9` 및 밑줄 `_` 문자로 구성되어야합니다.

### 변수(Variables), 모듈(Modules), 함수(Functions) 명

- 변수, 모듈, 함수 명에는 카멜케이스(lowerCamelCase)를 사용합니다.
  - 소문자로 시작하고 복합어일 경우에는 중간에 새로운 단어의 첫자는 대문자로 표기합니다.
  - 예) `newWorld`, `testDriver`, `helloWorld`

### 변수 선언

- `var`은 사용하지 않습니다.
- 값이 변경되지 않는 경우에는 `const`사용합니다.
- 그외 경우에는 `let`을 사용합니다.

### 타입 (Types)

- 되도록이면 항상 형식 선언을 해 줍니다.
- 함수를 선언 할 때 되도록이면 반환하는 형식을 선업해 줍니다.
- 배열은 `Array<type>` 대신 `type[]`형식으로 사용합니다.

```typescript
// ✋ 나쁨
let numbers = [];

// ✋ 나쁨
let numbers: Array<number> = [];

// 👍 좋음
let numbers: number[] = [];
```

- `any`의 사용을 자제하며, 되도록이면 interface를 만들어서 사용해 줍니다.

### 클래스 (Classes)

* 클래스명은 파스칼케이싱(Pascal Casing)을 사용합니다.
  * 대문자로 시작하고 복합어일 경우에는 중간에 새로운 단어의 첫자는 대문자로 표기합니다.
  * 예) `NewWorld`, `TestDriver`, `HelloWorld` 
* 메서드의 상단에는 1줄 이상의 빈줄을 추가합니다.
* public 인스턴스 멤버는 다른 파트의 어플리케이션에서 사용하는 경우에만 사용하십시오.

```typescript
class Rect {
  private _width : number;
  private _height: number;
    
  constructor(width: number, height: number) {
    this._width  = width;
    this._height = height;
  }
    
  public set width(width: number) {
    this._width = width; 
  }
}
```

### 인터페이스 (Interfaces)

- 인터페이스는 파스칼케이스(PascalCase)를 사용합니다.
- 인터페이스의 대문자 `I`를 프리픽스로 사용합니다. 프리픽스를 사용하는 이유는 클래스와 인터페이스를 구분하기 위해서 입니다.
- 인터페이스는 public 멤버만을 사용하며, `protected`와 `private` 멤버에서는 사용하지 않습니다.

```typescript
interface IPerson {
    firstName: string;
    lastName: string;
    toString(): string;
}
```



## 표현법 (Statements)

### 단순 표현

- 모든 문장의 뒤에는 세미콜론(`;`)을 넣어 줍니다. 

``` typescript
// ✋ 나쁨
alert('hello')

// 👍 좋음
alert('hello');
```

### 복합문 (Compound)

- `{}`로 둘러싸인 문장의 목록
  - 둘러싸인 문장은 새로운 라인으로 시작 합니다.

```typescript
// ✋ 나쁨
if (condition === true) { alert('Passed!'); }

// 👍 좋음
if (condition === true) {
  alert('Passed!');
}
```

* 왼쪽 곱슬 브레이스(`{`)는 복합 문을 시작하는 선의 끝에 있어야 합니다.
* 오른쪽 곱슬 브레이스(`}`)는 인단트에 맞춰서 왼쪽 곱슬 브레이스(`}`)의 시작 라인에 맞춰 줍니다.

````typescript
// ✋ 나쁨
if (condition === true)
{
  alert('Passed!');
}

// 👍 좋음
if (condition === true) {
  alert('Passed!');
}
````

* 한줄로 표현이 가능한 브레이스(`{}`)라도 브레이스를 사용해 줍니다.
  * 복잡문장 주변에 브레이스를 사용하지 않으면 실수가 생기기 쉽습니다.

```typescript
// ✋ 나쁨
if (condition === true) alert('Passed!');

// ✋ 나쁨
if (condition === true)
  alert('Passed!');
  return true;

// 👍 좋음
if (condition === true) {
  alert('Passed!');
  return true;
}
```

### 리턴 (Return)

* 리턴은 한줄에 표시해 줍니다.

```typescript
// ✋ 나쁨
return
    'Hello World!';

// 👍 좋음
return 'Hello World!';
```

* 가능하면 리턴은 먼저하는 것을 권장합니다.

```typescript
// ✋ 나쁨
function getHighestNumber(a: number, b: number): number {
    let out = b;

    if(a >= b) {
        out = a;
    }

    return out;
}

// 👍 좋음
function getHighestNumber(a: number, b: number): number {
    if(a >= b) {
        return a;
    }

    return b;
}
```

* 메서드나 함수에는 되도록이면 올바른 리턴 타입을 지정해 줍니다.

```typescript
// ✋ 나쁨
function getPerson(name: string) {
    return new Person(name);
}

// 👍 좋음
function getPerson(name: string): Person {
    return new Person(name);
}
```

### 비교문 (If)

* if문은 항상 명시적인 표현을 사용합니다. 

```typescript
// ✋ 나쁨
if (!!str) {
  return false;
}

// 👍 좋음
if (typeof str === 'string') {
  return false;
}
```

* if문도 복합문과 같은 형태로 표현합니다.

```typescript
if (/* condition */) {
    // ...
}

if (/* condition */) {
    // ...
} else {
    // ...
}

if (/* condition */) {
    // ...
} else if (/* condition */) {
    // ...
} else {
    // ...
}
```

* 되도록이면 `===`와 `!==` 연산자를 사용합니다.
  * `==`와 `!=`연산자는 타입을 무시해서 문제가 발생 할 수 있습니다.

### 객체와 배열 리터럴 (Object, Array Literals)

* `new Object()` 대신 `{}`를 사용합니다.
* `new Array()` 대신 `[]`를 사용합니다.



### TSLint

* 항상 Linter를 사용해 줍니다.

TSLint: https://github.com/palantir/tslint





## 참고

* https://github.com/Platypi/style_typescript