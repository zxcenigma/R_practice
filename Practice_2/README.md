> library(dplyr)  #Подключаем dplyr


> starwars  #Открываем базу
# A tibble: 87 × 14
   name     height  mass hair_color skin_color eye_color birth_year sex   gender
   <chr>     <int> <dbl> <chr>      <chr>      <chr>          <dbl> <chr> <chr> 
 1 Luke Sk…    172    77 blond      fair       blue            19   male  mascu…
 2 C-3PO       167    75 <NA>       gold       yellow         112   none  mascu…
 3 R2-D2        96    32 <NA>       white, bl… red             33   none  mascu…
 4 Darth V…    202   136 none       white      yellow          41.9 male  mascu…
 5 Leia Or…    150    49 brown      light      brown           19   fema… femin…
 6 Owen La…    178   120 brown, gr… light      blue            52   male  mascu…
 7 Beru Wh…    165    75 brown      light      blue            47   fema… femin…
 8 R5-D4        97    32 <NA>       white, red red             NA   none  mascu…
 9 Biggs D…    183    84 black      light      brown           24   male  mascu…
10 Obi-Wan…    182    77 auburn, w… fair       blue-gray       57   male  mascu…


# 1. Сколько строк в датафрейме
> starwars %>% nrow()
[1] 87

# 2. > starwars %>% ncol()
[1] 14

# 3. Как просмотреть примерный вид датафрейма?
> starwars %>% glimpse()
Rows: 87
Columns: 14
$ name       <chr> "Luke Skywalker", "C-3PO", "R2-D2", "Darth Vader", "Leia Organa", "Owen Lars", "Beru Whitesun lars", "R5-D4", "Biggs Darklighter", "Obi-Wan Kenobi", "Anakin Skywalker", "Wil…
$ height     <int> 172, 167, 96, 202, 150, 178, 165, 97, 183, 182, 188, 180, 228, 180, 173, 175, 170, 180, 66, 170, 183, 200, 190, 177, 175, 180, 150, NA, 88, 160, 193, 191, 170, 196, 224, 206…
$ mass       <dbl> 77.0, 75.0, 32.0, 136.0, 49.0, 120.0, 75.0, 32.0, 84.0, 77.0, 84.0, NA, 112.0, 80.0, 74.0, 1358.0, 77.0, 110.0, 17.0, 75.0, 78.2, 140.0, 113.0, 79.0, 79.0, 83.0, NA, NA, 20.…
$ hair_color <chr> "blond", NA, NA, "none", "brown", "brown, grey", "brown", NA, "black", "auburn, white", "blond", "auburn, grey", "brown", "brown", NA, NA, "brown", "brown", "white", "grey",…
$ skin_color <chr> "fair", "gold", "white, blue", "white", "light", "light", "light", "white, red", "light", "fair", "fair", "fair", "unknown", "fair", "green", "green-tan, brown", "fair", "fa…
$ eye_color  <chr> "blue", "yellow", "red", "yellow", "brown", "blue", "blue", "red", "brown", "blue-gray", "blue", "blue", "blue", "brown", "black", "orange", "hazel", "blue", "brown", "yello…
$ birth_year <dbl> 19.0, 112.0, 33.0, 41.9, 19.0, 52.0, 47.0, NA, 24.0, 57.0, 41.9, 64.0, 200.0, 29.0, 44.0, 600.0, 21.0, NA, 896.0, 82.0, 31.5, 15.0, 53.0, 31.0, 37.0, 41.0, 48.0, NA, 8.0, NA…
$ sex        <chr> "male", "none", "none", "male", "female", "male", "female", "none", "male", "male", "male", "male", "male", "male", "male", "hermaphroditic", "male", "male", "male", "male",…
$ gender     <chr> "masculine", "masculine", "masculine", "masculine", "feminine", "masculine", "feminine", "masculine", "masculine", "masculine", "masculine", "masculine", "masculine", "mascu…
$ homeworld  <chr> "Tatooine", "Tatooine", "Naboo", "Tatooine", "Alderaan", "Tatooine", "Tatooine", "Tatooine", "Tatooine", "Stewjon", "Tatooine", "Eriadu", "Kashyyyk", "Corellia", "Rodia", "N…
$ species    <chr> "Human", "Droid", "Droid", "Human", "Human", "Human", "Human", "Droid", "Human", "Human", "Human", "Human", "Wookiee", "Human", "Rodian", "Hutt", "Human", "Human", "Yoda's s…
$ films      <list> <"The Empire Strikes Back", "Revenge of the Sith", "Return of the Jedi", "A New Hope", "The Force Awakens">, <"The Empire Strikes Back", "Attack of the Clones", "The Phanto…
$ vehicles   <list> <"Snowspeeder", "Imperial Speeder Bike">, <>, <>, <>, "Imperial Speeder Bike", <>, <>, <>, <>, "Tribubble bongo", <"Zephyr-G swoop bike", "XJ-6 airspeeder">, <>, "AT-ST", <…
$ starships  <list> <"X-wing", "Imperial shuttle">, <>, <>, "TIE Advanced x1", <>, <>, <>, <>, "X-wing", <"Jedi starfighter", "Trade Federation cruiser", "Naboo star skiff", "Jedi Interceptor"…

