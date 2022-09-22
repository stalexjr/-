<div align="center">

# 자바스크립트 공부한거 정리

</div>

<h4>event listen 하는 방법</h4>

#


	title.addEventListener("click", handleTitleClick);
위 구조를 보면
HTML element( 요소 )를 가져와서 addEventListener / function을 실행 시켜주면 되는데
이곳에 어떤 event를 listen하고 싶은지 명시해줘야한다. 
왜냐하면 모든 event를 listen하고 싶지는 않기 때문이다.
그리고 유저가 이 element에 해당 event를 했을 때 어떤 함수를 실행 할지도 정해줘야한다.


event를 listen할 때 가장 좋은 방법은 구글에 찾고싶은 element의 이름 

00(html 구조 예를 들어 h1 p span 등등) html element mdn 를 구글에 입력하고 
링크에 Web APIs라는 문장이 포함된 페이지를 찾는다, 이건 javascript관점의 html Heading element 란 의미이기 때문이다.

다른방법도 있다, 대신 console.dir(000(element))을 통해서 console에 출력시키면된다. 그안에는 사용가능한 event를 찾을 수 있다.

#

<h4>form 안에 input 이 들어가야 제 기능을 다한다.</h4>

# 

input 안에 있는 button을 누르거나 type이 submit인 input을 클릭하면
form이 submit한다.

앞서 말했듯 form의 submit은 엔터를 누르거나 버튼을 클릭할 때 발생한다.

form이 submit될 때마다 페이지가 새로고침되는것은 우리가 원하는게 아니다.
그래서 이 form이 submit 되는 것을 막아야한다.

preventDefalut(); : 어떤 event의 기본 행동이든지 발생되지 않도록 막는 함수.
기본 행동이란 어떤 function에 대해 브라우저가 기본적으로 수행하는 동작이다.
누군가 form을 submit하면 브라우저는 기본적으로 페이지를 새로고침 하도록 되어있다.
하지만 preventDefalut()를 추가함으로써 그 기본 동작을 막고 있는것이다.

#

<h4>코드의 차이점</h4>

#

	greeting.innerText = "Hello " + username;
	greeting.innerText = `Hello ${username}`;

▼▼▼ 위에 있는 코드의 차이점

위에 있는 두 방식의 코드는 같은 결과를 가져오지만, 밑에 있는 표현이 좀 더 새로운 방법이다.
밑에있는 방법을 사용하기 위해서는 규칙이 있다.
규칙 하나는 만약 변수와 string을 결합하고 싶다면 안에 ${변수명} 이렇게 표현하면 된다.
그리고 `` 이 기호로 시작해야 된다는 것이다. ex) `Hello ${username}`;
'' 이것도 아니고 "" 이것도아니고 ``(백틱) 이것이다.

``, ${} 이것들을 함께 써야된다.


일반적으로 string만 포함된 변수는 대문자로 표기하고 string을 저장하고 싶을 때 사용한다.
그리고 중요한 정보를 담은게 아닐 시 에도 대문자로 작성한다.


#

<h4>localStorage로 값 저장하는 방법</h4>

#

	localStorage.setItem("username", username); 

▼▼▼

앞은 key값, ( 저장될 아이템의 이름 )이고 뒤는 value ( 변수 )값이다.


	function paintGreetings(username){
	    greeting.innerText = `Hello ${username}`;
	    greeting.classList.remove(HIDDEN_CLASSNAME);
	}


▼▼▼


자주 언급되는 함수를 함수안에 묶을 수 있다.

그리고 그 함수 안에 인자를 꼭 입력해줘야한다 위 코드를 보면 
함수 안에 (username)을 입력해주었다.

위 코드는 username을 인자로 받는 함수를 만든것이다.


#

<h4>interval은 '매번' 일어나야 하는 무언가를 말한다.</h4>

#

예를 들어 '매 2초'라고 하면 이게 interval이라는 거다.
매 2초마다 무슨 일이 일어나게 하고 싶을 때  interval 을 쓴다.

