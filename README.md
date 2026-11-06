# Git 실습 환경 구성 및 실습
실습 날짜 : 2026.11.06.

최종 프로젝트에서 Git을 활용하기 위해, 실습 환경을 구성하고 실습을 진행했다.

## 파이썬 가상환경 생성
```cmd
python -m venv .venv
```

## 가상환경 활성화
```cmd
.venv\Scripts\Activate.bat
```

## 프로젝트 디렉토리 및 파일 구조
```
my-git-project/ 
├── .idea/              # (IDE 설정 폴더 - .gitignore 테스트용)
│   └── workspace.xml 
├── .venv/              # (가상환경 폴더 - .gitignore 테스트용) 
│   └── pyvenv.cfg 
├── pybo/ 
│   └── templates/ 
│       ├── question_list.html
│       └── question_detail.html 
│       
├── .gitignore          # 깃 추적 제외 설정 파일
└── pybo.db             # (DB 파일 - .gitignore 테스트용)
```

## 실습 전 필수 환경 설정 (Git Initial Setup)
실습 명령어를 치기 전, terminal/bash 환경에서 사용자 인증 정보와 기본 브랜치 이름을 미리 설정하여 오류를 방지한다.
```powershell
# 1. 사용자 이메일 및 이름 설정 (최초 1회 실행 시 필수)
git config --global user.email "youremail@example.com"
git config --global user.name "YourName"

# 2. 기본 브랜치명을 main으로 설정
git config --global init.defaultBranch main
```

## 명령어 실습
```powershell
# 1. 저장소 초기화 및 상태 확인
git init
git status

# 2. 안전한 스테이징 및 첫 커밋
git add .
git status
git commit -m "프로젝트 최초 커밋"

# 3. 파일 수정 및 복구/커밋 실습
# (1) question_list.html 내용 수정 후 상태 확인
git status
git diff

# (2) 변경사항 취소/복구
git restore pybo/templates/question_list.html
git commit -m "질문 목록 문구 수정"

# 4. 실수로 .idea가 추가되었을 경우를 대비
# git rm -r --cached .idea
# git commit -m "Tracked .idea directory removed"

# 5. GitHub 원격 저장소 연결 및 푸시 (최신 main 브랜치 기준)
git remote add origin https://github.com/본인계정/저장소명.git
git branch -M main

git push -u origin main
```
