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

```bash
git init
# 또는
git init .
```

```bash
git init new-repo
```

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

## 파일 목록 출력
### 작업 디렉토리

```bash
ls [-a | -l | -al]
```

[숨긴 파일 보기 | 자세히 보기 | 둘 다]

### 스테이징 영역

```bash
git ls-files [-s / --stage]
```
- `-s`, `--stage`: SHA-1 해시 값도 출력

### 깃 저장소(로컬 리포지토리)

```bash
git ls-tree [--name-only | --object-only] HEAD
```

- `--name-only`: 파일 이름만 출력
- `--object-only`: SHA-1 해시 값만 출력

## 파일 내용 출력

```bash
cat file1 file2
```

## 파일 삭제
### 작업 디렉토리에서

```bash
rm file1 file2
```

### 스테이징 영역에서

```bash
git rm --cached file1
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

