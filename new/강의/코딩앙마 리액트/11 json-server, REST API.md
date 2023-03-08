### 1. json형식이란

JSON(JavaScript Object Notation)은 경량 데이터 교환 형식입니다. 일반적으로 웹에서 데이터를 전송하는 데 사용됩니다. 

JSON은 키-값 쌍으로 이루어진 데이터 오브젝트를 포함하며, 각 키-값 쌍은 콜론으로 구분됩니다. 데이터 오브젝트는 중괄호({})로 감싸져 있으며, 각 항목은 쉼표로 구분됩니다.

JSON 데이터 형식 예시:

json

```

{
  "name": "John",
  "age": 30,
  "city": "New York"
}

```

### 2. REST API란

REST API를 사용하면 네트워크를 통해 정보를 전송하고 수신할 수 있습니다.

REST API는 자원(Resource)과 HTTP 메소드를 기반으로 동작합니다. 자원은 URI(Uniform Resource Identifier)를 통해 표현되며, HTTP 메소드(GET, POST, PUT, DELETE 등)를 통해 해당 자원에 대한 작업을 수행합니다. 예를 들어, 서버의 사용자 정보에 대한 조회를 위해서는 GET /users와 같은 URI와 HTTP 메소드를 사용할 수 있습니다.

REST API는 일반적으로 JSON 형식의 데이터를 사용
