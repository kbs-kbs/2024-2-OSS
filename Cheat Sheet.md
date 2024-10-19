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
Add a line # Ctrl + C
```

```bash
touch emptyfile1 emptyfile2
```

## 파일 내용 출력

```bash
cat file1 file2
```

## 파일 삭제

```bash
rm file1 file2
```

## 깃 단축 명령어 설정

```bash
git config 
```