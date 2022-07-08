# Javascript

[TOC]



## TIL_0502

자바스크립트의 함수는 일급 객체:

변수에 할당 가능, 함수의 매개변수로 전달 가능, 함수의 반환값으로 사용 가능



... : rest parameter, spread operator



함수 선언식으로 선언하면 호이스팅 발생(동작도함)

함수 표현식으로 선언한 경우에만 익명함수 가능



Arrow:

function 키워드 생략 가능

매개변수가 하나이면 ()도 생략 가능

몸통이 표현식 하나라면 {}와 return 생략 가능

const arrow3 = name => \`hello, ${name}\`





array.unshift() : 첫 번째 요소 추가

array.shift() : 첫 번쨰 요소 제거



자바스크립트 만든사람 : 브랜던 아이크



key와 변수 이름 같으면 생략 가능(shorthand)

메서드 선언시 function 생략 가능(shorthand)

구조분해할당 : const {name} = userInformation



document.querySelector

document.querySelectorAll

document.createElement

Element.append() : 여러개 추가할수있음

Element.setAttribute()

Target.addEventListener('click',callback)

event.preventDefault()
