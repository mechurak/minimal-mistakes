---
title: "GitHub fork 후 원본과 싱크 맞추기"
categories:
  - General
tags:
  - git
---

GitHub에서 fork 해온 저장소는 주기적으로 싱크를 맞춰줄 필요가 있다.

remote 에 원래 저장소를 upstream 이라는 이름으로 설정하고, 해당 remote 를 가져와서 merge 하는 개념이다.

```bash
$ git remote -v
origin  https://github.com/mechurak/mechurak.github.io.git (fetch)
origin  https://github.com/mechurak/mechurak.github.io.git (push)

# upstream 추가
$ git remote add upstream https://github.com/mmistakes/minimal-mistakes.git

$ git remote -v
origin  https://github.com/mechurak/mechurak.github.io.git (fetch)
origin  https://github.com/mechurak/mechurak.github.io.git (push)
upstream        https://github.com/mmistakes/minimal-mistakes.git (fetch)
upstream        https://github.com/mmistakes/minimal-mistakes.git (push)

# upstream fetch
$ git fetch upstream

# upstream/master 를 master에 merge
$ git checkout master
$ git merge upstream/master
$ git commit

# origin에 push
$ git push origin master
```

## Reference
- [GitHub fork 후 원본과 sync 맞추기, Pull과 Fetch의 차이](http://blog.naver.com/leejk9592/221016277032)
- <https://help.github.com/articles/syncing-a-fork/>
- <https://help.github.com/articles/configuring-a-remote-for-a-fork/>