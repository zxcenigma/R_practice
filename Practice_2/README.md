> library(dplyr)  #Подключаем dplyr


> starwars  #Открываем базу


# 1. Сколько строк в датафрейме
> starwars %>% nrow()
[1] 87

# 2. > starwars %>% ncol()
[1] 14

# 3. Как просмотреть примерный вид датафрейма?
> starwars %>% glimpse()


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