№4. Сколько уникальных рас персонажей (species) представлено в данных?
> count(distinct(starwars, species))
# A tibble: 1 × 1
      n
  <int>
1    38

#5. Найти самого высокого персонажа.
> starwars[order(desc(starwars$height)), ]
# A tibble: 87 × 14
   name         height  mass hair_color skin_color   eye_color     birth_year sex    gender    homeworld species  films     vehicles  starships
   <chr>         <int> <dbl> <chr>      <chr>        <chr>              <dbl> <chr>  <chr>     <chr>     <chr>    <list>    <list>    <list>   
 1 Yarael Poof     264    NA none       white        yellow              NA   male   masculine Quermia   Quermian <chr [1]> <chr [0]> <chr [0]>
 2 Tarfful         234   136 brown      brown        blue                NA   male   masculine Kashyyyk  Wookiee  <chr [1]> <chr [0]> <chr [0]>
 3 Lama Su         229    88 none       grey         black               NA   male   masculine Kamino    Kaminoan <chr [1]> <chr [0]> <chr [0]>
 4 Chewbacca       228   112 brown      unknown      blue               200   male   masculine Kashyyyk  Wookiee  <chr [5]> <chr [1]> <chr [2]>
 5 Roos Tarpals    224    82 none       grey         orange              NA   male   masculine Naboo     Gungan   <chr [1]> <chr [0]> <chr [0]>
 6 Grievous        216   159 none       brown, white green, yellow       NA   male   masculine Kalee     Kaleesh  <chr [1]> <chr [1]> <chr [1]>
 7 Taun We         213    NA none       grey         black               NA   female feminine  Kamino    Kaminoan <chr [1]> <chr [0]> <chr [0]>
 8 Rugor Nass      206    NA none       green        orange              NA   male   masculine Naboo     Gungan   <chr [1]> <chr [0]> <chr [0]>
 9 Tion Medon      206    80 none       grey         black               NA   male   masculine Utapau    Pau'an   <chr [1]> <chr [0]> <chr [0]>
10 Darth Vader     202   136 none       white        yellow              41.9 male   masculine Tatooine  Human    <chr [4]> <chr [0]> <chr [1]>
# ℹ 77 more rows
# ℹ Use `print(n = ...)` to see more rows

#6. Найти всех персонажей ниже 170
> print(filter(starwars, height < 170))
# A tibble: 23 × 14
   name                  height  mass hair_color skin_color  eye_color birth_year sex    gender    homeworld species        films     vehicles  starships
   <chr>                  <int> <dbl> <chr>      <chr>       <chr>          <dbl> <chr>  <chr>     <chr>     <chr>          <list>    <list>    <list>   
 1 C-3PO                    167    75 <NA>       gold        yellow           112 none   masculine Tatooine  Droid          <chr [6]> <chr [0]> <chr [0]>
 2 R2-D2                     96    32 <NA>       white, blue red               33 none   masculine Naboo     Droid          <chr [7]> <chr [0]> <chr [0]>
 3 Leia Organa              150    49 brown      light       brown             19 female feminine  Alderaan  Human          <chr [5]> <chr [1]> <chr [0]>
 4 Beru Whitesun lars       165    75 brown      light       blue              47 female feminine  Tatooine  Human          <chr [3]> <chr [0]> <chr [0]>
 5 R5-D4                     97    32 <NA>       white, red  red               NA none   masculine Tatooine  Droid          <chr [1]> <chr [0]> <chr [0]>
 6 Yoda                      66    17 white      green       brown            896 male   masculine <NA>      Yoda's species <chr [5]> <chr [0]> <chr [0]>
 7 Mon Mothma               150    NA auburn     fair        blue              48 female feminine  Chandrila Human          <chr [1]> <chr [0]> <chr [0]>
 8 Wicket Systri Warrick     88    20 brown      brown       brown              8 male   masculine Endor     Ewok           <chr [1]> <chr [0]> <chr [0]>
 9 Nien Nunb                160    68 none       grey        black             NA male   masculine Sullust   Sullustan      <chr [1]> <chr [0]> <chr [1]>
10 Watto                    137    NA black      blue, grey  yellow            NA male   masculine Toydaria  Toydarian      <chr [2]> <chr [0]> <chr [0]>
# ℹ 13 more rows
# ℹ Use `print(n = ...)` to see more rows

#7.
> starwars %>% mutate("IMT" = mass/(height**2)) %>% select(name, IMT)
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
> 
