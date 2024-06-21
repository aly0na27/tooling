# Использование Chrome DevTools

Сделать в Chrome DevTools анализ открытия страницы https://www.rigla.ru.

## Network


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

