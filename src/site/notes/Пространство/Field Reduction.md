---
{"dg-publish":true,"permalink":"/prostranstvo/field-reduction/"}
---

Очередная #задача с [[Сайты/usaco.guide\|usaco.guide]] на тему геометрия или, как записано у меня в Obsidian — *Пространство*.

Можете её решить [здесь](https://usaco.org/index.php?page=viewproblem2&cpid=642)

# Условие
(*Я напишу своими словами)*


> У фермера Джона есть коровы (классика) на 2D поле, и он хочет огородить все коровы забором.  При этом у него заканчиваются деньги, поэтому он хочет уволить 3ёх коров.
> 
> Узнайте какая минимальная площадь может быть огорожена забором чтобы огородить всех, если он съест трёх коров?


# Размышление

Для начала надо вывести формулу площади загона для какого-то множества коров.  Забор это 4 прямых, захватывающий всех коров.

Ширина загона — разница между минимальным и максимальным `x`. Длина — тоже самое, но с `y`.

И формула:
`s = (max(xs) - min(xs)) * (max(ys) - min(ys))`

Окей.  Из этой формулы ясно, что площадь забора зависит лишь от четырёх коров, с максимальным/минимальным иксом или игриком.

Поэтому на каждом шаге у Джона есть 4 выбора.  И всего выборов $4^3 = 64$.  На каждом шаге от Джон ищет 4 коров за `O(N)` и делится на 4 альтернативных решений, каждое решение это удалить определённую корову, понятно что надо вернуть самую маленькую возможную площадь из 4 решений.  Базовый случай здесь тогда, когда 3 коровы уже было удалено.  С помощью простой [рекурсивной функции](рекурсия) можно сдать эту задачу.  Сложность будет `O(64*N)`, что равно `O(N)`

Важно, что здесь  что [[Жадный алгоритм\|Жадный алгоритм]] не работает, хз как это вы могли узнать только [[Proof by AC\|Proof by AC]]