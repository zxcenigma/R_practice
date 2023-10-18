> library(dplyr)  #Подключаем dplyr


> starwars  #Открываем базу


# 1. Сколько строк в датафрейме
> starwars %>% nrow()
[1] 87

# 2. Как просмотреть примерный вид датафрейма?
 > starwars %>% ncol()


# 3. Как просмотреть примерный вид датафрейма?
> starwars %>% glimpse()


№4. Сколько уникальных рас персонажей (species) представлено в данных?
> count(distinct(starwars, species))


#5. Найти самого высокого персонажа.
> starwars[order(desc(starwars$height)), ]

#6. Найти всех персонажей ниже 170
> print(filter(starwars, height < 170))


#7.
> starwars %>% mutate("IMT" = mass/(height**2)) %>% select(name, IMT)

