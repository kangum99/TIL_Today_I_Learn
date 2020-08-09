#Javascript-기초문법 정리
---

- 0부터 n-1까지 더하는 함수?

```jsx
function get_sum(n){
	let sum = 0 
	for (let i = 0; i < n; i ++){
		sum += 1
		}
	return sum
}
```

- 여러가지 함수의 정의 방법

```jsx
function a() {}
let func = function() {}
let func = () => {}
//호출방법은 같다
```

- 비구조 할당 방법

```jsx
const blog = {
	owner : "noah",
	url : "noahlogs.tistory.com",
	getPost() { 
		console.log("ES6 문법 정리");  //딕셔너리에는 함수도 넣기가능
	}
};

//기존
let owner = blog.owner
let getPost = blog.getPost()

//비구조 할당 방식
let { owner, getPost } = blog;       
//각각 blog 객체의 owner , getPost() 의 데이터가 할당

//배열

const pocket = ["coin" , 10 , true];
const [ first , second, third ] = pocket;    //배열의 순서대로 값이 할당

console.log(first,second,third);
//coin 10 true
```
- 딕셔너리(객체)리터럴

```jsx
//기존
var name = "조동현";
var job = "developer";

var hudi = {
  name: name,
  job: job
}

console.log(hudi);
//{name: "조동현", job: "developer"}

//최신
const name = "조동현";
const job = "developer";

const hudi = {
  name,
  job
}

console.log(hudi);
//{name: "조동현", job: "developer"}
```

- 딕셔너리 활용

```jsx
//딕셔너리를 리스트로 만들기
const object1 = {
  a: 'somestring',
  b: 42,
  c: false
};

console.log(Object.values(object1));
//["somestring", 42, false]

//빈 객체 확인하기
let emptyObject = {}
console.log(Object.keys(emptyObject).length)
//0

//반복문으로 순회해서 값 꺼내기
var dic = {
  first: "John",
  last: "Doe"
};

Object.keys(dic).forEach(function(key) {
  console.log(key, dic[key]);
});

// first John
// last Doe
```

- map-반복문(for)의 다른 모양

```jsx
//리스트의 길이로 무조건 돌린다, index값도 알려준다
const array = [1,2,3,4,5,6,7];

array.map((value,i)=> { 
	console.log(value,i) 
})
//1 0
//2 1 ....(값, 인덱스)

let result = array.map((value, i) => value+i)
//(value, i) => {return value + i }
//중괄호랑 return이 생략된거다
console.log(result)
//[1, 3, 5, 7, 9, 11, 13]
```

- filter-반복문+조건문의 다른 모양

```jsx
//모든 array를 돌면서 id와 value값이 같지 않은 것들을 array에 넣어라
let array = [1,2,3,4,5,6,7];
const deleteId = (id) => {
	array = array.filter((value) => {
		return value !== id
	})
}
//{}와 return을 뺴줄수 있다.
//array = array.filter((value) => value !== id)
console.log(array) //[1, 2, 3, 4, 5, 6, 7]
deleteId(6)
console.log(array) //[1, 2, 3, 4, 5, 7]
```

- spread - 딕셔너리나 리스트 값들을 합치기

```jsx
const phone= {
  number: '01012345678'
};

const users= {
  ...phone,
  name: '김건희'
};

const all= {
  ...users,
  color: 'purple'
};

console.log(phone);
console.log(users);
console.log(all); //phone, users, all 다 있다.

const animals = ['개', '고양이', '참새'];
const anotherAnimals = [...animals, '비둘기'];
```

- rest -함수 피라미터의 갯수를 모를 때

```jsx
function sum(...rest) {
  console.log(rest) // []
  console.log(...rest) // 1, 2, 3, 4, 5, 6, 7 
}

console.log( sum(1,2,3,4,5,6,7) )
```