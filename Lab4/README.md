## Практическое задание 4
## Медведев Александр БИСО-02-20

## Цель работы
1. Зекрепить практические навыки использования языка программирования R для обработки данных
2. Закрепить знания основных функций обработки данных экосистемы tidyverse языка R
3. Закрепить навыки исследования метаданных DNS трафика

## Исходные данные

ОС Windows

tidyverse

RStudio

## Задания

Подготовка данных

1. Импортируйте данные DNS
2. Добавьте пропущенные данные о структуре данных (назначении столбцов)
3. Преобразуйте данные в столбцах в нужный формат

## Ход работы
Импортируем dplyr
```R
library(dplyr)
```
```R
Присоединяю пакет: ‘dplyr’

Следующие объекты скрыты от ‘package:stats’:

    filter, lag

Следующие объекты скрыты от ‘package:base’:

    intersect, setdiff, setequal, union
```

```R
install.packages("tidyverse")
library(tidyverse)
```
```R
── Attaching core tidyverse packages ─────────
✔ forcats   1.0.0     ✔ readr     2.1.4
✔ ggplot2   3.4.4     ✔ stringr   1.5.0
✔ lubridate 1.9.3     ✔ tibble    3.2.1
✔ purrr     1.0.2     ✔ tidyr     1.3.0
── Conflicts ──────── tidyverse_conflicts() ──
✖ dplyr::filter() masks stats::filter()
✖ dplyr::lag()    masks stats::lag()
ℹ Use the conflicted package to force all conflicts to become errors
Предупреждения:
1: пакет ‘tidyverse’ был собран под R версии 4.3.2 
2: пакет ‘ggplot2’ был собран под R версии 4.3.2 
3: пакет ‘tidyr’ был собран под R версии 4.3.2 
4: пакет ‘readr’ был собран под R версии 4.3.2 
5: пакет ‘forcats’ был собран под R версии 4.3.2
```

1. Импортируйте данные DNS

```R
data = read.csv("dns.log", header = FALSE, sep="\t", encoding = "UTF-8")
```

2. Добавьте пропущенные данные о структуре данных (назначении столбцов)
```R
header = read.csv("header.csv", encoding = "UTF-8", skip = 1, header = FALSE, sep = ',')
```
```R
colnames(data) = header
```

3. Преобразуйте данные в столбцах в нужный формат
