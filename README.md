# 타입스크립트의 개요

1. 오픈소스 프로그래밍 언어
1. 자바스크립트의 상위 집합으로 ECMA스크립트의 최신 표준을 지원
1. 정적인 언어로 컴파일 시간에 타입을 검사
1. 장점
    -   강력한 타입으로 대규모 애플리케이션 개발에 용이
    -   유명한 자바스크립트 라이브러리와의 편리한 사용
    -   개발 도구에서 강력한 지원

### 타입스크립트 시작하기
1. npm install -g typescript [컴파일러 설치]
2. tsc index.ts -----> index.js [tsc 명령어를 통해 컴파일러 실행 시킬 수 있다.]
3. tsc index.ts --target es6
4. tsc 001_hello.ts --module commonjs --target es6

### 타입스크립트 컴파일 옵션 파일 만들기
1. 자바스크립트로 설정될 때 어떻게 될지 설정 할 수 있습니다.
<pre>
<code>
tsconfig.json
{
    "include":[
        컴파일할 파일들...
    ],
    "exclude:[
        컴파일 제외할 파일들...
    ],
    "compilerOptions":{
        컴파일 옵션들...
        "module":모듈시스템,
        "rootDir":
        "outDir":"컴파일 파일들의 위치",
        "target":컴파일 버전,
        "sourceMap": true,
        "removeComments": true, 주석제거
        "noImplicitAny": true, 어떤 형태의 타입이든 올 수 있다를 방지!! 타입을 무조건
    }
}
</code>
</pre>

### 타입스크립트의 기본 타입
1. 타입을 고정하기 위한 타입 어노테이션 
2. [let / const] score : number (숫자형만 넣을 수 있다)
<pre>
<code>
var v1 = 1; // var 키워드는 함수 단위의 스코프를 가진다
let v2 = 1;
const v3 = 3;

function outer(){
    var score = 1;
    function inner(){
        console.log(score) // undefined
        var score = 0 ;
        console.log(score) // 0
    }
    inner();
    console.log(score); // 1;
}

outer();


function outer1(){
    if(true){
        var score = 0;
    }

    //var 키워드는 함수 단위의 스코프를 가지기 때문에 var i 선언 호이스팅 발생 i ==> 3이 된다 
    for(var i = 0 ; i < 3 ; i++){
        setTimeout(()=>{
            console.log(i);
        },i*1000)
    }

    console.log(score); //0
}

outer1(); // 3
</code>
</pre>