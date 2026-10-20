---
name: gh_cli
description: GitHub 저장소 생성, 커밋/푸시 백업, GitHub Pages 배포, 저장소 목록·인증 상태 확인을 gh CLI로 수행한다. "깃허브에 올려줘", "GitHub에 백업해줘", "푸시해줘", "저장소 만들어줘", "Pages 배포해줘", "깃허브 저장소 목록" 등의 요청 시 사용.
---

# GitHub 백업 스킬 (gh CLI)

이 스킬은 gh CLI를 사용하여 GitHub 저장소 관리 및 배포를 수행한다.
모든 명령어는 Bash 도구로 직접 실행한다.

- GitHub 사용자명: `hyeun2000`
- `gh` 명령을 찾지 못하면(PATH 미등록) 전체 경로로 실행한다:
  `"/c/Program Files/GitHub CLI/gh.exe"`

## 저장소 생성
gh repo create [저장소명] --public --description "[설명]"

## 로컬 초기화 및 첫 push
git init
git add .
git commit -m "[메시지]"
git branch -M main
git remote add origin https://github.com/hyeun2000/[저장소명].git
git push -u origin main

## 변경사항 백업 (커밋 + 푸시)
git add .
git commit -m "[메시지]"
git push

## GitHub Pages 배포 (GitHub Actions 방식)
1. .github/workflows/deploy.yml 워크플로우 파일 생성
2. 커밋 후 푸시
3. gh api repos/hyeun2000/[저장소명]/pages -X PUT -f build_type=workflow

## 저장소 목록 확인
gh repo list

## 인증 상태 확인
gh auth status
