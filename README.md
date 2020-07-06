# Tag & Release 사용법

## 1. tag 사용하기!
태그는 간단하게 말하면 이름을 붙이는 것 입니다.   
태그를 사용하면 운영 및 배포에서 커밋 메시지 또는 브랜치로 해서 표시하는 것 보다 효과적으로 버전을 관리할 수 있습니다.   

그 이유는 태그명을 배포 버전으로 정하고 간략한 정보를 함께 저장할 수 있기때문입니다.   
또, 한 번 붙인 태그는 브랜치처럼 위치가 이동하지 않고 고정되어 태그를 사용해 원하는 태그로 돌아갈 수 있습니다.   
</br>
> Git 에서는 일반적으로 이름 정보만을 갖는 '태그(Lightweight tag)'와 보다 상세한 정보를 포함하는 > '주석 태그(Annotated tag)', 이 두 가지 태그를 사용할 수 있습니다.
</br>

### 태그 추가!
태그는 tag 명령어를 이용하여 추가 가능합니다.    
Lightweight 태그는 ``` git tag [Tag Name] ``` 으로 붙일 수 있습니다.   

    # git tag v1.0

Annotated 태그는 -a 옵션을 사용합니다. 메시지를 추가할 경우 -m 옵션을 추가 사용합니다.   

    # git tag -a v1.0 -m"Release version 1.0"

<img src="/img/tag.jpg"/>

<!-- <출처>
https://backlog.com/git-tutorial/kr/stepup/stepup4_1.html
http://minsone.github.io/git/git-addtion-and-modified-delete-tag
https://webisfree.com/2017-07-31/git-%ED%83%9C%EA%B9%85%ED%95%98%EA%B8%B0-tag-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0 -->