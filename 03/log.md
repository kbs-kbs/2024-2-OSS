## 여러 커밋과 로그 이력
### 깃 설정과 깃 저장소 설정
```
$ git config --global user.name ~
$ git config --global user.email ~
$ git config --global core.autocrlf true
$ git config --global user.name kbs-kbs
$ git config --global user.name kbs-kbs
$ git config --global user.name kbs-kbs

$ git init basic
cd basic
```


```
$ echo aaa > hello.txt
$ cat hello.txt
$ git status [--long]
$ git status -s
```

```

```

### 커밋과 로그 이력

`$ git log`: 여러 개의 로그 정보를 표시

|명령어|옵션|설명|
|---|---|---|
|git log|||
||||
||||

`$ git show`: 최신 커밋 또는 지정한 한 개의 로그 정보를 표시

### 스테이지 영역에 올린 파일 수정
`$ git status -s`를 했을 때 초록색 M이 스테이징 영역에 올라간 파일이 수정되었다는 의미.
빨간색 M은 작업 디렉토리에서 파일이 수정되었다는 의미.


### 커밋의 변경사항 

`$ git log --patch` 또는 `$ git log -p`


각 커밋의 변경사항을 확인