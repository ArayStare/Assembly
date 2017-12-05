library(foreign)
library(dplyr)
library(ggplot2)
library(readxl)

kowebs <- read.spss(file='./kowebs/Koweps_hpwc11_2016_beta1.sav', to.data.frame = T)
ko2016 <- kowebs

ko2016 <- rename(
    ko2016,
    gender = h11_g3,
    birth = h11_g4,
    marriage = h11_g10,
    religion = h11_g11,
    reg_income = h11_inc2,
    tmp_income = h11_inc3,
    biz_field = h11_eco8,
    job_field = h11_eco9,
    region = h11_reg7
)
ko2016$age <- 2016 - ko2016$birth + 1

analysis.df <- ko2016 %>% select(gender, reg_income)

res <- analysis.df %>% filter(!is.na(reg_income)) %>% group_by(gender) %>% summarise(mean_reg_income=mean(reg_income))
ggplot(data=res, aes(x=gender, y=mean_reg_income)) + geom_line()
