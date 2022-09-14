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


#### Внутри этого Файла такие настройки:

![Screen Shot 2022-09-15 at 00 42 44](https://user-images.githubusercontent.com/44497623/190237241-71592bbe-1fc7-4100-a2c8-981e05d51b5a.png)

Главное в этом файле это раздел `rules` в котором мы и будем переопределять некоторые правила которые пришли из aribinb

### Начнем отключать некоторые правила и не только

Для начала давайте переопределим некоторые правила для комфортной работы


#### 1. react/jsx-filename-extension 
> Запретить или же Разрешить расширения файлов, которые могут содержать .JSX
##### Параметры правила:
> Набор разрешенных расширений настраивается. По умолчанию разрешен '.jsx'. Если вы хотите разрешить как «.jsx», так и «.js», конфигурация будет такой:
```
"rules": {
  "react/jsx-filename-extension": [1, { "extensions": [".js", ".jsx"] }]
}
```
> Добавляем это правило в нашу копилку
> 


#### 2. "react/jsx-props-no-spreading"
> Запретить или же Разрешить spread оператор при передачи большего количество props'ов
> <MyCustomComponent {...props} /> 
##### Параметры правила:
> По умолчанию запрещено использовать. Если вы хотите разрешить {...props}, конфигурация будет такой:
``` 
"rules": {
  "react/jsx-filename-extension": [1, { "extensions": [".js", ".jsx"] }]
  "react/jsx-props-no-spreading": "off",
}

```
> Два праивла по счету идем дальше 
> 



