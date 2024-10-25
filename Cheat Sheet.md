# 설정
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

<br>

## 단축 명령어 설정

```bash
git config alias.ci commit
git config alias.cm "commit -m"
git config alias.cam "commit -am"
```

<br>

# 저장소
## 저장소 생성
### 현재 폴더를 저장소로 만들기

```bash
git init [.]
```

### 현재 폴더 하위에 저장소 생성

```bash
git init new-repo
```

<br>

## 저장소 복제
### 현재 폴더 하위에 원격 저장소를 복제

```bash
git clone <url>
```

### 하위 폴더를 만들고 내부에 원격 저장소를 복제

```bash
git clone <url> new-dir
```

<br>

# 파일
## 파일 목록 출력
### 작업 디렉토리의 파일 목록 출력

```bash
ls [-a | -l | -al]
```

- `-a`: 숨긴 파일 포함
- `-l`: 자세히 보기

### 인덱스의 파일 목록 출력

```bash
git ls-files [-s | --stage]
```
- `-s`, `--stage`: SHA-1 해시 값도 출력

### 최신 커밋의 파일 목록 출력

```bash
git ls-tree [--name-only | --object-only] HEAD
```

- `--name-only`: 파일 이름만 출력
- `--object-only`: SHA-1 해시 값만 출력

<br>

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

<br>

## 파일 이름 변경

```bash
git mv file_from file_to
```

```bash
mv file_from file_to
git rm file_from
git add file_to
```

<br>

## 파일 내용 출력

```bash
cat file1 file2
```

<br>

## 파일 삭제
### 작업 디렉토리에서 삭제

```bash
rm file1 file2
```

### 인덱스에서 삭제

```bash
git rm --cached file
```

### 인덱스와 작업 디렉토리에서 모두 삭제

```bash
git rm file
```

<br>

## 파일 복구
### 작업 디렉토리의 파일을 스테이징 영역의 파일 상태로 복구

```bash
git restore file
```

### 작업 디렉토리의 파일을 HEAD 커밋의 파일 상태로 복구

```bash
git restore --source=HEAD file
```

### 스테이징 영역의 파일을 HEAD 커밋의 파일 상태로 복구

```bash
git restore --staged file
```

### 작업 디렉토리와 스테이징 영역의 파일을 HEAD 커밋의 파일 상태로 복구

```bash
git restore --source=HEAD --staged --worktree file
```

<br>

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

<br>

## 커밋

```bash
git commit [-a | -m | -am]
```

- `-a`: 한 번 add 되었던 파일을 add를 거치지 않고 커밋
- `-m '커밋 메시지'`: 커밋 메시지를 작성

<br>

## 저장소의 파일 상태 보기

```bash
git status
```

index(tracked) ⊇ staging area(staged)

### 결과

저장소와 스테이지를 비교한 것은 녹색으로, 스테이지와 작업 트리를 비교한 것은 빨강으로 표시됩니다.

|지역 저장소|스테이징 영역|작업 디렉토리|상태|
|---|---|---|---|
|X|X|O|`??`|
|X|O|O|`A[ \|M]`|
|X|O|X|`AD`|
|O|O|O|`[ \|M][ \|M]`|
|O|O|X|`[ \|M]D`|
|O|X|X|`D `|

- `??`: "Untracked files"
- `[A\|M\|D]*`: "Changes to be committed"
  - `A`: "new file"
  - `M`: "modified"
  - `D`: "deleted"
- `*[M\|D]`: "Changes not staged for commit"
  - `M`: "modified"
  - `D`: "deleted"
- `  `: "nothing to commit, working tree clean"

<br>

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

<br>

## 커밋 이력 보기

```bash
git log --all
```

- `--all`: 현재 브랜치에 관계 없이 모든 브랜치의 커밋 이력 보기
- `--oneline`: 커밋 하나당 한 줄로 표시
- `--graph`:

<br>

## 커밋 로드
### 이전 커밋 로드

```bash
git checkout HEAD[~|^]
```

### n 단계 이전 커밋 로드

```bash
git checkout HEAD[~|^]n
```

### 최신 커밋 로드

```bash
git checkout HEAD | main
```

### 특정 커밋으로 전환

```bash
git checkout <tag name> | <revision number>
```

> [!NOTE]
> 이전 커밋으로 이동하면 반드시 "detached HEAD" 상태가 됩니다.   
> Detached HEAD가 가리키는 커밋은 브랜치가 참조할 수 없게 됩니다. 따라서 간접 참조(HEAD~ 등)가 불가능합니다.   
> 하지만 해시 값으로 직접 참조할 수 있습니다.
> add, commit은 여전히 가능합니다.
> Attached HEAD는 항상 현재 브랜치의 최신 커밋을 가리킵니다.

<br>

## 저장소의 브랜치 목록 보기

```bash
git branch
```

<br>

# 브랜치
## 브랜치 생성
### 생성만

```bash
git branch br
```

### 생성과 이동

```bash
git checkout -b br
```

```bash
git switch -c br
```

<br>

## 브랜치 이동
### 기본 브랜치로 이동
```bash
git switch main
```

### 특정 브랜치로 이동

```bash
git switch br
```

### 이전 브랜치로 이동

```bash
git switch -
```

```bash
git checkout -
```

### ?

```bash
git switch --detach <tag name> | <revision number>
```

<br>

## 브랜치 이름 변경
### 현재 브랜치 이름 변경

```bash
git branch -m new-br
```

<br>

## 브랜치 삭제
### 특정 브랜치 삭제

```bash
git branch -d br
```

### 변경 사항이 있는 브랜치 강제 삭제

```bash
git branch -D new-br
```

> [!NOTE]
> 현재 브랜치는 삭제할 수 없습니다.

<br>

# 버전
## 태그

특정 커밋을 버전으로 사용하기

```bash
git tag
```
