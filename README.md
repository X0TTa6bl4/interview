Шахматы
=======

`chess.php` — консольный проигрыватель шахматных партий.
Программа получает ходы игроков в качестве аргументов и выводит
состояние доски с фигурами после этих ходов.

Например:

```bash 
php chess.php e2-e4 e7-e5
```
```
    8 ♜♞♝♛♚♝♞♜
    7 ♟♟♟♟-♟♟♟
    6 --------
    5 ----♟---
    4 ----♙---
    3 --------
    2 ♙♙♙♙-♙♙♙
    1 ♖♘♗♕♔♗♘♖
      abcdefgh
```


В текущем виде `chess.php` никак не проверяет правильность ходов.

## Задача 1

Задача 1: дописать программу таким образом, чтобы она выкидывала исключение
при нарушении очерёдности хода (например, два раза подряд ход белых).

Чтобы проверить корректность решения, запустите тесты:

```bash
./vendor/bin/phpunit --group=rotation
```

## Задача 2

Задача 2: дописать программу таким образом, чтобы она выкидывала исключение
при нарушении правил хода пешкой (pawn).

Чтобы проверить корректность решения, запустите тесты:

```bash
./vendor/bin/phpunit --group=pawn
```

В тестах проверяются только ходы пешками, для других фигур валидацию ходов делать не нужно.

### Как ходит пешка

* Пешка может ходить вперёд (по вертикали) на одну клетку;
* Если пешка ещё ни разу не ходила, она может пойти вперёд на две клетки;
* Пешка не может перепрыгивать через другие фигуры;
* Пешка может бить фигуры противника только по диагонали вперёд на одну клетку;
* Также существует взятие на проходе, но им можно пренебречь :)

## Комментарии к выполнению 
Класс Figure изменил на абстрактный класс и добавил абстрактный метод. Сделал так потому что если надо будет добавить правила для других фигур то это решение выглядит лучше чем добавления интерфейса каждой фигуре. Во всех фигурах кроме пешки метод для описания правил пустой. Логика работы метода следующая, если ход соответствует одной из проверок то метод просто завершает работу, если нет то метод выбрасывает исключение. В начале поставил базовую проверку (возможно избыточна) для проверки того что пешка не пошла более чем на 2 клетки.
