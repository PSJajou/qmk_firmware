# QMK Docs 번역하기

루트 폴더(`docs/`)의 모든 파일은 영어로 작성되어 있어야 하며, 타 언어의 파일들은 ISO 639-1 언어코드와 관련 국가코드로 이뤄진 이름의 하위폴더에 위치해야 합니다. [언어/국가 코드는 이곳에서 확인할 수 있습니다.](https://www.andiamo.co.uk/resources/iso-language-codes/).해당 폴더가 없다면 직접 생성하셔도 되며, 번역된 파일들은 영어버전과 같은 파일명을 가져야 합니다.

`_summary.md` 파일은 각 파일에 대한 링크 목록으로, 다음과 같이 각 링크는 해당 언어 폴더의 파일을 가리키도록 수정되어야 합니다.


```markdown
 * [QMK简介](zh-cn/getting_started_introduction.md)
```

다른 문서를 향하는 모든 링크들 역시 해당 언어의 폴더 내에서 작동하도록 지정되어야 하며, 페이지의 특정 파트를 가리키는 링크는 다음과 같이 영어ID를 사용합니다.

```markdown
[建立你的环境](zh-cn/newbs-getting-started.md#set-up-your-environment)

## 建立你的环境 :id=set-up-your-environment
```

새 언어의 번역을 끝내면, 다음 파일들 역시 수정해야 합니다.

* [`docs/_langs.md`](https://github.com/qmk/qmk_firmware/blob/master/docs/_langs.md)  
  각 줄에는 다음과 같이 언어명 뒤에 [GitHub emoji shortcode](https://github.com/ikatyang/emoji-cheat-sheet/blob/master/README.md#country-flag) 를 통해 해당 국가 국기를 표기합니다.

  ```markdown
   - [:cn: 中文](/zh-cn/)
  ```

* [`docs/index.html`](https://github.com/qmk/qmk_firmware/blob/master/docs/index.html)  
  `placeholder` 와 `noData` 객체는 다음과 같이 언어 폴더에 대한 dictionary entry를 가져야 합니다.

  ```js
  '/zh-cn/': '没有结果!',
  ```

  사이드바에서 제목 링크 설정 위한 `nameLink` 객체 역시 추가되어야 합니다.

  ```js
  '/zh-cn/': '/#/zh-cn/',
  ```

  또한 `fallbackLanguages` 목록에 언어 폴더를 추가해 영어로 적절하게 fallback되도록 합니다.

  ```js
  fallbackLanguages: [
    // ...
    'zh-cn',
    // ...
  ],
  ```

## 번역 미리보기

문서의 local instance 설정은 [Previewing the Documentation](contributing.md#previewing-the-documentation)를 참조하세요. 우측 상단 "Translations" 메뉴에서 언어를 선택할 수 있어야 합니다.

만족스럽게 작업했다면 언제든 pull request를 보내셔도 됩니다!
