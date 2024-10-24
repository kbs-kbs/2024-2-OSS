## 기본 설정

```bash
git config --system core.autocrlf true
```

```bash
git config --system core.safecrlf false
```   

```bash
git config --global user.name kbs-kbs
```

```bash
git config --global user.email yaglus58@gmail.com
```

```bash
git config --global init.defaultBranch main
```

```bash
git config --local core.editor "code --wait"
```

## 저장소 생성
### 현재 폴더를 저장소로 만들기

```bash
git init [.]
```

### 현재 폴더 하위에 저장소 생성

```bash
git init new-repo
```

## 저장소 복제
### 현재 폴더 하위에 원격 저장소를 복제

```bash
git clone <url>
```

### 하위 폴더를 만들고 내부에 원격 저장소를 복제

```bash
git clone <url> new-dir
```

## 파일 목록 출력
### 작업 디렉토리의 파일 목록 출력

```bash
ls [-a | -l | -al]
```

- `-a`: 숨긴 파일 포함
- `-l`: 자세히 보기

### 스테이징 영역의 파일 목록 출력

```bash
git ls-files [-s / --stage]
```
- `-s`, `--stage`: SHA-1 해시 값도 출력

### 리포지토리의 파일 목록 출력

```bash
git ls-tree [--name-only | --object-only] HEAD
```

- `--name-only`: 파일 이름만 출력
- `--object-only`: SHA-1 해시 값만 출력


## 파일 생성

```bash
echo "1st version" > file1
```

```bash
echo "Add a line" >> file1
```

```bash
cat > file2
1st version # Enter
Add a line # Ctrl + D: 현재 행 저장 종료 / Ctrl + C: 현재 행 취소 종료
```

```bash
touch emptyfile1 emptyfile2
```

## 파일 내용 출력

```bash
cat file1 file2
```

## 파일 삭제
### 작업 디렉토리에서 삭제

```bash
rm file1 file2
```

### 스테이징 영역에서 삭제

```bash
git rm --cached file
```

### 작업 디렉토리와 스테이징 영역에서 모두 삭제

```bash
git rm file
```

## 파일 복구
### 작업 디렉토리의 파일을 스테이징 영역의 파일 상태로 복구

```bash
git restore file
```

### 스테이징 영역의 파일을 HEAD 커밋의 파일 상태로 복구

```bash
git restore --staged file
```

### 작업 디렉토리와 스테이징 영역의 파일을 HEAD 커밋의 파일 상태로 복구

```bash
git restore [--source=HEAD] --staged --worktree file
```


## 깃 단축 명령어 설정

```bash
git config alias.ci commit
git config alias.cm "commit -m"
git config alias.cam "commit -am"
```

## 스테이징 영역에 추가
### 작업 디렉토리의 모든 파일

```bash
git add --all | -A
```

### 현재 디렉토리의 모든 파일(ex: 작업 디렉토리 하위의)

```bash
git add .
```

### 특정 파일

```bash
git add [path/]file1
```

### 와일드카드

```bash
git add [path/]file*
```

## 커밋

```bash
git commit [-a | -m | -am]
```

- `-a`: 한 번 add 되었던 파일을 add를 거치지 않고 커밋
- `-m '커밋 메시지'`: 커밋 메시지를 작성

## 영역 비교
### 작업 디렉토리와 스테이징 영역 비교

```bash
git diff
```

### 작업 디렉토리와 깃 저장소 비교

```bash
git diff HEAD
```

### 스테이징 영역과 깃 저장소 비교

```bash
git diff --staged HEAD
```

Note: switching to 'HEAD~2'.
You are in 'detached HEAD' state. ...


## 커밋 이력 보기

```bash
git log --all
```

- `--all`: 현재 브랜치에 관계 없이 모든 브랜치의 커밋 이력 보기
- `--oneline`: 커밋 하나당 한 줄로 표시
- `--graph`:

## 커밋 전환
### 한 단계 이전 버전으로 전환

```bash
git checkout HEAD~
```

### n 단계 이전 버전으로 전환

```bash
git checkout HEAD~n
```

### 최신 버전으로 전환

```bash
git checkout HEAD | main
```

### 특정 버전으로 전환

```bash
git checkout <tag name> | <revision number>
```

> [!NOTE]
> 이전 커밋으로 이동하면 반드시 Detached HEAD 상태가 됩니다.   
> Detached HEAD가 가리키는 커밋은 브랜치가 참조할 수 없게 됩니다. 따라서 간접 참조(HEAD~ 등)가 불가능합니다.   
> 하지만 해시 값으로 직접 참조할 수 있습니다.
> add, commit은 여전히 가능합니다.
> Attached HEAD 상태에서는 HEAD가 항상 현재 체크아웃된 브랜치의 가장 최신 커밋을 가리키고 있습니다.

## 브랜치 생성

```bash
git branch hotfix
```

```bash
git checkout -b hotfix
```

```bash
git switch -c hotfix
```

### 브랜치 목록 보기

```bash
git branch
```



## 브랜치 이동

### 기본 브랜치로 이동
```bash
git switch main
```



```bash
git switch --detach <tag name> | <revision number>
```

## 태그

특정 커밋을 버전으로 사용하기

```bash
git tag
```