setInterval이라고 쓰는데 setInterval은 두 개의 argument를 받는다
첫번째 argument는 실행하고자 하는 function이다.
두번째 argument는 호출되는 function 간격을 몇 ms(millseconds)로 할 지 쓰면 된다.


setTimeout 사용법은 setInverval과 같지만 반복되지않고 한번만 실행된다.

#

<h4>padStart()는 string에 쓸 수 있는 function이다. </h4>

#

padStart()는 string에 쓸 수 있는 function이다. 
작성 방법은 () 안에 string이 가져야 하는 길이를 정하고
뒤에 그 길이에 맞춰 주가 될 "string"을 줘야한다.

"1".padStart()

▼▼▼

예를들어 앞에 string의 길이를 2로 만드는데 

"1".padStart(2, "0") <-----만약 그 string의 길이가 2가 아니라면 
앞쪽에 "0"을 추가한다 라는 뜻이다. 그래서 이 함수의 결과를 보면 '01'로 나오는 것이다. 

반대로 padEnd가 있는 그럴 경우에는 0이 뒤쪽에 붙는다.

그리고 이 함수를 쓸 땐 앞에 반드시 value값이 string이 온 뒤에 padStart를 쓸 수 있다.  
하지만 string을 number로 치환하는 함수가 있듯이 number에서 string으로 치환하는 함수가 있다

그것은 String이다.

예를 들어 date.getHours()라는 함수가 있다고 치자 그러면 이 value값은 nuber이기 때문에
date.getHours().getStart(2 , "0")라고 쓰면 에러가 난다.
그래서 이걸 String(date.getHours()).getStart(2, "0")라고 써야한다.

#

<h4>Math</h4> 

#

Math 라는 module는 Date() 처럼 자바스크립트에서 이미 로드되서 제공되어있다. 
Math는 흥미로운 function을 많이 가지고 있는데 그 중 하나는 random()이다.

Math.random()이라고 입력해주게되면 랜덤 숫자가 결과로 나타난다. /  0.821831298
만약 사용자가 0 ~ 10개 중에 랜덤으로 숫자를 얻기 원한다면
Math.random() * 10 <---- 10을 곱해주면 된다.  / 9.6822845689456
하지만 뒤에 소수점까지 필요하지 않다. 이걸 없애기 위해선 세가지 function을 사용 할 수 있다.

그 중 하나는 round()다.

예를 들어서 Math.round(1.1)이 있다고 치면
round()는 1으로 돌려준다. 1.2가 있어도 1 이고 1.3, 1.4도 1로 돌려준다.
하지만 1.5부터 1.6, 1.7, 1.8 은 2로 돌려준다.

보다시피 round()는 숫자를 반올림 해준다. 그래서 0.8은 1 이 되지만 0.1은 0이 된다.

두번째 방법은 ceil()이다. 

ceil()이 하는건 숫자를 천장(ceill)까지 높여주는 것이다. 말 그대로 머리 꼭대기 천장까지 올려준다.
그래서 Math.round(1.1)은 2다 1.9도 2가 되고 1.0만이 1이 될 수 있다. 1.01만 돼도 2다.
그게 ceil()이다.

마지막 세번째 방법은 floor()이다.
floor()는 걸어 다니는 바닥(floor)까지 숫자를 내려준다.
Math.round(1.9)는 1이 되고 1.99999999도 1이 된다.

내림을 해주는 floor()도 있고 반대로 올림을 해주는 ceil()도 있는셈이다.

여기서 사용할 것은 floor()다.

예를들어 0 ~ 10까지 랜덤하게 숫자를 낼라면 
위에 말했듯 Math.random() * 10 함수를 floor() 함수 안에 입히면된다.
Math.floor(Math.random()*10)을 입력하면 랜덤 결과가 도출된다.

랜덤한 숫자를 뽑아야 할 때 item이 5개 있는 Array에서 마지막 item을 가져오려면 필요한 숫자는 5가 아니라 4다.

