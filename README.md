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

- 모든 변수 및 함수 이름은 영숫자 A-Z, a-z, 0-9 및 밑줄 _ 문자로 구성되어야합니다.



### 클래스 (Class)

클래스명은 파스칼케이싱(Pascal Casing)을 사용합니다.

* 대문자로 시작하고 복합어일 경우에느 중간에 새로운 단어는 대문자로 표기합니다.
* 예) `NewWorld`, `TestDriver`, `HelloWorld` 





## 참고

* https://github.com/Platypi/style_typescript