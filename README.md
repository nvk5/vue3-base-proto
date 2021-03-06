# Vue3 (Vue-cli) project structure with options API (refactor to composition API in another branch)

## About
1. Исп. airbnb eslint config вместо standart
   - eslintrc настроен на использование табов (indent, no-tabs)
   - .editorconfig так же использует табы (indentstyle = tab)
   - f1-preferences-open settings(json) - настроено на автосохранение (файл editorSettingsJson в корне) editor.codeActionsOnSave 
    с исправлением ошибок но без prettier.
    При попытке отформатировать через shift + alt + f используется prettier от плагина vscode: "Prettier ESLint",
    который учитывает настройки линта + юзает prettier, который очень сильно увеличивает строчки кода, дробит лишнее.
    Так, временным решением будет не использовать prettier (shift + alt + f), а лишь сохранять (ctrl + S) для одного codestyle
2. Папка assets содержит папку scss и images 
    - common с общими стилями + стили компонентов,
    и папку utils с переменными, библиотеками, миксинами итд. все это импортируется в main.scss.
    Можно также следовать структуре папки components и создавать папки со стилями для соответствующих компонентов
   - images так же можно структурировать в стиле папки components
3. В компонентах исп-ся некоторые переиспользуемые UI компоненты типа input, textarea, button, modalWindow итд, 
   и все что они делают это принимают входные параметры и задают базовые стили для себя.
   При этом нужно учесть исключение margin и всего того что может сломать макет. Частные стили задаются через БЭМ
   в компоненте-родителе (сам UI исп. класс .myInput, в родителе на него вешается класс .request-form__input)
4. Компонент List "глупый", как и Item. Все что они делают это отрисовывают что-то на основе входных данных, 
   которые в List приходят из App, в Item из List
5. Компонент Form содержит поле для создания поста + кнопку отправки. Поле - это UI компонент TextArea (здесь имеем дело
   с Vue3 v-model). На поле вешаем класс через бэм, прокидываем что нужно (типа required, placeholder итд).
   По нажатию на кнопку submit мы эмиттим событие, которое ловим в родительском компоненте App.vue и обрабатываем (закидываем
   полученный пост в общий список постов, которые и отдаются на отрисовку в компонент List)
