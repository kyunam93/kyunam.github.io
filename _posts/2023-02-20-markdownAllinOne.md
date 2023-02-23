---
layout: single
title: "Markdown All in One 정보"
categories: markdown
tag: [markdown, vscode, visual studio code]
author_profile: false
toc: false
#sidebar:
#    nav: "docs"
#search: false    
---

![Markdown-mark](https://images.velog.io/images/nsunny0908/post/409f269d-2791-496d-abcc-896935163d3f/362222e42d54.jpg)
<div class="notice--danger">
    <h4>
    문서 원본 링크 : 
    <a href="https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one">https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one</a>
    </h4>
    
</div>

<!-- omit from toc -->
#  Visual Studio Code 대한 마크다운 지원

마크다운에 필요한 모든 기능(단축키, 목차, 자동 미리보기 등).

**_참고_**: VS Code는 Markdown 지원을 기본적으로 제공합니다.(예: **Markdown 미리 보기**) 
    자세한 내용은 [공식 문서](https://code.visualstudio.com/docs/languages/markdown)를 참조하십시오.

**목차**
- [특징(Features)](#특징features)
  - [단축키(Keyboard shortcuts)](#단축키keyboard-shortcuts)
  - [목차(Table of contents)](#목차table-of-contents)
  - [목록 편집(List editing)](#목록-편집list-editing)
  - [마크다운을 HTML로 변환(Print Markdown to HTML)](#마크다운을-html로-변환print-markdown-to-html)
  - [GitHub적인 마크다운(GitHub Flavored Markdown)](#github적인-마크다운github-flavored-markdown)
  - [수학(Math)](#수학math)
  - [자동완성(Auto completions)](#자동완성auto-completions)
  - [기타(Others)](#기타others)
- [사용 가능한 명령(Available Commands)](#사용-가능한-명령available-commands)
- [단축키](#단축키)
- [지원되는 설정](#지원되는-설정)

## 특징(Features)
### 단축키(Keyboard shortcuts)
![toggle-bold](/images/markdown/toggle-bold.gif)
<br/>
( 그림 오타: multiply(X) -> multiple(O) )

![check-task-list](/images/markdown/check-task-list.gif)
<br/>
단축키 섹션에서 전체 키 바인딩 목록 참조

### 목차(Table of contents)

![toc](/images/markdown/toc.png)
* ( [VS Code 명령 팔레트](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette)에서) " **목차 만들기** " 명령을 실행하여 새 목차를 삽입합니다.
  
* 목차는 기본적으로 파일 저장 시 **자동으로 업데이트**  됩니다.비활성화하려면 `toc.updateOnSave` 옵션을 변경하십시오.

* 목차의 들여쓰기 유형(탭 또는 공백)은 파일별로 구성할 수 있습니다 . VS Code의 상태 표시줄 오른쪽 하단에서 설정을 찾습니다.

    **_참고_**: `list.indentationSiz` 옵셥 또한 확인 바랍니다.

* **목록을 GitHub 또는 GitLab과 호환**되도록 하려면 `slugifyMode` 옵션을 설정하세요.

* 목차에 표시되는 제목을 제어하는 세 가지 방법:
    <details>
    <summary>확장하려면 클릭</summary>
    <div markdown="1"> 

    1. 제목 끝에 `<!-- omit from toc -->` 추가하여 목차에서 무시합니다.(제목 위에 추가할 수도 있습니다.)

    2. `toc.levels` 설정을 사용합니다.

    3. `toc.omittedFromToc` 설정을 사용하여 목차에서 일부 제목(및 부제목)을 생략 할 수도 있습니다.

        ```
        // .json 설정에서
        "markdown.extension.toc.omittedFromToc": {
            // 작업영역에 상대적인 경로를 사용합니다.
            "README.md": [
                "# 서론",
                "## 생략",
            ],
            // 또는 실행파일의 절대 경로를 사용합니다.
            "/home/foo/Documents/todo-list.md": [
                "## 부끄러운 목록 (절대 안해)",
            ]
        }
        ```
        
        **_참고_**:
        - 문단제목(=== 또는 ---로 만들어진 제목)도 생략할 수 있습니다. 각 설정에 #및 ##를 입력하세요.
        - 제목을 생략할 때 문서 내에서 고유한 제목인지 확인하세요. 중복된 제목은 예측할 수 없는 동작을 유발할 수 있습니다.
    </div>
    </details>

* 섹션 번호 지정을 쉽게 추가/수정/제거할 수 있습니다.
![section-numbers](/images/markdown/section-numbers.gif)

* 예상치 못한 목록이 표시되는 경우 목록 위에 `<!-- no toc -->` 주석을 추가할 수 있습니다.

### 목록 편집(List editing)
![on-enter-key](/images/markdown/on-enter-key.gif)

![tab-backspace](/images/markdown/tab-backspace.gif)

![fix-marker](/images/markdown/fix-marker.gif)

_**참고**_: 기본적으로 이 확장은 [공통 표시 규격]("https://spec.commonmark.org/0.29/#list-items")에 따라 다른 목록의 들여쓰기 크기를 결정하려고 합니다. 고정 탭 크기를 사용하려면 list.indentationSize 설정을 변경하십시오.

### 마크다운을 HTML로 변환(Print Markdown to HTML)

- 커맨드 `Markdown: Print current document to HTML` 및 `Markdown: Print documents to HTML` (batch mode)

- 설치된 다른 마크다운 플러그인과 **호환**됩니다.(예: [Markdown Footnotes](https://marketplace.visualstudio.com/items?itemName=bierner.markdown-footnotes)) 내보낸 HTML은 내부 VS 코드와 동일하게 보여야 합니다.(API의 제한으로 인한 몇 가지 테마 색상 제외)

- `<!-- title: Your Title -->` 주석을 사용하여 내보낸 HTML의 제목을 지정합니다.

- `.md`파일 확장자는 `.html`로 변환됩니다.

- 문서를 다른 사용자와 공유하려면 브라우저(예: Chrome)를 사용하여 내보낸 HTML을 PDF로 인쇄하는 것이 좋습니다.

### GitHub적인 마크다운(GitHub Flavored Markdown)
- 테이블 형식(Table Formatter)

    ![table-formatter](/images/markdown/table-formatter.gif)

    _**참고**_: Linux에서 키 바인딩은 Ctrl + Shift + I 입니다. [Visual Studio Code 키 바인딩](https://code.visualstudio.com/docs/getstarted/keybindings#_keyboard-shortcuts-reference)을 참조하십시오.

- 태스크 목록

### 수학(Math)
![math](/images/markdown/math.png)

수학 지원을 위한 전용 확장팩 [Markdown+Math](https://marketplace.visualstudio.com/items?itemName=goessner.mdmath)를 사용하십시오. 이 확장 프로그램의 `math.enabled` 옵션을 비활성해야 합니다.

### 자동완성(Auto completions)

팁: ` completion.root` 옵션도 지원합니다.
- 이미지/파일(`search.exclude` 옵션)

    ![image-completions](/images/markdown/image-completions.png)

- 수학 함수(`katex.macros` 옵션)

    ![math-completions](/images/markdown/math-completions.png)

- 참조 링크(Reference links)

    ![reference-link](/images/markdown/reference-link.png)

### 기타(Others)

- 선택한 텍스트에 링크 붙여넣기

    ![paste-link](/images/markdown/paste-link.gif)

- "미리보기 닫기" 키 바인딩을 추가하여 "미리보기 열기"와 동일한 키 바인딩(Ctrl + Shift + V 또는 Ctrl + KV)을 사용하여 미리보기 탭을 닫을 수 있습니다.

##  사용 가능한 명령(Available Commands)
- Markdown All in One: Create Table of Contents
- Markdown All in One: Update Table of Contents
- Markdown All in One: Add/Update section numbers
- Markdown All in One: Remove section numbers
- Markdown All in One: Toggle code span
- Markdown All in One: Toggle code block
- Markdown All in One: Print current document to HTML
- Markdown All in One: Print documents to HTML
- Markdown All in One: Toggle math environment
- Markdown All in One: Toggle list
  - 목록의 마커를 (기본 -, *, +, 1. 및 1 로)전환할 수 있고, 목록의 마커는 `list.toggle.candidate-markers` 옵션으로 변경할 수 있습니다.

## 단축키
<details>
<summary>테이블</summary>
<div markdown="1">

| Key                  |                      Command |
| :------------------- | ---------------------------: |
| Ctrl/Cmd + B         |                  Toggle bold |
| Ctrl/Cmd + B         |                  Toggle bold |
| Ctrl/Cmd + I         |                Toggle italic |
| Alt+S (on Windows)   |        Toggle strikethrough1 |
| Ctrl + Shift + ]     |     Toggle heading (uplevel) |
| Ctrl + Shift + [     |   Toggle heading (downlevel) |
| Ctrl/Cmd + M         |      Toggle math environment |
| Alt + C              | Check/Uncheck task list item |
| Ctrl/Cmd + Shift + V |               Toggle preview |
| Ctrl/Cmd + K V       |       Toggle preview to side |

</div>
</details>

## 지원되는 설정
<details>
<summary>테이블</summary>
<div markdown="1">

 | Name                                                       |             Default             |                                                                    Description |
 | :--------------------------------------------------------- | :-----------------------------: | -----------------------------------------------------------------------------: |
 | `markdown.extension.completion.respectVscodeSearchExclude` |             `true`              |               파일 경로 완성을 제공할 때 `search.exclude` 옵션을 고려할지 여부 |
 | `markdown.extension.completion.root`                       |                                 |            파일 경로 완성을 제공할 때 루트 폴더(경로가 `/`로 시작할 때 적용됨) |
 | `markdown.extension.italic.indicator`                      |               `*`               |                                   `*` 또는 `_`로 포장하여 이탤릭체 텍스트 바꿈 |
 | `markdown.extension.bold.indicator`                        |              `**`               |                                     `**` 또는 `__`로 포장하여 굵은 텍스트 바꿈 |
 | `markdown.extension.katex.macros`                          |              `{}`               |                            KaTeX macros (예: `{ "\\name": "expansion", ... }`) |
 | `markdown.extension.list.indentationSize`                  |           `adaptive`            |                     정렬된 목록과 정렬되지 않은 목록에 다른 들여쓰기 크기 사용 |
 | `markdown.extension.list.toggle.candidate-markers`         | `[ "-", "*", "+", "1.", "1)" ]` |                  정렬된 목록마커를 전환하기 위해 배열 사용 (예: `["*", "1."]`) |
 | `markdown.extension.orderedList.autoRenumber`              |             `true`              |                                                  편집할 때 목록 마커 자동 수정 |
 | `markdown.extension.orderedList.marker`                    |            `ordered`            |                                  또는 `one`: 항상 `1.`을 순서 목록 마커로 사용 |
 | `markdown.extension.preview.autoShowPreviewToSide`         |             `false`             |                                마크다운 파일을 열 때 미리 보기를 자동으로 표시 |
 | `markdown.extension.print.absoluteImgPath`                 |             `true`              |                                                 이미지 경로를 절대 경로로 변환 |
 | `markdown.extension.print.imgToBase64`                     |             `false`             |                                        HTML로 인쇄할 때 이미지를 base64로 변환 |
 | `markdown.extension.print.includeVscodeStylesheets`        |             `true`              |                                                VS Code의 기본 스타일 포함 여부 |
 | `markdown.extension.print.onFileSave`                      |             `false`             |                                                       파일 저장 시 HTML로 인쇄 |
 | `markdown.extension.print.theme`                           |             `light`             |                                                             내보낸 HTML의 테마 |
 | `markdown.extension.print.validateUrls`                    |             `true`              |                                               인쇄 시 URL 확인 활성화/비활성화 |
 | `markdown.extension.syntax.decorations`                    |             `true`              |                                       `~~취소선~~` 및 `code span` 에 장식 추가 |
 | `markdown.extension.syntax.decorationFileSizeLimit`        |             `50000`             |                      파일이 이 크기(byte/B)보다 큰 경우 구문 장식 렌더링 안 함 |
 | `markdown.extension.syntax.plainTheme`                     |             `false`             |                                                               집중력 향상 테마 |
 | `markdown.extension.tableFormatter.enabled`                |             `true`              |                                                         GFM 테이블 포맷터 사용 |
 | `markdown.extension.toc.slugifyMode`                       |            `github`             |   목차 링크 생성을 위한 Slagify 모드 (`vscode`, `github`, `gitlab` or `gitea`) |
 | `markdown.extension.toc.omittedFromToc`                    |              `{}`               | 프로젝트 파일별로 생략할 제목 목록 (예: `{ "README.md": ["# Introduction"] }`) |
 | `markdown.extension.toc.levels`                            |             `1..6`              |                                                   목차에 표시할 제목 레벨 제어 |
 | `markdown.extension.toc.orderedList`                       |             `false`             |                                                    목차에서 정렬된 목록을 사용 |
 | `markdown.extension.toc.plaintext`                         |             `false`             |                                                                   일반 텍스트. |
 | `markdown.extension.toc.unorderedList.marker`              |               `-`               |                        목차에 `-`, `*` or `+` 사용 (정렬되지 않은 목록의 경우) |
 | `markdown.extension.toc.updateOnSave`                      |             `true`              |                                             저장할 때 목차를 자동으로 업데이트 |

</div>
</details>
