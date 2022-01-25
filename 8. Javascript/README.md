# Javascript
## ready, load 차이
### document.ready(), $(document).ready()
- 외부 리소스, 이미지와는 상관없이 브라우저가 DOM(document object model)트리를 생성한 직후 실행
- window.load()보다 더 빠르게 실행되고 중복 사용하여 실행해도 선언한 순서대로 실행됨

### window.load, $(window).load()
- DOM의 standard 이벤트
- html의 로딩이 끝난 후에 시작
- 화면에 필요한 모든 요소(css, js, image, iframe etc, ...)들이 웹 브라우저 메모리에 모두 올려진 다음에 실행됨
- 화면이 모두 그려진 다음의 메세징이나 이미지가 관련 요소가 모두 올려진 다음의 애니메이션에 적합함
- 전체 페이지의 모든 외부 리소스와 이미지가 브라우저에 불려온 이후 작동하게 되어 이미지가 안뜨거나 딜레이가 생길 때에는 그만큼의 시간을 기다려야 함
- 외부 링크나 파일 인크로트시 그 안에 window.load 스크립트가 있으면 둘 중 하나만 적용됨ㅈ
- body onload 이벤트와 같이 body에서 onload 이벤트를 쓰게 되면 모든 window.load()가 실행되지 않는 현상이 발생함

※ window > document
- document는 window의 자식 객체
  - window의 자식 객체 : document, self, navigator, screen, forms, history, location ...
- document : html의 요소들이나 속성들에 접근할 시 사용하는 객체

# Jquery
 