#

<h4>document.body.appendChild()</h4>

#

document.body.appendChild()는 body에 html을 추가할 거다 


document.createElement("img"); createElement은 
html 태그를 자바스크립트로 작성해주겠다는 의미이다.

innerText는 안에 글자를 입력해 주겠다는 의미이다.


JSON.stringify()는 JavaScript object 나 array 또는 어떤 javascript 코드 건 간에 string으로 만들어 준다.

값을 string으로 저장하고 싶을 때 많이 사용한다.

JSON.parse()는 단순한 string을 javascript 가 이해할 수 있는 array로 만들어 준다.

array는 forEach라는 메서드를 가지고 있다. forEach는 array가 가지고있는 item들의 function을 실행시켜준다.

event.target.parentElement.innerText 에서 

target은 클릭 된 HTML.element다. 그리고 모든 HTML element 에는 하나 이상의 property가 있다.


로컬 스토리지에는 오직 텍스트만 저장할 수 있다. array를 저장할 수 없다.

로컬 스토리지에 배열처럼 저장하고싶다면 JSON.stringify()를 이용하면된다.

#

<h4>forEach</h4>

#
forEach 함수는 배열 item 요소마다 실행한다 forEach()안에 object함수를 주었다면 item 이 object가 된다.

forEach와 비슷한 작업이 있다. 그건 바로 filter다. 만약 array에서 뭔가를 삭제할 때 실제로 array에서 그걸 지우는것이 아니다. 진짜 일어나는 일은 지우고싶은 item을 빼고 새 array를 만든다. item을 지우는게 아니라 item을 제외하는 것이다. 그래서 예전 array는 여전이 있고, 지우고 싶은 item을 제외하고 새 array를 만드는 거다. 즉 지우고 싶은 item을 제외하는 것이다.

filter는 함수를 부르고 배열에 함수가 차례대로 실행된다.

▼▼▼

	function anyFunction(){

	}

	1, 2, 3, 4에 anyFunction이 차례대로 실행 된다.

▼▼▼

	[1, 2 , 3 , 4].filter(anyFunction)

filter는 anyFunction에서 1, 2, 3, 4를 넣어서 부른다 anyFunction만 호출 되지 않는다.
anyFunction에 1, 2, 3, 4 를 호출하게 된다.

▼▼▼

anyFunction(1 ~ 4)

이제 anyFunction의 역할은 뭘까 ? anyFunction 함수는 반드시 true를 리턴해야 된다.
만약 새 array에서 이 array를 유지하고 싶으면 false를 리턴하게되고 그 item은 새 array에 포함되지 않을 것이다. 

다시 위에있는 [1, 2, 3, 4].filter(anyFunction)의 뜻은 javascript가 anyFunction을 4번 부르는것이다. 하지만 매번 숫자는 달리진다.

javascript가 이렇게 할 것이다.

▼▼▼

	anyFunction(1) = 1 그리고 true를 리턴하면 javascript는 1을 유지할 것이다.
			2, 3, 4도 true면 유지 된다.
	anyFunction(2) = 2
	anyFunction(3) = 2
	anyFunction(4) = 4

그리고 새로 만들어지는 array 안에 1,2,3,4가 있다.
하지만 만약 3번째 단계에서 false를 리턴하면 javascript는 3을 빼고 1, 2, 4만 유지할 것이다.

!== 3 : 3이 아니라면 true를 리턴해라

argument의 이름이 뭐가 되도 상관없다.

parseint : 문자열을 숫자로 바꿔준다.

#

<h4>if문 중첩 제거하는 방법</h4>

#

1. if 문 다음에 나오는 공통된 절차를 각 분기점 내부에 넣는다.

2. 분기점에서 짧은 절차부터 실행하게 if 문을 작성한다.

3. 짧은 절차가 끝나면 return(함수 내부의 경우)이나 break(for 문 내부의 경우)로 중단한다.

4. else를 제거한다(이때 중첩 하나가 제거된다).

