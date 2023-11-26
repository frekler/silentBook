Среда исполнения кода

>  Возможность выполнения JS без браузера (обычно на сервере, но есть версии хоть под ардуино)
> поддержка модульности
> возможность не только слать запросы, но и получать и обрабатывать
> возможность работы с файловой системой
> менеджер зависимостей-пакетов (npm)

https://nodejs.org/en/download/ - mac, windows https://github.com/nodesource/distributions/blob/master/README.md - linux

Проверка установки / версии Node.js в терминале:
```sh
$ node -v
```


выполнение файла
```sh
$ node <название файла>
```

// node ./script.js
// результат исполнения 

-------


NPM Node Package Manager

библиотеки npm
npmjs.com
общедоступный регистр, содержащий пакеты (завершенные изолированные куски кода) от сторонних разработчиков
npmjs.com

npm - программа для работы с пакетами (входит в node)

npmtrends.com - сравнение и популярность npm пакетов

yarn - программа для работы с пакетами от Facebbok (устанавливаеися отдельно)

глобальная установка послед версии npm

```sh
$ npm i -g npm
```


Варианты установки пакета

Локально – работают только в текущей папке. Зашли в папку другого проекта – надо ставить по-новой
▸ Глобально – установлены в папку текущего пользователя компьютера. Работают из любой папки.

Надо ставить зависимость глобально (флаг -g) только если точно понимаешь, зачем это нужно в этом конкретном случае. Обычно всё ставим локально.



Глобальные пакеты:

 Лучше ставить глобальные зависимости без sudo.
На Windows это работает само.
Для linux/mac есть инструкция
https://github.com/sindresorhus/guides/blob/master/npm-global-without-sudo.md
 


 ЗАВИСИМОСТИ
  ▸ Программа может требовать для работы какие-то пакеты из NPM. Эти пакеты называются зависимостями программы.
▸ У этих пакетов могут быть свои зависимости, и так далее.
▸ Информация о зависимостях хранится в package.json
▸ Информация точных версиях используемых зависимостей находится в package-lock.json






 ТИПЫ ЗАВИСИМОСТЕЙ
  ▸ devDependencies – пакеты которые нужны только для разработки ( eslint, nodemon и др. “инструменты” )
▸ dependencies – список пакетов необходимых для работы приложения

И другие зависимости:
https://habr.com/ru/companies/ruvds/articles/499668/













 УСТАНОВКА ЗАВИСИМОСТЕЙ
  npm init [-yes] (если уже есть файл package.json, то init делать не надо) npm install jest -D (пример установки devDependencies зависимости)
Сразу после того, как сделали init, надо обязательно создать .gitignore и добавить в него /node_modules
или воспользуйтесь командой npx create-gitignore Node












инициализация проекта



cfonts
библиотека в npm
npm i cfonts 

extensions
better comments

// ! - red
// ? - blue
// \* - green
// todo - orange

если нет файла package.json
инициализация проекта
npm init -y (yes)











npx VS npm
npx помогает нам избежать версий, проблем с зависимостями и установки ненужных пакетов, которые мы просто хотим попробовать

npx - спец прога, которая автоматически устанавливается вместе с утилитой npm
npx позволяет работать с пакетами, без установки их на комп
напр
npx eslint --init 
пакет eslint скачается на комп, выполнится команда init, затем скачанные файлы (установочные) удалятся
не создавая зависимостей
установили только всё необходимое для работы eslint
cfonts ставилти с npm, значит он записал файлы в node_modules





NVM

nvm - Node Version Manager
утилита, которая позволяет переключаться между версиями node в системе

(на будущее, для контроля перескакивать с одной версии ноды на другую)






стандартные скрипты запуска файлов без run:
npm start
npm test
остальные - npm run <название скрипта(scripts)>
npm run dev

установка зависимостей
npm i - если уже есть package.json с зависимостями
npm i <названиебиблиотеки> - установка библиотеки в dependencies
npm i -D <название библиотеки> - установка библиотеки в devDependencies, напр npm install jest -D
npm i -g <название библиотеки> - установка библиотеки глобально

сразу после init - надо обязательно создать gitigonre
создание файла gitignore (исключения что не должно улетать на гитхаб, что не будет пушиться)
npx create-gitignore node

в package.json вся инфа о нашем проекте

все ключи и все значения пишутся только в двойных кавычках
json не понимает одинарные кавычки

json спец формат в котором все описывается в виде объектов или массивов

"scripts": {
"start": "node index.js",
"test": "",
}

devDependencies - это спец зависимости только для разработки  и разрабов
eslint, например, nodemon и др "инструменты"
они не нужны на клиенте, пользователям и тд
пакеты которые нужны только для разработки



dependencies - зависимости, которые нужны всем
список пакетов, необходимых для работы приложения





в package-lock.json
информация о точных версиях используемых зависимостей

у пакетов могут быть свои зависимости и тд




передача сущностей из файла в файл
JavaScript modules (import/export)
CommonJS (require/exports) (это ванильный) ----> (далее)



 синтаксис require / export используется для импорта и экспорта переменных, функций, классов между модулями (файлами) в проекте node.js



 

МОДУЛЬНА СИСТЕМА в JS

module.exports = summ (название экспортируемой фунцкии)

const sum = require('./(путь)')

console.log(sum(2, 7 ))

function.js:

```js
function summ(a, b) {
  return a + b;
}

const dolphins = () => {
  return "Привет";
};

module.exports = { summ, dolphins }; // передаем объектом (в объхект кладем две функции или сколько угодно сущностей) функции будут являться ключами, подзначения - классы будут эти функции??????
// { summ: [Function: summ], dolphins: [Function: dolphins]}
```

index.js:

```js
const sum = require("./function");

const getNum = (num) => {
  console.log(`Это число ${num}`);
};
getNum(sum.summ(2, 77)); //  обращаемся по ключу к этому объекту
console.log(sum.dolphins());
```

деструктуризация

```js
const { summ, dolphins } = require("./function"); // ключи указываем необходимые, можно только summ
// берем объект и достаем сразу все что нам неоходимо
// и тогда
getNum(summ(2, 77));
console.log(dolphins());
```

eslint
1установка
npm eslint --init
2необходимо установить расширение (extension)
3  настройка
.eslintrc.json - файл конфигурации еслинта

отключим ворнинги для console.log
"rules":{
"no-console": "off "
}


