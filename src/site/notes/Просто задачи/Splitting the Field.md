---
{"dg-publish":true,"permalink":"/prosto-zadachi/splitting-the-field/"}
---

Задача уровня *Gold* с [[Сайты/usaco.guide\|usaco.guide]], получается, что это самая СЛОЖНАЯ задача, которую я решал 🤯 (по крайней мере, считая что это задача уровня *Gold*, т.е. может в принципе попасться в *Региональном Этапе ВСОШ*, хотя так я думаю, Я же решал РЭ до этого так что нет) #задача 

# условие
> у Джона много коров, он хочет огородить всех одним забором, но потом он передумал и захотел использовать два забора, найдите сколько он может сэкономить с этого решения (если что первый раз он выбирал наилучшее решение и для второго тоже лучшее)

[Полное решение](https://usaco.org/index.php?page=viewproblem2&cpid=645)
# размышление

*Первое блюдо:* площадь забора вычисляется по формуле $(X-x) \cdot (Y-y)$, здесь $X, Y$ — максимальные, $x,y$ — минимальные

*Второе:* два забора не перекрываются, если между ними есть черта, причём или горизонтальная, или вертикальная

<style> .container {font-family: sans-serif; text-align: center;} .button-wrapper button {z-index: 1;height: 40px; width: 100px; margin: 10px;padding: 5px;} .excalidraw .App-menu_top .buttonList { display: flex;} .excalidraw-wrapper { height: 800px; margin: 50px; position: relative;} :root[dir="ltr"] .excalidraw .layer-ui__wrapper .zen-mode-transition.App-menu_bottom--transition-left {transform: none;} </style><script src="https://cdn.jsdelivr.net/npm/react@17/umd/react.production.min.js"></script><script src="https://cdn.jsdelivr.net/npm/react-dom@17/umd/react-dom.production.min.js"></script><script type="text/javascript" src="https://cdn.jsdelivr.net/npm/@excalidraw/excalidraw@0/dist/excalidraw.production.min.js"></script><div id="Splitting_the_Field_2024-04-20_1737.43.excalidraw.md1"></div><script>(function(){const InitialData={"type":"excalidraw","version":2,"source":"https://github.com/zsviczian/obsidian-excalidraw-plugin/releases/tag/2.0.26","elements":[{"type":"rectangle","version":397,"versionNonce":179636216,"isDeleted":false,"id":"pALtresekIOP0XW2mRZON","fillStyle":"solid","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":1.5699098115349557,"x":-31.169447092865234,"y":21.835490739573956,"strokeColor":"#2f9e44","backgroundColor":"transparent","width":75.55303119497248,"height":125.17502417697918,"seed":764003976,"groupIds":[],"frameId":null,"roundness":{"type":3},"boundElements":[],"updated":1713625776264,"link":null,"locked":false},{"type":"rectangle","version":66,"versionNonce":131525768,"isDeleted":false,"id":"zLZxpOtt67hssomeLmI_G","fillStyle":"solid","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":-104.66666412353516,"y":-146.33331298828125,"strokeColor":"#2f9e44","backgroundColor":"transparent","width":108.66666412353516,"height":102.66665649414062,"seed":1913587960,"groupIds":[],"frameId":null,"roundness":{"type":3},"boundElements":[],"updated":1713623933045,"link":null,"locked":false},{"type":"rectangle","version":454,"versionNonce":432930040,"isDeleted":false,"id":"QAm9FOL_Dsr89bIYJSrs6","fillStyle":"solid","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":4.7132754956446306,"x":-27.588191692386633,"y":182.90713985976325,"strokeColor":"#2f9e44","backgroundColor":"transparent","width":106.02103301603869,"height":76.2392417298527,"seed":776021240,"groupIds":[],"frameId":null,"roundness":{"type":3},"boundElements":[],"updated":1713625774367,"link":null,"locked":false},{"type":"rectangle","version":82,"versionNonce":1194425592,"isDeleted":false,"id":"U1Psq8cerWBQvgsOatXQ9","fillStyle":"solid","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":19.333328247070312,"y":-176.3333282470703,"strokeColor":"#2f9e44","backgroundColor":"transparent","width":126.66667175292969,"height":80.83332824707031,"seed":1434424200,"groupIds":[],"frameId":null,"roundness":{"type":3},"boundElements":[],"updated":1713623930679,"link":null,"locked":false},{"type":"line","version":267,"versionNonce":2068719496,"isDeleted":false,"id":"IQyZ60GsPEosVu4BB5xyl","fillStyle":"solid","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":12.261355062347016,"y":-187.67099455742286,"strokeColor":"#e03131","backgroundColor":"transparent","width":2.100143446091371,"height":184.83766631035255,"seed":1487714808,"groupIds":[],"frameId":null,"roundness":{"type":2},"boundElements":[],"updated":1713623917239,"link":null,"locked":false,"startBinding":null,"endBinding":null,"lastCommittedPoint":null,"startArrowhead":null,"endArrowhead":null,"points":[[0,0],[-2.100143446091371,184.83766631035255]]},{"type":"line","version":523,"versionNonce":1738062584,"isDeleted":false,"id":"-6r1R_ATdZRSYmX28ABeW","fillStyle":"solid","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":4.7132754956446306,"x":22.044933596004046,"y":52.7892626753073,"strokeColor":"#e03131","backgroundColor":"transparent","width":0.4030380701896963,"height":189.58348573814789,"seed":499238392,"groupIds":[],"frameId":null,"roundness":{"type":2},"boundElements":[],"updated":1713625858040,"link":null,"locked":false,"startBinding":null,"endBinding":null,"lastCommittedPoint":null,"startArrowhead":null,"endArrowhead":null,"points":[[0,0],[0.4030380701896963,189.58348573814789]]},{"type":"text","version":44,"versionNonce":1502628088,"isDeleted":false,"id":"aiopZM5A","fillStyle":"solid","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":-32.40818563267575,"y":-280.3182323648018,"strokeColor":"#2f9e44","backgroundColor":"transparent","width":208.29971313476562,"height":77.04911161321999,"seed":2055328136,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[],"updated":1713624027044,"link":null,"locked":false,"fontSize":61.639289290575995,"fontFamily":1,"text":"OK! 🫡","rawText":"OK! 🫡","textAlign":"left","verticalAlign":"top","containerId":null,"originalText":"OK! 🫡","lineHeight":1.25},{"type":"text","version":107,"versionNonce":1536515208,"isDeleted":false,"id":"A5bVLrdn","fillStyle":"solid","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":303.3000079529638,"y":-282.9887796366403,"strokeColor":"#e03131","backgroundColor":"transparent","width":148.506103515625,"height":77.11082142967165,"seed":1682501512,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[],"updated":1713624031357,"link":null,"locked":false,"fontSize":61.688657143737316,"fontFamily":1,"text":"But..","rawText":"But..","textAlign":"left","verticalAlign":"top","containerId":null,"originalText":"But..","lineHeight":1.25},{"type":"rectangle","version":89,"versionNonce":1790501256,"isDeleted":false,"id":"7NXWW66pdH95ohn8Vs0w4","fillStyle":"solid","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":286.6509222602307,"y":-47.32963183463153,"strokeColor":"#e03131","backgroundColor":"transparent","width":179.62395181552063,"height":114.03513015689896,"seed":74056184,"groupIds":[],"frameId":null,"roundness":{"type":3},"boundElements":[],"updated":1713624046917,"link":null,"locked":false},{"type":"rectangle","version":55,"versionNonce":213094904,"isDeleted":false,"id":"bP0lBlU-STgsO_H5KcoC6","fillStyle":"solid","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":379.81688964356636,"y":-3.3553233432521665,"strokeColor":"#e03131","backgroundColor":"transparent","width":140.12157509425504,"height":106.58183093046114,"seed":140491768,"groupIds":[],"frameId":null,"roundness":{"type":3},"boundElements":[],"updated":1713624051536,"link":null,"locked":false},{"id":"sX3upEPn","type":"text","x":-95.2738593531125,"y":214.3645076405143,"width":18,"height":45,"angle":0,"strokeColor":"#e03131","backgroundColor":"transparent","fillStyle":"solid","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"groupIds":[],"frameId":null,"roundness":null,"seed":269094536,"version":2,"versionNonce":908987528,"isDeleted":true,"boundElements":null,"updated":1713625859523,"link":null,"locked":false,"text":"","rawText":"","fontSize":36,"fontFamily":1,"textAlign":"left","verticalAlign":"top","containerId":null,"originalText":"","lineHeight":1.25}],"appState":{"theme":"light","viewBackgroundColor":"#ffffff","currentItemStrokeColor":"#e03131","currentItemBackgroundColor":"transparent","currentItemFillStyle":"solid","currentItemStrokeWidth":2,"currentItemStrokeStyle":"solid","currentItemRoughness":1,"currentItemOpacity":100,"currentItemFontFamily":1,"currentItemFontSize":36,"currentItemTextAlign":"left","currentItemStartArrowhead":null,"currentItemEndArrowhead":"arrow","scrollX":210.1474038154131,"scrollY":483.31087808093827,"zoom":{"value":0.6617628816077107},"currentItemRoundness":"round","gridSize":null,"gridColor":{"Bold":"#C9C9C9FF","Regular":"#EDEDEDFF"},"currentStrokeOptions":null,"previousGridSize":null,"frameRendering":{"enabled":true,"clip":true,"name":true,"outline":true}},"files":{}};InitialData.scrollToContent=true;App=()=>{const e=React.useRef(null),t=React.useRef(null),[n,i]=React.useState({width:void 0,height:void 0});return React.useEffect(()=>{i({width:t.current.getBoundingClientRect().width,height:t.current.getBoundingClientRect().height});const e=()=>{i({width:t.current.getBoundingClientRect().width,height:t.current.getBoundingClientRect().height})};return window.addEventListener("resize",e),()=>window.removeEventListener("resize",e)},[t]),React.createElement(React.Fragment,null,React.createElement("div",{className:"excalidraw-wrapper",ref:t},React.createElement(ExcalidrawLib.Excalidraw,{ref:e,width:n.width,height:n.height,initialData:InitialData,viewModeEnabled:!0,zenModeEnabled:!0,gridModeEnabled:!1})))},excalidrawWrapper=document.getElementById("Splitting_the_Field_2024-04-20_1737.43.excalidraw.md1");ReactDOM.render(React.createElement(App),excalidrawWrapper);})();</script>

*Третье:* если мы научимся искать ответ для построения двух заборов между которыми есть вертикальная линия, то мы решили задачу.  Ведь мы можем найти ответ для всех коров, потом поменять $x$ и $y$ местами и опять решить задачу

*Четвёртое блюдо:* теперь отсортируем все коровы по $x$, теперь все коровы левее линии находятся в массиве с индексом меньше равно $i$, правее больше $i$

*Пятое:* теперь нужно научиться быстро искать максимальное, минимальное $x$ и $y$ (в отсортированном массиве на интервале).  В отсортированном по $x$ массиве минимальный $x$ — слева, максимальный $x$ — справа. Осталось искать быстро минимальный и максимальный $y$, буду использовать [[Структуры Данных/Префиксное гавно\|Префиксное гавно]] и [[Структуры Данных/Суффиксное гавно\|Суффиксное гавно]].

Супер! Вот алгоритм.
1. Строить префиксный и суффиксный максимум минимум
2. Отсортируем по $x$
3. Итерируемся по коровам, выбираем $x$ коровы — вертикальная линия
4. Для этой коровы с индексом $i$ ищем минимальный и максимальный $x$ и $y$, выше упомянутыми способами слева (на диапазоне $[0; i]$) и справа $[i+1; n)$
5. По вышеупомянутой формуле находим площади двух прямоугольников
6. Из этих всех сум площадей двух прямоугольников ищем минимальную
7. Меняем для каждой коровы $x$ и $y$ местами
8. Повторяем всё заново
9. Ответ: изначальная площадь забора минус минимум

Yope!

# код
```cpp
// Copyright 2024 semenInRussia
#include <bits/stdc++.h>
using namespace std;

using ll = long long;
const ll inf = (ll)1e10;

inline ll area(ll a, ll b) { return 1LL * a * b; }

int main() {
  ifstream cin("split.in");
  ofstream cout("split.out");
  int n;
  cin >> n;

  vector<pair<ll, ll>> ps(n);
  for (auto &p : ps)
    cin >> p.first >> p.second;

  ll ans = inf, ar;
  for (int _axis : {1, 2}) {
    sort(ps.begin(), ps.end());

    // prefix and suffix maximum and minimum
    vector<ll> smx(n), smn(n), pmx(n), pmn(n);

    // suffix maximum/minimum
    ll mx = -inf, mn = inf;
    for (int i = n - 1; i >= 0; i--) {
      mx = max(mx, ps[i].second), mn = min(mn, ps[i].second);
      smx[i] = mx, smn[i] = mn;
    }

    // prefix maximum/minimum
    mx = -inf, mn = inf;
    for (int i = 0; i < n; i++) {
      mx = max(mx, ps[i].second), mn = min(mn, ps[i].second);
      pmx[i] = mx, pmn[i] = mn;
    }

    // also check if only one area
    ll s = area(ps[n - 1].first - ps[0].first, pmx[n - 1] - pmn[n - 1]);
    ans = min(ans, s);

    for (int i = 1; i + 1 < n; i++) {
      if (ps[i].first == ps[i + 1].first)
        continue;
      // Rectangle lefter line, cows in diapason [0; i]
      ll a = area(pmx[i] - pmn[i],
                  ps[i].first - ps[0].first);

      // Rectangle righter line, cows in diapason [i+1; n)
      ll b = area(smx[i + 1] - smn[i + 1],
                  ps[n - 1].first - ps[i + 1].first);
      ans = min(ans, a + b);
    }

    ar = area(pmx.back() - pmn.back(), ps.back().first - ps.front().first);

    // change axis
    for (auto &p : ps)
      swap(p.first, p.second);
  }

  cout << (ar - ans) << endl;
}
```