---
layout: single
title:  "fine_tuning"
categories: fine_tuning
# tags: [Daily_Record]
toc: true
author_profile: false
sidebar:
    nav: "docs"
---

# Trouble Shooting

## Git

- 로컬의 깃 디렉토리를 최신화 하고자 할 때 git pull 명령어를 쓰면 레거시 데이터는 제거되지 않았다. 이에 디렉토리를 전체 삭제한 뒤 git clone을 새로 받곤 했는데 이를 해결할 방안을 찾았다.
- 작업 디렉토리의 변경 내용과 스테이징 영역의 변경 내용을 모두 제거하고 이전 커밋의 상태로 완전히 초기화한다.
- 작업 디렉토리에서 추적되지 않은 파일 및 디렉토리를 제거한다.

```
git reset --hard
git clean -fd
git pull origin master
```

## requirements.txt

- 아래 에러는 GPT2 pre-trained 모델을 쓰기 위한 PyTorch 라는 패키지가 설치되지 않아 발생한 에러였다. 단어 그대로 PyTorch라는 패키지를 설치했지만 해결되지 않아 다양한 시도를 했다.

```
ImportError:
GPT2LMHeadModel requires the PyTorch library but it was not found in your environment. Checkout the instructions on the
installation page: https://pytorch.org/get-started/locally/ and follow the ones that match your environment.
```

- 아래와 같이 requirements에 torch를 추가하니 해결되었다.

```
uvicorn==0.23.2
fastapi==0.104.0
jinja2
requests==2.31.0
transformers==4.11.3
torch==1.10.0
```
