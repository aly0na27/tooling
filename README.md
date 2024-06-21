# Использование Chrome DevTools

Сделать в Chrome DevTools анализ открытия страницы https://www.rigla.ru.

## Network

* найти неоптимальные места:

  - дублирование ресурсов:
 
    <img width="631" alt="Снимок экрана 2024-06-21 в 11 22 16" src="https://github.com/aly0na27/shri_tooling/assets/120110608/b2c9dd7d-28c4-44b1-a920-783cd8758a08">

    
    <img width="500" alt="Снимок экрана 2024-06-21 в 14 33 23" src="https://github.com/aly0na27/shri_tooling/assets/120110608/706a6d9a-c870-4abc-8d71-38250e6bf9f1">

  - лишний размер ресурса:
 
  - медленно загружающиеся ресурсы:
 
  - ресурсы, блокирующие загрузку


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
