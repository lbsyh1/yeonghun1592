AJAX(Asynchronous JavaScript And XML, 비동기적 JavaScript와 XML)라는 용어를 들어보신 분이 있으실 겁니다. AJAX는 서버에서 추가 정보를 비동기적으로 가져올 수 있게 해주는 포괄적인 기술을 나타내는 용어로, 만들어진 지 오래되었습니다. AJAX에 XML이 포함된 이유가 바로 이 때문이죠.

AJAX 이외에도 서버에 네트워크 요청을 보내고 정보를 받아올 수 있는 방법은 다양합니다.

그중 이번 챕터에선 모던하고 다재다능한 fetch() 메서드에 대해 소개해드리려 합니다. fetch()는 구식 브라우저에선 지원하진 않지만(폴리필을 쓰면 사용 가능) 대부분의 모던 브라우저가 지원합니다.

fetch() 기본 문법은 다음과 같습니다.

let promise = fetch(url, [options])
url – 접근하고자 하는 URL
options – 선택 매개변수, method나 header 등을 지정할 수 있음
options에 아무것도 넘기지 않으면 요청은 GET 메서드로 진행되어 url로부터 콘텐츠가 다운로드 됩니다.

fetch()를 호출하면 브라우저는 네트워크 요청을 보내고 프라미스가 반환됩니다. 반환되는 프라미스는 fetch()를 호출하는 코드에서 사용됩니다.

POST 요청
GET 이외의 요청을 보내려면 추가 옵션을 사용해야 합니다.

method – HTTP 메서드(예: POST)
body – 요청 본문으로 다음 항목 중 하나이어야 합니다.
문자열(예: JSON 문자열)
FormData객체 – form/multipart 형태로 데이터를 전송하기 위해 쓰입니다.
Blob나 BufferSource – 바이너리 데이터 전송을 위해 쓰입니다.
URLSearchParams – 데이터를 x-www-form-urlencoded 형태로 보내기 위해 쓰이는데, 요즘엔 잘 사용하지 않습니다.
대부분은 JSON을 요청 본문에 실어 보내게 됩니다.

user 객체를 본문에 실어 보내는 예시를 살펴봅시다.

let user = {
  name: 'John',
  surname: 'Smith'
};

let response = await fetch('/article/fetch/post/user', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json;charset=utf-8'
  },
  body: JSON.stringify(user)
});

let result = await response.json();
alert(result.message);
POST 요청을 보낼 때 주의할 점은 요청 본문이 문자열일 때 Content-Type 헤더가 text/plain;charset=UTF-8로 기본 설정된다는 점입니다.

하지만 위 예시에선 JSON을 전송하고 있기 때문에 headers에 제대로 된 Content-Type인 application/json을 설정해 주었습니다.

