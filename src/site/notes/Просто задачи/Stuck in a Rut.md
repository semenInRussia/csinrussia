---
{"dg-publish":true,"permalink":"/prosto-zadachi/stuck-in-a-rut/"}
---

Это #задача c *Bronze* дивизиона [[Сайты/usaco.guide\|usaco.guide]] в главе *Simulation* (см. [[Просто задачи/Задача на Симуляцию\|Задача на Симуляцию]]), хоть это невозможно решить симуляцией (см. главу Решение Симуляцией)

*Ссылка*: https://usaco.guide/problems/usaco-1061-stuck-in-a-rut/solution

# Условие 📝

> Недавно Фермер Джон увеличил размер своей фермы, теперь с точки зрения коров, она бесконечная по размеру. Коровы представляют пастбище фермы как бесконечную 2D решётку квадратных ячеек, каждая из которых заполнена вкуснейшей травой. (Думайте о каждой ячейке как о клетке на шахматной доске). Каждая из $N$ коров ($1 \leq N \leq 100$) ФД начинает в различной ячейке. Некоторые начинают, глядя на север, а некоторые - на восток.  Каждый час корова или Останавливается, если трава в текущей ячейке уже съедена другой коровой.  Съедает всю траву в текущей ячейке и перемещается на одну ячейку вперёд в своём исходном направлении.
>
> Через некоторое время каждая корова оставит за собой колею пустых ячеек.
>
> Если две коровы попадут одновременно на одну и ту же ячейку с травой, они поедят вместе и продолжат движение в своих направлениях в следующий час.
>
> Определите количество травы, съеденной каждой коровой. Некоторые коровы никогда не остановятся и поэтому съедят бесконечно количество травы.
>
> ### Формат ввода (с клавиатуры / stdin):
>
> Первая строка ввода содержит $N$. Каждая из последующих $N$ строк описывает стартовую позицию коровы в терминах символ ($N$ - если будет двигаться на север, E если будет двигаться на восток) и два неотрицательных целых числа x и y ($0 \leq x \leq 10^9$; $0 \leq y \leq 10^9$) координаты ячейки. $x$ -**координаты различны для всех** коров, аналогично и $y$ -**координаты различны для всех коров**.  Чтобы было понятнее, относительно направлений и координат, если корова находится в ячейке $(x, y)$ и двигается на север, то она перейдёт в ячейку $(x, y+1)$ , а если на восток - то в ячейку $(x+1, y)$.
>
> ### Формат вывода (на экран / stdout):
> Выведите $N$ строк. Строка $i$ должна содержать количество ячеек травы, которая съест $i$-ая корова. Если корова съест бесконечное количество травы, выведите "Infinity" для этой коровы.
>

# Описание

Надо посмотреть когда корова оказывается на съеденной клетке и должна остановиться.  Это происходит тогда когда две коровы, одно, ходящая на север, другая, ходящая на восток, коровы попадаются на пути.  Т. е. можно разделить коровы на *E-коровы* (на Восток) и *W-коровы* (на Север), и смотреть через какое время они могут встретиться.  Для каждой *E-коровы* будем искать *W-корову* и если *E-корова* быстрее доходит до другой, то здесь она останавливается.  Обще изи.  Чтобы ответ был правильным надо отсортировать коров по их `x` и `y`

# Их официальное решение 🧑‍💻

```cpp
#include <bits/stdc++.h>
using namespace std;

struct Cow {
  int x, y;
  int ind;
};

int main() {
  int n;
  cin >> n;
  vector<Cow> n_cows;
  vector<Cow> e_cows;

  for (int i = 0; i < n; i++) {
    char dir;
    int x, y;
    cin >> dir >> x >> y;
    if (dir == 'N') {
      n_cows.push_back({x, y, i});
    } else if (dir == 'E') {
      e_cows.push_back({x, y, i});
    }
  }

  sort(n_cows.begin(), n_cows.end(),
       [&](const Cow &c1, const Cow &c2) { return c1.x < c2.x; });
  sort(e_cows.begin(), e_cows.end(),
       [&](const Cow &c1, const Cow &c2) { return c1.y < c2.y; });

  vector<int> stop_pos(n, -1);
  for (const Cow &ncow : n_cows) {
    for (const Cow &ecow : e_cows) {
      // Check that the two cows will intersect.
      if (ncow.x > ecow.x && ncow.y < ecow.y) {
        // Distance they travel before reaching the other cow's line.
        int n_trav = ecow.y - ncow.y;
        int e_trav = ncow.x - ecow.x;

        // Check if the north cow blocks the east cow.
        if (n_trav < e_trav && stop_pos[ecow.ind] == -1) {
          // # Save the x-coordinate at which the east cow stops
          stop_pos[ecow.ind] = ncow.x;
        }

        // Check if the east cow blocks the north cow.
        if (n_trav > e_trav && stop_pos[ecow.ind] == -1) {
          // Save the y-coordinate at which the north cow stops
          stop_pos[ncow.ind] = ecow.y;
          // At this point we can move on- this cow won't move
          // anymore.
          break;
        }
      }
    }
  }

  vector<int> dist(n, -1);
  for (const Cow &nc : n_cows) {
    // A cow eats a finite amount of grass if & only if this value isn't -1.
    if (stop_pos[nc.ind] != -1) {
      // Eaten is (stopped position - original position)
      dist[nc.ind] = stop_pos[nc.ind] - nc.y;
    }
  }

  for (const Cow &ec : e_cows) {
    if (stop_pos[ec.ind] != -1) {
      dist[ec.ind] = stop_pos[ec.ind] - ec.x;
    }
  }

  for (int d : dist) {
    cout << (d == -1 ? "Infinity" : to_string(d)) << '\n';
  }
}
```


# Решение Симуляцией

Я просто создам своё поле коров, каждая из коров будет двигаться в нужном направлении, сталкиваться, а я буду над этим смотреть.  Решение думаю обхяснять не стоит.  Единственное я хранил "съеденные клетки" в `map` ([[Структуры Данных/Красные, Чёрные Деревья\|Красные, Чёрные Деревья]]), чтобы за `O(log N)` смотреть съедена ли клетка.  Буду играть 100'000 раундов, что недостаточно, но на большее не хватит ограничений времени

И да это решение не работает на 100%

```cpp
#include <iostream>
#include <set>
#include <vector>

using namespace std;

struct Cow {
  int id, x, y;
  char dir;
};

int main() {
  int n;
  cin >> n;
  vector<Cow> cows(n);
  int t = 0;
  for (auto &cow : cows) {
    cin >> cow.dir >> cow.x >> cow.y;
    cow.id = t++;
  }

  using point = pair<int, int>;

  set<point> f;
  vector<int> eaten(n);

  const int maxround = 100'000;

  for (int round = 0; round < maxround; round++) {
    vector<point> toadd;
    for (auto &cow : cows) {
      if (cow.id == -1)
        continue;

      point p = {cow.x, cow.y};
      if (f.count(p)) {
        // a cell is busy
        cow.id = -1;
        continue;
      }

      eaten[cow.id]++;
      toadd.push_back(p);
      if (cow.dir == 'N')
        cow.y++;
      else
        cow.x++;
    }

    for (auto p : toadd)
      f.insert(p);
  }

  for (auto cow : cows)
    if (cow.id != -1)
      eaten[cow.id] = -1;

  for (int i = 0; i < n; i++) {
    cout << (eaten[i] == -1 ? "Infinity" : tostring(eaten[i])) << '\n';
  }
}

```