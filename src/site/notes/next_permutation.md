---
{"dg-publish":true,"permalink":"/next-permutation/"}
---

Просто расскажу о встроенном в `std` методе `next_permutation`.

*Что он делает?*

Это клёвая функция и самое крутое в ней — это её минимализм.  

`next_permutation` (как ясно из названия) необходимо для того , чтобы с генерировать все варианты перестановок данного массива.  Прикол в том, что `next_permutation` приставит данный массив, как "число", а его элементы "цифры", а эта функция тогда просто добавляет один к этому числу, изменяя цифры по всем правилам сложения