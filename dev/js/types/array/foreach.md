не мутирующий

выполняет указанную функцию один раз для каждого элемента в массиве

метод только массивов
принимает в себя функцию коллбэк в которую у нас заходит каждый элемент данного массива
и мы можем что-то с ним сделать

метод не меняет исходный массив (не мутирует исходник)

и метод никогда и нигде ничего не возвращает





```js
// let arr = ['Ваня', 'Иштван', 'Оля',];
arr.forEach(function (item, index, array) {
    console.log(`${item} находится на ${index} позиции в ${array}`);
})

/*  выведет:
Ваня находится на 0 позиции в Ваня,Иштван,Оля
Иштван находится на 1 позиции в Ваня,Иштван,Оля
Оля находится на 2 позиции в Ваня,Иштван,Оля
 */

// ИЛИ
// СТРЕЛОЧНАЯ ФУНКЦИЯ
arr.forEach(item, index, array) => {
    console.log(`${item} находится на ${index} позиции в ${array}`);
}
```

Также при использовании метода forEach мы можем указывать просто имя некой отдельной функции и работать все будет точно также:

```js
let arr = ['Ваня', 'Иштван', 'Оля',];

arr.forEach(show);

function show(item) {
    console.log(item);
}
```