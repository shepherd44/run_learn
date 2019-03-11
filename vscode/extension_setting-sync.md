# [vscode-extension] Settings Sync

Synchronize Settings, Snippets, Themes, File Icons, Launch, Keybindings, Workspaces and Extensions Across Multiple Machines Using GitHub Gist.

* [VS Marketplace Link](https://marketplace.visualstudio.com/items?itemName=Shan.code-settings-sync)

## 설정 방법

### 최초 등록 시

1. github에서 token 생성

   * 생성 시 gitst 권한만 주면 된다.
   * 다른 개발 환경에서 받을 때 해당 토큰과 gist id가 필요하므로 해당 토큰은 따로 기록해주자.
   * token의 경우 생성 당시에만 확인 가능하므로 잃어버릴 경우 재발급을 해야한다.

1. vscode_command_pallet> Sync: update/upload setting 선택

1. github에서 생성한 token을 삽입하면 gist로 현재 setting을 저장한다.

   * 업로드 시 gist를 생성하는데 해당 gist의 id를 기록해두자.
   * 기록하지 않은 경우 github에서 확인 가능하니 token과 달리 걱정할 필요 없음.

### 다른 환경에서 셋팅 가져오기

1. 다른 개발 환경에서 settins sync를 설치한 다음 아래 커맨드 선택

   * vscode_command_pallet> Sync: download settings

1. 생성해둔 token 입력

1. 생성된 gist id 입력

   * gist id가 기억나지 않는다면 gist에 로그인 하여 생성된 cloudSettings의 id를 입력하면 된다.
   * gist id는 url로 확인
      * ex) https://gist.github.com/shepherd44/7d48d76bf4a7de28719733d0e434b050
        에서 뒤의 7d48d76bf4a7de28719733d0e434b050 가 gist id가 된다.

1. setting이 다운로드 되며, extention들이 자동으로 설치된다.

### 팁

* 워크스페이스의 설정은 동기화 되지 않음.