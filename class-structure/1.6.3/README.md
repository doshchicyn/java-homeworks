# Домашнее задание к занятию 3.1 Структура класса.
**ВАЖНО:** Перед отправкой домашнего задания, убедитесь, что вы соблюдаете все правила форматирования кода: от правила именований, до пробелов и отступов (последнее можно исправлять автоматически в идее через Code -> Reformat code).

## Задача 3. Считаем онлайн-пользователей

### Описание
Давайте научимся считать, сколько пользователей сейчас находится онлайн в нашей библиотеке.
Будем считать, что пользователь онлайнится в момент создания его объекта и никогда не уходит в оффлайн.
Для этого нужно создать класс "Пользователь" (`User`), среди полей должны быть как минимум: интернет-почта, имя и фамилия (email, name, surname).

### Функционал программы
1. Класс `User`;
2. Подсчет созданных пользователей;
3. Демонстрация работы подсчёта в `Main`;
4. Для работы подсчёта пользователей в `Main` не должно предприниматься никаких дополнительных действий помимо создания объектов класса `User`.

### Пример реализации
1. Создадим класс `User`.
2. Добавим к этому классу статическое поле `totalOnline`, в котором будем подсчитывать, сколько пользователей сейчас онлайн (не забудьте продумать тип данных для этой переменной).
3. В классе `Main` в методе `main` необходимо создать не менее 3 пользователей.
4. Заполните все объекты класса `User` (например, именами знаменитостей).
6. Выведите в консоль, сколько пользователей находятся онлайн (значение поля `User.totalOnline`).
