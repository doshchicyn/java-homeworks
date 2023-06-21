# Домашнее задание к занятию "Многомерные массивы"

## Цель задания

1. Научиться работать с двумерными наборами данных в Java с помощью массивов

------

## Инструкция к заданию

1. Для каждой задачи создайте отдельный реплит, если об обратном не сказано в условии
1. Саму программу вы пишете в IDEA, реплит используется только для сдачи кода
3. В окне редактора IDEA наберите программный код, решающий поставленную задачу
5. Загружаете файлы из папки src проекта в реплит
6. Отправьте выполненную работу на проверку в личном кабинете Нетологии

------

## Материалы, которые пригодятся для выполнения задания

1. [Как поделиться реплитом для проверки?](https://github.com/netology-code/java-homeworks/blob/java-43/QA_ReplitShare.md)
2. [Как автоотформатировать код?](https://github.com/netology-code/java-homeworks/blob/java-43/QA_Format.md)
3. [Как залить проект из IDEA в реплит?](https://github.com/netology-code/java-homeworks/blob/java-43/QA_ReplitUpload.md)

------

## Задание 1 (обязательное)

Научимся поворачивать матрицу с равными сторонами. Этот алгоритм мог бы быть использован в графических редакторах 
вроде Photoshop для поворота изображений.

Дано: двумерная матрица 8 на 8 из случайных чисел от 0 до 255 (спектр цветов GrayScale).
Напишите алгоритм "поворота" такой матрицы на 90 градусов по часовой стрелке.

### Функционал программы
1. Создание матрицы в программе;
2. Вывод матрицы до поворота;
3. Разворот матрицы;
4. Вывод матрицы после поворота на 90 градусов.
5. Вывод должен быть вынесен в отдельный метод, с помощью которого будут выведены и исходная, и перевёрнутая матрицы

### Пример
Дана следующая матрица:
``` 
114 112 148  83 204  22 125  31
192 231 245 128  63 246 139  17
 61 128 224  45  91  57 239  34
219 237 167 191 236 146 144 117
 35 199 102 124 208 195  21 147
 52 229 126  32  24 145  19  39
107  43 190  43  47 172  18  19
 62 221   6 208 241 198 187  85
```  
Вывод:
```  
 62 107  52  35 219  61 192 114
221  43 229 199 237 128 231 112
  6 190 126 102 167 224 245 148
208  43  32 124 191  45 128  83
241  47  24 208 236  91  63 204
198 172 145 195 146  57 246  22
187  18  19  21 144 239 139 125
 85  19  39 147 117  34  17  31
```  

### Пример реализации
1. Итак, у нас есть матрица с размерами 8x8, которую нужно повернуть на 90 градусов по часовой стрелке.
Для начала создадим матрицу (размерность матрицы сохраним в статическом поле `public static final int SIZE = 8`).
    ```java
      int[][] colors = new int[SIZE][SIZE];
    ```  

2. Теперь заполним матрицу случайными значениями в диапазоне от 0 до 255:
    ```java
      Random random = new Random();
      for (int i = 0; i < SIZE; i++) {
        for (int j = 0; j < SIZE; j++) {
          // для случайных значений воспользуемся готовым решением из библиотеки java.util.Random
          colors[i][j] = random.nextInt(256);
        }
      }
    ```  
3. Выводим матрицу на экран (оформите это в виде отдельного метода):
    ```java
      for (int i = 0; i < SIZE; i++) {
          for (int j = 0; j < SIZE; j++) {
              // %4d означает, что мы под каждый номер резервируем 4 знака
              // (незанятые будут заполнены пробелами)
              // таким образом, у нас получится ровная таблица
              System.out.format("%4d", colors[i][j]);
          }
          // Переход на следующую строку
          System.out.println();
      }
    ```  
4. Для повернутой матрицы создадим пустой массив той же размерности:
    ```java
      int[][] rotatedColors = new int[SIZE][SIZE];
    ``` 
5. Новая матрица должна принять значения ячеек первой матрицы, но с поворотом на 90 градусов по часовой стрелке.
Это значит, что значение первой ячейки `rotatedColors[0][0]` (первая строка, первое значение) новой матрицы
должно быть равно первому значению ячейки последней строки матрицы colors (`colors[SIZE - 1][0]`).
6. Исходя из вышесказанного нужно: 
  * написать циклы, при помощи которых можно пробежаться по матрицам,
  * каждому элементу новой матрицы `rotatedColors` присвоить соответствующее значение из имеющейся `colors` матрицы.

Перебор элементов матрицы можно организовать встроенными циклами так же, как вы вывели значения на экран colors матрицы.

После поворота нужно вывести получившуюся матрицу на экран.

------

## Задание 2 (НЕобязательное)

:warning: _Эта задача - усложнение первой задачи, поэтому делается в том же реплите. Как итог вы сдаёте один реплит, в которой либо первая, либо вторая задача._

Добавьте в задачу возможности выбора пользователем угла поворота: 90, 180 или 270 градусов.

------

## Правила приема работы

Прикреплена только одна ссылка на один реплит с решением либо первой, либо второй задачи.

------

## Критерии оценки

1. Программа запускается и отрабатывает без ошибок
2. Программа соответствует всем требованиям из условия задачи
3. Программа работает правильно на всех примерах из условия
4. Программный код отформатирован и соответствует пройденным требованиям к качеству кода
5. Программа спроектирована достаточно логично и правильно, не противоречит общепринятым в производстве практикам и традициям
6. Программа реализована только с использованием пройденных интсрументов и не содержит в себе побочного не упомянутого в условии функционала
7. При наличии недочётов, в зависимости от их серьёзности и количества, работа может быть отправлена на доработку или принята; решение принимается на основе экспертной оценки работы.