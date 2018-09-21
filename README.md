# crypress_guide_KR

cypress guide 한국어 버전

목적 
- 사내 프로젝트 서비스 품질 향상을 위한 POC


## 선택을 위한 다른 테스트 러너와의 차이 및 특징 

다른 e2e 테스트 툴들(예 : Selenium)는 브라우저 외부에서 실행되고 네트워크에서 원격 명령을 실행하여 작동함
하지만 cypress는 nodejs 와 실시간 통신으로 네트워크 계층에서 테스트 작업을 진행합니다.

- 브라우저 설정 및 기능을 제어하며 테스트 가능
- web worker 객체에 접근 가능
- redux등의 상태관리툴에 있는 상태를 직접 제어 할수 있음.
- 서버 rest-api를 인터셉트하여 오류 디버깅을 할 수 있음.
- cypress 내에서 응용프로그램 코드를 다르게 작동하도록 변경 가능 (websoket 메세지 변경등)
- 바로가기 기능(어떤 기능을 사용하기 위해서는 사용자의 관점에서 많은 과정을 걸쳐야 하는데 스킵 가능)
- 페이지 로딩 시간과 로딩이 되었는지 트래킹 할수 있다. (특정 상태나 요소가 생길때 까지 자동 대기함)
- 테스트중 에러가 난곳을 표기해주고 세세한 디버깅이 가능하게 이유를 찾아준다.


## 설치하기

해당 프로젝트소스파일 폴더(repository)

```
> cd/[my_project]
> npm install cypress --save-dev

or

> yarn add cypress --dev 
```

## 테스트 환경 구성

cypress 폴더 생성하기
```
> mkdir cypress
```

package.json 스크립트 수정(추가)하기
```js
"scripts": {
    "_cypress": "./node_modules/.bin/cypress run",
}
```

테스트 스크립트를 실행하면 기본 프로젝트 구성이 자동으로 셋팅된다.

## 간단한 테스트 코드 작성 및 실행

```
> cd cypress/integration
> vim test.spec.js
```

기본적인 테스트코드 스타일은 mocha와 유사함을 볼수 있다.
```js
describe('App E2E', () => {
    it('should assert that true is equal to true', () => {
        expect(true).to.equal(true);
    });
});
```


## 간단한 사용방법

제이쿼리 셀릭트 방식과 비슷함.
```js
cy.get('#id')
cy.get('.classname')
cy.get('input')

// alias 세팅하기
.get('.my-selector').as('myElement') 
// after 
.get('@myElement').click()
// or 
this.myElement.click()

...

```

### 이벤트 추가

```js
cy.get('#id').click()



```

