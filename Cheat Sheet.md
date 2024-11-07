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

# 지역 저장소로 시작
## 저장소 생성
### 현재 폴더를 저장소로 만들기

```bash
git init [.]
```

### 현재 폴더 하위에 저장소 생성

```bash
git init repo
```

<br>

# 원격 저장소로 시작
## 원격 저장소 복제
### 현재 폴더 하위에 원격 저장소를 복제

```bash
git clone <url>
```

### 하위 폴더를 만들고 내부에 원격 저장소를 복제

```bash
git clone <url> dir
```

<br>

## 원격 저장소 별칭 출력

```bash
git remote [-v]
```

- `-v`: 주소도 출력

<br>

## 원격 저장소 별칭 변경

```bash
git remote rename origin org
```

<br>

## 원격 저장소 정보 출력

```bash
git remote show origin
```

### 결과

- `(up to date)`: 지역 저장소의 상태가 원격 저장소와 동일
- `(local out of date)`: 원격 저장소에 변경 사항이 있음 (pull 필요)
- `(local ahead)`: 지역 저장소에 변경 사항이 있음 (push 필요)
- `(local diverged)`: 지역 저장소와 원격 저장소에 서로 다른 변경 사항이 있음 (pull, push 필요)

<br>

## 원격 저장소 연결 해제

```bash
git remote rm orgin
```

<br>

## pull

연결된 원격 저장소의 변경 사항을 브랜치에 적용합니다.

```bash
git pull origin main
```

```bash
git fetch origin
git merge origin/main
```

<br>

## push

지역 저장소의 변경 사항을 원격 저장소에 적용합니다. (깃허브에 로그인 또는 PAT 필요)

```bash
git push origin main [-u]
```

- `-u`: 다음부터 인자를 생략하여 `git push`로 푸시가 가능해집니다.

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
git restore [--source=HEAD] --staged file
```

### 작업 디렉토리와 스테이징 영역의 파일을 HEAD 커밋의 파일 상태로 복구

```bash
git restore [--source=HEAD] --staged --worktree file
```

<br>

## 스테이징 영역에 추가
### 작업 디렉토리의 모든 파일

```bash
git add --all|-A
```

### 현재 디렉토리와 하위의 모든 파일

```bash
git add .
```

### 현재 디렉토리의 특정 파일

```bash
git add file
```

<br>

# 커밋
## 커밋 하기

```bash
git commit [-a|-m|-am]
```

- `-a`: 스테이징 영역의 unstaged 상태의 파일을 staged 상태를 거치지 않고 커밋
- `-m <message>`: 커밋 메시지를 작성

<br>

## 커밋 이력

현재 브랜치의 커밋 이력을 출력합니다.

```bash
git log [--all|--oneline|--graph]
```

- `--all`: 모든 브랜치의 커밋 이력 출력
- `--oneline`: 각 커밋을 한 줄로 표시
- `--graph`: 시각화하여 보여줍니다.

## 커밋 정보

```bash
git show <commit-hash>
```

- `HEAD`: 최신 커밋의 정보 확인(기본값)

<br>

## 커밋 이동
### 이전 커밋 이동

```bash
git checkout HEAD[~|^]
```

### n 단계 이전 커밋 이동

```bash
git checkout HEAD[~|^]n
```

### 최신 커밋 이동

```bash
git checkout HEAD | main
```

### 특정 커밋 이동

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

# 커밋에 버전 이름 붙이기
## 태그

특정 커밋을 버전으로 사용하기

```bash
git tag
```

<br>

# 추적 상태 확인

영역을 비교하여 추적 상태를 보여줍니다.

```bash
git status [-s]
```

`-s`: 추적 상태를 두 개의 문자로 간략히 표시합니다.

## 결과 의미

- "Untracked files": 작업 디렉토리에 깃이 추적하지 않는 파일 있음
- "Changes to be committed": 스테이지 영역에 변경 사항 있음
  - "new file": 새로운 파일
  - "modified": 수정된 파일
  - "deleted": 삭제된 파일
- "Changes not staged for commit": 작업 디렉토리에 변경 사항 있음
  - "modified": 수정된 파일
  - "deleted": 삭제된 파일
- "nothing to commit, working tree clean": 모든 영역이 동일함

## 간략히 표시된 결과 의미

첫 번째 문자(초록)는 저장소와 스테이지를 비교한 결과이며, 두 번째 문자(빨강)는 스테이지와 작업 트리를 비교한 결과입니다.   
이것으로 추적 상태를 판단할 수 있습니다.   

|지역 저장소|스테이징 영역|작업 디렉토리|상태|
|---|---|---|---|
|X|X|O|`??`|
|X|O|O|`A[ \|M]`|
|X|O|X|`AD`|
|O|O|O|`[ \|M][ \|M]`|
|O|O|X|`[ \|M]D`|
|O|X|X|`D `|

- `??`: "Untracked files"
- `[A|M|D]_`: "Changes to be committed"
  - `A`: "new file"
  - `M`: "modified"
  - `D`: "deleted"
- `_[M|D]`: "Changes not staged for commit"
  - `M`: "modified"
  - `D`: "deleted"
- `  `: "nothing to commit, working tree clean"

<br>

# 비교
## 파일 비교
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
git diff --staged [HEAD]
```

## 커밋 비교

```bash
git diff HEAD HEAD^2
```

```bash
git diff hash1 hash2
```

<br>


# 브랜치
## 브랜치 목록 출력

```bash
git branch [--all]
```

- `--all`: 원격 저장소와 연결된 브랜치도 출력합니다.

<br>

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

# 임시 저장소(스태시)

작업 디렉토리 또는 스테이지 영역에 변경 사항이 있으면 커밋 이동이나 브랜치 이동을 못합니다. 이럴 때는 임시 저장소에 변경 사항을 저장하고 필요할 때 복원할 수 있습니다.

## 임시 저장

```bash
git stash [save|-m]
```

- `save|-m 메시지`: 메시지를 함께 저장합니다.

> [!NOTE]
> 명령어를 실행하면 작업 디렉토리의 변경 사항과 스테이징 영역의 변경 사항이 모두 하나의 임시 저장 항목으로 합쳐집니다.

## 임시 저장 목록 확인

```bash
git stash list
```

## 임시 저장 파일 확인

```bash
git stash show [stash@{n}]
```

- `stash@{0}`: 기본 값이며 생략 가능합니다.

## 임시 저장된 변경 사항 적용
### 임시 저장 항목을 작업 디렉토리에 적용

```bash
git stash apply [stash@{n}] 
```

### 임시 저장 항목을 작업 디렉토리와 스테이징 영역에 모두 적용

```bash
git stash apply --index [stash@{n}] 
```

### 결과

- `AA`: "both added"

> [!NOTE]
> git stash apply 후에 스테이징 영역과 헤드를 비교하기 위해 $ git diff --staged 명령어를 사용했는데 비교 결과가 나오지 않고 * Unmerged path f3 이런 결과가 나오는 이유
> 깃의 충돌 판정은 메타데이터로 판단하기 때문에 적용하려는 파일의 내용이 비어있더라고 충돌이 발생할 수 있습니다.
> 즉, 임시 저장 후 임시 저장한 원본을 한 번이라도 수정하게 되면 충돌이 발생합니다.
 
## 임시 저장 항목 적용 후 삭제

```bash
git stash pop [stash@{n}]
```

## 임시 저장 항목 삭제
### 최신 또는 특정 항목 삭제

```bash
git stash drop [stash@{n}]
```

### 전부 삭제

```bash
git stash clear
```
