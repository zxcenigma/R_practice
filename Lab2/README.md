## Практическое задание 2

## Медведев Александр БИСО-02-20
##   Цель работы
1.Развить практические навыки использования языка программирования R для обработки данных

2.Закрепить знания базовых типов данных языка R

3.Научиться работать с пакетом dlpyr

## Исходные данные

ОС Windows

Пакет starwars

RStudio

## Ход работы
Подключаем dplyr
```R
library(dplyr)

Присоединяю пакет: ‘dplyr’

Следующие объекты скрыты от ‘package:stats’:

    filter, lag

Следующие объекты скрыты от ‘package:base’:

    intersect, setdiff, setequal, union  
```
Открываем базу
```R
starwars
```

1. Сколько строк в датафрейме
```R
starwars %>% nrow()

[1] 87
```

2. Как просмотреть примерный вид датафрейма?
```R
starwars %>% ncol()

[1] 14
```

3. Как просмотреть примерный вид датафрейма?
```R
starwars %>% glimpse()

Rows: 87
Columns: 14
$ name       <chr> "Luke Skywalker", "C-3PO", "R2-D2", "Darth Vader", "Leia Organa", "Owen Lars",…
$ height     <int> 172, 167, 96, 202, 150, 178, 165, 97, 183, 182, 188, 180, 228, 180, 173, 175, …
$ mass       <dbl> 77.0, 75.0, 32.0, 136.0, 49.0, 120.0, 75.0, 32.0, 84.0, 77.0, 84.0, NA, 112.0,…
$ hair_color <chr> "blond", NA, NA, "none", "brown", "brown, grey", "brown", NA, "black", "auburn…
$ skin_color <chr> "fair", "gold", "white, blue", "white", "light", "light", "light", "white, red…
$ eye_color  <chr> "blue", "yellow", "red", "yellow", "brown", "blue", "blue", "red", "brown", "b…
$ birth_year <dbl> 19.0, 112.0, 33.0, 41.9, 19.0, 52.0, 47.0, NA, 24.0, 57.0, 41.9, 64.0, 200.0, …
$ sex        <chr> "male", "none", "none", "male", "female", "male", "female", "none", "male", "m…
$ gender     <chr> "masculine", "masculine", "masculine", "masculine", "feminine", "masculine", "…
$ homeworld  <chr> "Tatooine", "Tatooine", "Naboo", "Tatooine", "Alderaan", "Tatooine", "Tatooine…
$ species    <chr> "Human", "Droid", "Droid", "Human", "Human", "Human", "Human", "Droid", "Human…
$ films      <list> <"The Empire Strikes Back", "Revenge of the Sith", "Return of the Jedi", "A N…
$ vehicles   <list> <"Snowspeeder", "Imperial Speeder Bike">, <>, <>, <>, "Imperial Speeder Bike"…
$ starships  <list> <"X-wing", "Imperial shuttle">, <>, <>, "TIE Advanced x1", <>, <>, <>, <>, "X…
```

4. Сколько уникальных рас персонажей (species) представлено в данных?
```R
count(distinct(starwars, species))

# A tibble: 1 × 1
      n
  <int>
1    38
```

5. Найти самого высокого персонажа.
```R
starwars %>% filter(height == max(height, na.rm = TRUE))

# A tibble: 1 × 14
  name       height  mass hair_color skin_color eye_color birth_year sex   gender homeworld species
  <chr>       <int> <dbl> <chr>      <chr>      <chr>          <dbl> <chr> <chr>  <chr>     <chr>  
1 Yarael Po…    264    NA none       white      yellow            NA male  mascu… Quermia   Quermi…
# ℹ 3 more variables: films <list>, vehicles <list>, starships <list>
```
6. Найти всех персонажей ниже 170
```R
print(filter(starwars, height < 170))

# A tibble: 23 × 14
   name      height  mass hair_color skin_color eye_color birth_year sex   gender homeworld species
   <chr>      <int> <dbl> <chr>      <chr>      <chr>          <dbl> <chr> <chr>  <chr>     <chr>  
 1 C-3PO        167    75 NA         gold       yellow           112 none  mascu… Tatooine  Droid  
 2 R2-D2         96    32 NA         white, bl… red               33 none  mascu… Naboo     Droid  
 3 Leia Org…    150    49 brown      light      brown             19 fema… femin… Alderaan  Human  
 4 Beru Whi…    165    75 brown      light      blue              47 fema… femin… Tatooine  Human  
 5 R5-D4         97    32 NA         white, red red               NA none  mascu… Tatooine  Droid  
 6 Yoda          66    17 white      green      brown            896 male  mascu… NA        Yoda's…
 7 Mon Moth…    150    NA auburn     fair       blue              48 fema… femin… Chandrila Human  
 8 Wicket S…     88    20 brown      brown      brown              8 male  mascu… Endor     Ewok   
 9 Nien Nunb    160    68 none       grey       black             NA male  mascu… Sullust   Sullus…
10 Watto        137    NA black      blue, grey yellow            NA male  mascu… Toydaria  Toydar…
# ℹ 13 more rows
# ℹ 3 more variables: films <list>, vehicles <list>, starships <list>
# ℹ Use `print(n = ...)` to see more rows
```

