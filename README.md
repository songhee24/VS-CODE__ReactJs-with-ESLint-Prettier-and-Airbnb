# VS-CODE__ReactJs-with-ESLint-Prettier-and-Airbnb


## Один из самых простых способов улучшить свой код — использовать линтер!

Не только улучшить💪, но и унифицировать код вашей команды. 
У каждого разработчика свой стиль, поэтому линтер может помочь вам сделать код вашей команды понятным и понятным для всех.

### Но сначала, что такое Lint или Linter❓

Это синтаксический анализатор/инструмент, который проверяет код и отмечает ошибки, 
опечатки или любую потенциальную ошибку в коде программиста.

![image](https://user-images.githubusercontent.com/44497623/190224727-331ae1f3-7ef7-45a6-97fc-f5f50877898c.png)


> ________________
> Предварительное условие: у вас должны быть установлены [Visual Studio Code](https://code.visualstudio.com/) и [NodeJS](https://nodejs.org/en/).
> ________________

 ## И так Начнем
### 1. Создать приложение ReactJS

Давайте создадим приложение ReactJS и назовем его «eslint-app». Мы создадим приложение с помощью терминала.

```npm
npx create-react-app eslint-app 
```
Дальше нужно открыть наш проект через Vs Code. Чтобы в дальнейшем с ним работать.

### 2. Установка ESLint Но сначала, что такое ESlint❓
![image](https://user-images.githubusercontent.com/44497623/190225171-c4e97f6f-4625-4191-8fd7-d45b9cceeef3.png) 


ESLint — это программа, которая просматривает ваш код и анализирует его на наличие потенциальных ошибок.
Расширение легко настраивается, с набором встроенных опций. 
Он может выделять ошибки, пока вы печатаете в своем редакторе, а также отображать подробный список ошибок в вашей консоли. 



![image](https://user-images.githubusercontent.com/44497623/190227458-7de44648-3b04-4c53-9b71-a2fe523cc471.png)


Теперь устанавливаем ESLint для поддержки нашего редактора кода просто переходя по [ссылке](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint#:~:text=If%20you%20haven't%20installed,eslintrc%20configuration%20file.)

>____________
> Каждый раз устанавливать ESLint в наш редактор кода не нужно это делается только один раз 
>____________

После того как вы открыли проект.

Откройте терминал в VSCode, выбрав View->Terminal или используя сочетание клавиш:
- Windows Ctrl + `
- Mac Control + `

`
Дальше идет сам процесс установки ESLint

Устанавливаем инструмент в наш проект командой:
```
npm install eslint --save-dev
```
![Screen Shot 2022-09-15 at 00 03 11](https://user-images.githubusercontent.com/44497623/190229196-7bb8051d-da30-4b87-854d-52b666535308.png)


Дальше нужно запустить процесс инициализаций, который в дальнейшем и определить какой тип правил будет примен к вашему проекту.
Для этого запускаем команду:

```
npx eslint --init
```
Во время инициализации вам будет задано несколько вопросов по настройке конфигурационного файла eslint.

1. How would you like to use ESLint?
   - To check syntax, find problems, and enforce code style
   
2. What type of modules does your project use?
   - JavaScript modules (import/export)
   
3. Which framework does your project use?
   - React
   
4. Does your project use TypeScript?
   - No
   
5. Where does your code run? 
   - Browser
   
6. How would you like to define a style for your project? 
   - Use a popular style guide
   
7. Which style guide do you want to follow?
   - Airbnb (https://github.com/airbnb/javascript)

8. What format do you want your config file to be in? 
   - JSON


![Screen Shot 2022-09-15 at 00 15 06](https://user-images.githubusercontent.com/44497623/190231442-a2ed51ef-4617-44ba-aad0-a19b63bd5725.png)

>________________
> Сразу после этого вопроса eslint проверит, есть ли у вас отсутствующие зависимости, и если да, то предложит их установить.
> В моем случае мне не хватало:
> - eslint-plugin-react@^7.28.0 
> - eslint-config-airbnb@latest 
> - eslint@^7.32.0 || ^8.2.0 
> - eslint-plugin-import@^2.25.3 
> - eslint-plugin-jsx-a11y@^6.5.1 
> - eslint-plugin-react-hooks@^4.3.0
>________________

```diff
- Would you like to install them now with npm? - Yes
```

После того как вы нажали Yes. 
У вас будет выбор через какой пакетный менеджер нужно установить: 

![Screen Shot 2022-09-15 at 00 27 27](https://user-images.githubusercontent.com/44497623/190233974-f33f72a2-992b-4f6f-8f9f-12a3c47ebb69.png)

Выбираем npm

В результате вы должны были успешно создать файл .eslintrc.json и увидеть его в своем каталоге.

![Screen Shot 2022-09-15 at 00 32 16](https://user-images.githubusercontent.com/44497623/190235356-3a1d1dce-f004-4f1b-a7b7-5b3d96038ab3.png)


### 3. Переопределяем правила в ESLint 🤢


#### Внутри этого Файла такие настройки:

![Screen Shot 2022-09-15 at 00 42 44](https://user-images.githubusercontent.com/44497623/190237241-71592bbe-1fc7-4100-a2c8-981e05d51b5a.png)

Главное в этом файле это раздел `rules` в котором мы и будем переопределять некоторые правила которые пришли из aribinb

### Начнем отключать некоторые правила и не только

Для начала давайте переопределим некоторые правила для комфортной работы


#### 1. react/jsx-filename-extension 
Запретить или же Разрешить расширения файлов, которые могут содержать .JSX

##### Параметры правила:
Набор разрешенных расширений настраивается. По умолчанию разрешен '.jsx'. Если вы хотите разрешить как «.jsx», так и «.js», конфигурация будет такой:
``` diff
"rules": {
+ "react/jsx-filename-extension": [1, { "extensions": [".js", ".jsx"] }]
}

```
> Добавляем это правило в нашу копилку
>_______


#### 2. "react/jsx-props-no-spreading"
Запретить или же Разрешить spread оператор при передачи большего количество props'ов
> <MyCustomComponent {...props} /> 

##### Параметры правила:
По умолчанию запрещено использовать. Если вы хотите разрешить {...props}, конфигурация будет такой:

``` diff
"rules": {
  "react/jsx-filename-extension": [1, { "extensions": [".js", ".jsx"] }]
+ "react/jsx-props-no-spreading": "off",
}

```
Два правила по счету идем дальше 
>_______


#### 3.  "react/react-in-jsx-scope"
Это правило будет ругаться каждый раз если вы забудете использовать 
import React from 'react'; 
в файлах использующие jsx 

##### Параметры правила:
По умолчанию нужно импортировать реакт там где jsx код. Если вы хотите убрать это правило, конфигурация будет такой:


``` diff 
"rules": {
  "react/jsx-filename-extension": [1, { "extensions": [".js", ".jsx"] }]
  "react/jsx-props-no-spreading": "off",
+ "react/react-in-jsx-scope": "off",
}

```
>_______

### 4. "import/prefer-default-export"
Когда есть только один экспорт из файла, предпочтительнее использовать экспорт по умолчанию(export default), 
а не именованный экспорт(export const foo = 'foo').

##### Параметры правила:
Если вы хотите убрать это правило, конфигурация будет такой:
``` diff 
"rules": {
  "react/jsx-filename-extension": [1, { "extensions": [".js", ".jsx"] }]
  "react/jsx-props-no-spreading": "off",
  "react/react-in-jsx-scope": "off",
+ "import/prefer-default-export": "off",
}

```
>_______

### 5. "no-shadow"
Теневое копирование — это процесс, при котором локальная переменная имеет то же имя, что и переменная в содержащей ее области. Например:
Примеры неправильного кода для этого правила:

```
var a = 3;
function b() {
    var a = 10;
}
```

##### Параметры правила:
Если вы хотите убрать это правило, конфигурация будет такой:

``` diff 
"rules": {
  "react/jsx-filename-extension": [1, { "extensions": [".js", ".jsx"] }]
  "react/jsx-props-no-spreading": "off",
  "react/react-in-jsx-scope": "off",
  "import/prefer-default-export": "off",
+ "no-shadow": "off",
}

```

>_______

### 6.  "react-hooks/exhaustive-deps"
Правило «react-hooks/exhaustive-deps» предупреждает нас, когда у нас отсутствует зависимость в хуке эффекта.
Иногда это правило раздражает когда вам нужно постоянно отдавать в качестве зависимостей функцию  


##### Параметры правила:
Если вы хотите убрать это правило, конфигурация будет такой:
 
``` diff 
"rules": {
  "react/jsx-filename-extension": [1, { "extensions": [".js", ".jsx"] }]
  "react/jsx-props-no-spreading": "off",
  "react/react-in-jsx-scope": "off",
  "import/prefer-default-export": "off",
  "no-shadow": "off",
+ "react-hooks/exhaustive-deps": "off",
}

```

>_______

### 7. "react-hooks/rules-of-hooks"
Only Call Hooks at the Top Level - это правило мы не отключаем а переопределяем. 
На самом деле это распространённое правило при использовании хуков 
Не вызывайте хуки внутри циклов, условий или вложенных функций.
Следуя этому правилу, вы гарантируете, что хуки вызываются в одном и том же порядке каждый раз при рендеринге компонента.

##### Параметры правила:
Чтобы использовать это правило нужно изменить `rules` как мы до этого делали и еще кое что..
Сначала меняем `rules:`

``` diff 
"rules": {
  "react/jsx-filename-extension": [1, { "extensions": [".js", ".jsx"] }]
  "react/jsx-props-no-spreading": "off",
  "react/react-in-jsx-scope": "off",
  "import/prefer-default-export": "off",
  "no-shadow": "off",
  "react-hooks/exhaustive-deps": "off",
+ "react-hooks/rules-of-hooks": "error",
}

```

Дальше нам нужно добавить значение уже в другую часть не в rules а в plugins:

![Screen Shot 2022-09-15 at 02 26 06](https://user-images.githubusercontent.com/44497623/190255552-c61f6f88-957a-4718-be9b-ecf30a31fd32.png)

Плагины это своего рода анализаторы вашего кода, в данном случае как раз стоит плагин "react",
которы нужен для анализа когда реакт приложения и выявления потенциальных ошибок.

Кончено мы в самом начале уже установили некоторые плагины просто их нужно подключить, "react" уже подключен. 
Подключим теперь плагин под названием "react-hooks" который тоже во время конфигурации был установлен.

``` diff
  "plugins": [
  "react", 
+ "react-hooks"
 ],
```
>_______



### 8. "react/function-component-definition"
И так правило гласит какой именно тип функции вы будете использовать при функциональных компонентах

##### Параметры правила:
Если вы хотите убрать это правило, конфигурация будет такой:

``` diff 
"rules": {
  "react/jsx-filename-extension": [1, { "extensions": [".js", ".jsx"] }]
  "react/jsx-props-no-spreading": "off",
  "react/react-in-jsx-scope": "off",
  "import/prefer-default-export": "off",
  "no-shadow": "off",
  "react-hooks/exhaustive-deps": "off",
  "react-hooks/rules-of-hooks": "error",
+ "react/function-component-definition": "off",
}

```

>_______

### 9. "react/function-component-definition"

Очень длинные строки кода на любом языке могут быть трудны для чтения. Чтобы облегчить читаемость и удобство сопровождения, многие программисты разработали соглашение, ограничивающее количество строк кода до X символов (традиционно 80 символов).

##### Параметры правила:
Мы настраиваем это правило вот таким образом: 

``` diff
"rules": {
  "react/jsx-filename-extension": [1, { "extensions": [".js", ".jsx"] }]
  "react/jsx-props-no-spreading": "off",
  "react/react-in-jsx-scope": "off",
  "import/prefer-default-export": "off",
  "no-shadow": "off",
  "react-hooks/exhaustive-deps": "off",
  "react-hooks/rules-of-hooks": "error",
  "react/function-component-definition": "off",
+ "max-len": [
+        "error",
+    {
+      "code": 100,
+      "ignoreStrings": true,
+      "ignoreTemplateLiterals": true,
+      "ignoreRegExpLiterals": true
+    }
   ],
}

```
>_______

### 10. "no-console"

Это правило запрещает вызовы или присвоения методов объекта консоли. То есть нужно убирать за собой мусор

##### Параметры правила:
Мы настраиваем это правило вот таким образом, где просто предупреждаем не использовать консоль:

``` diff
"rules": {
  "react/jsx-filename-extension": [1, { "extensions": [".js", ".jsx"] }]
  "react/jsx-props-no-spreading": "off",
  "react/react-in-jsx-scope": "off",
  "import/prefer-default-export": "off",
  "no-shadow": "off",
  "react-hooks/exhaustive-deps": "off",
  "react-hooks/rules-of-hooks": "error",
  "react/function-component-definition": "off",
  "max-len": [
         "error",
     {
       "code": 100,
       "ignoreStrings": true,
       "ignoreTemplateLiterals": true,
       "ignoreRegExpLiterals": true
     }
   ],
+ "no-console": ["warn", { "allow": ["warn", "error"] }],
}

```

>_______

### 11.  "jsx-a11y/label-has-associated-control"
Это правило проверяет, что любой тег label (или указанный пользовательский компонент, который будет выводить тег метки) либо (1) является оболочкой элемента ввода (или указанного пользовательского компонента, который выводит входной тег), либо (2) имеет атрибут htmlFor и что тег label имеет текстовое содержимое.

##### Параметры правила:
Мы настраиваем это правило вот таким образом:

``` diff
"rules": {
  "react/jsx-filename-extension": [1, { "extensions": [".js", ".jsx"] }]
  "react/jsx-props-no-spreading": "off",
  "react/react-in-jsx-scope": "off",
  "import/prefer-default-export": "off",
  "no-shadow": "off",
  "react-hooks/exhaustive-deps": "off",
  "react-hooks/rules-of-hooks": "error",
  "react/function-component-definition": "off",
  "max-len": [
         "error",
     {
       "code": 100,
       "ignoreStrings": true,
       "ignoreTemplateLiterals": true,
       "ignoreRegExpLiterals": true
     }
   ],
  "no-console": ["warn", { "allow": ["warn", "error"] }],
+ "jsx-a11y/label-has-associated-control": [
+        "error",
+        {
+           "required": {
+              "some": ["nesting", "id"]
+           }
+        }
+     ],
}

```
### В целом наши привила выглядят таким вот образом:

```
"rules": {
  "react/jsx-filename-extension": [1, { "extensions": [".js", ".jsx"] }]
  "react/jsx-props-no-spreading": "off",
  "react/react-in-jsx-scope": "off",
  "import/prefer-default-export": "off",
  "no-shadow": "off",
  "react-hooks/exhaustive-deps": "off",
  "react-hooks/rules-of-hooks": "error",
  "react/function-component-definition": "off",
  "max-len": [
         "error",
     {
       "code": 100,
       "ignoreStrings": true,
       "ignoreTemplateLiterals": true,
       "ignoreRegExpLiterals": true
     }
   ],
  "no-console": ["warn", { "allow": ["warn", "error"] }],
  "jsx-a11y/label-has-associated-control": [
         "error",
         {
            "required": {
               "some": ["nesting", "id"]
            }
         }
      ],
}
```
На это мы еще не закончили

### 3. Установка Prettier💅

![image](https://user-images.githubusercontent.com/44497623/190261545-84f724de-e689-4d6f-ac4b-6d04f01b24c9.png)

Сначала устанавливаем Prettier для поддержки нашего редактора кода просто переходя по [ссылке](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)

Скачали ? Окей. Скажу пару слов про Prettier

Я не пишу самый красивый код, но с Prettier мне больше не нужно об этом беспокоиться. После долгого сеанса яростной работы на клавиатуре я могу сохранить свой файл, а затем *пуф* — он автоматически волшебным образом форматирует мой код!

Окей. наша среда разработки поддерживает Prettier
Осталось установить его в сам наш проект 
```
 npm i prettier -D
```
просто вводим эту команду и скачиваем пакет 

> Но на этом еще не все. Мы Установили ESLint определили правила которые нам не нужны, 
> и теперь нам как то нужно настроить Prettier так чтобы он форматировал наш код по правилами ESLint'а который использует правила airbnb

Для этого скаичваем еще пару пакетов через npm

```
npm i eslint-config-prettier eslint-plugin-prettier -D
```
Вы можете здесь увидеть два пакета, первый это сама настройка которая по умолчанию отключает форматирование кода у ESLint, и делает конфигурацию для работы с Prettier, и второе это плагин, который мы тоже должны подключить, для правильной комбинации этих двух программ

После установки пакетов теперь нужно изменить значение "extends" в файле ".eslintrc.json"

```diff

    "extends": [
        "plugin:react/recommended",
        "airbnb",
      + "plugin:prettier/recommended"
    ],

```

Но почему мы должны добавлять что то в extends ? Eсли мы установили плагин ? Вообще что такое extends ?
Короче вот тебе [доки](https://eslint.org/docs/latest/user-guide/configuring/)
Читай и кайфуё 😇

### 4. Переопределяем форматинг в Prettier 🥱

Если вам не нравится конфигурация Prettier по умолчанию, вы можете создать файл .prettierrc в каталоге «eslint-app»

![Screen Shot 2022-09-15 at 03 25 14](https://user-images.githubusercontent.com/44497623/190265553-fe932685-f7df-4e4c-ac00-0b3c440b3848.png)


Для чего он нам ?  А я вам скажу - Для удобного форматирования нашего когда тоже по каким то аспектам 
К примеру если написать:
```
{
   "semi": false,
}
```
То он всегда будет форматировать убирая точку с запятой после объявления переменных, вызова функции и.т.д
Мы добавим такие указания:

```
{
   "trailingComma": "es5",
   "tabWidth": 3,
   "semi": false,
   "singleQuote": true,
   "endOfLine": "auto"
}
```
### 6. Проверяем работает ли ESLint
Открываем код и видим море кровииии

![Screen Shot 2022-09-15 at 03 31 33](https://user-images.githubusercontent.com/44497623/190266338-b5d39dce-9e82-4285-a250-d27946a6757b.png)

Это означает что правила кода работают и указывают мне что очень много ошибок в написани когда 

Поэтому теперь нужно настроить последнее....

При сохранении чтобы запускался Prettier и форматировал наш код под стандартами airbnb 

Заходим в vs code
1. Используйте Ctrl/Command + ,  или перейдите в File ->Preferences ->Settings.
2. Ищем в строке поиска format on save
   - находим нужный элемент иставим галочку


![Screen Shot 2022-09-15 at 03 44 55](https://user-images.githubusercontent.com/44497623/190269182-c7438e5a-88ea-4e31-9eb8-92ac9ef1fda7.png)


После проверяем...


![ezgif com-gif-maker](https://user-images.githubusercontent.com/44497623/190269240-d768c457-b00e-4ddd-af77-04e0e3faeaf8.gif)


### Поздравляем!

Теперь, когда ваш проект ReactJS настроен в стиле ESLint, Prettier и Airbnb, 
вы можете поддерживать согласованный и чистый код. 
Вы также будете получать уведомления о проблемах с линтингом и форматированием.


 
