# visual studio code python setting

extention install

* python
* python extention pack
* python extended
* python snippets
* magicpython

## lint

* PEP8 추천(for intellisense)

  ```bash
  pip install pep8
  ```

### rulers

editor에 80 character ruler 추가
User setting에 rulers 옵션 추가

* 옵션 창 열기
  * 옵션(File > Preference > setting)
  * command pallet: Preference: Open User Setting
* ruler 검색 후 옵션 추가(settings.json)

  ``` json
  {
    "editor.rulers": [80, 120]
  }
  ```

### flask

### PyQt5 lint setting

* python extention 설치 시 jedi를 지원하며, jedi 내부에 PyQt5 린트가 가능하다
* 대신 linter를 PEP8로 써야 가능

## ref

* [visual code - python](https://code.visualstudio.com/docs/python/python-tutorial)
* [visual code - customizing-intellisense](https://code.visualstudio.com/docs/editor/intellisense#_customizing-intellisense)
* [PyQt5 lint error issue](https://code.visualstudio.com/docs/editor/intellisense#_customizing-intellisense)
* [jedi git](https://github.com/davidhalter/jedi)