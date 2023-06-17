# shri-tooling-2

Анализ открытия [страницы](https://www.gd.ru/articles/9039-finansovyy-kontroldevtools) в Chrome DevTools

## Network

### Профили загрузки ресурсов

Профиль загрузки ресурсов при открытии страницы находится в корне проекта в директории`./profiles/www.gd.ru.har`<br>
Профиль загрузки ресурсов при включенном vpn `./profiles/vpn-ww.gd.ru.har`

### Дублирование ресурсов

Часть одних тех же ресурсов запрашивается по 2 раза

![double-1](https://github.com/AlexanderStreltsov/shri-tooling-2/assets/56827313/d2667257-64f3-4fad-8741-7c89a0c2b6bf)

---

![double-2](https://github.com/AlexanderStreltsov/shri-tooling-2/assets/56827313/e04b1766-a58d-4db4-8849-21804fdd040a)

---

![double-3](https://github.com/AlexanderStreltsov/shri-tooling-2/assets/56827313/f79ee725-45e7-4f1c-bf49-2084efa709af)

---

![double-4](https://github.com/AlexanderStreltsov/shri-tooling-2/assets/56827313/daf9497a-25b4-4382-881a-b087da945edb)

---

![double-5](https://github.com/AlexanderStreltsov/shri-tooling-2/assets/56827313/e81b5b4c-7ced-4027-844b-1c37b8b9d1ab)

---

![double-6](https://github.com/AlexanderStreltsov/shri-tooling-2/assets/56827313/916c9af4-c8ad-4672-a28d-f69a9a052e9f)

---

![double-7](https://github.com/AlexanderStreltsov/shri-tooling-2/assets/56827313/27124b4f-eabb-48a1-ab01-d19586618bd7)

---

![double-8](https://github.com/AlexanderStreltsov/shri-tooling-2/assets/56827313/340e4623-8d93-4e08-a8b7-af1aa518467a)

---

![double-9](https://github.com/AlexanderStreltsov/shri-tooling-2/assets/56827313/13ce3c88-f24e-46dc-be9e-5190a6ad58d2)

---

![double-10](https://github.com/AlexanderStreltsov/shri-tooling-2/assets/56827313/32d130d1-02cb-4642-b383-7c8513468431)

### Лишний размер ресурса

На странице почти везде используется шрифт PT Sans, только в нескольких элементах нашёл другие шрифты.<br>
Подгрузка шрифтов, которые почти не используются на странице, кажется излишней.
Можно попробовать отказаться от этих шрифтов (скрин ниже) в пользу основного.

![font-1](https://github.com/AlexanderStreltsov/shri-tooling-2/assets/56827313/e1b65c0e-a6ef-4389-8ee9-1b36ee5ce12a)

---

![font-2](https://github.com/AlexanderStreltsov/shri-tooling-2/assets/56827313/bd976de7-0343-4b94-a424-8b2fcedbf976)

---

Подгружаются неминифицированнные js файлы

![min-1](https://github.com/AlexanderStreltsov/shri-tooling-2/assets/56827313/062a5c40-7fb7-4fc2-88ce-8839017c3863)

---

## ![min-2](https://github.com/AlexanderStreltsov/shri-tooling-2/assets/56827313/f57cfe9c-bd90-4ca2-959a-82ee823b8d7c)

---

## ![min-3](https://github.com/AlexanderStreltsov/shri-tooling-2/assets/56827313/519cf62e-d2e3-400d-95ae-94dfbea507ff)

---

Часть получаемого контента не сжата в gzip/br, что увеличивает размер трафика

![zip-1](https://github.com/AlexanderStreltsov/shri-tooling-2/assets/56827313/32a3df6b-4ca3-469b-a05a-2196fa49db7c)

### Медленно загружающиеся / блокирующие загрузку ресурсы

Есть запросы которые подвешиваются и потом падают с ошибкой.<br>
Они увеличивают полную загрузку страницы приблизительно до 20 с.<br>
Также можно попробовать оптимизировать время работы самых долгих из отсортированных по времени запросов.

![block-1](https://github.com/AlexanderStreltsov/shri-tooling-2/assets/56827313/17bfa96b-b775-41b3-867c-a6cd567314b4)

---

Замечание, что при включенном vpn, сайт грузится быстрее. Запросы, которые падают на скрине выше, с vpn отрабатывают успешно.

![block-2](https://github.com/AlexanderStreltsov/shri-tooling-2/assets/56827313/5b4b3584-3241-491c-8cb6-2d7720db37d7)

---

Часть запросов идёт с редиректом, что увеличивает время запроса получения ресурса

![redirect-1](https://github.com/AlexanderStreltsov/shri-tooling-2/assets/56827313/ae7a86ec-ef7f-47a4-9e0b-2ef794e16647)<br>

---

![redirect-2](https://github.com/AlexanderStreltsov/shri-tooling-2/assets/56827313/d64a490e-01b1-4f98-8df4-8924e79fa917)<br>

---

![redirect-3](https://github.com/AlexanderStreltsov/shri-tooling-2/assets/56827313/eee608dc-3929-47cc-a3b0-7da33503d769)<br>

---

![redirect-4](https://github.com/AlexanderStreltsov/shri-tooling-2/assets/56827313/9e24e4b4-77ea-4c0c-bb56-4b2d63bdd23a)<br>

## Performance

### Профиль загрузки страницы

Профиль загрузки страницы находится в корне проекта в директории`./profiles/Trace-20230617T120003.json`<br>

### Измерение времени от начала навигации до событий

First Paint (FP) **706.3 ms**

![fp](https://github.com/AlexanderStreltsov/shri-tooling-2/assets/56827313/53ce9a00-acb3-4115-980f-5ca1ae53fe44)

---

First Contentful Paint (FCP) **706.3 ms**

## ![fcp](https://github.com/AlexanderStreltsov/shri-tooling-2/assets/56827313/f4a4441e-3f13-41ba-bc18-17ba4676119d)

---

DOM Content Loaded (DCL) **2158.9 ms**

![dcl](https://github.com/AlexanderStreltsov/shri-tooling-2/assets/56827313/eac7fde8-4653-4002-8698-a80c71096cc6)

---

Largest Contentful Paint (LCP) **2455.1 ms**

![lcp-element](https://github.com/AlexanderStreltsov/shri-tooling-2/assets/56827313/04ac518d-c460-4491-b817-f69769bed19a)

---

![lcp-element-2](https://github.com/AlexanderStreltsov/shri-tooling-2/assets/56827313/0e755a1f-edb7-49d3-9db1-969052d67181)

---

Load **18109.0 ms**

![onload](https://github.com/AlexanderStreltsov/shri-tooling-2/assets/56827313/18b6673a-f449-4dce-8f4b-d3e3d5bcebc6)

### Измерение времени на разные этапы обработки документа

- Loading **57 ms**
- Scripting **2483 ms**
- Rendering **1208 ms**
- Painting **74 ms**

![summary](https://github.com/AlexanderStreltsov/shri-tooling-2/assets/56827313/b90edda0-9114-470e-93c0-daeda4b2c6e2)

## Coverage

### Измерение после загрузки страницы

- Oбъём неиспользованного CSS **540 kB**
- Объём неиспользованного JS **2.3 MB**

![unused-1](https://github.com/AlexanderStreltsov/shri-tooling-2/assets/56827313/876857aa-1740-41e3-8afc-739c4bd03a0d)

## Perfomance Slow 3G

Профиль загрузки страницы на медленной работе интернета находится в корне проекта в директории`./profiles/slow-trace-20230617T140436`

---

- First Paint (FP) **10020.1 ms**
- First Contentful Paint (FCP) **10020.1 ms**
- DOM Content Loaded (DCL) **40443.7 ms**
- Largest Contentful Paint (LCP) **49194.8 ms**
- Load **59947.6 ms**

---

- Loading **98 ms**
- Scripting **3524 ms**
- Rendering **3166 ms**
- Painting **349 ms**

---

![slow](https://github.com/AlexanderStreltsov/shri-tooling-2/assets/56827313/130af599-10da-4b8a-95be-4b1084becd58)
