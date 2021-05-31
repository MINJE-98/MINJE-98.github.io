---
layout: project
permalink: /:title/
category: projects

meta:
  keywords: "Express, JavaScript"

project:
  title: "Express, RestAPI 구현-1"
  type: "Express, JavaScript"
#   url: "/"
  logo: "/assets/images/projects/express/express-256x256.png"
  tech: "Express, JavaScript"

agency:
  title: "조민제"
  url: "https://github.com/MINJE-98"
  year: "2020"
  month: "05"
  day: "30"
---
DeadLine을 하면서 Express를 썻었는데 그냥 무작정 써보기만하고 정리를 안했었다.

그래서 Express로 RestAPI를 구현하면서 배운 내용을 정리하기로 해보았다.

# ExpressJS란

Express가 nodejs를  가장 많이 사용하고 있는 웹 프레임 워크이다.

또한 MVC 형태의 구조를 제공하여, BACKEND로  REST API, SOCKET.IO와 같은 웹앱 기능을 제공한다.

# **Express.js의 작동 방식**

보통 Express.js에는 메인 파일이라고 하는 진입점이 있다. 메인 파일에서는 다음과 같은 단계를 밟는다.

1. controller, utils, help, model과 같은 자체적인 모듈을 비롯한 서드파티 의존 모듈을 인클루드한다.
2. 템플릿 엔진과 해당 템플릿 엔진의 파일 확장자와 같은 Express.js 앱 설정을 구성한다.
3. 오류 핸들러, 정적 파일 폴더, 쿠키 및 기타 파서와 같은 미들웨어를 정의한다.
4. 라우팅을 정의한다.
5. MongoDB, Redis 또는 MySQL과 같은 데이터베이스에 연결한다.
6. 앱을 구동한다.

# 기본 라우팅

라우팅은 URL 및 HTTP 요청 메소드인 특정 엔드포인트에 대한 클라이언트 요청에 응답하는 방법을 말한다.

라우터마다 하나이상의 핸들러 함수를 가질 수 있다.

라우터는 다음과 같은 구조이다.

```jsx
app.METHOD(PATH, HANDLER)
```

라우터는 기본적으로 CRUD를 제공한다. 아래는 CRUD 구현한 예이다.

### GET

```jsx
app.get('/', (req, res)=> res.send('get/ Hello!'))
```

### POST

```jsx
app.post('/', (req, res)=> res.send('PSOT 요청을 받았습니다.'))
```

### PUT

```jsx
app.put('/user', (req, res)=> res.send('/user에서 PUT요청을 받았습니다.'))
```

### DELETE

```jsx
app.delete('/user', (req, res)=> res.send('/user에서 DELETE요청을 받았습니다.'))
```

# 미들웨어

애플리케이션 요청-응답(req-res)주기 중 그 다음의 미들웨어 함수에 대한 엑세스 권한을 갖는 함수이다.

미들웨어 함수는 next라는 변수로 표시된다

즉, HTTP BODY에 request, response가 존재하는데, 클라이언트가 request를 받고 response를 생성해서 보내주는 과정의 중간에 개발자가 간섭하여 로직생성, req, res 변경 및 흐름제어를 할 수 있다.

### app.use()


```jsx
const auth = require("/auth") // #1
app.use("/auth", auth) // #2
app.use(cookieParser())) // #3
```
애플리케이션 단계에서 URL을 분리하고

### express.router()

```jsx
router.get('/', (req, res, next)=> {
	console.log(req);
	res.send('respond with a resource');
	next());
}
```
라우터 단계에서 URL제어를 한다