7. Подсчитать ИМТ (индекс массы тела) для всех персонажей. ИМТ подсчитать по формуле 𝐼 = 𝑚/ℎ2 , где 𝑚-- масса (weight), а ℎ -- рост (height).
```R
starwars %>% mutate("IMT" = mass/(height**2)) %>% select(name, IMT)

# A tibble: 87 × 2
   name                   IMT
   <chr>                <dbl>
 1 Luke Skywalker     0.00260
 2 C-3PO              0.00269
 3 R2-D2              0.00347
 4 Darth Vader        0.00333
 5 Leia Organa        0.00218
 6 Owen Lars          0.00379
 7 Beru Whitesun lars 0.00275
 8 R5-D4              0.00340
 9 Biggs Darklighter  0.00251
10 Obi-Wan Kenobi     0.00232
# ℹ 77 more rows
# ℹ Use `print(n = ...)` to see more rows
```
8. Найти 10 самых “вытянутых” персонажей. “Вытянутость” оценить по отношению массы (mass) к росту (height) персонажей.
```R
starwars %>% mutate("Вытянутость" = mass/height) %>% arrange(desc(Вытянутость)) %>% slice(1:10) %>% select(name,Вытянутость)

# A tibble: 10 × 2
   name                  Вытянутость
   <chr>                       <dbl>
 1 Jabba Desilijic Tiure       7.76 
 2 Grievous                    0.736
 3 IG-88                       0.7  
 4 Owen Lars                   0.674
 5 Darth Vader                 0.673
 6 Jek Tono Porkins            0.611
 7 Bossk                       0.595
 8 Tarfful                     0.581
 9 Dexter Jettster             0.515
10 Chewbacca                   0.491
```
9. Найти средний возраст персонажей каждой расы вселенной Звездных войн
```R
starwars %>% group_by(species) %>% summarise(average_age = mean(birth_year, na.rm = TRUE))

# A tibble: 38 × 2
   species   average_age
   <chr>           <dbl>
 1 Aleena          NaN  
 2 Besalisk        NaN  
 3 Cerean           92  
 4 Chagrian        NaN  
 5 Clawdite        NaN  
 6 Droid            53.3
 7 Dug             NaN  
 8 Ewok              8  
 9 Geonosian       NaN  
10 Gungan           52  
```

10. Найти самый распространенный цвет глаз персонажей вселенной Звездных войн.

```R
starwars %>% count(eye_color) %>% filter(n == max(n))

A tibble: 1 × 2
  eye_color     n
  <chr>     <int>
1 brown        21
```

11. Подсчитать среднюю длину имени в каждой расе вселенной Звездных войн.

```R
starwars %>% group_by(species) %>% summarise(avg_lenth = mean(nchar(name)))

# A tibble: 38 × 2
   species   avg_lenth
   <chr>         <dbl>
 1 Aleena        13   
 2 Besalisk      15   
 3 Cerean        12   
 4 Chagrian      10   
 5 Clawdite      10   
 6 Droid          4.83
 7 Dug            7   
 8 Ewok          21   
 9 Geonosian     17   
10 Gungan        11.7 
# ℹ 28 more rows
# ℹ Use `print(n = ...)` to see more rows
```
## Оценка результатов

Был изучен пакет dplyr. Работа проделана с ипользованием языка R в RStudio

## Вывод

Ознакомлен с базовыми командами R и работой с пакетом starwars
