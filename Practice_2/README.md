> library(dplyr)  #Подключаем dplyr


> starwars  #Открываем базу


# 1. Сколько строк в датафрейме

starwars %>% nrow()


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


#7. Подсчитать ИМТ (индекс массы тела) для всех персонажей. ИМТ подсчитать по формуле 𝐼 = 𝑚/ℎ2 , где 𝑚-- масса (weight), а ℎ -- рост (height).
> starwars %>% mutate("IMT" = mass/(height**2)) %>% select(name, IMT)

