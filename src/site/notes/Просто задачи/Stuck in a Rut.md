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

<style> .container {font-family: sans-serif; text-align: center;} .button-wrapper button {z-index: 1;height: 40px; width: 100px; margin: 10px;padding: 5px;} .excalidraw .App-menu_top .buttonList { display: flex;} .excalidraw-wrapper { height: 800px; margin: 50px; position: relative;} :root[dir="ltr"] .excalidraw .layer-ui__wrapper .zen-mode-transition.App-menu_bottom--transition-left {transform: none;} </style><script src="https://cdn.jsdelivr.net/npm/react@17/umd/react.production.min.js"></script><script src="https://cdn.jsdelivr.net/npm/react-dom@17/umd/react-dom.production.min.js"></script><script type="text/javascript" src="https://cdn.jsdelivr.net/npm/@excalidraw/excalidraw@0/dist/excalidraw.production.min.js"></script><div id="Stuck_in_a_Rut_2024-03-31_1417.05.excalidraw.md1"></div><script>(function(){const InitialData={"type":"excalidraw","version":2,"source":"https://github.com/zsviczian/obsidian-excalidraw-plugin/releases/tag/2.0.26","elements":[{"type":"rectangle","version":198,"versionNonce":1892818561,"isDeleted":false,"id":"e5g79zl4fi6gvevz0DQTW","fillStyle":"solid","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":-138,"y":-225.3333282470703,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":275.3333435058594,"height":256.3333282470703,"seed":1119210273,"groupIds":[],"frameId":null,"roundness":{"type":3},"boundElements":[],"updated":1711883834225,"link":null,"locked":false},{"type":"text","version":3,"versionNonce":1926780079,"isDeleted":false,"id":"TcNxyasK","fillStyle":"solid","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":-106.42780134081949,"y":-201.13042232708733,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":24.90234375,"height":25,"seed":1167260911,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[{"id":"JUe_yVvCvM37nBDwI8w6O","type":"arrow"}],"updated":1711883925279,"link":null,"locked":false,"fontSize":20,"fontFamily":1,"text":"🐮","rawText":"🐮","textAlign":"left","verticalAlign":"top","containerId":null,"originalText":"🐮","lineHeight":1.25},{"type":"text","version":247,"versionNonce":916369793,"isDeleted":false,"id":"TeQvH50o","fillStyle":"solid","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":-104.520568610082,"y":-116.80697391656332,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":23.73504638671875,"height":23.83792073099826,"seed":1352150401,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[{"id":"iUjl3tD8psQRo10JitlI6","type":"arrow"}],"updated":1711884144285,"link":null,"locked":false,"fontSize":19.070336584798607,"fontFamily":1,"text":"🐮","rawText":"🐮","textAlign":"left","verticalAlign":"top","containerId":null,"originalText":"🐮","lineHeight":1.25},{"type":"text","version":147,"versionNonce":1923326401,"isDeleted":false,"id":"SmQLaLVG","fillStyle":"solid","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":59.92322090143966,"y":-23.426040126314074,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":27.275848388671875,"height":27.38855416989669,"seed":1065696481,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[{"id":"xPRfqBr8hvkPdOShL1Mag","type":"arrow"}],"updated":1711884149968,"link":null,"locked":false,"fontSize":21.910843335917352,"fontFamily":1,"text":"🐮","rawText":"🐮","textAlign":"left","verticalAlign":"top","containerId":null,"originalText":"🐮","lineHeight":1.25},{"type":"text","version":202,"versionNonce":1527415393,"isDeleted":false,"id":"vNwXD0DP","fillStyle":"solid","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":-18.780419959944822,"y":-23.30304531812241,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":27.275848388671875,"height":27.38855416989669,"seed":1540803279,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[{"id":"pAzBjehKq1vO9NPaLdFZ4","type":"arrow"}],"updated":1711884148357,"link":null,"locked":false,"fontSize":21.910843335917352,"fontFamily":1,"text":"🐮","rawText":"🐮","textAlign":"left","verticalAlign":"top","containerId":null,"originalText":"🐮","lineHeight":1.25},{"type":"arrow","version":184,"versionNonce":204723265,"isDeleted":false,"id":"JUe_yVvCvM37nBDwI8w6O","fillStyle":"solid","strokeWidth":2,"strokeStyle":"dashed","roughness":1,"opacity":100,"angle":0,"x":-76.90372006508828,"y":-186.89134452279265,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":116.97723455622726,"height":0.8286254803427369,"seed":386952879,"groupIds":[],"frameId":null,"roundness":{"type":2},"boundElements":[],"updated":1711884004831,"link":null,"locked":false,"startBinding":{"elementId":"TcNxyasK","focus":0.1477587198202628,"gap":4.621737525731206},"endBinding":null,"lastCommittedPoint":null,"startArrowhead":null,"endArrowhead":"arrow","points":[[0,0],[116.97723455622726,-0.8286254803427369]]},{"type":"arrow","version":708,"versionNonce":1143932225,"isDeleted":false,"id":"iUjl3tD8psQRo10JitlI6","fillStyle":"solid","strokeWidth":2,"strokeStyle":"dashed","roughness":1,"opacity":100,"angle":0,"x":-78.39704737192247,"y":-102.60031422334953,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":55.34947472205937,"height":0.15415782354000385,"seed":1181493007,"groupIds":[],"frameId":null,"roundness":{"type":2},"boundElements":[],"updated":1711884144286,"link":null,"locked":false,"startBinding":{"elementId":"TeQvH50o","focus":0.18808916412807586,"gap":2.388474851440769},"endBinding":{"elementId":"HSCG7sZC0CugzvD8hVnZJ","focus":0.44627625718066893,"gap":7.47996989935125},"lastCommittedPoint":null,"startArrowhead":null,"endArrowhead":"arrow","points":[[0,0],[55.34947472205937,0.15415782354000385]]},{"type":"arrow","version":471,"versionNonce":1935992193,"isDeleted":false,"id":"xPRfqBr8hvkPdOShL1Mag","fillStyle":"solid","strokeWidth":2,"strokeStyle":"dashed","roughness":1,"opacity":100,"angle":0,"x":76.22820527351513,"y":-24.426040126314078,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":1.6360412810290939,"height":146.98802835708847,"seed":207397103,"groupIds":[],"frameId":null,"roundness":{"type":2},"boundElements":[],"updated":1711884149969,"link":null,"locked":false,"startBinding":{"elementId":"SmQLaLVG","gap":1,"focus":0.1815422448395761},"endBinding":{"elementId":"QjrpAD5WA7YVcUjsXkuI4","gap":8.53902519555231,"focus":-0.23987577491113918},"lastCommittedPoint":null,"startArrowhead":null,"endArrowhead":"arrow","points":[[0,0],[1.6360412810290939,-146.98802835708847]]},{"type":"arrow","version":565,"versionNonce":2093227553,"isDeleted":false,"id":"pAzBjehKq1vO9NPaLdFZ4","fillStyle":"solid","strokeWidth":2,"strokeStyle":"dashed","roughness":1,"opacity":100,"angle":0,"x":-5.943943612145353,"y":-33.492326995424875,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":1.2591606977810148,"height":49.299727214761916,"seed":1125700961,"groupIds":[],"frameId":null,"roundness":{"type":2},"boundElements":[],"updated":1711884148358,"link":null,"locked":false,"startBinding":{"elementId":"vNwXD0DP","focus":-0.013650163833273844,"gap":10.189281677302462},"endBinding":{"elementId":"HSCG7sZC0CugzvD8hVnZJ","focus":-0.12369539977372773,"gap":9.019224401160827},"lastCommittedPoint":null,"startArrowhead":null,"endArrowhead":"arrow","points":[[0,0],[-1.2591606977810148,-49.299727214761916]]},{"type":"ellipse","version":231,"versionNonce":639174351,"isDeleted":false,"id":"QjrpAD5WA7YVcUjsXkuI4","fillStyle":"solid","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":68.72160758008447,"y":-194.26322978751534,"strokeColor":"#1e1e1e","backgroundColor":"#ffc9c9","width":15.028549270450583,"height":14.391292675918777,"seed":594193007,"groupIds":[],"frameId":null,"roundness":{"type":2},"boundElements":[{"id":"xPRfqBr8hvkPdOShL1Mag","type":"arrow"}],"updated":1711884135715,"link":null,"locked":false},{"id":"HSCG7sZC0CugzvD8hVnZJ","type":"ellipse","x":-15.946293065149405,"y":-106.48264367189145,"width":14.818721869913027,"height":14.725446994678379,"angle":0,"strokeColor":"#1e1e1e","backgroundColor":"#ffec99","fillStyle":"solid","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"groupIds":[],"frameId":null,"roundness":{"type":2},"seed":731319791,"version":95,"versionNonce":208307343,"isDeleted":false,"boundElements":[{"id":"iUjl3tD8psQRo10JitlI6","type":"arrow"},{"id":"pAzBjehKq1vO9NPaLdFZ4","type":"arrow"}],"updated":1711884124360,"link":null,"locked":false}],"appState":{"theme":"light","viewBackgroundColor":"#ffffff","currentItemStrokeColor":"#1e1e1e","currentItemBackgroundColor":"#ffec99","currentItemFillStyle":"solid","currentItemStrokeWidth":2,"currentItemStrokeStyle":"solid","currentItemRoughness":1,"currentItemOpacity":100,"currentItemFontFamily":1,"currentItemFontSize":20,"currentItemTextAlign":"left","currentItemStartArrowhead":null,"currentItemEndArrowhead":"arrow","scrollX":132.95750422999112,"scrollY":279.76022012003654,"zoom":{"value":1.391314165168919},"currentItemRoundness":"round","gridSize":null,"gridColor":{"Bold":"#C9C9C9FF","Regular":"#EDEDEDFF"},"currentStrokeOptions":null,"previousGridSize":null,"frameRendering":{"enabled":true,"clip":true,"name":true,"outline":true}},"files":{}};InitialData.scrollToContent=true;App=()=>{const e=React.useRef(null),t=React.useRef(null),[n,i]=React.useState({width:void 0,height:void 0});return React.useEffect(()=>{i({width:t.current.getBoundingClientRect().width,height:t.current.getBoundingClientRect().height});const e=()=>{i({width:t.current.getBoundingClientRect().width,height:t.current.getBoundingClientRect().height})};return window.addEventListener("resize",e),()=>window.removeEventListener("resize",e)},[t]),React.createElement(React.Fragment,null,React.createElement("div",{className:"excalidraw-wrapper",ref:t},React.createElement(ExcalidrawLib.Excalidraw,{ref:e,width:n.width,height:n.height,initialData:InitialData,viewModeEnabled:!0,zenModeEnabled:!0,gridModeEnabled:!1})))},excalidrawWrapper=document.getElementById("Stuck_in_a_Rut_2024-03-31_1417.05.excalidraw.md1");ReactDOM.render(React.createElement(App),excalidrawWrapper);})();</script>

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