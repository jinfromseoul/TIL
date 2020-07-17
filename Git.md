# Git

> Git은 분산버전관리시스템(DVCS)이다. Distributed Version Control System
>
> 소스코드의 버전 및 이력을 관리할 수 있다. 

## 준비하기

 윈도우에서 git을 활용하기 위해서 git bash를 설치한다. 

git을 활용하기 위해서 GUI툴인 `source tree, github desktop` 등을 활용할 수도 있다. 

초기 설치를 완료한 이후에 컴퓨터에 author 정보를 입력한다. 

```bash
$ git config --global user.name {user name}
$ git config --global user.email {user email}
```



##  로컬 저장소(Repository) 활용하기

### 1. 저장소 초기화

```bash
$ git init
Initialized empty Git repository in C:/Users/jinyoung/storage/.git/
```

- `.git` folder has created, all information related git will be saved in this folder.
- git bash 에 `(master)` 라고 표시되는데, 이는 현재 폴더가 git으로 관리되고 있다는 뜻이며, `master` branch에 있다는 뜻이다. 

### 2. `Add`

`working directiory`,즉 작업 공간에서 변경된 사항을 이력으로 저장하기 위해서는 반드시 `staging area`를 거쳐야 한다.

```bash
$ git add {files/folders}
$ git add filename.md      # file
$ git add folder/          # folder (folders must include /)
$ git add .  			   # All files and folders in current directory
```

- `markdown.md` file has created in folder but has not been managed by git, `add` 전 상태

```bash
$ git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        markdown.md
nothing added to commit but untracked files present (use "git add" to track)
```

- `markdown.md` file has been add and been up to staging area

```bash
$ git status 
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   markdown.md
```



### 3. Commit

commit은 **이력을 확정짓는 명령어**로, 해당 시점의 스탭샷을 기록한다. 

You must put messages when commit, messages must be written clearly to recognize tasks.

```bash
$ git commit -m "마크다운 정리"
[master (root-commit) 6c84015] 마크다운 정리
 1 file changed, 170 insertions(+)
 create mode 100644 markdown.md
```

커밋 이후에는 아래의 명령어를 통해 지금까지 작성도니 커밋 이력을 확인한다. 

```bash 
$ git log
commit 6c840158f44a51f40c02f08d226289d899a6c904 (HEAD -> master)
Author: edujason-hphk <edujason.hphk@gmail.com>
Date:   Fri Jul 17 14:17:22 2020 +0900

    마크다운 정리
    
$ git log --oneline
6c84015 (HEAD -> master) 마크다운 정리
```

커밋은 해시값을 바탕으로 구분된다. 



### 원격 저장소(Remote Repository) 활용하기

원격 저장소 기능을 제공하는 다양한 서비스 중에 `github`을 기준으로 설명한다. 

#### 0. 준비사항

- Github에 repository 생성

#### 1. 원격 저장소 등록

```bash
$ git remote add origin {githun url}
```

- 원격 저장소(remote)를 origin이라는 이름으로 github url을 등록(add)한다.
- 등록된 원격 저장소를 보기 위해서는 아래의 명령어를 활용한다. 

```bash
$ git remote -v


```



#### 2. Push - 원격 저장소로 업로드

```bash
$ git push origin master
```

`origin`이라는 이름의 원격 저장소로 commit 기록들을 업로드한다. 

이후 변경사항이 생길 때마다, `add` - `commit` - `push`를 반복한다. 



