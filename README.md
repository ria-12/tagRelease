# Release & Tag 사용법 v2.0

## 1. tag 사용하기!
태그는 간단하게 말하면 이름을 붙이는 것 입니다.   
태그를 사용하면 운영 및 배포에서 커밋 메시지 또는 브랜치로 해서 표시하는 것 보다 효과적으로 버전을 관리할 수 있습니다.   

그 이유는 태그명을 배포 버전으로 정하고 간략한 정보를 함께 저장할 수 있기때문입니다.   
또, 한 번 붙인 태그는 브랜치처럼 위치가 이동하지 않고 고정되어 태그를 사용해 원하는 태그로 돌아갈 수 있습니다.   
</br>
> Git 에서는 일반적으로 이름 정보만을 갖는 '태그(Lightweight tag)'와 보다 상세한 정보를 포함하는 '주석 태그(Annotated tag)', 이 두 가지 태그를 사용할 수 있습니다.
</br>

### ● 태그 추가
태그는 tag 명령어를 이용하여 추가 가능합니다.    
Lightweight 태그는 ``` git tag [Tag Name] ``` 으로 붙일 수 있습니다.   
```bash
    $ git tag v0.1
```
Annotated 태그는 -a 옵션을 사용합니다. 메시지를 추가할 경우 -m 옵션을 추가 사용합니다.   
```bash
    $ git tag -a v0.1 -m "version 0.1"
```
-------------
### ● 태그 확인
-n 옵션을 지정하여 tag 명령어를 실행하면 태그 목록과 주석 내용을 확인할 수 있습니다.
```bash
    $ git tag -n
```
<img src="/img/tag-n.PNG"/>

show 옵션을 사용하면 태그의 세부 정보를 볼 수 있습니다.
```bash
    $ git show v0.1
```
   
-------------
### ● 태그 원격 저장소에 올리기
```bash
    $ git push origin v0.2
```
모든 태그를 올리려면 ```--tags```를 사용
```bash
    $ git push origin --tags 
```
   
-------------
### ● 태그 삭제하기
-d 옵션을 추가하여 사용
```bash
    $ git tag -d v0.2
```

원격 저장소에 올라간 태그 삭제
```bash
    $ git push origin :v0.2
```
-------------
### ● 태그로 branch 생성
```bash
    $ git branch release-v1.1 v1.0
```
</br>

## 2. Release Branch란?
Release Branch는 배포를 위한 전용 브랜치 입니다.
이름은 보통 'release-'를 앞에 붙입니다.
release를 위한 최종적인 버그 수정 등의 개발을 수행하며, 모든 기능이 정상적으로 동작하는지 확인 후 배포 가능 상태가 되면 master 브랜치에 병합합니다. 배포 완료 후 develop 브랜치에도 병합을 수행합니다.   
</br>

> master로 병합한 커밋에 해당 버전 태그를 추가합니다.
</br>

### ● release flow

<img src="/img/release_branch.PNG"/>

</br>

## 3. tag를 활용한 release하기!

이제 tag와 함께 release를 해보겠습니다.
먼저 ``` develop ``` branch 에서 release branch를 생성합니다.
```bash
    $ git checkout -b release-1.0 develop
```
이 후, 배포 가능 상태가 되면 ``` master ``` branch에 병합합니다.

```bash
    $ git checkout master

    $ git merge release-1.0
```
release 버전의 태그를 붙여줍니다.    
보통 '릴리스 브랜치(Release branch)'에서는 주석 태그를 사용합니다.

```bash
    $ git tag -a v1.0 -m "version 1.0"
```
배포 완료 후 develop 브랜치에도 병합을 수행합니다.

```bash
    $ git checkout develop

    $ git merge release-1.0
```

release branch를 삭제합니다.

```bash
    $ git branch -d release-1.0
```
        
</br>

## 4. Github Release!
방금 만든 v1.0 태그로 Github를 사용해 봅시다!
release에 들어가면 생성한 ``` v1.0 ```이 있음을 확인할 수 있습니다.

<img src="/img/tag_v1.0.PNG"/>

[Draft a new release]를 눌러 들어갑니다.

<img src="/img/release_draft.png"/>

위에서부터 채워나갑니다.

- 사용할 태그 이름 입력
- title 입력
- describe 입력
- 추가 파일 attach

아직 안정적이지 않은 release면 해당 체크박스를 클릭합니다.   
release 버튼을 누르면 다음과 같이 완료됩니다.
<img src="/img/release_finish.png"/>

</br>

## 5. References
> https://backlog.com/git-tutorial/kr/stepup/stepup4_1.html
> http://minsone.github.io/git/git-addtion-and-modified-delete-tag
> https://webisfree.com/2017-07-31/git-%ED%83%9C%EA%B9%85%ED%95%98%EA%B8%B0-tag-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0
>    
> https://gmlwjd9405.github.io/2018/05/11/types-of-git-branch.html
> https://mobicon.tistory.com/117?category=527260
> https://backlog.com/git-tutorial/kr/stepup/stepup1_5.html
