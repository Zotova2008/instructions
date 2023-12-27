#Настройка setting.json для VS Code
===================================

Нужно установить следующие плагины
- Для сортировки свойств в css, настройки пробелов и переносов
[Csscomb](https://marketplace.visualstudio.com/items?itemName=mrmlnc.vscode-csscomb)
- Для форматирования css кода, настройки пробелов и переносов, и т.д. [Stylelint](https://marketplace.visualstudio.com/items?itemName=stylelint.vscode-stylelint)
- Для форматирования scss кода лучше воспользоваться встроенным форматировщиком для scss в vs code в тандеме с CSSComb и с [Stylelint](https://marketplace.visualstudio.com/items?itemName=stylelint.vscode-stylelint).
- Для проверки html на ошибки
[HTMLHint](https://marketplace.visualstudio.com/items?itemName=HTMLHint.vscode-htmlhint)
или
[LintHtml](https://marketplace.visualstudio.com/items?itemName=kamikillerto.vscode-linthtml)
- Для форматирования html файлов лучше воспользоваться встроенным форматировщиком для html в vs code

Все плагины работают с файлами конфигураций, которые должны находится в рабочей области.

Настройки для VS Code и подстройке установленных плагинов нужно прописать в файле пользовательских настроек settings.json 

Параметры - Палитра команд - набрать settings - выбрать "Preferences: Open User Settings (JSON)" или "Параметры: Открыть пользовательские настройки (JSON)" 

```
{
	"[css]": {
		"editor.defaultFormatter": "stylelint.vscode-stylelint"
	},
	"[scss]": {
		"editor.defaultFormatter": "vscode.css-language-features"
	},
	"[sass]": {
		"editor.defaultFormatter": "vscode.css-language-features"
	},
	"[less]": {
		"editor.defaultFormatter": "vscode.css-language-features"
	},
	"[html]": {
		"editor.defaultFormatter": "vscode.html-language-features"
	},
	"[javascript]": {
		"editor.defaultFormatter": "dbaeumer.vscode-eslint"
	},
	"[svg]": {
		"editor.defaultFormatter": "jock.svg"
	},
	"[jsonc]": {
		"editor.defaultFormatter": "vscode.json-language-features"
	},
	"[json]": {
		"editor.defaultFormatter": "vscode.json-language-features",
		"files.trimFinalNewlines": false
	},
	"fiveServer.highlight": true,
	"fiveServer.injectBody": true,
	"fiveServer.navigate": true,
	"liveServer.settings.donotShowInfoMsg": true,
	"emmet.triggerExpansionOnTab": true,
	// Фикс бага Emmet
	"emmet.includeLanguages": {
		"javascript": "javascriptreact",
		"typescript": "javascriptreact",
		"vue-html": "html",
		"php": "html"
	},
	"emmet.preferences": {
		"output.reverseAttributes": true
	},
	"eslint.format.enable": true,
	"figma.assetExportDirectory": "raw/icons",
	"git.autofetchPeriod": 30,
	"git.confirmSync": false,
	"git.rebaseWhenSync": true,
	"git.autofetch": true,
	"githubPullRequests.defaultMergeMethod": "rebase",
	"githubPullRequests.fileListLayout": "tree",
	"githubPullRequests.remotes": [
		"origin",
		"upstream",
		"fork"
	],
	// Настройки встроенного форматирования html
	"html.format.indentHandlebars": true,
	"html.format.extraLiners": "head, body, /html",
	"html.format.indentInnerHtml": false,
	// Чудо настройки отменяют перенос атрибутов при форматировщике
	"html.format.wrapLineLength": 0,
	"html.format.enable": true,
	// Удаляет пустые строки
	"html.format.maxPreserveNewLines": 1,
	"htmlhint.options": {
		"doctype-first": false,
		"doctype-html5": true,
		"html-lang-require": true,
		"head-script-disabled": true,
		"style-disabled": true,
		"script-disabled": false,
		"title-require": true,
		"attr-lowercase": true,
		"attr-no-duplication": true,
		"attr-no-unnecessary-whitespace": true,
		"attr-unsafe-chars": true,
		"attr-value-double-quotes": true,
		"attr-value-single-quotes": false,
		"attr-value-not-empty": false,
		"attr-sorted": false,
		"attr-whitespace": true,
		"alt-require": true,
		"input-requires-label": true,
		"tags-check": false,
		"tag-pair": true,
		"tag-self-close": false,
		"tagname-lowercase": true,
		"tagname-specialchars": true,
		"empty-tag-not-self-closed": true,
		"src-not-empty": true,
		"href-abs-or-rel": false,
		"id-class-ad-disabled": true,
		"id-class-value": true,
		"id-unique": true,
		"inline-script-disabled": true,
		"inline-style-disabled": true,
		"space-tab-mixed-disabled": "space",
		"spec-char-escape": true,
	},
	// Форматирование плагином Prettier - Code formatter.
	// Плохо форматирует длинные свойства, начинает перенос.
	// Для исправления нужно в корень проекта поместить файл .prettierrc с соответствующей настройкой:  { "printWidth": 120 }
	// Настройки встроенного форматирования стилей
	// "css.format.spaceAroundSelectorSeparator": true,
	// "css.hover.references": false,
	// "css.lint.duplicateProperties": "warning",
	// "css.lint.idSelector": "warning",
	// "css.lint.important": "warning",
	// "css.lint.zeroUnits": "warning",
	// "scss.hover.references": false,
	// "scss.lint.compatibleVendorPrefixes": "warning",
	// "scss.lint.duplicateProperties": "warning",
	// "scss.lint.idSelector": "warning",
	// "scss.lint.important": "warning",
	// "scss.lint.zeroUnits": "warning",
	// "scss.lint.float": "warning",
	// "scss.format.spaceAroundSelectorSeparator": true,
	// "less.format.spaceAroundSelectorSeparator": true,
	// "css.validate": false,
	// "scss.validate": false,
	// "less.validate": false,
	// Настройки для плагина Stylelint
	"stylelint.enable": true,
	"stylelint.validate": [
		"css",
		"less",
		"postcss",
		"scss",
	],
	"csscomb.formatOnSave": true,
	"svg.preview.boundingBox": false,
	"svg.preview.transparencyGrid": false,
	"markdown.preview.scrollEditorWithPreview": true,
	"markdown.updateLinksOnFileMove.enabled": "always",
	"markdown-preview-enhanced.previewTheme": "none.css",
	"multiDiffEditor.experimental.enabled": true,
	// Плагин Colorize
	"colorize.enable_search_variables": true,
	"colorize.languages": [
		"CSS",
		"SASS",
		"SCSS",
		"LESS",
		"PostCSS",
		"SSS",
		"Stylus",
		"xml",
		"svg"
	],
	"colorize.colorized_variables": [
		"CSS",
		"SASS",
		"STYLUS",
		"LESS"
	],
	"colorize.hide_current_line_decorations": false,
	//Фикс бага "json ошибка"
	"http.proxySupport": "fallback",
	"codesnap.shutterAction": "save",
	"redhat.telemetry.enabled": true,
	"gutterpreview.imagePreviewMaxHeight": 30,
	"gutterpreview.imagePreviewMaxWidth": 30,
	"gutterpreview.enableReferenceLookup": true,
	"javascript.suggest.names": false,
	"javascript.suggest.autoImports": true,
	"javascript.updateImportsOnFileMove.enabled": "always",
	"diffEditor.diffAlgorithm": "advanced",
	"diffEditor.maxComputationTime": 0,
	"diffEditor.renderSideBySide": false,
	// Настройки редактора
	"breadcrumbs.symbolPath": "off",
	"editor.inlineSuggest.showToolbar": "never",
	"editor.minimap.enabled": false,
	"editor.formatOnSave": true,
	"editor.formatOnPaste": true,
	"editor.wordWrap": "bounded",
	"editor.wordWrapColumn": 500,
	"editor.fontSize": 14,
	"editor.tabSize": 2,
	"editor.indentSize": "tabSize",
	"editor.detectIndentation": true,
	"editor.linkedEditing": true,
	"editor.bracketPairColorization.enabled": true,
	"editor.bracketPairColorization.independentColorPoolPerBracketType": true,
	"editor.multiCursorModifier": "ctrlCmd",
	"editor.cursorSmoothCaretAnimation": "on",
	"editor.guides.bracketPairs": true,
	"editor.hover.delay": 500,
	"editor.insertSpaces": false,
	"editor.smoothScrolling": true,
	"editor.wordSeparators": " _`~!@#$%^&*()-=+[{]}\\|;:'\",.<>/?",
	"editor.wrappingIndent": "indent",
	"editor.codeActionsOnSave": {
		"source.fixAll": "explicit"
	},
	// Контролирует, должны ли появляться быстрые предложения при наборе текста
	// "editor.quickSuggestions": {
	// 	"other": true,
	// 	"comments": false,
	// 	"strings": false
	// },
	"explorer.confirmDelete": false,
	"explorer.confirmPasteNative": false,
	"explorer.confirmDragAndDrop": false,
	"explorer.compactFolders": false,
	"files.autoSave": "onFocusChange",
	"files.insertFinalNewline": true,
	"files.trimFinalNewlines": true,
	"files.trimTrailingWhitespace": true,
	"terminal.integrated.cursorBlinking": true,
	"terminal.integrated.cursorStyle": "line",
	"terminal.integrated.defaultProfile.linux": "zsh",
	"terminal.integrated.defaultProfile.windows": "bash",
	"terminal.integrated.profiles.linux": {
		"zsh": {
			"path": "/usr/bin/zsh"
		}
	},
	"terminal.integrated.scrollback": 10000,
	"terminal.integrated.stickyScroll.enabled": true,
	"terminal.integrated.tabs.enabled": false,
	// Визуальные настройки редактора
	"workbench.colorTheme": "Vulgocode Theme Bold",
	"workbench.startupEditor": "newUntitledFile",
	"workbench.iconTheme": "vscode-icons",
	"workbench.list.smoothScrolling": true,
	"workbench.settings.openDefaultSettings": true,
	"workbench.colorCustomizations": {
		"tab.activeBackground": "#fff3",
		"editorSuggestWidget.selectedBackground": "#0a036b",
		"list.activeSelectionBackground": "#0a036b",
		"list.inactiveSelectionBackground": "#0a036b",
		"list.focusBackground": "#0a036b",
		"list.hoverBackground": "#0a036b",
		"terminalCursor.foreground": "#C45DFF"
	},
	"workbench.editor.limit.value": 5,
	"workbench.editor.sharedViewState": true,
	"workbench.editor.empty.hint": "hidden",
	"workbench.editorAssociations": {
		"git-rebase-todo": "default"
	},
	"vsicons.dontShowNewVersionMessage": true,
}

```
