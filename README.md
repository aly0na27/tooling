# Использование Chrome DevTools

Сделать в Chrome DevTools анализ открытия страницы https://www.rigla.ru.

## Network

* найти неоптимальные места:

  - дублирование ресурсов:
  
    <img width="518" alt="Снимок экрана 2024-06-23 в 22 36 48" src="https://github.com/aly0na27/tooling/assets/120110608/0adc43c6-2b8d-47bf-bb4d-beed8c9cf004">

    <img width="748" alt="Снимок экрана 2024-06-23 в 22 37 26" src="https://github.com/aly0na27/tooling/assets/120110608/d35373a2-1535-496a-ab4a-4a5d988104e6">

    <img width="748" alt="Снимок экрана 2024-06-23 в 22 37 54" src="https://github.com/aly0na27/tooling/assets/120110608/b4670e9c-d4e8-4488-a7c9-63c2987a0a47">

    <img width="745" alt="Снимок экрана 2024-06-23 в 22 38 15" src="https://github.com/aly0na27/tooling/assets/120110608/8b6bcb4c-2d99-4be5-8319-c91deb82c8bd">

    <img width="413" alt="Снимок экрана 2024-06-23 в 22 39 02" src="https://github.com/aly0na27/tooling/assets/120110608/eecee3a8-6c68-4498-b938-2ec07580a584">

  - лишний размер ресурса:
  
    <img width="789" alt="Снимок экрана 2024-06-23 в 22 39 59" src="https://github.com/aly0na27/tooling/assets/120110608/00962134-4be5-4a3f-8dea-8d4f9239418e">

    Картники можно было бы сжать.

  - медленно загружающиеся ресурсы:
  
    <img width="901" alt="Снимок экрана 2024-06-23 в 22 40 28" src="https://github.com/aly0na27/tooling/assets/120110608/e7cd9415-dbaf-45d0-88de-4bd98212ac04">

  - ресурсы, блокирующие загрузку:

    <img width="409" alt="Снимок экрана 2024-06-23 в 22 51 00" src="https://github.com/aly0na27/tooling/assets/120110608/5524f7c7-6e97-4403-afc9-dcfe619a0ebd">

    <img width="1404" alt="Снимок экрана 2024-06-23 в 22 52 18" src="https://github.com/aly0na27/tooling/assets/120110608/0b281b85-7e57-45d4-a822-ed38fa4ea4fb">

    <img width="1358" alt="Снимок экрана 2024-06-23 в 22 53 27" src="https://github.com/aly0na27/tooling/assets/120110608/d5a58f98-1f36-49b0-9ea7-d8233ef967d7">

    Так как эти ресурсы находились в head без async/defer, они являются блокирующими.
    
## Performance

