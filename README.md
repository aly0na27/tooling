# Использование Chrome DevTools

Сделать в Chrome DevTools анализ открытия страницы https://www.rigla.ru.

## Network

* найти неоптимальные места:

  - дублирование ресурсов:
 
    <img width="922" alt="Снимок экрана 2024-06-22 в 10 03 10" src="https://github.com/aly0na27/shri_tooling/assets/120110608/296dd66a-bbf0-4de3-a9b8-20633f4eb821">

    <img width="921" alt="Снимок экрана 2024-06-22 в 10 04 38" src="https://github.com/aly0na27/shri_tooling/assets/120110608/6093519d-a02b-424d-8383-4896d4e449eb">

    <img width="922" alt="Снимок экрана 2024-06-22 в 10 06 17" src="https://github.com/aly0na27/shri_tooling/assets/120110608/8fd83287-b0f6-4adc-ad07-354ef58171e9">

    <img width="620" alt="Снимок экрана 2024-06-22 в 10 07 03" src="https://github.com/aly0na27/shri_tooling/assets/120110608/b7ff90e4-c53a-443c-96a2-c8a22fc54df5">

    <img width="805" alt="Снимок экрана 2024-06-22 в 10 09 18" src="https://github.com/aly0na27/shri_tooling/assets/120110608/f5daa6eb-5f0b-4e69-9a1f-023a59b5709d">
    
    <img width="936" alt="Снимок экрана 2024-06-22 в 10 12 12" src="https://github.com/aly0na27/shri_tooling/assets/120110608/dc5e6db9-1b21-4fca-8440-8a6e0891d367">

  - лишний размер ресурса:
  
    <img width="797" alt="Снимок экрана 2024-06-22 в 10 02 01" src="https://github.com/aly0na27/shri_tooling/assets/120110608/0e830957-814e-45e4-8252-fffce75c3ffa">

    Картники можно было бы сжать.

  - медленно загружающиеся ресурсы:

    <img width="958" alt="Снимок экрана 2024-06-22 в 10 00 07" src="https://github.com/aly0na27/shri_tooling/assets/120110608/112c23a1-a241-46cf-bcc3-4b366224084f">

  - ресурсы, блокирующие загрузку:
 
    Ресурсы, которые загружаются до красной линии (Load event) блокируют загрузку страницы

    <img width="1440" alt="Снимок экрана 2024-06-22 в 09 55 30" src="https://github.com/aly0na27/shri_tooling/assets/120110608/f149c593-20c2-4556-8121-918e6967c54f">

  - ресурсы, блокирующие рендеринг:

    Ресурсы, которые загружаются до синей линии (First paint) блокируют рендеринг

    <img width="1440" alt="Снимок экрана 2024-06-22 в 10 40 19" src="https://github.com/aly0na27/shri_tooling/assets/120110608/b9c399e1-5da6-4e90-9a9b-d557182f867e">

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
  
