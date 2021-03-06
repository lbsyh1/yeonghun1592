## 요약: 도메인의 최상위(root)에 있지 않은 사이트를 만드려면 baseurl을 사용하세요.

Jekyll의 설정 중 하나인 baseurl은 몇가지 모호한 부분이 있습니다. 많은 유연성이 있다는 것은 오픈소스의 아름다움 중 하나이고 또한 Jekyll에도 해당됩니다. 불행히도 baseurl은 이러한 유연성과는 거리가 멉니다. 여기에 그 사용의도를 빠르게 파악하고 사용하는 방법을 설명합니다.

# GitHub Pages 모방하기
baseurl은 2010년에 최초로 추가되었는데 그 의도는 다음과 같습니다. “내부 웹서버를 이용하여 테스트하는 유저가 프로덕션에 배포될 때와 같은 baseurl을 가지고 테스트 할 수 있도록 하기 위해”1

# 예제
![https://kairos03.github.io/assets/img/posts/jekyll/2017-09-11-learing-Up-Confusion-Around-baseurl/1.png)

자! 이제 아주 멋진 새로운 프로젝트를 시작한다고 가정해 봅시다. 나는 그 프로젝트의 문서를 “example”이라는 곳에 만들고 싶고, “@jekyll”이라는 이름으로 GitHub-Page에 배포 하고 싶습니다. 이 문서는 다음 URL로 접근이 가능할 것입니다. http://jekyll.github.io/example

이 예제에서 “base URL”은 /example을 뜻합니다. 또한 그것은 _config.yml 파일에 다음과 같이 정의되어 있습니다.

baseurl: /example
웹사이트를 개발하려 할 때는 보통과 같이 jekyll serve를 실행시킵니다. 그러나 이번에는 http://localhost:4000/example/로 들어갑니다. baseurl은 사이트가 존재하는 도메인에 상대적인 기본 경로를 지정합니다. 만약 http://localhost:4000/으로 접근을 시도했다면 에러메시지를 볼 수 있을 것입니다. 모든 링크를 올바르게 걸었다면 경로의 시작 부분에 /example이 없는 URL은 절대 볼수 없을 것입니다.
경로는 다음과 같이 설정할 수 있을 것입니다.

{{ page.path | prepend: site.baseurl }}
# 사이트를 올바르게 설정하기
_config.yml파일에 baseurl을 설정합니다. 단, host는 제외해야 합니다. (e.g. /example이 맞고, http://jekyll.github.io/example은 틀린설정입니다.)
jekyll serve를 실행하고, http://localhost:4000/your_baseurl/에서 your_baseurl을 _config.yml에서 설정한 baseurl로 바꾼주소로 들어가세요. 주소 맨마지막에 /를 써 넣는것을 잊지 마세요.
모든것이 작동하는지 확인하세요. 언제든지 url에 site.baseurl을 prepend하세요.
host에 push하고 그 곳에서도 모든것이 작동하는지 확인하세요!
# 그럼 도데체 site.url은 무엇일까?
site.url은 site.baseurl과 함께 전체 URL이 포함 된 링크를 원할 때 사용됩니다. 일반적인 패러다임 중의 하나 입니다.

#출처
[baseurl과 관련된 모호한 것들 정리](https://kairos03.github.io/jekyll/2017/09/11/learing-Up-Confusion-Around-baseurl.html)
