# svn to git

git 에선 svn에서 git으로 전환을 지원한다.
회사에서 svn repository를 git으로 전환할 일이 있어 다음 명령을 통해 svn 에서 git으로 전환 후 모든 branch를 밀어넣었다.
더 상세한 내용은 git-scm.com의 git으로 이전하기를 참고하면 된다.

1. svn user list 생성(users.txt)

   ```console
   $ svn log ^/ --xml | grep -P "^<author" | sort -u | \
         perl -pe 's/<author>(.*?)<\/author>/$1 = /' > users.txt
   ```

1. git repository 형식으로 svn repository clone하기

   ```shell
   git svn clone http://my-project.googlecode.com/svn/ --authors-file=users.txt --no-metadata -s my_project
   ```

1. svn tags branch를 git tag로 변환

   ```shell
   $ git for-each-ref refs/remotes/tags | cut -d / -f 4- | grep -v @ | \
      while read tagname; do git tag "$tagname" "tags/$tagname"; git branch -r -d "tags/$tagname"; done
   ```

1. 나머지 branch를 git branch로 만들기

   ```shell
   git for-each-ref refs/remotes | cut -d / -f 3- | grep -v @ | while read branchname; do git branch "$branchname" "refs/remotes/$branchname"; git branch -r -d "$branchname"; done
   ```

1. remote git repogitory 추가

   ```shell
   git remote add origin git@my-git-server:myrepository.git
   ```

1. 모든 branch, tag push

   ```shell
   git push origin --all
   ```

## 참고

1. [Git으로 이전하기](https://git-scm.com/book/ko/v1/Git%EC%9C%BC%EB%A1%9C-%EC%9D%B4%EC%A0%84%ED%95%98%EA%B8%B0-Git%EC%9C%BC%EB%A1%9C-%EC%98%AE%EA%B8%B0%EA%B8%B0)