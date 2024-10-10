리눅스 명령어

간편 파일 편집

$ echo a > f
$ echo b >> f
$ cat 파일명	파일의 내용을 화면에 표시합니다.
$ cat 파일1 >> 파일2	파일1의 내용을 파일2 끝에 연결합니다.
$ cat 파일1,파일2 ... 파일n > 새파일	파일 n개를 차례로 연결해서 새로운 파일을 생성합니다.


기본 설정

$ git config --system core.autocrlf true   
$ git config --system core.safecrlf false   
$ git config --global user.name hskang
$ git config --global user.email.hskang@gmail.com
$ git config --global init.defaultBranch main
$ git config --local core.editor 'code --wait'

저장소 생성

$ git init
= $ git init .
$ git init new-repo


