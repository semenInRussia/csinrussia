---
{"dg-publish":true,"permalink":"/prosto-zadachi/mowing-the-field/"}
---

#задача  с [[Сайты/usaco.guide\|usaco.guide]] ссылка:

https://usaco.org/index.php?page=viewproblem2&cpid=593

Простая [[Просто задачи/Задача на Симуляцию\|задача на симуляцию]], надо тупо симулировать походку Джона, сохранять время когда он посетил клетки в посетил в `map` ([[Структуры Данных/Красные, Чёрные Деревья\|Красные, Чёрные Деревья]]) и если мы посещаем, то обновляем `x`

> `x = min(x, t - x); t++`

# Код
Вот


```cpp
using namespace std;

#include <climits>
#include <fstream>
#include <unordered_map>

int main() {
  ifstream cin("mowing.in");
  ofstream cout("mowing.out");

  int n;
  cin >> n;
  char d[n];
  int s[n];
  for (int i = 0; i < n; i++)
    cin >> d[i] >> s[i];

  const int w = 10'000;
  int delta['W' - 'E' + 1];
  delta['W' - 'E'] = -1; // left
  delta['E' - 'E'] = +1; // right
  delta['N' - 'E'] = -w; // up
  delta['S' - 'E'] = w;  // down

  unordered_map<int, int> h;
  int point = 0, x = INT_MAX, t = 0, found = 0;
  h[point] = t++;

  for (int i = 0; i < n; i++) {
    // field is (2w; 2w) square at two sides
    int dpoint = delta[d[i] - 'E'];
    for (int j = 0; j < s[i]; j++) {
      point += dpoint;
      // already was here
      if (h.count(point)) {
        found = true;
        x = min(x, t - h[point]);
      }
      h[point] = t++;
    }
  }

  cout << (found ? x : -1);
}
```