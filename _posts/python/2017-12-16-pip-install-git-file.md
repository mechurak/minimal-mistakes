---
title: "PIP install from local git repository"
categories:
  - Python
tags:
  - Python
---

pip로 인스톨할 수 있는 파이썬 모듈 자체를 수정하고 싶을 때  
혹시 모르니까 기존 설치된 모듈은 지우고  
로컬 git repo 에서 설치해서 수정해보면 될 듯 하다.

윈도우에서 아래처럼 로컬 설치 가능

```bash
(C:\Anaconda3\envs\py27) C:\>pip install git+file://C:\Workspace_py\pyalgotrade
```

## Reference
- [PIP install from local git repository](http://www.developerfiles.com/pip-install-from-local-git-repository/)