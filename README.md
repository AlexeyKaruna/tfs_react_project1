# TFS Frontend - React Homework

![react logo](public/react-logo.png)

Репозиторий с домашними заданиями по курсу React.

Основан на [create-react-app](https://github.com/facebook/create-react-app).

## FAQ

<details>
<summary>Как выполнять домашние задания?</summary>

* Клонируем репозиторий.
* Запускаем команду `yarn install`.
* Запускаем команду `yarn run test` и если видим "No tests found.." нажимаем на кнопку "A" на клавиатуре
* Видим упавшие тесты (не расстраиваемся).
* Начинаем реализовывать компоненты и добиваемся полного прохождения всех тестов.
* Все зеленое, а значит мы справились и мы молодец.
* Настраиваем репозиторий (нужно только один раз см. "Настройка CI").
* Пушим и отправляем на проверку.
</details>

<details>
<summary>Как запустить проект в браузере?</summary>

* Запускаем команду `yarn run start`.
* Открываем [http://localhost:3000](http://localhost:3000)
</details>

<details>
<summary>Настройка CI</summary>

Нам нужно настроить автоматический деплой сайта на хостинг для того, чтобы было удобно проводить ревью приложения.

1. Создаем аккаунт в сервисе vercel https://vercel.com/.
1. Привязываем в настройках https://vercel.com/account/login-connections свой Gitlab аккаунт
1. Заходим на страницу https://vercel.com/dashboard и нажимаем 'New project'
1. Выбираете 'Import git repository' -> Находите свой репозиторий с заданием -> Import
1. В настройках выбираете Framework preset = Create React App
</details>


## ДЗ №1 "Первые шаги"

*Ориентировочное время выполнения 3 часа.*

Мы решили разработать свой интернет-банк. УРА!

Начнем с возможности просмотра списка банковских продуктов, которые есть у пользователя.

Продукты могут быть разными - это дебетовые и кредитные карты, вклады, кредиты, а также привязанные карты сторонних банков. 

Вся информация о продукте содержится в объекте

```
{
    id: '1',
    name: 'Дебетовая карта',
    customName: 'Моя карта',
    type: 'debit' | 'credit' | 'saving' | 'loan',
    amount: '50000',
    currency: 'RUB | USD'
}
```

Баланс и валюту привязанных карт мы не знаем, поэтому с ними попроще
```
{
    id: '2',
    name: 'Карта ББТ',
    customName: 'Моя карта',
    type: 'external'
}
```

Для отображения информации о продукте уже реализован компонент `BoardItem`, но его нужно немного доработать. (см. BoardItem.test.js)

За отображение списка всех продуктов отвечает компонент `Board`, его нужно реализовать самостоятельно.

**Не забудь про сортировку :).**

Порядок следующий: дебетовые карты (debit) => кредитные (credit) => карты сторонних банков (external) => вклады (saving) => кредиты (loan).
Если есть несколько аккаунтов одного типа, то сортируем их по валюте RUB => USD => EUR => GBP

Тестов довольно много и они могут сбить столку. Поэтому рекомендую начать с реализации небольших компонентов `Button` и `Money`. Затем можно приступить к `BoardItem`, `Board` и `NewAccountForm`. Если все сделано правильно, то интеграционные тесты `App.test.js` пройдут тоже.

**Большая часть стилей реализована, главное их правильно подключить и исправить недостающие.**

## Тесты

Тесты в этом задании рассчитаны на то, что компоненты будут 

## Пример работы приложения

![пример работы приложения](public/hm1-example.gif)

## Структура оценки

Максимум за работу можно получить 200 баллов.

* Компонент `BoardItem` - 60 баллов
* Форма привязки карт сторонних банков `NewAccountForm` - 60 баллов
* Компонент `Board` - 80 баллов

## TypeScript (допзадание)

В домашнем задании в качестве основного языка используется TypeScript. Использовать
его **не обязательно**.

Если вы решили **не** использовать TypeScript, на любую ошибку типизации ставьте
в качестве типа `any`.

Если вы решили использовать TypeScript, то:
* Типизируйте все компоненты, входящие в задание (props и state)
* Типизируйте все вспомогательные функции и компоненты, которые будете использовать
* Не должно быть ни одного `any` в проекте