* измерить время в миллисекундах от начала навигации до событий FP, FCP, LCP, DCL, Load

  ![alt text](https://github.com/aly0na27/shri_tooling/blob/master/screenshots/performance_1.png?raw=true)

  ![alt text](https://github.com/aly0na27/shri_tooling/blob/master/screenshots/performance_2.png?raw=true)

  `1) От начала навигации до FP прошло 648.5 мс.`

     ![alt text](https://github.com/aly0na27/shri_tooling/blob/master/screenshots/fp.png?raw=true)

  `2) От начала навигации до FCP прошло 648.5 мс.`

     ![alt text](https://github.com/aly0na27/shri_tooling/blob/master/screenshots/fcp.png?raw=true)

  `3) От начала навигации до LCP прошло 1875.2 мс`

     ![alt text](https://github.com/aly0na27/shri_tooling/blob/master/screenshots/lcp.png?raw=true)

  `4) От начала навигации до DCL прошло 388.2 мс.`

     ![alt text](https://github.com/aly0na27/shri_tooling/blob/master/screenshots/dcl.png?raw=true)

  `5) От начала навигации до L прошло 30129.1 мс.`

     ![alt text](https://github.com/aly0na27/shri_tooling/blob/master/screenshots/l.png?raw=true)

* определить, на каком DOM-элементе происходит LCP

  LCP происходит на DOM-елементе `<img>`:
  
  ![alt text](https://github.com/aly0na27/shri_tooling/blob/master/screenshots/lcp_dom_element.png?raw=true)

* измерить, сколько времени в миллисекундах тратится на разные этапы обработки документа (Loading, Scripting, Rendering, Painting)

   ![alt text](https://github.com/aly0na27/shri_tooling/blob/master/screenshots/process_stages.png?raw=true)

   - На этап Loading тратится 11ms.
   - На этап Scripting тратится 1283ms.
   - На этап Redndering тратится 291ms.
   - На этап Painting тратится 238ms.
  
## Coverage

  * сохранить скриншот вкладки после загрузки страницы:

    ![alt text](https://github.com/aly0na27/shri_tooling/blob/master/screenshots/coverage.png?raw=true)
    
  * измерить в килобайтах объём неиспользованного CSS в ходе загрузки страницы - 45.3 kB

     ![alt text](https://github.com/aly0na27/shri_tooling/blob/master/screenshots/coverage_css.png?raw=true)
    
  * измерить в килобайтах объём неиспользованного JS в ходе загрузки страницы - 5900 kB

     ![alt text](https://github.com/aly0na27/shri_tooling/blob/master/screenshots/coverage_js.png?raw=true)

## Доп. задание

  * Включить замедление CPU 4x slowdown и эмуляцию сети Slow 3G. Сделать такой же анализ. (Поскольку с включенными настройками во вкладке Network и
    Coverage ничего не поменялось, ниже приложу анализ только вкладки Performance)
    
### Performance

* измерить время в миллисекундах от начала навигации до событий FP, FCP, LCP, DCL, Load

  <img width="703" alt="Снимок экрана 2024-06-21 в 15 50 18" src="https://github.com/aly0na27/shri_tooling/assets/120110608/fb06b82e-6c5e-45ba-b4da-2510d3a6c64e">

   `1) От начала навигации до FP прошло 26526.5 мс.`

  <img width="331" alt="Снимок экрана 2024-06-21 в 15 54 30" src="https://github.com/aly0na27/shri_tooling/assets/120110608/76a229c9-d01f-429f-b568-b96e3102dfe3">

  `2) От начала навигации до FCP прошло 26526.5  мс.`

  <img width="324" alt="Снимок экрана 2024-06-21 в 15 54 51" src="https://github.com/aly0na27/shri_tooling/assets/120110608/46035b12-67cb-4518-8210-97ee53edd588">

  `3) От начала навигации до LCP прошло 26526.5 мс`

  <img width="333" alt="Снимок экрана 2024-06-21 в 15 55 47" src="https://github.com/aly0na27/shri_tooling/assets/120110608/961a7325-71f8-4a20-9c72-a6629320abef">

  `4) От начала навигации до DCL прошло 38308.1 мс.`

  <img width="368" alt="Снимок экрана 2024-06-21 в 15 56 08" src="https://github.com/aly0na27/shri_tooling/assets/120110608/c5fb0e44-9a66-4368-a265-dc1fcad51fc0">

  `5) От начала навигации до L прошло 43159.3 мс.`

  <img width="350" alt="Снимок экрана 2024-06-21 в 15 56 26" src="https://github.com/aly0na27/shri_tooling/assets/120110608/cf2a8433-f8bf-4356-8211-922bf9eb4577">


* определить, на каком DOM-элементе происходит LCP

  LCP происходит на DOM-елементе `<img>`:
  
  <img width="759" alt="Снимок экрана 2024-06-21 в 15 59 18" src="https://github.com/aly0na27/shri_tooling/assets/120110608/79b2cea2-471c-48c7-93f6-6112ce784354">

* измерить, сколько времени в миллисекундах тратится на разные этапы обработки документа (Loading, Scripting, Rendering, Painting)

  <img width="378" alt="Снимок экрана 2024-06-21 в 16 01 20" src="https://github.com/aly0na27/shri_tooling/assets/120110608/572edde0-a82c-4a4c-92d9-7bc9bf321af6">

  - На этап Loading тратится 19ms.
  - На этап Scripting тратится 1929ms.
  - На этап Redndering тратится 61ms.
  - На этап Painting тратится 9ms.

  [Ссылка на файл профиль загрузки](https://disk.yandex.ru/d/fUNrZTImCPL0Xw)
  
