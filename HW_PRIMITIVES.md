# Домашнее задание к занятию "Типы данных в Java: примитивы"

## Цель задания

1. Напишете программу с использованием разных числовых типов данных
1. Попрактикуетесь с условным оператором `switch`

------

## Инструкция к заданию

1. Для каждой задачи создайте отдельный реплит, если об обратном не сказано в условии
1. :new: Саму программу вы пишете в IDEA, реплит используется только для сдачи кода
3. :new: В окне редактора IDEA наберите программный код, решающий поставленную задачу
5. :new: Загружаете файлы из папки src проекта в реплит
6. Отправьте выполненную работу на проверку в личном кабинете Нетологии

------

## Материалы, которые пригодятся для выполнения задания

1. [Как поделиться реплитом для проверки?](https://github.com/netology-code/java-homeworks/blob/java-43/QA_ReplitShare.md)
2. :new: [Как автоотформатировать код?](https://github.com/netology-code/java-homeworks/blob/java-43/QA_Format.md)
3. :new: [Как залить проект из IDEA в реплит?](https://github.com/netology-code/java-homeworks/blob/java-43/QA_ReplitUpload.md)

------

## Задание 1 (обязательное)

Нужно написать программу-помощника индивидуальному предпринимателю (далее - ИП), которая помогает ему выбрать лучшую систему налогообложения.
ИП будет заносить суммы доходов и расходов, а программа будет выбирать для него лучшую систему налогообложения из двух:
* УСН доходы - налог 6% от доходов;
* УСН доходы минус расходы - налог 15% от разницы доходов и расходов.

Налоги можно считать целочисленными.

### Функционал программы
1. Ввод сумм доходов и расходов ИП;
2. ИП может несколько раз вносить доходы и расходы, они должны суммироваться с введёнными ранее данными;
3. При выборе ИП опции определения наиболее выгодной системы налогообложения, программа должна вывести название такой системы (`УСН доходы` или `УСН доходы минус расходы`);
4. Если налоги на обеих системах равны, об этом должно быть сообщено пользователю (например, сообщением `Можете выбрать любую систему налогообложения`);
5. При выводе самой выгодной системы налогообложения, программа должна вывести также сумму, которую удастся сэкономить, если выбрать эту систему, а также налоги на каждой из доступных систем налогообложения;
6. Программа должна завершаться при вводе слова `end`;
7. Нужно помнить, что налог не может быть отрицательным;
8. Программа должна быть структурирована в методы (например, расчёт налога для одной системы налогообложения должен представлять собой отдельный статический метод)

### Пример 
```
Выберите операцию и введите её номер:
1. Добавить новый доход
2. Добавить новый расход
3. Выбрать систему налогообложения
1 <Enter>
Введите сумму дохода:
400 <Enter>

Выберите операцию и введите её номер:
1. Добавить новый доход
2. Добавить новый расход
3. Выбрать систему налогообложения
2 <Enter>
Введите сумму расхода:
100 <Enter>

Выберите операцию и введите её номер:
1. Добавить новый доход
2. Добавить новый расход
3. Выбрать систему налогообложения
1 <Enter>
Введите сумму дохода:
600 <Enter>

Выберите операцию и введите её номер:
1. Добавить новый доход
2. Добавить новый расход
3. Выбрать систему налогообложения
3 <Enter>

Мы советуем вам УСН доходы
Ваш налог составит: 60 рублей
Налог на другой системе: 135 рублей
Экономия: 75 рублей

Выберите операцию и введите её номер:
1. Добавить новый доход
2. Добавить новый расход
3. Выбрать систему налогообложения
end <Enter>

Программа завершена!
```

Такой вывод программы основан на следующих расчётах:
* Доходы ИП: 400 + 600 = 1000 рублей
* Расходы ИП: 100 рублей
* УСН доходы: 6% от 1000 рублей = 60 рублей
* УСН доходы минус расходы: 15% от 1000-100 рублей = 135 рублей
* Экономия: 135 - 60 = 75 рублей

### Шаги реализации
При запуске программы необходимо создать цикл, который будет запрашивать ввод данных пользователем.

Также нужно добавить условие выхода из цикла. Если пользователь ввел `end` вместо кода символа и нажал <enter>, то завершим цикл ввода и выведем результат:
   ```java
   //Создаем scanner - объект, который будет считывать из стандартного потока ввода/вывода (console)
   Scanner scanner = new Scanner(System.in);

   //Цикл будет работать, пока пользователь не введет `end`
   while (true) {     
       // Выводим информацию о возможных операциях пользователю
   
       String input = scanner.nextLine();
       if ("end".equals(input)) {
           break;
       }
       ...
   }
   System.out.println("Программа завершена!");
   ```

Заведите переменные для хранения доходов и расходов. При вводе новых доходов и расходов увеличивайте их на введённое число:
   ```java
      int earnings = 0;    // доходы
      int spendings = 0;   // расходы
   ```

Если пользователь ввёл номер операции, то превращаем текст в число и делаем по нему свич:
   ```java
   int operation = Integer.parseInt(input);
   switch (operation) {
      case 1:
         System.out.println("Введите сумму дохода:");
         String moneyStr = scanner.nextLine(); // Не используйте тут nextInt (!)
         int money = Integer.parseInt(moneyStr);
         earnings += money;
         break;
      case 2:
         // действия при выборе второй операции
         ...
         break;
      case 3:
         // действия при выборе третьей операции
         ...
         break;
      default:
         System.out.println("Такой операции нет");
   }
   ```

Для каждой системы налогообложения напишите метод, рассчитывающий налог. Не забудьте что налог отрицательным быть не может. Например, для УСН доходы минус расходы это будет выглядеть так:
   ```java
   public static int taxEarningsMinusSpendings(int earnings, int spendings) {
      int tax = (earnings - spendings) * 15 / 100;
      if (tax >= 0) {
         return tax;
      } else {
         // если расходы оказались больше, то налог посчитается отрицательным
         return 0;
      }
   }
   ```

В коде выбора лучшей системы налогообложения рассчитайте налоги для каждой системы. Сравните полуенные значения, выберите условным оператором лучшую и выведите на экран всю необходимую ИП информацию.

Выведите результат работы на экран.

------

## Правила приема работы

Прикреплена ссылка на реплит с решением задачи.

------

## Критерии оценки

1. Программа запускается и отрабатывает без ошибок
2. Программа соответствует всем требованиям из условия задачи
3. Программа работает правильно на всех примерах из условия
4. Программный код отформатирован и соответствует пройденным требованиям к качеству кода
5. Программа спроектирована достаточно логично и правильно, не противоречит общепринятым в производстве практикам и традициям
6. Программа реализована только с использованием пройденных интсрументов и не содержит в себе побочного не упомянутого в условии функционала
7. При наличии недочётов, в зависимости от их серьёзности и количества, работа может быть отправлена на доработку или принята; решение принимается на основе экспертной оценки работы.