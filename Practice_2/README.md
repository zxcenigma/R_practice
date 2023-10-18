> library(dplyr)  #Подключаем dplyr


> starwars  #Открываем базу


# 1. Сколько строк в датафрейме

> starwars %>% nrow()


# 2. Как просмотреть примерный вид датафрейма?

 > starwars %>% ncol()


# 3. Как просмотреть примерный вид датафрейма?

> starwars %>% glimpse()


# 4. Сколько уникальных рас персонажей (species) представлено в данных?

> count(distinct(starwars, species))


# 5. Найти самого высокого персонажа.

> starwars[order(desc(starwars$height)), ]

# 6. Найти всех персонажей ниже 170

> print(filter(starwars, height < 170))


# 7. Подсчитать ИМТ (индекс массы тела) для всех персонажей. ИМТ подсчитать по формуле 𝐼 = 𝑚/ℎ2 , где 𝑚-- масса (weight), а ℎ -- рост (height).
> starwars %>% mutate("IMT" = mass/(height**2)) %>% select(name, IMT)

# 8. Найти 10 самых “вытянутых” персонажей. “Вытянутость” оценить по отношению массы (mass) к росту (height) персонажей.
> starwars %>% mutate("Вытянутость" = mass/height) %>% arrange(desc(Вытянутость)) %>% slice(1:10) %>% select(name,Вытянутость)

# 9. Найти средний возраст персонажей каждой расы вселенной Звездных войн
> starwars %>% group_by(species) %>% summarise(average_age = mean(birth_year, na.rm = TRUE))

