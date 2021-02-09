# OpenAPI와 Swagger

2020년 1학기에 개발했던 'petmate'를 RestAPI로 바꾸는 작업을 진행하면서 API 문서를 정리해야겠다는 필요성을 느꼈다.
하지만... API 문서를 어떻게 뭘 정리를 해야 할지도 모르겠어서 검색했더니 OpenAPI와 Swagger에 대한 글들이 나와서 내친김에 같이 정리하기로 했다!

<br>

### OpenAPI 3.0이란?🙄

OpenAPI Specification 즉, OAS는 RESTful 웹 서비스를 약속된 규칙에 따라 API 스펙을 json이나 yaml형식으로 표현한 것을 말한다.
공식문서는 [여기](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.1.0.md)에서 확인할 수 있다.

<br>

### Swagger

OpenAPI가 API 정의서의 스펙같은 거라면 Swagger는 API 문서를 작성하는 데 도움을 주는 툴이다. Swagger는 [여기](https://editor.swagger.io/)에서 확인할 수 있다. 아직 사용하진 않았지만 곧 Spring과 연동해서 문서를 정의하는 데 사용할 예정이다.
처음엔 막연히 노션으로 정리해야겠다고 생각했는데 API 문서를 노션이나 엑셀 등 일반 문서로 정리해 두면 API가 변경될 때마다 문서를 수정해야 하는 단점이 있다고 해서 자동으로 처리해 주는 Swagger를 사용하기로 했다. 더 구체적인 적용 방식은 실제로 적용해 본 후 정리해 봐야겠다.

이건 [API에 대해 잘 정리해 둔 글](https://devraphy.tistory.com/120)이다!