5. 다음 중첩된 분기점이 나오면 1~4의 과정을 반복한다.

#

<h4>fetch</h4>

#

javascript는 const = url 을 불렀다. 하지만 얻은 정보를 사용하지 않았다.
이제 이걸 얻었을 때 뭘 하라고 javascript에게 말해주어야 한다.
fetch는 promise 다.
promise는 당장 뭔가 일어나지 않고 시간이 좀 걸린 뒤에 일어나는 것이다.
서버에 뭔가 물어봤는데 서버가 응답하는 데 5분 걸린다고 해보자
그러면 서버의 응답을 기다려야 한다.
그래서 then을 사용해야 된다. 이제 어떤 일이 일어나냐면
url을 fetch하고 그 다음으로 response를 받아야 한다. 그리고 response의 json을 얻어야 한다.
response.json()은 이게 JSON이다.
그리고 내용을 추출했으면 data를 얻을 것이다.
그리고 여기에 console.log로 우리가 원하는 걸 볼 수 있다.


▼▼▼


	const url = `https://api.openweathermap.org/data/2.5/weather?lat=${lat}&lon=${lon}&appid=${API_KEY}`

	fetch(url).then(Response => Response.json()).then(data =>{
		console.log(data.name, data.weather[0].main);
	    });
	}

#

<h4>document.querySelector</h4>

#

	const h1 = document.querySelector("div.hello:first-child h1");

	function handleTitleClick(){
	   h1.classList.toggle("clicked");
	}

	h1.addEventListener("click", handleTitleClick);

▼▼▼

ex) h1.classList.toggle("clicked");
(element) (element의 클래스를) (함수) (클래스명)

classList는 class들의 목록으로 작업할 수 있게끔 허용해준다.
className은 그냥 모든걸 교체해버린다 element에 class가 부여되있던 말던
toggle함수는 element의 정해놓은 클래스가 포함되어 있다면 지우고 포함되어 있지 않다면 추가한다

contains는 HTML element의 class에 포함되어 있는지 말해준다는 것이다. 

#

<h4>코드 짧게 줄이는 법</h4>

#


	const loginForm = document.getElementById("login-form");
	const loginInput = loginForm.querySelector("input");
	const loginButton = loginForm.querySelector("button");


▼▼▼  위에 있는 코드를 더 짧게 줄이는 방법

첫 줄은 지우고 바로 querySelector("#login-form input 이랑 button")로 바꾸고
맨앞에 선언 되어있었던 loginForm 함수를 document로 바꿔야된다.
이렇듯 document 또는 하나의 element를 통해서 검색이 가능하다.

배열에 추가로 데이터를 넣고싶으면

arr = ['나', '다', '라', '마', '바'];

	arr.unshift('가') // 배열데이터 맨 앞에 넣기
	arr.push('사'); // 배열데이터 맨 뒤에 넣기 
	arr.pop(); // 배열데이터 맨 뒤 삭제
	arr.splice(1,1) // 앞에는 배열데이터 인덱스, 그리고 뒤 숫자는 지우고 싶은 개수
	arr.includes('다'); // 배열데이터 안에 '다'라는 데이터가 들어있는지 확인하는 방법 결과값은 true false 다.
	arr.indexOf('다'); // 배열데이터 위치를 정확히 알려준다 결과값 1.
	arr.lastIndexOf('라')

#

<h4>toggle</h4>

#

예전 개발자들은 어떤 active가 걸렸을 때 element에 class name을 포함하고 지우는 행동을

add(), remove()를 통해 사용해 왔다. 하지만 이런 작업은 흔한 작업이다. 
이런 이유 덕분에 더 쉽게 해줄 function이 존재한다.

그리고 그 function 중 하나가, toggle function 이다.
toggle function은 class name 이 존재하는지 확인 할 것이다.

만약 class name이 존재한다면 toggle 은 class name 을 제거할 것이다.

그리고 class name이 존재하지 않는다면 toggle은 class name을 추가할 것이다.

