# DOM (Document Object Model)

## 1. DOM이란?
- **Document Object Model**의 약자.
- HTML, XML 문서를 **객체(Object)**로 표현한 **트리 구조**.
- 웹 페이지의 구조화된 표현이며, **JavaScript를 통해 문서 구조, 스타일, 내용 등을 동적으로 조작**할 수 있음.



---

## 2. DOM 트리 구조
- HTML 문서는 DOM 트리로 변환됨.
- 각 HTML 요소는 **노드(Node)**로 표현됨.

### 노드 종류 알아보기기

| 노드 종류       | 설명                             |
|----------------|----------------------------------|
| Document 노드   | DOM 전체 문서의 루트 노드        |
| Element 노드    | HTML 요소를 나타내는 노드        |
| Text 노드       | 요소 내부의 텍스트               |
| Attribute 노드  | 요소의 속성                      |
| Comment 노드    | 주석 노드                        |

### 예시:
```html
<body>
  <h1>Hello</h1>
</body>
```

## 3. DOM 접근 방식
- document 객체
- 브라우저가 HTML 문서를 해석하여 제공하는 최상위 객체

### 주요 접근 메서드 
- getElementById(id) : ID로 요소 찾기
- getElementsByClassName(class) : 클래스 이름으로 요소 목록 찾기
- getElementsByTagName(tag) : 태그 이름으로 요소 목록 찾기
- querySelector(css) : css 선택자로 첫 번째 요소 찾기
- querySelectorAll(css) : css 선택자로 모든 요소 찾기

## 4. DOM 조작
- 속성 및 내용 변경
- 요소 추가 및 삭제

## 5. 이벤트 처리
- 사용자 동작 ( 클릭, 키보드 입력 등)을 감지하여 실행행