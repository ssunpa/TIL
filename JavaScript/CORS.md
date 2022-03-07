# CORS

-   Cross-Origin Resource Sharing
-   도메인이나 서브도메인, 프로토콜, 포트가 다른 곳에 요청을 주고 받을 수 있도록 사용하는 방책

<aside>
💡 보안 이슈로 인해 웹 브라우저는 기본 정책으로 한 사이트의 스크립트에서 다른 사이트에 있는 콘텐츠에 접근 불가능하게 한다.

</aside>

## CORS 이전 사용하던 트릭

-   폼 이용
    어디든 데이터를 보낼 수 있다는 특징을 이용해 `<form>`안에 `<iframe>`을 넣어 `GET`,`POST` 요청을 했다.
    다른 사이트에서 `<iframe>`에 있는 콘텐츠를 읽는 것은 금지되었기 때문에 응답을 읽는 것은 불가능했다.
-   스크립트 이용
    `script` 태그의 `src` 속성 값에 도메인 제약이 없다는 특징을 이용해 *JSONP*라 불리는 프로토콜을 사용해 데이터를 가져올 수 있었다.
      <aside>
      💡 JSONP(JSON with padding 또는 JSON-P)
      
      </aside>

## Cross-Origin Resquest

도메인이나 서브도메인, 프로토콜, 포트가 다른 곳에 요청을 보내는 것

-   안전한 요청
    : 다음 두 가지 조건 모두를 충족하는 요청
    1. 안전한 메서드(safe method) - `GET`이나 `POST`, `HEAD`를 사용한 요청
    2. 안전한 헤더(safe header)
        - `Accept`
        - `Accept-Language`
        - `Content-Language`
        - 값이 `application/x-www-form-urlencoded` 이나 `multipart/form-data`, `text/plain`인 `Content-Type`
-   그 외의 요청
    : 안전한 요청의 조건을 모두 충족하지 않는 요청
    : `PUT`, `DELETE` 메소드를 이용하거나 헤더에 `API-Key`가 명시된 경우

<aside>
💡 브라우저는 안전하지 않은 요청을 서버에 전송하기 전에 ‘preflight’요청을 먼저 전송해 서버가 크로스 오리진 요청을 받을 준비가 되어있나 확인한다.

</aside>