ex) h1.classList.toggle("clicked");

#

<h4>obj</h4>

#

기본적으로 ''을 안붙여도 되지만 붙여줘야하는 특수한 경우가 있다. 맨앞에 숫자가 붙는다거나 공백이 붙는다거나 사이에 - 같은게 붙으면 문자열로 묶어줘야한다.

ex) '2ca' 'c a' 'c-a' 


	const woojin = {
	    name : 'woojin',
	    year : 1996,
	    month : 10,
	    dete: 31,
	    gender : 'M',
	};


	woojin.gender
	'M'
	woojin['gender']
	'M'

obj의 값을 받아오는 두 방법이다. 왜 방법이 두가지냐면 위에 woojin.gender 
이 방법은 만약 obj를 'name' : 'wojin' 이랬을 경우 위에 방법으로는 값을 못 가져온다.
그래서 밑의 방법을 사용해야한다.

#

<h4>nvm 오류 처리 방법</h4>

#

Windows 시스템인 경우 
1. C:\Program Files\nodejs로 이동한다. 
2. 그런 다음 해당 폴더의 이름을 C:\Program Files\nodejsx로 바꾼다. 
3. 그런 다음 "nvm use vvv"를 확인해라

#

<h4>for문</h4>

#

짝수를 제외한 나머지를 추출해보자

이중 조건문을 사용하면 된다.


	for(let i =0; i < 10; i++){
	for(let j =0; j <10; j++){
	if(i % 2 ===0 || j % 2 ===0)continue;
	console.log(i,'x',j ,'=', i * j);
	}   
	}
하면 결과값이 제대로 나온다.

별찍기 

for문을 사용하여 *을 찍어보자

	*
	**
	***
	****
	***** 


	for(let i = 0; i <10; i++){
  	console.log('*'.repeat(i));
	}

반대로 찍어보기

	*****
	****
	***
	**
	*

	for(let i =0; i <5; i++){
	 console.log('*'.repeat(5- i));
	}


	*********
	*******
	*****
	***
	*

	*
	***
	*****
	*******
	********* 

1,3,5,7,9 개를 찍어보자 

	for(let i = 0; i<10; i++){
	 if(i % 2 ===0)continue;
 	console.log('*'.repeat(i));
	}

	for(let i = 0; i<10; i++){
 	if(i % 2 ===0)continue;
 	console.log('*'.repeat(10 - i));
	}

앞의 공백을 만들어서 별을 찍어보자

          *
         **
        ***
       ****
      *****
      *****
       ****
        ***
         **
          *

	for(let i = 0; i<5; i++){
	 console.log(' '.repeat(i) + '*'.repeat(5 - i));
	}

	for(let i = 0; i<5; i++){
	 console.log(' '.repeat(5 - i) + '*'.repeat(i + 1));
	}


	for(let i = 0; i < 5; i++){
	    if(i < 3){
		console.log(' '.repeat(2-i) + '*'.repeat(2*i + 1) + ' '.repeat(2-i));    
	    }else{
		console.log(' '.repeat(i-2) + '*'.repeat(9-2*i) + ' '.repeat(i-2));
	    }

	}


	for ( let i = 0; i < 5; i++) {
	console.log(' '.repeat(4-i),'*'.repeat(i*2 + 1),' '.repeat(4-i))
	}


#

<h4>splice와 slice의 차이점</h4>

#

splice는 기존 배열에 영향을 주고 처음에는 인덱스번호 두번째는 갯수고 slice은 기존 배열에 영향을 주지 않고 둘다 인덱스 번호를 뜻하고 처음 인덱스 번호는 포함 두번째 인덱스 번호는 미포함을 뜻한다.

#

<h4>for문과 while문을 쓸 때 참고사항</h4>

#

조건이 간단하거나, 몇번 반복해야할지 정확히 감이 안올때 while문, 
조건이 복잡하거나 몇번 반복할지 정확히 알고 있을때 for문
